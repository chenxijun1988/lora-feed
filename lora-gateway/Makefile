#
# Copyright (C) 2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=lora_gateway
PKG_VERSION:=5.0.1
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/Lora-net/lora_gateway/archive/
PKG_MD5SUM:=5d07f8471e1a67920787e3879afe0cb6

include $(INCLUDE_DIR)/package.mk

define Package/lora-gateway/Default
  TITLE:=Semtech lora-gateway package
  URL:=http://www.semtech.com/wireless-rf/lora.html
endef

define Package/lora-gateway
$(call Package/lora-gateway/Default)
  SECTION:=utils
  CATEGORY:=Utilities
endef

define Package/lora-gateway/description
  lora-gateway is a library to build a gateway based on 
  a Semtech LoRa multi-channel RF receiver (a.k.a. concentrator).
endef

TARGET_CFLAGS += $(FPIC) -O2 -Wall -Wextra -std=c99 -Iinc -I. -lm

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/lora-gateway
	$(CP) $(PKG_BUILD_DIR)/libloragw/inc/* $(1)/usr/include/lora-gateway
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libloragw/libloragw.a $(1)/usr/lib/
endef

define Package/lora-gateway/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libloragw/test* $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/util_pkt_logger/util_pkt_logger $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/util_tx_continuous/util_tx_continuous $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/util_spi_stress/util_spi_stress $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/util_tx_test/util_tx_test $(1)/usr/bin
endef

$(eval $(call BuildPackage,lora-gateway))
