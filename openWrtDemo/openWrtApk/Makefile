include $(TOPDIR)/rules.mk

PKG_NAME:=openWrtApk
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_BUILD_DIR := $(BUILD_DIR)/$(PKG_NAME)

include $(INCLUDE_DIR)/package.mk

define Package/openWrtApk
	SECTION:=whatever
	CATEGORY:=whatever
	TITLE:=openWrtApk
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(CP) ./src/* $(PKG_BUILD_DIR)/
endef

define Build/Compile/openWrtApk
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

define Package/openWrtApk/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/openWrtApk $(1)/bin/
endef

$(eval $(call BuildPackage,openWrtApk))