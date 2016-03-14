include $(TOPDIR)/rules.mk

PKG_NAME:=flow_button_gateway
PKG_VERSION:=dev
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/CreatorKit/flow_button_gateway.git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

CMAKE_OPTIONS += -DSTAGING_DIR=$(STAGING_DIR)

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/flow_button_gateway
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:= +awalwm2m +libflowmessaging +libflowcore +libconfig
  TITLE:=Flow button gateway app
endef

define Package/flow_button_gateway/description
  Imagination Technologies flow button gateway app
endef

define Build/Compile
	$(call Build/Compile/Default,all)
endef

define Build/Clean
	$(call Build/Compile/Default,clean)
endef

define Package/flow_button_gateway/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/files/set_led.sh $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/files/flow_button_gateway_continuous.sh $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/files/flow_button_gateway_appd $(1)/etc/init.d/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/files/flow_button_gateway_continuousd $(1)/etc/init.d/
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
