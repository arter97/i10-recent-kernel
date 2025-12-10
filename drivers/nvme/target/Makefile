# SPDX-License-Identifier: GPL-2.0

ccflags-y				+= -I$(src)

obj-m		+= nvmet.o
obj-m		+= nvme-loop.o
obj-m		+= nvmet-rdma.o
obj-m		+= nvmet-fc.o
obj-m	+= nvme-fcloop.o
obj-m		+= nvmet-tcp.o
obj-m		+= i10-target.o

nvmet-y		+= core.o configfs.o admin-cmd.o fabrics-cmd.o \
			discovery.o io-cmd-file.o io-cmd-bdev.o
nvmet-m	+= passthru.o
nvmet-$(CONFIG_BLK_DEV_ZONED)		+= zns.o
nvme-loop-y	+= loop.o
nvmet-rdma-y	+= rdma.o
nvmet-fc-y	+= fc.o
nvme-fcloop-y	+= fcloop.o
nvmet-tcp-y	+= tcp.o
i10-target-y	+= i10.o
nvmet-$(CONFIG_TRACING)	+= trace.o

PWD := $(shell pwd)

ifeq ($(KVERSION),)
  KVERSION := $(shell uname -r)
endif

all:
	make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean
