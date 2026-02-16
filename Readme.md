## Waybar Countdown
A lightweight Bash script that provides countdowns (for days) for Waybar. A terminal-based UI for (add/edit/delete) of `target dates`, and allows switching between multiple countdowns using mouse scroll.

## Features

- Store multiple countdowns  
- Interactive menu for adding, editing and deleting countdowns
- Mouse scroll switches between configured countdowns
- Shows countdown in `days left` or `X% left` (configurable)

## Preview

**Showing all tooltip, rofi ui and terminal ui**

![img](/preview/img9.png)

**To get my waybar config with all of my cool scripts** [modern-labwc](https://github.com/Harsh-bin/modern-labwc/)


## Installation 

1. Clone the repository:
```bash
git clone https://github.com/Harsh-bin/waybar-countdown.git 
```

2. Copy the scripts to your Waybar config directory:
```bash
mkdir -p ~/.config/waybar/scripts/countdown
cp -r  waybar-countdown/* ~/.config/waybar/scripts/countdown/
chmod +x ~/.config/waybar/scripts/countdown/*.sh
```

> [!CAUTION]
> The bash script is configured to use `$HOME/.config/waybar/scripts/countdown/` (as the DATA_FILE and STATE_FILE variable). So, you can use the suggested installation step or modify it as needed.

3. Add the module to your Waybar configuration: 
```json
      "custom/countdown":
      {
          "exec": "~/.config/waybar/scripts/countdown/countdown.sh",
          "return-type": "json",
          "format": "{}",
          "interval": 3600,

          /// To use tui on right click use something like this
          ///  "on-click-right": "foot ~/.config/waybar/scripts/countdown/countdown.sh --show-tui",	

          "on-click-right": "killall rofi || bash ~/.config/waybar/scripts/countdown/countdown.sh --show-rofi",
          "on-scroll-up": "~/.config/waybar/scripts/countdown/countdown.sh --scroll-up",
          "on-scroll-down": "~/.config/waybar/scripts/countdown/countdown.sh --scroll-down"
      },
```

You can use this css class property .expired to change waybar view when a countdown expired

NOTE: if you change name of module such as `"custom/tracker":` then css class will become `#custom-countdown.tracker`


```
 #custom-countdown.expired {
    background-color: @power;
    color: @bar_bg;            
    animation-name: blink-critical;
    animation-duration: 2s;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
    animation-direction: alternate;
}

@keyframes blink-critical {
    0% {
        background-color: @power;
        color: @bar_bg;
    }
    50% {
        background-color: @module_bg;
        color: @power;
    }
    100% {
        background-color: @power;
        color: @bar_bg;
    }
}
```

## Usage if you use my `configuration`.

- **Right Click**: Open the interactive TUI
- **Scroll wheel**: To change the countdown displaying on bar


## Author ✍️

Created by [Harsh-bin](https://github.com/Harsh-bin)

---

**Enjoy! 🎉**





