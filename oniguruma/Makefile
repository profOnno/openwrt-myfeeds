#
# Copyright (C) 2010-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libonig
PKG_VERSION:=5.9.6
PKG_RELEASE:=1
#PKG_REV:=e73951f3d1928591b3a9a60de11ae975a21e621f

#PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE:=onig-$(PKG_VERSION).tar.gz
#PKG_SOURCE_URL:=git://github.com/stedolan/jq
PKG_SOURCE_URL:= http://www.geocities.jp/kosako3/oniguruma/archive/
#PKG_SOURCE_PROTO:=http
#PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_SUBDIR:=onig-$(PKG_VERSION)
PKG_SOURCE_VERSION:=$(PKG_REV)


#PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
#PKG_SOURCE_URL:=http://www.greenwoodsoftware.com/jqless
#PKG_MD5SUM:=935b38aa2e73c888c210dedf8fd94f49

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=profOnno <profonno@kuopzi.nl>

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)/onig-$(PKG_VERSION)
PKG_INSTALL:=1
#PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libonig
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Oniguruma
  URL:=http://www.geocities.jp/kosako3/oniguruma
#  DEPENDS:=+libncurses
endef

#PKG_FIXUP:=autoreconf
#PKG_FIXUP:=patch-libtool
#PKG_FIXUP:=gettext-version

define Build/Configure
#    autoreconf -i
#    ./configure
#    make -j8
#    make check
#	(cd $(PKG_BUILD_DIR) && autoreconf -i)
#	(cd $(PKG_BUILD_DIR) && autoreconf -i)
#	$(call Build/Configure/Default,--disable-maintainer-mode --prefix=$(PKG_BUILD_DIR)/ipkg-install/)
#	$(call Build/Configure/Default,)
endef
#TARGET_CFLAGS = -std=c99
define Build/Compile
#	(cd $(PKG_BUILD_DIR) && make -j8)
	$(call Build/Compile/Default, -j8)
endef

define Package/libonig/Description
Oniguruma is a regular expressions library.
The characteristics of this library is that different character encoding
for every regular expression object can be specified.
(supported APIs: GNU regex, POSIX and Oniguruma native)
endef

#define Package/unrar/install
#        $(INSTALL_DIR) $(1)/usr/bin
#        $(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/unrar $(1)/usr/bin/
#endef

#define Build/Install
#	(cd $(PKG_BUILD_DIR) && make install)
#TARGET_CFLAGS += $(FPIC)
#$TARGET_LDFLAGS += -Wl,-rpath-link=$(STAGING_DIR)/usr/lib -lm

define Build/InstallDev
        $(INSTALL_DIR) $(1)/usr/{lib,include}
        $(INSTALL_DIR) $(1)/usr/lib/pkgconfig
        $(CP) $(PKG_INSTALL_DIR)/usr/lib/libonig* $(1)/usr/lib
        $(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* $(1)/usr/lib/pkgconfig
        $(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/libgonig/install
        $(INSTALL_DIR) $(1)/usr/lib
        $(CP) $(PKG_INSTALL_DIR)/usr/lib/libonig*so* $(1)/usr/lib/
endef
#endef

#define Package/onig/install
#	$(INSTALL_DIR) $(1)/usr/bin
#	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/jq $(1)/usr/bin/
#endef

$(eval $(call BuildPackage,libonig))
