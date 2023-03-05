#!/bin/bash
#
# Copyright (c) 2019-2020 P3TERX <https://p3terx.com>
#
# This is free software, licensed under the MIT License.
# See /LICENSE for more information.
#
# https://github.com/P3TERX/Actions-OpenWrt
# File name: diy-part2.sh
# Description: OpenWrt DIY script part 2 (After Update feeds)
#

# 删除软件包
 #rm -rf feeds/packages/net/openssh
 #rm -rf feeds/packages/sound/fdk-aac
 #rm -rf feeds/packages/utils/lvm2
 #rm -rf feeds/packages/utils/tini
 #rm -rf feeds/packages/net/kcptun
 #rm -rf package/lean/ntfs3
 #rm -rf package/lean/luci-app-cpufreq
 #rm include/feeds.mk
 #wget -P include https://raw.githubusercontent.com/openwrt/openwrt/master/include/feeds.mk
 #rm -rf package/libs/elfutils
 #rm -rf feeds/packages/utils/gnupg
 #rm -rf feeds/packages/lang/python/python3
 #rm -rf package/lean/n2n_v2
 
# ARM64: Add CPU model name in proc cpuinfo
#wget -P target/linux/generic/pending-5.4 https://github.com/immortalwrt/immortalwrt/raw/master/target/linux/generic/hack-5.4/312-arm64-cpuinfo-Add-model-name-in-proc-cpuinfo-for-64bit-ta.patch
# autocore
sed -i 's/DEPENDS:=@(.*/DEPENDS:=@(TARGET_bcm27xx||TARGET_bcm53xx||TARGET_ipq40xx||TARGET_ipq806x||TARGET_ipq807x||TARGET_mvebu||TARGET_rockchip||TARGET_armvirt) \\/g' package/lean/autocore/Makefile
# Add cputemp.sh
#cp -rf $(pwd)/PATCH/new/script/cputemp.sh ./package/base-files/files/bin/cputemp.sh

# Modify default IP
sed -i 's/192.168.1.1/192.168.1.254/g' package/base-files/files/bin/config_generate

#添加额外软件包
#git clone https://github.com/immortalwrt/luci-app-unblockneteasemusic package/luci-app-unblockneteasemusic
#git clone https://github.com/jerrykuku/luci-app-jd-dailybonus.git package/luci-app-jd-dailybonus
#git clone https://github.com/jerrykuku/lua-maxminddb.git package/lua-maxminddb
svn co https://github.com/jerrykuku/lua-maxminddb/trunk package/lua-maxminddb
svn co https://github.com/jerrykuku/luci-app-vssr/trunk package/luci-app-vssr
svn co https://github.com/vernesong/OpenClash/trunk/luci-app-openclash package/luci-app-openclash
#git clone https://github.com/project-lede/luci-app-godproxy package/luci-app-godproxy
svn co https://github.com/iwrt/luci-app-ikoolproxy/trunk package/luci-app-ikoolproxy
#svn co https://github.com/openwrt/luci/trunk/modules/luci-mod-dashboard feeds/luci/modules/luci-mod-dashboard
#svn co https://github.com/openwrt/packages/trunk/net/openssh package/openssh
#svn co https://github.com/openwrt/packages/trunk/libs/libfido2 package/libfido2
#svn co https://github.com/openwrt/packages/trunk/libs/libcbor package/libcbor
svn co https://github.com/ophub/luci-app-amlogic/trunk/luci-app-amlogic package/luci-app-amlogic
#svn co https://github.com/breakings/OpenWrt/trunk/general/luci-app-cpufreq package/luci-app-cpufreq
#svn co https://github.com/breakings/OpenWrt/trunk/general/ntfs3 package/lean/ntfs3
#svn co https://github.com/Lienol/openwrt-package/trunk/luci-app-socat package/luci-app-socat
#svn co https://github.com/neheb/openwrt/branches/elf/package/libs/elfutils package/libs/elfutils
#svn co https://github.com/breakings/OpenWrt/trunk/general/gnupg feeds/packages/utils/gnupg
#svn co https://github.com/breakings/OpenWrt/trunk/general/n2n_v2 package/lean/n2n_v2

