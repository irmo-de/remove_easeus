# EaseUS Data Recovery Wizard Free installs a kernel driver but has no uninstaller
Version 2025

You need a terminal window to do this.


## Unload the driver

Run this in Terminal:

```
sudo kextunload -b com.easeus.driver
```

Result should be something like 
```Executing: /usr/bin/kmutil unload -b com.easeus.driver```

⚠️ If you see a "not permitted" error, SIP may be blocking it — skip to the SIP note at the end.


Delete the kernel module hidden in:

```
sudo rm -rf ~/.easeus/
```


### On macOS Big Sur or later (including M1/M2/M3/M4):
Rebuild the kernel cache
```
sudo kmutil install --update-all --volume-root /
sudo kextcache -i /   
```


### Uninstall files
```
sudo rm -rf ~/Library/Application\ Support/EaseUS
sudo rm -rf ~/Library/Preferences/com.easeus.datarecoverynet
sudo rm -rf ~/Library/Caches/com.easeus.datarecoverynet
```



### Disable SIP if needed

https://developer.apple.com/documentation/security/disabling-and-enabling-system-integrity-protection
