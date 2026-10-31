# Smart TVs! helper

The TV's browser for the Project Zomboid mod **Smart TVs!** on the Steam Workshop.
The game's Workshop allows no programs in mods, so this part comes as its own download.

**Windows only for now.** Linux and macOS are planned.

## Install

1. Download **SmartTVsHelper.zip** from the [latest release](https://github.com/eneden/SmartTVs/releases/latest) and extract the whole zip.
2. Run `LiveChannelsHost.exe` from it once. It copies itself and its files to `%LOCALAPPDATA%\LiveChannels\bin`, where the mod looks for it, and says so.
3. You can delete the download. The game starts the helper by itself and closes it with the game.

The TV also needs the [Microsoft Edge WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/), already on Windows 11 and on most Windows 10 PCs.

Windows may warn about the program the first time, as it does about new programs that are not code-signed.

## Update

When the TV says the helper is too old for the mod, do the same with the new download.

## Remove

Quit the game and delete the folder `%LOCALAPPDATA%\LiveChannels`. It also holds the TV browser's logins, cookies and logs.

## Microsoft's files

`Microsoft.Web.WebView2.Core.dll`, `Microsoft.Web.WebView2.WinForms.dll` and `WebView2Loader.dll` are Microsoft's, redistributed under their license: see `WebView2-LICENSE.txt` and `WebView2-NOTICE.txt` in the download.