# 编译 po2lmo (如果有po2lmo可跳过)
pushd package/luci-app-openclash/tools/po2lmo
make && sudo make install
popd
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/brook package/brook
cp -rf $(pwd)/general/brook package/brook
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/chinadns-ng package/chinadns-ng
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/tcping package/tcping
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/trojan-go package/trojan-go
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/trojan-plus package/trojan-plus
#svn co https://github.com/project-openwrt/openwrt/trunk/package/ctcgfw/luci-app-filebrowser package/luci-app-filebrowser
#svn co https://github.com/project-openwrt/openwrt/trunk/package/ctcgfw/filebrowser package/filebrowser
#svn co https://github.com/project-openwrt/openwrt/trunk/package/lienol/luci-app-fileassistant package/luci-app-fileassistant
svn co https://github.com/xiaorouji/openwrt-passwall/branches/luci/luci-app-passwall package/luci-app-passwall
svn co https://github.com/xiaorouji/openwrt-passwall2/trunk/luci-app-passwall2 package/luci-app-passwall2
#cp -rf $(pwd)/general/luci-app-passwall package/luci-app-passwall
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/shadowsocks-rust package/shadowsocks-rust
#svn co https://github.com/fw876/helloworld/trunk/shadowsocks-rust package/shadowsocks-rust
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/xray-core package/xray-core
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/xray-plugin package/xray-plugin
cp -rf $(pwd)/general/xray-core package/xray-core
cp -rf $(pwd)/general/xray-plugin package/xray-plugin
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/ssocks package/ssocks
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/dns2socks package/dns2socks
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/ipt2socks package/ipt2socks
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/microsocks package/microsocks 
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/pdnsd-alt package/pdnsd-alt
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/shadowsocksr-libev package/shadowsocksr-libev
svn co https://github.com/fw876/helloworld/trunk/shadowsocksr-libev package/shadowsocksr-libev
svn co https://github.com/fw876/helloworld/trunk/lua-neturl package/lua-neturl
#svn co https://github.com/fw876/helloworld/trunk/tcping package/tcping
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/v2ray-core package/v2ray-core
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/v2ray-plugin package/v2ray-plugin
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/v2ray-geodata package/v2ray-geodata
#svn co https://github.com/fw876/helloworld/trunk/v2ray-plugin package/v2ray-plugin
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/simple-obfs package/simple-obfs
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/kcptun package/kcptun
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/trojan package/trojan
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/hysteria package/hysteria
#svn co https://github.com/xiaorouji/openwrt-passwall/trunk/dns2tcp package/dns2tcp
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/sagernet-core package/sagernet-core

svn co https://github.com/fw876/helloworld/trunk/dns2tcp package/dns2tcp
svn co https://github.com/fw876/helloworld/trunk/v2ray-geodata package/v2ray-geodata
#svn co https://github.com/fw876/helloworld/trunk/xray-core package/xray-core
#svn co https://github.com/fw876/helloworld/trunk/xray-plugin package/xray-plugin
#svn co https://github.com/kenzok8/openwrt-packages/trunk/luci-app-gost package/luci-app-gost
cp -rf $(pwd)/general/luci-app-gost package/luci-app-gost
svn co https://github.com/kenzok8/openwrt-packages/trunk/gost package/gost
#svn co https://github.com/project-openwrt/openwrt/trunk/package/ctcgfw/luci-app-gost package/luci-app-gost
#svn co https://github.com/project-openwrt/openwrt/trunk/package/ctcgfw/gost package/gost
svn co https://github.com/kenzok8/openwrt-packages/trunk/luci-app-eqos package/luci-app-eqos
git clone https://github.com/tty228/luci-app-serverchan.git package/luci-app-serverchan
svn co https://github.com/fw876/helloworld/trunk/luci-app-ssr-plus package/luci-app-ssr-plus
#svn co https://github.com/fw876/helloworld/trunk/naiveproxy package/naiveproxy
svn co https://github.com/xiaorouji/openwrt-passwall/trunk/naiveproxy package/naiveproxy
svn co https://github.com/fw876/helloworld/trunk/redsocks2 package/redsocks2
svn co https://github.com/rufengsuixing/luci-app-adguardhome/trunk package/luci-app-adguardhome
svn co https://github.com/Lienol/openwrt-package/trunk/luci-app-filebrowser package/luci-app-filebrowser
svn co https://github.com/Lienol/openwrt-package/trunk/luci-app-ssr-mudb-server package/luci-app-ssr-mudb-server
#svn co https://gh.fakev.cn/kiddin9/openwrt-packages/trunk/luci-app-speederv2 package/luci-app-speederv2

#添加smartdns
#svn co https://github.com/project-openwrt/openwrt/trunk/package/ntlf9t/smartdns package/smartdns
#svn co https://github.com/project-openwrt/openwrt/trunk/package/ntlf9t/luci-app-smartdns package/luci-app-smartdns
#svn co https://github.com/openwrt/luci/trunk/applications/luci-app-smartdns package/luci-app-smartdns
svn co https://github.com/kenzok8/openwrt-packages/trunk/luci-app-smartdns package/luci-app-smartdns


#添加ddnsto
#svn co https://github.com/linkease/ddnsto-openwrt/trunk/ddnsto package/ddnsto
#svn co https://github.com/linkease/ddnsto-openwrt/trunk/luci-app-ddnsto package/luci-app-ddnsto
#添加udp2raw
#git clone https://github.com/sensec/openwrt-udp2raw package/openwrt-udp2raw
svn co https://github.com/sensec/openwrt-udp2raw/trunk package/openwrt-udp2raw
#git clone https://github.com/sensec/luci-app-udp2raw package/luci-app-udp2raw
svn co https://github.com/sensec/luci-app-udp2raw/trunk package/luci-app-udp2raw
sed -i "s/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=f2f90a9a150be94d50af555b53657a2a4309f287/" package/openwrt-udp2raw/Makefile
sed -i "s/PKG_VERSION:=.*/PKG_VERSION:=20200920\.0/" package/openwrt-udp2raw/Makefile

#themes
svn co https://github.com/rosywrt/luci-theme-rosy/trunk/luci-theme-rosy package/luci-theme-rosy
#git clone https://github.com/rosywrt/luci-theme-purple.git package/luci-theme-purple
#git clone https://github.com/Leo-Jo-My/luci-theme-opentomcat.git package/luci-theme-opentomcat
svn co https://github.com/Leo-Jo-My/luci-theme-opentomcat/trunk package/luci-theme-opentomcat
svn co https://github.com/Leo-Jo-My/luci-theme-opentomato/trunk package/luci-theme-opentomato
#svn co https://github.com/sirpdboy/luci-theme-opentopd/trunk package/luci-theme-opentopd
#git clone https://github.com/kevin-morgan/luci-theme-argon-dark.git package/luci-theme-argon-dark
#svn co https://github.com/kevin-morgan/luci-theme-argon-dark/trunk package/luci-theme-argon-dark
#svn co https://github.com/openwrt/luci/trunk/themes/luci-theme-openwrt-2020 package/luci-theme-openwrt-2020
svn co https://github.com/thinktip/luci-theme-neobird/trunk package/luci-theme-neobird


# samba4
#sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=4.14.13/g' feeds/packages/net/samba4/Makefile
#sed -i 's/PKG_HASH:=.*/PKG_HASH:=e1df792818a17d8d21faf33580d32939214694c92b84fb499464210d86a7ff75/g' feeds/packages/net/samba4/Makefile
rm -rf feeds/packages/net/samba4
svn co https://github.com/openwrt/packages/trunk/net/samba4 feeds/packages/net/samba4


# 晶晨宝盒
sed -i "s|https.*/amlogic-s9xxx-openwrt|https://github.com/breakings/OpenWrt|g" package/luci-app-amlogic/root/etc/config/amlogic
sed -i "s|http.*/library|https://github.com/breakings/OpenWrt/opt/kernel|g" package/luci-app-amlogic/root/etc/config/amlogic
sed -i "s|s9xxx_lede|ARMv8|g" package/luci-app-amlogic/root/etc/config/amlogic
#sed -i "s|.img.gz|..OPENWRT_SUFFIX|g" package/luci-app-amlogic/root/etc/config/amlogic

# btrfs-progs
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=6.1.3/g' feeds/packages/utils/btrfs-progs/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=d37fc9ec4fa5778b20aa7548fe706eb3a300338c1473318271ae54024dac7167/g' feeds/packages/utils/btrfs-progs/Makefile
rm -rf feeds/packages/utils/btrfs-progs/patches
#sed -i '68i\	--disable-libudev \\' feeds/packages/utils/btrfs-progs/Makefile

# qBittorrent (use cmake)
#sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=4.4.0/g' feeds/packages/net/qBittorrent/Makefile
#sed -i 's/PKG_HASH:=.*/PKG_HASH:=da240744c6cc5953d7c4d298a02a0cf36d2c8897931819f1e6459bd5270a7c5c/g' feeds/packages/net/qBittorrent/Makefile
#sed -i '41i\		+qt5-sql \\' feeds/packages/net/qBittorrent/Makefile
cp -rf $(pwd)/general/qBittorrent/patches feeds/packages/net/qBittorrent
cp -f $(pwd)/general/qBittorrent/Makefile feeds/packages/net/qBittorrent/Makefile
sed -i 's/zh/zh_CN/g' feeds/luci/applications/luci-app-qbittorrent/root/etc/config/qbittorrent

# libtorrent-rasterbar_v2
rm -rf feeds/packages/libs/libtorrent-rasterbar/patches
cp -f $(pwd)/general/libtorrent-rasterbar/Makefile feeds/packages/libs/libtorrent-rasterbar

