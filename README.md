# Intro

x-tablet-mapper (xtm) is  a small x11 interactive front  end to xinput with the purpose of visualizating  and interactively change  a tablet (e.g. Wacom) to screen mapping.

`xtm` makes it much easier to work with a small tablet on a big screen. E.g. I typically take handwritten notes in a small window on the screen, and the stylus resolution is much higher if I only map the tablet rectangle to part of the screen, instead of to the whole screen.

# Dependencies

This script requires python and gtk installed through `gi` (GObject Instrospection).

# Usage

Run from command line, or your window manager on X11 startup. See fvwm details below for common fvwm macros.

## Screenshot:

![`xtm` mapping of a tablet in portait mode to part of the scree](xtm-screenshot.png)

Keyboard bindings:

* Mouse drag. Move the mapped window
* Mouse scroll wheel. Decrease and increase the mapped area.

## json rpc 

`xtm` also includes an json rpc server, and `xtm` may function as a client with the `-c` command line argument. The following command line may be used to change the mapping in a running xtm instance:

* `xtm -c --key left` - move the mapped window to the left
* `xtm -c --key right` - move the mapped window to the left
* `xtm -c --key up` - move the mapped window up
* `xtm -c --key down` - move the mapped window down

In the fvwm section below, I show attach these commands to keyboard bindings.

# License

xtm is licensed under the MIT License. See file:LICENSE.txt for details

# Author

Dov Grobgeld <dov.grobgeld@gmail.com>
2023-12-02 Sat

# fvwm notes

My prefered window manager is fvwm and the following are some special setups that may be done to work with fvwm:

## Get rid of title

```
Style "xtm" NoTitle
```

## Add to startup
```
# For 4k screen
AddToFunc InitFunction 	  "I" Module FvwmPager *
:
+                         "I" exec xtm -g +3221-5 &
```

## Keyboard bindings

The following binds use the (for me) unused keys PrtScn and Pause to move the xtm rectangle to the left and the right:

```
Key Print	A	A	Exec xtm -c --key left
Key Pause	A	A	Exec xtm -c --key right
```
