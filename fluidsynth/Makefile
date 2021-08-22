#
# This software is licensed under the Public Domain.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=fluidsynth
PKG_VERSION:=1.1.11
PKG_RELEASE:=1

PKG_MAINTAINER:=Adam Chasen <adam@chasen.name>
PKG_LICENSE:=CC0-1.0

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/FluidSynth/fluidsynth/archive/refs/tags/

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
# to provide intl lib
include $(INCLUDE_DIR)/nls.mk

# related to https://github.com/chaseadam/openwrt-zipit-packages/issues/1
# /root/openwrt-zipit/staging_dir/target-arm_xscale_musl-1.1.14_eabi/usr/lib/libreadline.so: undefined reference to `tputs'
TARGET_LDFLAGS+= -lsalsa -lncurses

define Package/$(PKG_NAME)
	SECTION:=utils
	# Select package by default
	#DEFAULT:=y
	CATEGORY:=Utilities
	TITLE:=fluidsynth
	URL:=https://www.fluidsynth.org
	DEPENDS:=+alsa-lib +libncurses +libdbus +glib2 +libintl-full +libreadline +libsndfile
endef

define Package/$(PKG_NAME)/description
	Real-time software synthesizer
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin $(1)/usr/lib 
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/fluidsynth $(1)/usr/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/libfluidsynth.so* $(1)/usr/lib/

endef

$(eval $(call BuildPackage,$(PKG_NAME)))
