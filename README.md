# album-cover-waybar
Bash script which shows the album cover from spotify on a waybar. I'll show you how to add it to your waybar's jsonc.

__By the way__, you can change player, which from the image fetches to the bar by changing --player flag in the scripts first variable.

It's here:
```bash
CURRENT_URL=$(playerctl --player spotify metadata --format '{{mpris:artUrl}}' 2>/dev/null)
```
Just change spotify for another player name in your system and that's it.

## Preview

![](https://raw.githubusercontent.com/Haridula/album-cover-waybar/48eed0b285bafafb5ffe86b6ef860f6e2cf0b85c/assets/preview.png)

## Dependencies
You must have these packages:
- `playerctl`
- `wget`

## HOWTO:
Simply add this snippet to your `config.jsonc` at `~/.config/waybar` and specify the location of the script in your filesystem.
```json
"image": {
        "exec": "~/scripts/album-cover.sh",
        "size": 38, //You can modify this parameter as you want.
        "interval": 1
    }
```
The module with the script is supposed to go before mpris module.

And also icnlude `"image"` module to modules list.

*Example:*
```json
    "modules-left": [
        "custom/arch-logo",
        "hyprland/workspaces",
        "album",
        "image", // <------- This should be somewhere in modules
	    "mpris"
    ],
    "modules-center": [
        "clock"
    ],
    "modules-right": [
        "wireplumber#output",
        "wireplumber#input",
        "hyprland/language",
        "bluetooth",
        "cpu",
        "network",
        "custom/swaync",
        "custom/power"
    ],
```
I put it in `"modules-left"` near the mpris to make up a media general module from smaller ones. You can put it wherever __you__ want. 

__Voilà!__

You've just got the album cover at your waybar!

_P.S. I attached my waybar config to the repo just in case you need to realize something about implementing all that stuff on your own_ ;)