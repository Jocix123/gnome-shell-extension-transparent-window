# gnome-shell-extension-transparent-window
## Summary
The extension will change the opacity of window through simple mouse/keyboard operation.

## Usage
Move mouse cursor into the window you want to change, hover over the window, hold Alt key(or customized modifier key) and scroll to make the window transparent. 

## Environment
Tested on:
1. Ubuntu 18.04 Gnome 3.28.
2. Ubuntu 20.04 Gnome 3.36.

## Motivation
Transparent window is a very useful feature that can improve work effeciency. It is implemented by software on multiple platforms. Even other Linux desktops like Ubuntu Unity can use Compiz to achieve this goal. There is no reason Gnome doesn't have this feature.

## Method
Use GdkKeymap to monitor the hotkeys. When the modifier key is pressed, create an overlay actor that will monitor the scroll event. Once the scroll event is detected, modify the opacity of the mouse hovered window.

## Limits
In gnome-shell I didn't find a way to monitor the scroll event for each window actor, so I can only create an overlay that is on top of all windows. Thus Alt+drag won't work if you toggle on this extension. Feel free to contact me or make a commit if you have a better idea to fix this.

## Background knowledge
### Clutter
#### Overview
Clutter is a GObject-based **graphics library** for creating user interfaces.
#### Actor
Actor is a basic element of Clutter. It encapsulates the postion/size/event of a node in the scene graph. In short, it is the abstraction of a window.
### Mutter
Mutter is the default **window manager** of GNOME3 which uses Clutter as library.
#### Tips
Mutter is a portmanteau of "Metacity"(The deprecated window manger of GNOME2) and "Clutter".
### GNOME Shell
GNOME Shell itself is a plugin of Mutter. This means when devloping shell extension, we are building plugin on plugin lol.

## Debugging
### Looking Glass
Looking Glass is GNOME Shell's integrated debugger and inspector tool. It would be helpful to debug any issue of the extension.
#### Usage
Press Alt-F2, type **lg**, then hit Enter.


## Reference
1. https://wiki.gnome.org/Projects/GnomeShell/LookingGlass

## LICENSE
MIT