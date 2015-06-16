#
# Copyright (C) 2015 Bright Things UN Ltd.
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bcm43340-mod
PKG_VERSION:=1.141
PKG_RELEASE=1

PKG_LICENSE:=GPL
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=git://github.com/01org/edison-bcm43340.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=9d609e1ffadbf8895a701e6283392bb54bd962f9
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz

PKG_MAINTAINER:=Lars Boegild Thomsen <lth@bright-things.com>
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/bcm43340-mod
  SUBMENU:=Wireless Drivers
  TITLE:=Broadcom 43340 Driver for the Intel Edison
  DEPENDS:=+kmod-mac80211 +@DRIVER_11N_SUPPORT @PCI_SUPPORT
  FILES:=$(PKG_BUILD_DIR)/mwlwifi.ko
  AUTOLOAD:=$(call AutoLoad,50,mac80211 mwlwifi)
endef

NOSTDINC_FLAGS = \
	-I$(PKG_BUILD_DIR) \
	-I$(STAGING_DIR)/usr/include/mac80211-backport/uapi \
	-I$(STAGING_DIR)/usr/include/mac80211-backport \
	-I$(STAGING_DIR)/usr/include/mac80211/uapi \
	-I$(STAGING_DIR)/usr/include/mac80211 \
	-include backport/backport.h

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		ARCH="$(LINUX_KARCH)" \
		CROSS_COMPILE="$(TARGET_CROSS)" \
		SUBDIRS="$(PKG_BUILD_DIR)" \
		NOSTDINC_FLAGS="$(NOSTDINC_FLAGS)" \
		modules
endef

define KernelPackage/bcm43340-mod/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DIR) $(1)/lib/firmware/mwlwifi
	$(CP) $(PKG_BUILD_DIR)/bin/firmware/88W8864.bin $(1)/lib/firmware/mwlwifi/
endef

$(eval $(call KernelPackage,bcm43340-mod))

