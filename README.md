# ath9k_csi_kernel
Patches for Linux Kernel to implement [CSI](http://pdcc.ntu.edu.sg/wands/Atheros/) on OpenWrt

**Installation**

Buildroot = `~/openwrt/`
WorkingDir = `~/openwrt/build_dir/target-mips*/linux-ar71xx_generic/compat-wireless-2016/drivers/net/wireless/ath/ath9k`

1. Build OpenWrt for the [Arduino Yun](https://github.com/RedSnake64/openwrt-yun)
2. Copy patches into `$Buildroot/package/kernelmac80211/patches`
3. Rebuild ath9k Driver
    1. Apply patches from Buildroot by `make package/kernel/mac80211/{clean,prepare} V=s QUILT=1`
    2. Check if patches applied correctly. Change into WorkingDir and execute `quilt series`, the previously added patches should appear last.
    3. Update mac80211 package from Buildroot by `make package/kernel/mac80211/update V=s` 
    4. Compile mac80211 package from Buildroot by `make package/kernel/mac80211/{clean,compile} package/index V=s`
4. Locate new packages in `$Buildroot/bin/ar71xx/packages/base/`
5. Copy `ath9k*.ipk` to your device and install them with `opkg install ath9k*`

