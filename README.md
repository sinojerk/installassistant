# installassistant
InstallAssistant, a shell script to get the "InstallAssistant.pkg" and build "Install macOS XXX.app" for macOS you can even use it in the Recovery mode
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