# golang
sed -i 's/GO_VERSION_MAJOR_MINOR:=.*/GO_VERSION_MAJOR_MINOR:=1.19/g' feeds/packages/lang/golang/golang/Makefile
sed -i 's/GO_VERSION_PATCH:=.*/GO_VERSION_PATCH:=6/g' feeds/packages/lang/golang/golang/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=d7f0013f82e6d7f862cc6cb5c8cdb48eef5f2e239b35baa97e2f1a7466043767/g' feeds/packages/lang/golang/golang/Makefile
rm -rf feeds/packages/lang/golang/golang/patches/010-cmd-compile-turn-off-jump-tables-when-spectre-retpolines-.patch
#cp -rf $(pwd)/general/golang feeds/packages/lang/golang

# curl
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=7.88.1/g' feeds/packages/net/curl/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=1dae31b2a7c1fe269de99c0c31bb488346aab3459b5ffca909d6938249ae415f/g' feeds/packages/net/curl/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/net/curl/Makefile
#rm -f feeds/packages/net/curl
#svn co https://github.com/openwrt/packages/trunk/net/curl feeds/packages/net/curl

# Qt5 -qtbase
sed -i "s/PKG_BUGFIX:=.*/PKG_BUGFIX:=8/g" feeds/packages/libs/qtbase/Makefile
sed -i "s/PKG_HASH:=.*/PKG_HASH:=bfb11126c7f3abc3fdf86425ce912988b864a7e79a606d77325cffdbacb4be9c/g" feeds/packages/libs/qtbase/Makefile
#rm -rf feeds/packages/libs/qtbase/patches
#cp -rf $(pwd)/general/qt6base feeds/packages/libs

# Qt5 -qttools
sed -i "s/PKG_BUGFIX:=.*/PKG_BUGFIX:=8/g" feeds/packages/libs/qttools/Makefile
sed -i "s/PKG_HASH:=.*/PKG_HASH:=a3bef8de13032dae17450f5df35e8abbb4f41f71e3b628871d3da5633577e9c4/g" feeds/packages/libs/qttools/Makefile
#rm -rf feeds/packages/libs/qttools
#cp -rf $(pwd)/general/qt6tools feeds/packages/libs




# docker
#sed -i 's/PKG_VERSION:=20.10.17/PKG_VERSION:=20.10.23/g' feeds/packages/utils/docker/Makefile
#sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/utils/docker/Makefile
#sed -i 's/PKG_HASH:=.*/PKG_HASH:=55563b87050ce7b9b2124a9b882fdef4fa17e23f431ad502c8227101d5e789fd/g' feeds/packages/utils/docker/Makefile
#sed -i 's/PKG_GIT_SHORT_COMMIT:=100c701/PKG_GIT_SHORT_COMMIT:=7155243/g' feeds/packages/utils/docker/Makefile
rm -rf feeds/packages/utils/docker
cp -rf $(pwd)/general/docker feeds/packages/utils/docker

# dockerd
#sed -i 's/PKG_VERSION:=20.10.17/PKG_VERSION:=20.10.23/g' feeds/packages/utils/dockerd/Makefile
#sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/utils/dockerd/Makefile
#sed -i 's/PKG_HASH:=.*/PKG_HASH:=61bb3f4f0c935ac9a719adbac69fca0d727b6b5c3eb889571e00b1cc3ff1e368/g' feeds/packages/utils/dockerd/Makefile
#sed -i 's/PKG_GIT_SHORT_COMMIT:=a89b842/PKG_GIT_SHORT_COMMIT:=6051f14/g' feeds/packages/utils/dockerd/Makefile
#sed -i 's/^\s*$[(]call\sEnsureVendoredVersion/#&/' feeds/packages/utils/dockerd/Makefile
rm -rf feeds/packages/utils/dockerd
cp -rf $(pwd)/general/dockerd feeds/packages/utils/dockerd

# docker-compose
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=2.16.0/g' feeds/packages/utils/docker-compose/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=556dc59075280442128f5b45a8ff37638fb357c2a956bd751dd0ba747c93e71d/g' feeds/packages/utils/docker-compose/Makefile

# containerd
#sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.5.11/g' feeds/packages/utils/containerd/Makefile
#sed -i 's/PKG_HASH:=.*/PKG_HASH:=skip/g' feeds/packages/utils/containerd/Makefile
#sed -i 's/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=3df54a852345ae127d1fa3092b95168e4a88e2f8/g' feeds/packages/utils/containerd/Makefile
cp -f $(pwd)/general/containerd/Makefile feeds/packages/utils/containerd

# runc
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.1.4/g' feeds/packages/utils/runc/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=4f02077432642eebd768fc857318ae7929290b3a3511eb1be338005e360cfa34/g' feeds/packages/utils/runc/Makefile
sed -i 's/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=5fd4c4d144137e991c4acebb2146ab1483a97925/g' feeds/packages/utils/runc/Makefile
#sed -i '12d' feeds/packages/utils/runc/Makefile


# pcre
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=8.45/g' package/libs/pcre/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' package/libs/pcre/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=4dae6fdcd2bb0bb6c37b5f97c33c2be954da743985369cddac3546e3218bffb8/g' package/libs/pcre/Makefile

# pcre2
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=10.42/g' feeds/packages/libs/pcre2/Makefile
sed -i 's|PKG_SOURCE_URL:=.*|PKG_SOURCE_URL:=https://github.com/PCRE2Project/pcre2/releases/download/$(PKG_NAME)-$(PKG_VERSION)|g' feeds/packages/libs/pcre2/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=8d36cd8cb6ea2a4c2bb358ff6411b0c788633a2a45dabbf1aeb4b701d1b5e840/g' feeds/packages/libs/pcre2/Makefile
#sed -i '58i\	-DPCRE2_SUPPORT_UNICODE=ON \\' feeds/packages/libs/pcre2/Makefile


# wsdd2
sed -i 's/PKG_SOURCE_DATE:=.*/PKG_SOURCE_DATE:=2022-04-25/g' feeds/packages/net/wsdd2//Makefile
sed -i 's/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=e37443ac4c757dbf14167ec3f754ebe88244ad4b/g' feeds/packages/net/wsdd2//Makefile
sed -i 's/PKG_MIRROR_HASH:=.*/PKG_MIRROR_HASH:=45e0c37b8e275c8d088506f953aa25b30a31600ce67ccb4f60b1eda6688a5a8b/g' feeds/packages/net/wsdd2//Makefile

# php8
#rm -rf feeds/packages/lang/php8
#svn co https://github.com/openwrt/packages/trunk/lang/php8 feeds/packages/lang/php8
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=8.2.3/g' feeds/packages/lang/php8/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=b9b566686e351125d67568a33291650eb8dfa26614d205d70d82e6e92613d457/g' feeds/packages/lang/php8/Makefile

# python-docker
#sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=6.0.1/g' feeds/packages/lang/python/python-docker/Makefile
#sed -i 's/PKG_HASH:=.*/PKG_HASH:=896c4282e5c7af5c45e8b683b0b0c33932974fe6e50fc6906a0a83616ab3da97/g' feeds/packages/lang/python/python-docker/Makefile
#cp -f $(pwd)/general/python-docker/Makefile feeds/packages/lang/python/python-docker

# parted
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3.5/g' feeds/packages/utils/parted/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=4938dd5c1c125f6c78b1f4b3e297526f18ee74aa43d45c248578b1d2470c05a2/g' feeds/packages/utils/parted/Makefile


# socat
#rm -rf feeds/packages/net/socat
#svn co https://github.com/openwrt/packages/trunk/net/socat feeds/packages/net/socat
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.7.4.4/g' feeds/packages/net/socat/Makefile
#sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/net/socat/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=fbd42bd2f0e54a3af6d01bdf15385384ab82dbc0e4f1a5e153b3e0be1b6380ac/g' feeds/packages/net/socat/Makefile
#sed -i '75i\	  sc_cv_getprotobynumber_r=2 \\' feeds/packages/net/socat/Makefile
#rm -f feeds/packages/net/socat/patches/100-usleep.patch

# transmission-web-control
sed -i 's/PKG_SOURCE_DATE:=.*/PKG_SOURCE_DATE:=2021-09-25/g' feeds/packages/net/transmission-web-control/Makefile
sed -i 's/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=4b2e1858f7a46ee678d5d1f3fa1a6cf2c739b88a/g' feeds/packages/net/transmission-web-control/Makefile
sed -i 's/PKG_MIRROR_HASH:=.*/PKG_MIRROR_HASH:=ea014c295766e2efc7b890dc6a6940176ba9c5bdcf85a029090f2bb850e59708/g' feeds/packages/net/transmission-web-control/Makefile

# htop
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3.2.2/g' feeds/packages/admin/htop/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=3829c742a835a0426db41bb039d1b976420c21ec65e93b35cd9bfd2d57f44ac8/g' feeds/packages/admin/htop/Makefile

# python3
sed -i 's/PYTHON3_VERSION_MICRO:=.*/PYTHON3_VERSION_MICRO:=9/g' feeds/packages/lang/python/python3-version.mk
sed -i 's/PYTHON3_SETUPTOOLS_VERSION:=.*/PYTHON3_SETUPTOOLS_VERSION:=65.5.0/g' feeds/packages/lang/python/python3-version.mk
sed -i 's/PYTHON3_PIP_VERSION:=.*/PYTHON3_PIP_VERSION:=22.3.1/g' feeds/packages/lang/python/python3-version.mk
#sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/lang/python/python3/Makefile
#svn co https://github.com/openwrt/packages/branches/openwrt-21.02/lang/python/python3 feeds/packages/lang/python/python3
sed -i 's/PKG_HASH:=.*/PKG_HASH:=5ae03e308260164baba39921fdb4dbf8e6d03d8235a939d4582b33f0b5e46a83/g' feeds/packages/lang/python/python3/Makefile
rm -rf feeds/packages/lang/python/python3/patches-pip


# python-websocket-client
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.5.1/g' feeds/packages/lang/python/python-websocket-client/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=3f09e6d8230892547132177f575a4e3e73cfdf06526e20cc02aa1c3b47184d40/g' feeds/packages/lang/python/python-websocket-client/Makefile

# python-urllib3
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.26.14/g' feeds/packages/lang/python/python-urllib3/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=076907bf8fd355cde77728471316625a4d2f7e713c125f51953bb5b3eecf4f72/g' feeds/packages/lang/python/python-urllib3/Makefile

# python-sqlalchemy
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=2.0.3/g' feeds/packages/lang/python/python-sqlalchemy/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=c2b924f6d0162ed1c0d8f47db1e56498702b1c3c953ad84f0eefbf5b4e53bb05/g' feeds/packages/lang/python/python-sqlalchemy/Makefile

# python-simplejson
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3.18.3/g' feeds/packages/lang/python/python-simplejson/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=ebb53837c5ffcb6100646018565d3f1afed6f4b185b14b2c9cbccf874fe40157/g' feeds/packages/lang/python/python-simplejson/Makefile

# python-pyrsistent
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=0.19.3/g' feeds/packages/lang/python/python-pyrsistent/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=1a2994773706bbb4995c31a97bc94f1418314923bd1048c6d964837040376440/g' feeds/packages/lang/python/python-pyrsistent/Makefile


# python-paramiko
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3.0.0/g' feeds/packages/lang/python/python-paramiko/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=fedc9b1dd43bc1d45f67f1ceca10bc336605427a46dcdf8dec6bfea3edf57965/g' feeds/packages/lang/python/python-paramiko/Makefile

# python-lxml
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=4.9.2/g' feeds/packages/lang/python/python-lxml/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=2455cfaeb7ac70338b3257f41e21f0724f4b5b0c0e7702da67ee6c3640835b67/g' feeds/packages/lang/python/python-lxml/Makefile

# python-idna
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3.4/g' feeds/packages/lang/python/python-idna/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=814f528e8dead7d329833b91c5faa87d60bf71824cd12a7530b5526063d02cb4/g' feeds/packages/lang/python/python-idna/Makefile

# python-dns
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=2.2.1/g' feeds/packages/lang/python/python-dns/Makefile
sed -i 's/PYPI_SOURCE_EXT:=.*/PYPI_SOURCE_EXT:=tar.gz/g' feeds/packages/lang/python/python-dns/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=0f7569a4a6ff151958b64304071d370daa3243d15941a7beedf0c9fe5105603e/g' feeds/packages/lang/python/python-dns/Makefile

# python-certifi
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=2022.12.7/g' feeds/packages/lang/python/python-certifi/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=35824b4c3a97115964b408844d64aa14db1cc518f6562e8d7261699d1350a9e3/g' feeds/packages/lang/python/python-certifi/Makefile

# bcrypt
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3.2.2/g' feeds/packages/lang/python/bcrypt/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/lang/python/bcrypt/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=433c410c2177057705da2a9f2cd01dd157493b2a7ac14c8593a16b3dab6b6bfb/g' feeds/packages/lang/python/bcrypt/Makefile

# python-dotenv
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=0.21.1/g' feeds/packages/lang/python/python-dotenv/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=1c93de8f636cde3ce377292818d0e440b6e45a82f215c3744979151fa8151c49/g' feeds/packages/lang/python/python-dotenv/Makefile



sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=2.28.2/g' feeds/packages/lang/python/python-requests/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/lang/python/python-requests/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=98b1b2782e3c6c4904938b84c0eb932721069dfdb9134313beff7c83c2df24bf/g' feeds/packages/lang/python/python-requests/Makefile

# gzip
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.12/g' feeds/packages/utils/gzip/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/utils/gzip/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=ce5e03e519f637e1f814011ace35c4f87b33c0bbabeec35baf5fbd3479e91956/g' feeds/packages/utils/gzip/Makefile


# zerotier
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.10.3/g' feeds/packages/net/zerotier/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=f2ce8a63a459a5fab129fb398e379b8c0875bdfeccb7bf15f9683ad22e43e629/g' feeds/packages/net/zerotier/Makefile


