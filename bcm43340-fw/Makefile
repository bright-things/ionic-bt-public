#
# Copyright (C) 2015 Bright Things UN Ltd.
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=bcm43340-fw
PKG_VERSION:=6.20.190
PKG_RELEASE=1

PKG_LICENSE:=Proprietary
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=git://github.com/01org/edison-firmware.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=8585a10b3527666b2d35b3dcacffede3ec00cb53
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz

PKG_MAINTAINER:=Lars Boegild Thomsen <lth@bright-things.com>
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/bcm43340-fw
  SUBMENU:=Wireless Drivers
  TITLE:=Broadcom 43340 Firmware for the Intel Edison
  DEPENDS:=+kmod-mac80211 +@DRIVER_11N_SUPPORT @PCI_SUPPORT
endef

define Build/Compile
	# NoOP
endef

define KernelPackage/bcm43340-fw/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/broadcom_cws/wlan/firmware/bcmdhd_aob.cal_4334x_b0 $(1)/lib/firmware/
endef

$(eval $(call KernelPackage,bcm43340-fw))

