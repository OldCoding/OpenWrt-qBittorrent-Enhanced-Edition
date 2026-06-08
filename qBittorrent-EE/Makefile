include $(TOPDIR)/rules.mk

PKG_NAME:=qBittorrent-EE
PKG_VERSION:=5.1.3.10
PKG_RELEASE:=4

PKG_SOURCE:=qBittorrent-Enhanced-Edition-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/c0re100/qBittorrent-Enhanced-Edition/tar.gz/release-$(PKG_VERSION)?
PKG_HASH:=b153428db354775de59b850751ad9d6bafb418dde115b3208b41eab14308f6d1
PKG_BUILD_DIR:=$(BUILD_DIR)/qBittorrent-Enhanced-Edition-release-$(PKG_VERSION)

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING
PKG_CPE_ID:=cpe:/a:qbittorrent:qbittorrent

PKG_BUILD_DEPENDS:=qt6tools/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/qBittorrent-EE
  SUBMENU:=BitTorrent
  SECTION:=net
  CATEGORY:=Network
  TITLE:=bittorrent client programmed in C++ / Qt
  URL:=https://github.com/c0re100/qBittorrent-Enhanced-Edition
  DEPENDS:=+libtorrent-rasterbar +libQt6Core +libQt6Network +libQt6Sql \
    +libQt6Xml +qt6-plugin-libqopensslbackend +qt6-plugin-libqsqlite
  CONFLICTS:=qbittorrent
endef

define Package/qBittorrent-EE/description
  qBittorrent is a bittorrent client programmed in C++ / Qt that uses
  libtorrent (sometimes called libtorrent-rasterbar) by Arvid Norberg.
  It aims to be a good alternative to all other bittorrent clients out
  there. qBittorrent is fast, stable and provides unicode support as
  well as many features.
endef

CMAKE_OPTIONS+= \
	-DGUI=OFF \
	-DQT6=ON \
	-DSTACKTRACE=OFF \
	-DWEBUI=ON \
	-DQT_ADDITIONAL_PACKAGES_PREFIX_PATH=$(STAGING_DIR_HOSTPKG)

define Package/qBittorrent-EE/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/qbittorrent-nox $(1)/usr/bin/qBittorrentEE-nox
endef

$(eval $(call BuildPackage,qBittorrent-EE))
