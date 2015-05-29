#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-pyserial
PKG_VERSION:=2.7
PKG_RELEASE:=1

PKG_LICENSE:=Apache 2.0
PKG_MAINTAINER:=Cyril Roques <cyril.roques@maplehightech.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/pyserial
PKG_MD5SUM:=794506184df83ef2290de0d18803dd11

PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python-package.mk)

define Package/python3-pyserial
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python Serial Port Extension
  URL:=http://pyserial.sourceforge.net
  DEPENDS:=+python3-base
endef

define Package/python3-pyserial/description
  serial port python bindings
endef

define Build/Compile
	$(call Build/Compile/PyMod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-pyserial/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python3-pyserial))
