#
# Copyright (C) 2008-2011 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-netifaces
PKG_VERSION:=0.10.4
PKG_RELEASE:=1

PKG_LICENSE:=MIT
PKG_MAINTAINER:=Cyril Roques <cyril.roques@maplehightech.com>

PKG_SOURCE:=netifaces-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://pypi.python.org/packages/source/n/netifaces/
PKG_MD5SUM:=36da76e2cfadd24cc7510c2c0012eb1e
PKG_SOURCE_SUBDIR:=netifaces-$(PKG_VERSION)

PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk
$(call include_mk, python3-package.mk)

define Package/python3-netifaces
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Portable network interface information
  URL:= https://bitbucket.org/al45tair/netifaces
  DEPENDS:=+python3
endef

define Package/python3-netifaces/description
  It’s been annoying me for some time that there’s no easy way to get the address(es) of the machine’s network interfaces from Python. There is a good reason for this difficulty, which is that it is virtually impossible to do so in a portable manner. However, it seems to me that there should be a package you can easy_install that will take care of working out the details of doing so on the machine you’re using, then you can get on with writing Python code without concerning yourself with the nitty gritty of system-dependent low-level networking APIs.
  This package attempts to solve that problem.
endef

UNPACK_CMD=gzip -dc "$(DL_DIR)/$(PKG_SOURCE)" | tar -C $(PKG_BUILD_DIR) -xf -


define Build/Compile
	$(call Build/Compile/Py3Mod,netifaces-$(PKG_VERSION), \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)

endef

define Package/python3-netifaces/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)/
endef

$(eval $(call BuildPackage,python3-netifaces))
