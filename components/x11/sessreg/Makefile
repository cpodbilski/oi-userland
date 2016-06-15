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
# Copyright 2015 Aurelien Larcher
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=           sessreg
COMPONENT_VERSION=        1.1.0
COMPONENT_FMRI=           x11/session/sessreg
COMPONENT_CLASSIFICATION= System/X11
COMPONENT_SUMMARY=  sessreg - manage utmp/wtmp entries for non-init clients
COMPONENT_SRC=      $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=  $(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH= \
  sha256:551177657835e0902b5eee7b19713035beaa1581bbd3c6506baa553e751e017c
COMPONENT_ARCHIVE_URL= \
  http://www.x.org/releases/individual/app/sessreg-1.1.0.tar.bz2
COMPONENT_PROJECT_URL = http://www.x.org/
COMPONENT_LICENSE=      MIT License
COMPONENT_LICENSE_FILE= sessreg.license

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

PATH=/usr/gnu/bin:/usr/bin

build: $(BUILD_32_and_64)

install: $(INSTALL_32_and_64)

test: $(NO_TESTS)


REQUIRED_PACKAGES += system/library