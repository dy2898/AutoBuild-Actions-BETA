#
# Copyright (C) 2021 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tailscale
PKG_VERSION:=1.38.2
PKG_RELEASE:=$(AUTORELEASE)




PKG_BUILD_DIR:=$(BUILD_DIR)/tailscale-$(PKG_VERSION)


include $(INCLUDE_DIR)/package.mk


define Package/tailscale/Default
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=Zero config VPN
  URL:=https://tailscale.com
endef

define Package/tailscaled
  $(call Package/tailscale/Default)
  TITLE+= (daemon)
  DEPENDS+= +ca-bundle +kmod-tun
endef

define Package/tailscale
  $(call Package/tailscale/Default)
  TITLE+= (utility)
  DEPENDS+= +tailscaled
endef

define Package/tailscale/description
  It creates a secure network between your servers, computers,
  and cloud instances. Even when separated by firewalls or subnets.
endef

Package/tailscaled/description:=$(Package/tailscale/description)

define Build/Prepare
endef



define Build/Configure
endef



define Build/Compile
endef

define Package/tailscale/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) ./files/tailscale $(1)/usr/sbin
endef

define Package/tailscaled/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) ./files/tailscaled $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/init.d/
	$(INSTALL_BIN) ./files//tailscale.init $(1)/etc/init.d/tailscale
	$(INSTALL_DIR) $(1)/etc/config/
	$(INSTALL_DATA) ./files//tailscale.conf $(1)/etc/config/tailscale
endef

define Package/tailscaled/conffiles
/etc/config/tailscale
endef

$(eval $(call BuildPackage,tailscale))
$(eval $(call BuildPackage,tailscaled))
