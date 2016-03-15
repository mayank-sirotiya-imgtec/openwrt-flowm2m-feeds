include $(TOPDIR)/rules.mk

PKG_NAME:=libflow
PKG_VERSION:=dev
PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/FlowM2M/FlowLibs-C.git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

PKG_INSTALL:= 1

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
	$(call Build/Compile/Default,DIR__STAGING=$(PKG_BUILD_DIR)/tmp/usr -f Makefile.libflowcore)
	$(call Build/Compile/Default,DIR__STAGING=$(PKG_BUILD_DIR)/tmp/usr -f Makefile.libflowmessaging)
endef

define Build/Install
	$(call Build/Install/Default,DIR__STAGING=$(PKG_BUILD_DIR)/tmp/usr install -f Makefile.libflowcore)
	$(call Build/Install/Default,DIR__STAGING=$(PKG_BUILD_DIR)/tmp/usr install -f Makefile.libflowmessaging)
endef

define Build/Clean
	$(call Build/Compile/Default,DIR__STAGING=$(PKG_BUILD_DIR)/tmp/usr clean -f Makefile.libflowcore)
	$(call Build/Compile/Default,DIR__STAGING=$(PKG_BUILD_DIR)/tmp/usr clean -f Makefile.libflowcore)
endef

define Package/libflow/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/tmp/usr/lib/libflowcore* $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/tmp/usr/lib/libflowcore* $(STAGING_DIR)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/tmp/usr/lib/libflowmessaging* $(1)/usr/lib
	$(CP) -Rf $(PKG_BUILD_DIR)/tmp/usr/lib/libflowmessaging* $(STAGING_DIR)/usr/lib
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) -Rf $(PKG_BUILD_DIR)/tmp/usr/include/* $(1)/usr/include
	$(CP) -Rf $(PKG_BUILD_DIR)/tmp/usr/include/* $(STAGING_DIR)/usr/include
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
