# opwin
Omni-Present Window

This small script allows you to embed *any* window (application) in a `tabbed` window instance that can be shown and hidden anywhere: in any desktop environment.

The idea is to have something similar to a *dropdown terminal* like *Tilda* but instead of just a terminal, you can just have any application. Very useful for have applications that you want to have quick access to, like messaging applications, music, browsers... whatever you want really.

## Installation

1. Place the `opwin` script anywhere in a directory present in your `PATH`.
2. Copy the sample `opwin_conf` to `~/.config/opwin/conf` and change its parameters to whaterver you need.
3. Install the dependencies: `xwininfo`, `xdotool`, `wmctrl` and `tabbed`
4. Set up keybindings for toggling the *opwin* visibility (calling `opwin toggle`)
5. Recommended: Set up keybindings to add/remove windows to/from *opwin* (calling `opwin add_current`, `opwin del_current` and `opwin add_selected`)

## Usage

Here is the `--help`

```
Use: ./opwin <command> <parameters>

 Commands:

    toggle        Show/Hide the opwin

    add_select    Select a window to be added as a tab to the opwin

    add_currrent  Add current active window as a tab to the opwin

    del_current   Remove currently focused opwin tab from the opwin
                  insttance.

```
Once you have everything setup, you should be able to add windows to the *opwin* instance. This window is an instance of [tabbed](https://tools.suckless.org/tabbed/) and you can change among the embedded windows using the *tabbed* key bindings.

To remove a window you must have it focused (*opwin* visible and selected in the *tabbed* instance) and then call `opwin del_current`.


## Disclaimer

I tried this script to work well with any window manager, **however** sometimes there are some glitches.

* Sometimes the *opwin* window is temporally not *floating*. This behavior seems to be quite random. You can prevent this by marking the window class `OPwinClaSs` as *floating*.
  ```
  # BSPWM
  bspc rule -a "*:OPwinClaSs" sticky=on state=floating

  #i3
  for_window [class="OPwinClaSs"] floating enable
  for_window [class="OPwinClaSs"] sticky enable
  ```

* Sometimes, when you remove a window, it is not comnpletely dettached from *opwin* so when you delete the *opwin*, the removed window is closed too. I did not find a fix for this, however I do not personally find it very problematic in my daily use.
