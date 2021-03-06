#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2014 Alexander Pyhalov.  All rights reserved.
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME= gdk-pixbuf

COMPONENT_VERSION= 2.31.6
COMPONENT_REVISION= 1
COMPONENT_SUMMARY= GNOME gdk-pixbuf
COMPONENT_SRC= $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE= $(COMPONENT_SRC).tar.xz
COMPONENT_ARCHIVE_HASH= \
  sha256:111203d6f295d69d36e7190204248331cd37285130ac483becdedcd3f0135d18
COMPONENT_ARCHIVE_URL= \
  ftp://ftp.gnome.org/pub/GNOME/sources/$(COMPONENT_NAME)/2.31/$(COMPONENT_ARCHIVE)
COMPONENT_PROJECT_URL = http://cairographics.org

include $(WS_MAKE_RULES)/prep.mk
include $(WS_MAKE_RULES)/configure.mk
include $(WS_MAKE_RULES)/ips.mk

COMPONENT_PREP_ACTION = ( cd $(@D) && aclocal  -I m4 && \
				libtoolize --force --copy&&\
				autoheader &&\
				automake -a -f -c --gnu &&\
				autoconf )


CONFIGURE_OPTIONS.32 += --sysconfdir=/etc
CONFIGURE_OPTIONS.64 += --sysconfdir=/etc/$(MACH64)
CONFIGURE_OPTIONS += --with-x11

# CFLAGS are not passed to compiler when g-ir-scanner is used
COMPONENT_BUILD_ENV += CFLAGS="$(CFLAGS)"

COMPONENT_POST_INSTALL_ACTION.32 = ( LD_LIBRARY_PATH=$(PROTO_DIR)/usr/lib \
	$(PROTO_DIR)/usr/bin/gdk-pixbuf-query-loaders \
	   $(PROTO_DIR)/usr/lib/gdk-pixbuf-2.0/*/loaders/*.so	| sed -e "s:$(PROTO_DIR)::" \
	   > $(PROTO_DIR)/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders.cache )

COMPONENT_POST_INSTALL_ACTION.64 = ( LD_LIBRARY_PATH=$(PROTO_DIR)/usr/lib/$(MACH64) \
	$(PROTO_DIR)/usr/bin/$(MACH64)/gdk-pixbuf-query-loaders \
	   $(PROTO_DIR)/usr/lib/$(MACH64)/gdk-pixbuf-2.0/*/loaders/*.so	| sed -e "s:$(PROTO_DIR)::" \
	   > $(PROTO_DIR)/usr/lib/$(MACH64)/gdk-pixbuf-2.0/2.10.0/loaders.cache )

COMPONENT_POST_INSTALL_ACTION=$(COMPONENT_POST_INSTALL_ACTION.$(BITS))

COMPONENT_BUILD_ENV += CC="$(CC)"

build: $(BUILD_32_and_64)

install: $(INSTALL_32_and_64)

# TOTAL: 77
# PASS:  71
# SKIP:  0
# XFAIL: 0
# FAIL:  0
# XPASS: 0
# ERROR: 6

test: $(TEST_32_and_64)

REQUIRED_PACKAGES += image/library/libjpeg6
REQUIRED_PACKAGES += image/library/libjpeg6-ijg
REQUIRED_PACKAGES += image/library/libpng16
REQUIRED_PACKAGES += image/library/libtiff
REQUIRED_PACKAGES += library/glib2
REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += system/library/math
REQUIRED_PACKAGES += x11/library/libx11
