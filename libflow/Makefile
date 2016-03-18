include $(TOPDIR)/rules.mk

PKG_NAME:=libflow
PKG_VERSION:=2016-03-18
PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/FlowM2M/FlowLibs-C-binary.git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/libflow
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+libc +libpthread +libm +librt +libgnutls
  TITLE:=FlowCloud Core and Messaging Libraries by Imagination
endef

define Package/libflow/description
        Core Library for FlowCloud SDK APIS.
endef

define Build/Compile

endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/libflow/usr/lib/libflowcore* $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/libflow/usr/lib/libflowmessaging* $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) -Rf $(PKG_BUILD_DIR)/libflow/usr/include/* $(1)/usr/include
endef

define Package/libflow/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/libflow/usr/lib/libflowcore* $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/libflow/usr/lib/libflowmessaging* $(1)/usr/lib
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
