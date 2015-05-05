#
# Copyright (C) 2015 Bright Things UN Ltd. <lth@bright-things.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=iojs
PKG_VERSION:=2015-05-05
PKG_RELEASE:=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/iojs/io.js.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=7dde95a8bdd1b5aaeb3bb68a1f0abf7cfc8b3c96
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_INSTALL:=1
PKG_FIXUP:=autoreconf

PKG_LICENSE:=GPL2
PKG_LICENSE_FILES:=

PKG_MAINTAINER:=Lars Boegild Thomsen <lth@bright-things.com>

PKG_BUILD_DEPENDS:=

include $(INCLUDE_DIR)/package.mk

define Package/iojs
	TITLE:=iojs
	SECTION:=utils
	CATEGORY:=Ionic
	DEPENDS:=+
endef

define Package/iojs/description
	io.js
endef

#TARGET_CFLAGS = -std=c99

define Package/iojs/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libjsonparser.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,iojs))

