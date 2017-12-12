#
# Copyright (C) 2011-2017 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=i2pd
PKG_VERSION:=2.17.0
PKG_REV:=1c970b07147908fd2351577f09298fa82601f7a2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/PurpleI2P/i2pd
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk

define Package/i2pd
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+zlib +libopenssl +boost-filesystem +boost-program_options +boost-date_time +boost-chrono +boost-system +boost-thread +libatomic +libminiupnpc
	TITLE:=simplified C++ implementation of I2P client
	URL:=$(PKG_SOURCE_URL)
	MAINTAINER:=Entware team, http://entware.net
endef

define Package/i2pd/description
 i2p router for Linux written on C++.
endef

TARGET_LDFLAGS += -latomic

define Package/i2pd/conffiles
/etc/i2pd.conf
/etc/i2pd_tunnels.conf
/etc/i2pd/subscription.txt
endef

define Package/i2pd/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/i2pd $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/contrib/i2pd.conf $(1)/etc
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/contrib/tunnels.conf \
		$(1)/etc/i2pd_tunnels.conf
	$(INSTALL_BIN) ./files/S30i2p $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/etc/i2pd
	$(INSTALL_CONF) $(PKG_BUILD_DIR)/contrib/subscriptions.txt \
		$(1)/etc/i2pd
	$(CP) $(PKG_BUILD_DIR)/contrib/certificates \
		$(1)/etc/i2pd
endef

define Package/i2pd/postinst
#!/bin/sh

[ -f /etc/i2p.conf ] || exit 0
echo 'Please note: new path of configuration file is /etc/i2pd.conf'
echo 'You may check /etc/i2p.conf for custom options and delete it as obsolete.'
endef

$(eval $(call BuildPackage,i2pd))
