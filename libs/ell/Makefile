include $(TOPDIR)/rules.mk

PKG_NAME:=ell
PKG_VERSION:=0.78
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://git.kernel.org/pub/scm/libs/ell/ell.git
PKG_SOURCE_VERSION:=$(PKG_VERSION)
PKG_MIRROR_HASH:=f748e96575dc3eb6b98a3feb6334b8df011c304d7c9ee467d797121f5281d408

PKG_MAINTAINER:=Daniel Golle <daniel@makrotopia.org>
PKG_LICENSE:=GPL-2.0-only
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/ell
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=Embedded Linux Library
	URL:=https://patchwork.kernel.org/project/ell/
endef

define Package/ell/description
	ELL (Embedded Linux Library) provides core, low-level functionality for system daemons.
	It integrates with standard libc functionality and replaces some parts of it with more optimal implementations.
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/ell $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libell.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/ell.pc $(1)/usr/lib/pkgconfig/
endef

define Package/ell/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libell.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,ell))
