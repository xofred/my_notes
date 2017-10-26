Xcode's size(13.4GB) is so big. Since I'm not an apple developer, all I need are standalone command line tools. After Xcode uninstalled, `git` stop working immediately. For example, when I ran `git status`
```
xcrun: error: active developer path ("/Applications/Xcode.app/Contents/Developer") does not exist
Use `sudo xcode-select --switch path/to/Xcode.app` to specify the Xcode that you wish to use for command line developer tools, or use `xcode-select --install` to install the standalone command line developer tools.
See `man xcode-select` for more details.
```

So I ran `xcode-select --install`
```
xcode-select: error: command line tools are already installed, use "Software Update" to install updates
```

# WTF? R U KIDDING ME APPLE?

Luckily, I googled it and found a [blog](http://railsapps.github.io/xcode-command-line-tools.html). I noticed that the new path to the currently selected directory when `xcode-select -p`, is different from mine(/Applications/Xcode.app/Contents/Developer)
```
/Library/Developer/CommandLineTools
```


So I try:
```shell
sudo xcode-select --switch /Library/Developer/CommandLineTools
```

And it worked!

---

Reference:

**[Xcode Command Line Tools · macOS Sierra · Install](http://railsapps.github.io/xcode-command-line-tools.html)**

**xcode-select man page**