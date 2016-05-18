kill spotlight, stop it from indexing the disk

```shell
sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.metadata.mds.plist
```

see if disk still be using( /Volumes/Backup/ is the name of TM partition )

```shell
ps -ax | awk '/[m]ds/{print $1}'
sudo lsof | grep /Volumes/Backup/
```