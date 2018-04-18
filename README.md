# LGOGDownloader Flatpak build manifest
 
[LGOGDownloader project website](https://sites.google.com/site/gogdownloader/)
 
## Building
 Install flatpak-builder then run:

```
 flatpak-builder --disable-updates --repo=dev-lgogdownloader lgogdownloader [PATH/]io.github.Sude.lgogdownloader.json
 
 flatpak --user remote-add --no-gpg-verify --if-not-exists dev-lgogdownloader dev-lgogdownloader
```

## Running
If running flatpak 0.10.2+ with the wrapper bin path setup you can simply run the app as `io.github.Sude.lgogdownloader`. Otherwise:
```
flatpak run io.github.Sude.lgogdownloader [ COMMANDS ]
```

A full example:
```
flatpak run io.github.Sude.lgogdownloader --download --game star_wars_xwing_1993 --platform 4 --directory ~/GOG\ Games
```

Out of the box the application is sandbox to allow access only to *XDG-DOWNLOAD* (your home download directory) and *~/GOG Games*. This means you must tell lgogdownloader to download specifically to one of those two folders out of the box:
```
flatpak run io.github.Sude.lgogdownloader --directory ~/Downloads ...
```
You can allow access to other directories by passing the `--filesystem' switch to flatpak like so:
```
flatpak run --filesystem=~/Games io.github.Sude.lgogdownloader ... --directory ~/Games/GOG\ Games/Files
```

Thus if you wanted to download to your current directory anywhere within your home directory (the default behavior of lgogdownloader) you can do it like so:
```
flatpak run --filesystem=~ io.github.Sude.lgogdownloader --download --game star_wars_xwing_1993
```
