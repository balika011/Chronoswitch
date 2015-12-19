release: all
	cp $(TARGET).prx $(TARGET660).prx
	psp-fixup-imports -m 631mapfile.txt $(TARGET).prx
	psp-fixup-imports -m 660mapfile.txt $(TARGET660).prx
	../bin/psp-packer $(TARGET).prx
	../bin/psp-packer $(TARGET660).prx
	bin2c $(TARGET).prx ../$(TARGET).h $(TARGET)
	bin2c $(TARGET660).prx ../$(TARGET660).h $(TARGET660)
	rm -f $(TARGET660).prx

TARGET = downgrade_ctrl
TARGET660 = downgrade660_ctrl
OBJS = main.o utils.o patch_table.o decrypt.o pspdecrypt.o extra_stubs.o

INCDIR = ../include
CFLAGS = -Os -G0 -Wall -fno-pic -fshort-wchar
ASFLAGS = $(CFLAGS)

BUILD_PRX = 1
PRX_EXPORTS = exports.exp

PSP_FW_VERSION = 660

USE_KERNEL_LIBS=1
USE_KERNEL_LIBC=1

LIBDIR = ../lib
LDFLAGS = -mno-crt0 -nostartfiles
LIBS = -lpspsystemctrl_kernel

PSPSDK=$(shell psp-config --pspsdk-path)
include $(PSPSDK)/lib/build.mak

