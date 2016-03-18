include $(TOPDIR)/rules.mk

PKG_NAME:=libflow-ex
PKG_VERSION:=2016-03-18
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/FlowM2M/FlowLibs-C-examples.git

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)

CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/libflow-ex
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:= +libflow
  TITLE:=Libflow examples
endef

define Package/libflow-ex/description
  Libflowcore and Libflowmessaging examples.
endef

define Package/libflow-ex/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
