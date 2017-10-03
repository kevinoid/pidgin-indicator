pidgin-indicator: AppIndicator/KStatusNotifierItem Plugin for Pidgin
====================================================================

This plugins provides an AppIndicator/KStatusNotifierItem for pidgin. All
the current desktop environments are moving away from XEmbed based systray
icons, and that is the only kind of icon that Pidigin provides out of the
box.

Ubuntu Unity (now deprecated) and KDE Plasma provide native support for
AppIndicators/KStatusNotifierItems, and a gnome-shell extension provides
support in GNOME (and this extension is installed by default in Ubuntu
starting in 17.10).

I originally developed this plugin when Ubuntu Unity dropped support for
legacy systray icons and I found the official alternative - their Messaging
indicator - to be inadequate. It consolidated status from multiple
applications, and I found it to be much less usable than the original Pidgin
tray icon. Ultimately, with the move from Unity to GNOME in Ubuntu, this
Messaging indicator has been deprecated so there's even more reason for
this plugin to exist.

Functionality
-------------

The indicator provides all the same functionality as the original tray icon,
but not in exactly the same way.

* The 'smart' click behaviour that either shows the buddy list or unread
  messages is mapped to the appindicator 'secondary action'.
  * This is because indicators do not get to control what happens on clicks.
    The 'secondary action' is intended to be something done instead of showing
    the menu. It is up to the indicator provider in the destkop environment
    to decide what action triggers the secondary action, if at all.
  * In Unity, a middle-click triggers the secondary action
  * In gnome-shell using the AppIndicator/KStatusNotifierItem extension,
    very recent versions now support the same middle-click behaviour as in
    Unity. This extension is installed by default with Ubuntu 17.10.
  * I'm not sure what KDE Plasma does. Some people have said it also
    does secondary activation on a middle click, and some say a left click.
    I think this may have changed over successive releases.
* As the indicator is a separate process from pidgin itself, there are
  sometimes conflicts with Focus Stealing Prevention when you use the
  indicator to go to unread messages. You may need to disable FSP for
  Pidgin to get around this.
* Due to how indicators work, the secondary action must also be a menu
  item, so it's the new Show/Hide item at the top of the menu.
* Due to indicator limitations, some of the special icons can't be shown
  next to menu items any more.

Required packages
-----------------

Runtime:
* pidgin 2.10.x
* libappindicator-0.1

Buildtime:
* build-essential
* pidgin-dev
* libappindicator-dev
* autoconf
* automake
* libtool
* intltool

The ``configure`` script can be generated by running:
* autoreconf -i

Binary Package Repositories
---------------------------

These repositories are managed by third parties, so I can't take credit
or blame for them. But I can definitely thank them for their efforts!

* Ubuntu: https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8
* Fedora (Official): http://koji.fedoraproject.org/koji/packageinfo?packageID=22135
