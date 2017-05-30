#
# Copyright (C) 2014-2017 Jian Chang <aa65535@live.com>
#
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=lnav
PKG_VERSION:=cd76eae

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/tstack/lnav
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=cd76eae5b817b70c542f499e987f6228a1d65b24
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf
PKG_USE_MIPS16:=0
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/lnav/Default
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Lightweight Secured Socks5 Proxy
	URL:=https://github.com/tstack/lnav
	DEPENDS:=+libsqlite3 +libssh2 +libpcre +libbz2 +libcurl +libopenssl +libevent2 +libpthread +libncursesw +libncurses +libreadline +libpthread
endef

Package/lnav = $(Package/lnav/Default)



CONFIGURE_ARGS += --disable-static

define Package/lnav/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/lnav $(1)/usr/bin
endef


$(eval $(call BuildPackage,lnav))
