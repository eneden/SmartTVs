# Smart TVs! helper

The TV's browser for the Project Zomboid mod **Smart TVs!** on the Steam Workshop.
The game's Workshop allows no programs in mods, so on Windows this part comes as its own download.
On Linux and macOS there is nothing to download: the mod uses the browser you already have.

The mod itself is on the [Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3831834885).

**Windows, Linux and macOS.** Linux and macOS work from version 2.1 of the mod. The helper below is for Windows only.

## Windows

### Install

1. Download **SmartTVsHelper.zip** from the [latest release](https://github.com/eneden/SmartTVs/releases/latest) and extract the whole zip.
2. Run `LiveChannelsHost.exe` from it once. It copies itself and its files to `%LOCALAPPDATA%\LiveChannels\bin`, where the mod looks for it, and says so.
3. You can delete the download. The game starts the helper by itself and closes it with the game.

The TV also needs the [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/), already on Windows 11 and on most Windows 10 PCs.

Windows may warn about the program the first time, as it does about new programs that are not code-signed.

### Update

When the TV says the helper is too old for the mod, do the same with the new download.

### Remove

Quit the game and delete the folder `%LOCALAPPDATA%\LiveChannels`. It also holds the TV browser's logins, cookies and logs.

## Linux and macOS

No helper, no download. The game starts a Chromium-based browser that is already on your computer, **Google Chrome, Chromium, Microsoft Edge or Brave** (in that order of preference), in the background, without a window and with a profile of its own, so your own browser's logins and tabs are never touched. The TV shows its pages and plays their sound.

- **Nothing found?** The TV says it needs a browser. Install one of the four and restart the game. Version 112 or newer is needed.
- **Typing.** Click into the page and your keyboard goes to the TV: the character does not walk while you type. Escape, or a click into the game, gives the keyboard back.
- **Copy-protected video** (Netflix and the like, DRM) cannot play on Linux and macOS. The TV shows a notice instead of the page.
- **Sound.** The TV's volume bar sets the volume of the page's video and audio. A page that makes sound only through Web Audio (some games) ignores it.
- **macOS** is new and has had less testing than the others. Please report what does not work in the mod's Discord.

### Where things are

| | Linux | macOS |
|---|---|---|
| The TV's files | `~/.local/share/LiveChannels` (or `$XDG_DATA_HOME/LiveChannels`) | `~/Library/Application Support/LiveChannels` |
| Log of the mod's side | `game.log` there | `game.log` there |
| Log of the browser | `browser.log` there | `browser.log` there |
| The browser's profile (logins, cookies) | `profile` there | `profile` there |

A browser from snap keeps the profile in `~/snap/<name>/common/LiveChannels`, one from Flatpak in `~/.var/app/<app id>/data/LiveChannels`: those browsers cannot reach other folders. To remove everything the TV keeps, quit the game and delete these folders.

### Options

A text file `backend.txt` in the TV's folder, one line per option (text after `#` is ignored):

```
browser=/path/to/chrome     # use this browser instead of looking for one
no-sandbox                  # start the browser without its safety sandbox (see below)
websocket                   # talk to the browser through a port on localhost, not a pipe
debug                       # more in game.log
```

### If the TV cannot start the browser

The TV tells which of these it is. `game.log` and `browser.log` have the details.

- **The sandbox cannot start.** Some systems (recent Ubuntu releases, for one) restrict what the browser's safety sandbox needs, for browsers that were not installed from the distribution's or the vendor's own package. Use Google Chrome from Google's package, or Chromium from your distribution's package. The line `no-sandbox` in `backend.txt` starts the browser without the sandbox; then a hostile page could harm your computer, so use it only for pages you trust, and only if nothing else works.
- **Steam Deck and other Flatpak browsers.** A Flatpak browser cannot be handed a pipe, so the TV tries a debugging port on localhost for it. This has not been tested on a real Steam Deck.
- **Chromium from snap** is found and given a profile inside its snap folder. It has not been tested either.
- **The game runs in a container** (Steam Linux Runtime): browsers of your system are looked for under `/run/host`, too.

## Microsoft's files (Windows)

`Microsoft.Web.WebView2.Core.dll`, `Microsoft.Web.WebView2.WinForms.dll` and `WebView2Loader.dll` are Microsoft's, redistributed under their license: see `WebView2-LICENSE.txt` and `WebView2-NOTICE.txt` in the download.