rm -rf feeds/packages/net/openssh
cp -rf $(pwd)/general/openssh feeds/packages/net


# hwdata
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=0.366/g' feeds/packages/utils/hwdata/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=bdc91561ec210877e6d1e3ec3abf0305389d7bcc3bf616bcecb2bdf74e3a7696/g' feeds/packages/utils/hwdata/Makefile

# gawk
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=5.2.1/g' feeds/packages/utils/gawk/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=673553b91f9e18cc5792ed51075df8d510c9040f550a6f74e09c9add243a7e4f/g' feeds/packages/utils/gawk/Makefile

# unrar
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=6.2.6/g' feeds/packages/utils/unrar/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=0c2d4cbc8b34d0e3bec7b474e0f52bbcc6c4320ec089b4141223ee355f63c318/g' feeds/packages/utils/unrar/Makefile

rm -rf feeds/packages/utils/at
cp -rf $(pwd)/general/at feeds/packages/utils


# nano
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=7.2/g' feeds/packages/utils/nano/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=86f3442768bd2873cec693f83cdf80b4b444ad3cc14760b74361474fc87a4526/g' feeds/packages/utils/nano/Makefile

# dnsproxy
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=0.48.0/g' feeds/packages/net/dnsproxy/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=b63d10b0f7d4ede68aae9bda9ef306a0673c8ca97ef9d57b838edb53e0023f8b/g' feeds/packages/net/dnsproxy/Makefile

# less
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=608/g' feeds/packages/utils/less/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=a69abe2e0a126777e021d3b73aa3222e1b261f10e64624d41ec079685a6ac209/g' feeds/packages/utils/less/Makefile

# file
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=5.43/g' feeds/packages/libs/file/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=8c8015e91ae0e8d0321d94c78239892ef9dbc70c4ade0008c0e95894abfb1991/g' feeds/packages/libs/file/Makefile

# nginx
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.21.4/g' feeds/packages/net/nginx/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/net/nginx/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=d1f72f474e71bcaaf465dcc7e6f7b6a4705e4b1ed95c581af31df697551f3bfe/g' feeds/packages/net/nginx/Makefile

# smartdns
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.2023.40/g' feeds/packages/net/smartdns/Makefile
sed -i 's/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=ee4816da5c66619c4210f7fda6245adf4c1c7ee8/g' feeds/packages/net/smartdns/Makefile
sed -i 's/PKG_MIRROR_HASH:=.*/PKG_MIRROR_HASH:=fb4661291e79450f51a70f9b988c7452710acd1599529de48fef42c7dda0b29c/g' feeds/packages/net/smartdns/Makefile
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.2023.40/g' package/luci-app-smartdns/Makefile

# readd cpufreq for aarch64
sed -i 's/LUCI_DEPENDS.*/LUCI_DEPENDS:=\@\(arm\|\|aarch64\)/g' feeds/luci/applications/luci-app-cpufreq/Makefile
sed -i 's/services/system/g'  feeds/luci/applications/luci-app-cpufreq/luasrc/controller/cpufreq.lua

# luci-app-openvpn
sed -i 's/services/vpn/g'  feeds/luci/applications/luci-app-openvpn/luasrc/controller/openvpn.lua
sed -i 's/services/vpn/g'  feeds/luci/applications/luci-app-openvpn/luasrc/model/cbi/openvpn.lua
sed -i 's/services/vpn/g'  feeds/luci/applications/luci-app-openvpn/luasrc/view/openvpn/pageswitch.htm

rm -rf package/naiveproxy
cp -rf $(pwd)/general/naiveproxy package/naiveproxy

sed -i 's/DEPENDS:=.*/DEPENDS:=@(LINUX_5_4||LINUX_5_10) +kmod-nls-utf8/g' package/lean/ntfs3-oot/Makefile

# replace banner
cp -f $(pwd)/general/openwrt_banner package/base-files/files/etc/banner

# fix luci-theme-opentomcat dockerman icon missing
rm -f package/luci-theme-opentomcat/files/htdocs/fonts/advancedtomato.woff
cp $(pwd)/general/advancedtomato.woff package/luci-theme-opentomcat/files/htdocs/fonts
sed -i 's/e025/e02c/g' package/luci-theme-opentomcat/files/htdocs/css/style.css
sed -i 's/66CC00/00b2ee/g' package/luci-theme-opentomcat/files/htdocs/css/style.css

# flac
rm -rf feeds/packages/libs/flac
cp -r $(pwd)/general/flac feeds/packages/libs

# frp
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=0.47.0/g' feeds/packages/net/frp/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=d98ebf8638701cf8662604b9fe2fb355f91209f87edcb77f2830c7fa40ccbe37/g' feeds/packages/net/frp/Makefile


