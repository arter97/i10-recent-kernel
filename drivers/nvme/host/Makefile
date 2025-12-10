# SPDX-License-Identifier: GPL-2.0

ccflags-y				+= -I$(src)

obj-m			+= nvme-core.o
obj-$(CONFIG_BLK_DEV_NVME)		+= nvme.o
obj-m		+= nvme-fabrics.o
obj-m			+= nvme-rdma.o
obj-m			+= nvme-fc.o
obj-m			+= nvme-tcp.o
obj-m			+= i10-host.o

nvme-core-y				:= core.o ioctl.o
nvme-core-$(CONFIG_TRACING)		+= trace.o
nvme-core-m	+= multipath.o
nvme-core-$(CONFIG_NVM)			+= lightnvm.o
nvme-core-$(CONFIG_BLK_DEV_ZONED)	+= zns.o
nvme-core-$(CONFIG_FAULT_INJECTION_DEBUG_FS)	+= fault_inject.o
nvme-core-m		+= hwmon.o

nvme-y					+= pci.o

nvme-fabrics-y				+= fabrics.o

nvme-rdma-y				+= rdma.o

nvme-fc-y				+= fc.o

nvme-tcp-y				+= tcp.o

i10-host-y				+= i10.o

PWD := $(shell pwd)

ifeq ($(KVERSION),)
  KVERSION := $(shell uname -r)
endif

all:
	make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean
