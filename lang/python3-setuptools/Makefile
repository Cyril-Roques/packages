#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-setuptools
PKG_VERSION:=2.7
PKG_RELEASE:=1

PKG_LICENSE:=Apache 2.0
PKG_MAINTAINER:=Cyril Roques <cyril.roques@maplehightech.com>

PKG_SOURCE:=setuptools-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/s/setuptools
PKG_MD5SUM:=fd15d24ed1e4c95e56d8c6e812f3a84f
PKG_SOURCE_SUBDIR:=setuptools-$(PKG_VERSION)

PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-setuptools
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=python3-setuptools
  URL:=https://bitbucket.org/pypa/setuptools
  DEPENDS:=+python3
endef

define Package/python3-setuptools/description
  Easily download, build, install, upgrade, and uninstall Python packages
endef

UNPACK_CMD=gzip -dc "$(DL_DIR)/$(PKG_SOURCE)" | tar -C $(PKG_BUILD_DIR) -xf -


define Build/Compile
	$(call Build/Compile/Py3Mod,pyserial-$(PKG_VERSION), \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)

endef

define Package/python3-setuptools/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python3-setuptools))
