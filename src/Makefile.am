# SPDX-License-Identifier: BSD-3-Clause
# Copyright 2018 Jonathan Ribas, FraudBuster. All rights reserved.

bin_PROGRAMS		=	dpdk-replay
dpdk_replay_SOURCES	=	main.c \
						cpus.c \
						dpdk.c \
						pcap.c \
						utils.c
LD_DPDK=$(shell pkg-config --cflags --libs libdpdk --static ) -mssse3
dpdk_replay_CFLAGS	:=	$(CFLAGS) -I/usr/include/dpdk -march=native -I$(includedir)
dpdk_replay_LDFLAGS	:=	$(LDFLAGS) -L$(libdir) -pthread -lnuma -lm -ldl \
						-Wl,--whole-archive -Wl,--start-group \
						$(LD_DPDK) -lm \
						-Wl,--end-group -Wl,--no-whole-archive
