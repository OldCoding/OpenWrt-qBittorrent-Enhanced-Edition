include $(TOPDIR)/rules.mk

PKG_NAME:=qBittorrent-EE
PKG_VERSION:=5.1.3.10
PKG_RELEASE:=1
PKG_LICENSE:=GPL-2.0+

include $(INCLUDE_DIR)/package.mk

define Package/qBittorrent-EE
  SUBMENU:=BitTorrent
  SECTION:=net
  CATEGORY:=Network
  TITLE:=bittorrent client programmed in C++ / Qt
  DEPENDS:=
endef

PKG_ARCH_SUFFIX:=$(ARCH)

ifeq ($(ARCH),i386)
  PKG_ARCH_SUFFIX:=i686
endif

ifeq ($(ARCH),arm)
  ifdef CONFIG_HAS_FPU
    PKG_ARCH_SUFFIX:=arm-linux-musleabihf
  else
    PKG_ARCH_SUFFIX:=arm-linux-musleabi
  endif
endif

PKG_SOURCE:=qbittorrent-enhanced-nox_$(PKG_ARCH_SUFFIX)-linux-musl_static.zip
PKG_SOURCE_URL:=https://github.com/c0re100/qBittorrent-Enhanced-Edition/releases/download/release-$(PKG_VERSION)/
UNTAR_DIR:=$(BUILD_DIR)/$(PKG_NAME)
PKG_HASH:=skip

define Package/qBittorrent-EE/description
	qBittorrent-EE is based on qBittorrent, it's aimed at blocking leeching clients automatically.
endef

define Build/Prepare
	rm -rf $(UNTAR_DIR)
	mkdir -vp $(UNTAR_DIR)
	unzip $(DL_DIR)/$(PKG_SOURCE) -d $(UNTAR_DIR)
	mv -f $(UNTAR_DIR)/qbittorrent-nox $(UNTAR_DIR)/qBittorrentEE-nox
endef

define Build/Configure
endef

define Build/Compile
endef

define Package/qBittorrent-EE/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(UNTAR_DIR)/qBittorrentEE-nox $(1)/usr/bin
	chmod 755 $(1)/usr/bin/qBittorrentEE-nox
endef

$(eval $(call BuildPackage,qBittorrent-EE))