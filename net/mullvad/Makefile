#
# Copyright (C) 2026 Markus Pettersson (https://www.0x23.se)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mullvad
PKG_VERSION:=2026.2_beta1
PKG_RELEASE:=1

PKG_SOURCE:=mullvadvpn-app-2026.2-beta1.tar.gz
PKG_SOURCE_SUBDIR=mullvadvpn-app-2026.2-beta1
PKG_SOURCE_URL:=https://codeload.github.com/mullvad/mullvadvpn-app/tar.gz/2026.2-beta1?
PKG_HASH:=e193f490d5a94bf165e4d687a0dd2eeafeaa6caacab6509a9b58e1338ea9faed

PKG_MAINTAINER:=Markus Pettersson <m@0x23.se>
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DIR:=$(BUILD_DIR)/mullvadvpn-app-2026.2-beta1
PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1
# mullvad crate manifest is not in the project root.
MAKE_PATH=mullvad-cli

include $(INCLUDE_DIR)/package.mk
include ../../lang/rust/rust-package.mk

# Ensure lock file remains unchanged.
RUST_PKG_LOCKED:=1

define Package/mullvad
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=Privacy preserving VPN
  URL:=https://mullvad.net
  DEPENDS:=$(RUST_ARCH_DEPENDS) +mullvad-daemon
  PROVIDES:=mullvad
endef

define Package/mullvad/description
  Mullvad VPN command line interface.
endef

$(eval $(call RustBinPackage,mullvad))
$(eval $(call BuildPackage,mullvad))
