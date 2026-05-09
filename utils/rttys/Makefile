#
# Copyright (C) 2026 Jianhui Zhao
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rttys
PKG_VERSION:=5.5.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/zhaojh329/rttys/tar.gz/refs/tags/v$(PKG_VERSION)?
PKG_HASH:=50e4ac22c869a731e68ff01fd12ab6e31e231fae8693672566d22418e41db22a

PKG_MAINTAINER:=Jianhui Zhao <zhaojh329@gmail.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=github.com/zhaojh329/rttys/v5
GO_PKG_BUILD_PKG:=github.com/zhaojh329/rttys/v5
GO_PKG_LDFLAGS:=-s -w

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/rttys
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Terminal
  TITLE:=The server side for rtty
  URL:=https://github.com/zhaojh329/rttys
  DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/rttys/description
  rttys is the server-side component of rtty remote terminal system.
endef

define Package/rttys/conffiles
/etc/config/rttys
endef

define Package/rttys/install
	$(call GoPackage/Package/Install/Bin,$(1))
	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d
	$(INSTALL_CONF) ./files/rttys.config $(1)/etc/config/rttys
	$(INSTALL_BIN) ./files/rttys.init $(1)/etc/init.d/rttys
endef

$(eval $(call GoBinPackage,rttys))
$(eval $(call BuildPackage,rttys))
