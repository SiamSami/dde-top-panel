# DDE Top Panel

【中文请看】：[Deepin 论坛](https://bbs.deepin.org/forum.php?mod=viewthread&tid=195128&extra=)

Top panel for deepin desktop environment v20.

This is a modification of dde-dock for top panel. Comparing to dde-dock, it:
* remove the launcher, show desktop, multi tasking, and application icons
* full support for dde-dock plugins and tray
* remove lots of unnecessary things so it is just a top panel. It is fixed to the top of the screen, and there is no way to change that.
* separate plugin config gsetting path `/com/deepin/dde/toppanel`
* different plugin directories: `/usr/lib/dde-top-panel/plugins` and `~/.local/lib/dde-top-panel/plugins`

> Still in development.

## Features

* show window title on top panel
* show title buttons on top panel when current window maximized
* double click on empty area on top panel will maximize current window
* coping with `~/.config/kwinrc` can remove the window title bar when maximized
* support multi monitors

Know issues:
* it seems impossible to set the minimum height of the top panel less than 40, or there will be abnormal left and right spacing/margin around the plugin widgets. `setMargins` and `setSpacing` seem not work.
* panels on **non-primary monitors** only have the window title function. The plugins can not work on them. `It is not an issue` because the `QPluginLoader` can only create one instance from one plugin file. So the panel cannot create as many plugin widgets as the panels. Still trying to add the plugin back to all panels

## Screenshot

![](./screenshots/toppanel1.png)
![](./screenshots/toppanel2.png)
![](./screenshots/demo.gif)

## How to run

1. download zip from release page and unzip it
1. cp `*.xml` to `/usr/share/glib-2.0/schemas`, and run `sudo glib-compile-schemas /usr/share/glib-2.0/schemas`
2. run `./dde-top-panel`
3. for removing the title bar of maximized windows, make sure your `~/.config/kwinrc` contains items below, then logout.
```shell script
[Windows]
BorderlessMaximizedWindows=true
```
4. If you want to use plugins on top panel, just copy the plugin files to `~/.local/lib/dde-top-panel/plugins`. For example, if you want to get tray icons on top panel, just `cp /usr/lib/dde-dock/plugins/libtray.so ~/.local/lib/dde-top-panel/plugins`
