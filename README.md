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
