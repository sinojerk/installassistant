# installassistant
InstallAssistant, a shell script to get the "InstallAssistant.pkg" and build "Install macOS XXX.app" for macOS you can even use it in the Recovery mode
## macOS 14 beta
```sh
installassistant -v -c https://swscan.apple.com/content/catalogs/others/index-14seed-14-13-12-10.16-10.15-10.14-10.13-10.12-10.11-10.10-10.9-mountainlion-lion-snowleopard-leopard.merged-1.sucatalog.gz
```

## how to use:
list available versions
```sh
sh -c "$(curl -fsSL "https://raw.githubusercontent.com/sinojerk/installassistant/main/installassistant")"
```
list and with InstallAssistant.pkg url
```sh
sh -c "$(curl -fsSL "https://raw.githubusercontent.com/sinojerk/installassistant/main/installassistant")" -- -v
```
installassistant only find urls for you, you can download the "InstallAssistant.pkg" use your favorite tool
after your "InstallAssistant.pkg" downloaded
```sh
sh -c "$(curl -fsSL "https://raw.githubusercontent.com/sinojerk/installassistant/main/installassistant")" -- build <path to your InstallAssistant.pkg>
```
will build the "Install macOS XXX.app" for you

## setup install macOS app in memery on Recovery Mode (for large memery device such as `m1 pro/max/ultra` at least 32Gib)
1. reset your mac if needed, must go first(because your mac will reboot)
2. setup a ramdisk maybe 16GiB size
  ```sh 
  diskutil eraseDisk JHFS+ IA `hdiutil attach -nomount ram://$((16*1024*2048))`
  ```
3. `cd /Volumes/IA` then get a macOS version, download it, build to `install macOS <xxx>.app` see `how to use` section
4. run install macOS app (check the real path for `install macOS <xxx>.app`)
  ```sh
  ("/Volumes/IA/Applications/install macOS <xxx>.app/Contents/MacOS/InstallAssistant_springboard" &)
  ```

## want file Integrity check for `InstallAssistant.pkg` after download, see [sinojerk/cnkl](https://github.com/sinojerk/cnkl)
need to download `InstallAssistant.pkg.integrityDataV1` file at the same time, the url is InstallAssistant.pkg file url by append `.integrityDataV1`
