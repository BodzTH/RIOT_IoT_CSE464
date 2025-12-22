# name of your application
APPLICATION = default

# If no BOARD is found in the environment, use this default:
BOARD ?= native

# This has to be the absolute path to the RIOT base directory:
RIOTBASE ?= $(CURDIR)/../../..

DEVELHELP ?= 1
QUIET ?= 1

# --- CORE SHELL MODULES ---
USEMODULE += shell
USEMODULE += shell_cmds_default
USEMODULE += ps
USEMODULE += saul_default

# --- NETWORK & RPL (ADD THIS SECTION) ---
# 1. Enable the default network device (TAP for native)
USEMODULE += netdev_default
USEMODULE += auto_init_gnrc_netif

# 2. Enable IPv6
USEMODULE += gnrc_ipv6_default

# 3. Enable ICMPv6 (so you can ping)
USEMODULE += gnrc_icmpv6_echo

# 4. Enable RPL (CRITICAL for Task Group 1)
# This ensures your modified 'of0.c' is actually compiled and linked!
USEMODULE += gnrc_rpl
USEMODULE += auto_init_gnrc_rpl

FEATURES_OPTIONAL += netif
FEATURES_OPTIONAL += periph_rtc

ifneq (,$(filter msba2,$(BOARD)))
  USEMODULE += mci
  USEMODULE += random
endif

include $(RIOTBASE)/Makefile.include
include $(RIOTMAKE)/default-radio-settings.inc.mk
