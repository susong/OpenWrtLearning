include $(TOPDIR)/rules.mk

PKG_NAME:=openWrtLib
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/openWrtLib
	SECTION:=whatever
	CATEGORY:=whatever
	TITLE:=openWrtLib
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile/openWrtLib
	$(MAKE) -C $(PKG_BUILD_DIR) \
	CC="$(TARGET_CC)" \
	AR="$(TARGET_AR)" \
	CFLAGS="$(TARGET_CFLAGS) -funwind-tables -mfloat-abi=hard" -Wall  \
	LDFLAGS="$(TARGET_LDFLAGS)" \
	LD="$(TARGET_CROSS)ld" \
	CONFIG_PREFIX="$(PKG_BUILD_DIR)" \
	LIBS="" \
	all
endef

define Package/openWrtLib/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libopenWrtLib.so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,openWrtLib))