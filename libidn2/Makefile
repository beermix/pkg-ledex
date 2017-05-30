#
# Copyright (C) 2009-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libidn2
PKG_VERSION:=2.0.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://fossies.org/linux/misc
PKG_MD5SUM:=a9aa7e003665de9c82bd3f9fc6ccf308

PKG_LICENSE:=GPL-2.0+ GPL-3.0+ LGPL-2.1+ LGPL-3.0+ Apache-2.0
PKG_LICENSE_FILES:=COPYING COPYINGv2 COPYINGv3 COPYING.LESSERv2 COPYING.LESSERv3 java/LICENSE-2.0.txt

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/idn2/Default
  SECTION:=net
  CATEGORY:=Network
  URL:=http://www.gnu.org/software/libidn2/
  MAINTAINER:=Kevin Darbyshire-Bryant <kevin@darbyshire-bryant.me.uk>
endef

define Package/idn2/Default/description
  GNU libidn2 is a fully documented implementation of the Stringprep,
  Punycode and IDNA specifications. libidn2's purpose is to encode and
  decode internationalized domain names.
endef

define Package/idn2
  $(call Package/idn2/Default)
  SUBMENU:=IP Addresses and Names
  TITLE:=GNU IDN (Internationalized Domain Name) tool
  DEPENDS:=+libidn2
endef

define Package/idn2/description
$(call Package/idn2/Default/description)

  Command line tool using libidn2

endef

define Package/libidn2
  $(call Package/idn2/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Stringprep, Punycode and IDNA implementation
endef

define Package/libidn2/description
$(call Package/idn2/Default/description)

  Library only package

endef

TARGET_CFLAGS += $(FPIC)

CONFIGURE_ARGS += \
	--enable-shared \
	--enable-static \
	--disable-java \

MAKE_FLAGS += \
	CC="$(TARGET_CC)" \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libidn2.{a,so*} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libidn2.pc $(1)/usr/lib/pkgconfig/
endef

define Package/idn2/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
endef

define Package/libidn2/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libidn2.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,idn2))
$(eval $(call BuildPackage,libidn2))
