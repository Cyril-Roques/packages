#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-zeroconf
PKG_REV:=420b5b34aafee0fdf3b81877a999e4f4eb5b7f09
PKG_VERSION:=0.17.1
PKG_RELEASE:=1

PKG_LICENSE:=Apache 2.0
PKG_MAINTAINER:=Cyril Roques <cyril.roques@maplehightech.com>

PKG_SOURCE_VERSION:=$(PKG_REV)
PKG_SOURCE_URL:=git://github.com/Cyril-Roques/git://github.com/
PKG_REV:=420b5b34aafee0fdf3b81877a999e4f4eb5b7f09
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_SOURCE_SUBDIR).tar.gz
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_SOURCE_SUBDIR)


PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python3-zeroconf
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Multicast DNS Service Discovery for Python
  URL:=https://github.com/Cyril-Roques/python-zeroconf
  DEPENDS:=+python3-base
endef

define Package/python3-zeroconf/description
  This is fork of pyzeroconf, Multicast DNS Service Discovery for Python, originally by Paul Scott-Murphy (https://github.com/paulsm/pyzeroconf), modified by William McBrine (https://github.com/wmcbrine/pyzeroconf).

endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-zeroconf/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python3-zeroconf))
