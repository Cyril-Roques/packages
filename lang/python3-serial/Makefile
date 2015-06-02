#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-serial
PKG_VERSION:=2.7
PKG_RELEASE:=1

PKG_LICENSE:=Apache 2.0
PKG_MAINTAINER:=Cyril Roques <cyril.roques@maplehightech.com>

PKG_SOURCE:=pyserial-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/p/pyserial
PKG_MD5SUM:=794506184df83ef2290de0d18803dd11
PKG_SOURCE_SUBDIR:=pyserial-$(PKG_VERSION)

PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-serial
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python Serial Port Extension
  URL:=http://pyserial.sourceforge.net
  DEPENDS:=+python3
endef

define Package/python3-serial/description
  serial port python bindings
endef

UNPACK_CMD=gzip -dc "$(DL_DIR)/$(PKG_SOURCE)" | tar -C $(PKG_BUILD_DIR) -xf -


define Build/Compile
	echo "BUILD ________________________________________________________________"
	echo $(PKG_BUILD_DIR)
	echo $(PYTHON_PKG_DIR)
	echo $(PYTHON3_PKG_DIR)
	echo $(PKG_INSTALL_DIR)
	echo $(INSTALL_DIR)
	$(call Build/Compile/Py3Mod,pyserial-$(PKG_VERSION), \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)

endef

define Package/python3-serial/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python3-serial))
