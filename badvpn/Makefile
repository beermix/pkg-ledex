# Copyright (C) 2009 Ambroz Bizjak
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=badvpn
PKG_VERSION:=1.999.129
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/ambrop72/badvpn.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_RELEASE)
PKG_SOURCE_VERSION:=c90711372c0e9bb87a0a8ecf741f27b72946b28b
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz

include $(INCLUDE_DIR)/package.mk

define Package/badvpn
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+librt +libpthread +udev +coreutils +coreutils-stdbuf
	TITLE:=BadVPN
	SUBMENU:=VPN
endef

CMAKE_OPTIONS += \
	-DBUILD_NOTHING_BY_DEFAULT=1 \
	-DBUILD_TUN2SOCKS=1 \
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR)
endef

define Package/badvpn/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/tun2socks/badvpn-tun2socks $(1)/usr/bin/badvpn-tun2socks
endef

$(eval $(call BuildPackage,badvpn))
