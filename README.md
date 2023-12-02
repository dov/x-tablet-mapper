# Intro

x-tablet-mapper (xtm) is a small x11 interactive front end to xinput
with the purpose of visualizating and interactively change a tablet
(e.g. Wacom) to screen mapping. 

# Dependencies

This script requires python and gtk installed through `gi` (GObject Instrospection).

# Usage

Run from command line, your window manager. See fvwm details below for common fvwm macros.

# License

xtm is licensed under the MIT License. See file:LICENSE.txt for details

# Author

Dov Grobgeld <dov.grobgeld@gmail.com>
2023-12-02 Sat

# Keyboard bindings

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