# sqlite3
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=3410000/g' feeds/packages/libs/sqlite3/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=49f77ac53fd9aa5d7395f2499cb816410e5621984a121b858ccca05310b05c70/g' feeds/packages/libs/sqlite3/Makefile
sed -i 's|PKG_SOURCE_URL:=.*|PKG_SOURCE_URL:=https://www.sqlite.org/2023/|g' feeds/packages/libs/sqlite3/Makefile


# haproxy
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=2.6.9/g' feeds/packages/net/haproxy/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/net/haproxy/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=f01a1c5f465dc1b5cd175d0b28b98beb4dfe82b5b5b63ddcc68d1df433641701/g' feeds/packages/net/haproxy/Makefile
sed -i 's/BASE_TAG:=.*/BASE_TAG=v2.6.9/g' feeds/packages/net/haproxy/get-latest-patches.sh

# perl
rm -rf feeds/packages/lang/perl
cp -rf $(pwd)/general/perl feeds/packages/lang

# tailscale
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.36.2/g' feeds/packages/net/tailscale/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=eadbc78e5f36d3af2af54bea3d7f051d06b9fabc239df8e48be243c273727f47/g' feeds/packages/net/tailscale/Makefile


# util-linux
rm -rf package/utils/util-linux
cp -rf $(pwd)/general/util-linux package/utils

# lsof
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=4.95.0/g' feeds/packages/utils/lsof/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=e9faa0fbcc48638c1d1f143e93573ac43b65e76646150f83e24bd8c18786303c/g' feeds/packages/utils/lsof/Makefile

# libnetwork
sed -i 's/PKG_SOURCE_VERSION:=.*/PKG_SOURCE_VERSION:=05b93e0d3a95952f70c113b0bc5bdb538d7afdd7/g' feeds/packages/utils/libnetwork/Makefile
sed -i 's/PKG_SOURCE_DATE:=.*/PKG_SOURCE_DATE:=2023-01-19/g' feeds/packages/utils/libnetwork/Makefile
sed -i 's/PKG_MIRROR_HASH:=.*/PKG_MIRROR_HASH:=d1f590909e7e70dca3a02ce194015208291fcc28d1f13bb5c23d68194f18660f/g' feeds/packages/utils/libnetwork/Makefile

# nghttp2
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.51.0/g' feeds/packages/libs/nghttp2/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=66aa76d97c143f42295405a31413e5e7d157968dad9f957bb4b015b598882e6b/g' feeds/packages/libs/nghttp2/Makefile

# sagernet-core
sed -i 's|$(LN) v2ray $(1)/usr/bin/xray|#$(LN) v2ray $(1)/usr/bin/xray|g' package/sagernet-core/Makefile
sed -i 's|CONFLICTS:=v2ray-core xray-core|#CONFLICTS:=v2ray-core xray-core|g' package/sagernet-core/Makefile

# bind
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=9.18.11/g' feeds/packages/net/bind/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=8ff3352812230cbcbda42df87cad961f94163d3da457c5e4bef8057fd5df2158/g' feeds/packages/net/bind/Makefile


# vim
rm -rf feeds/packages/utils/vim
cp -rf $(pwd)/general/vim feeds/packages/utils

# python-packaging
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=21.3/g' feeds/packages/lang/python/python-packaging/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=dd47c42927d89ab911e606518907cc2d3a1f38bbd026385970643f9c5b8ecfeb/g' feeds/packages/lang/python/python-packaging/Makefile

# python-click
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=8.1.3/g' feeds/packages/lang/python/click/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=7682dc8afb30297001674575ea00d1814d808d6a36af415a82bd481d37ba7b8e/g' feeds/packages/lang/python/click/Makefile



# python-jsonschema
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=4.17.3/g' feeds/packages/lang/python/python-jsonschema/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=0f864437ab8b6076ba6707453ef8f98a6a0d512a80e93f8abdb676f737ecb60d/g' feeds/packages/lang/python/python-jsonschema/Makefile

# ttyd
sed -i 's/PKG_VERSION:=.*/PKG_VERSION:=1.7.2/g' feeds/packages/utils/ttyd/Makefile
sed -i 's/PKG_RELEASE:=.*/PKG_RELEASE:=1/g' feeds/packages/utils/ttyd/Makefile
sed -i 's/PKG_HASH:=.*/PKG_HASH:=edc44cd5319c0c9d0858081496cae36fc5c54ee7722e0a547dde39537dfb63de/g' feeds/packages/utils/ttyd/Makefile
rm -f feeds/packages/utils/ttyd/patches/090*.patch



./scripts/feeds update -a
./scripts/feeds install -a
