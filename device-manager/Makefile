include $(TOPDIR)/rules.mk

PKG_NAME:=device-manager
PKG_VERSION:=dev
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/CreatorKit/device-manager.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk


define Package/device-manager
  SECTION:=utils
  CATEGORY:=Utilities
  DEFAULT:=n
  DEPENDS:=+awalwm2m +ubus +ubox
  TITLE:=Device manager
  MENU:=1
endef

define Package/device-manager/description
 Device manager is an application for provisioning devices with access details for flow cloud
endef

CMAKE_OPTIONS += -DSTAGING_DIR=$(STAGING_DIR)

define Build/Compile
	$(call Build/Compile/Default,all)
endef

define Build/Clean
	$(call Build/Compile/Default,clean)
endef

define Package/device-manager/install
	$(INSTALL_DIR) $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/* $(STAGING_DIR)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/* $(1)/etc/init.d/
endef

$(eval $(call BuildPackage,device-manager))
