PROJECT = hello
BUILDDIR = build
GRUBFILE_ORIG = grub_file
BOOTCD := $(BUILDDIR)/cd
GRUBMENU := $(BOOTCD)/boot/grub/menu.lst
BINFILE := $(BOOTCD)/boot/$(PROJECT).elf
GRUBFILE := $(BOOTCD)/boot/grub/stage2_eltorito

$(BOOTCD):
	@-if [ ! -e $(BOOTCD) ]; then mkdir -p $(BOOTCD)/boot/grub ; fi;

$(GRUBMENU): $(BOOTCD)
	@echo "default 0" > $(GRUBMENU)
	@echo "timeout=0" >> $(GRUBMENU)
	@echo "title $(PROJECT)" >> $(GRUBMENU)
	@echo "root (cd)" >> $(GRUBMENU)
	@echo "kernel /boot/$(PROJECT).elf" >> $(GRUBMENU)
	@echo "boot" >> $(GRUBMENU)

$(GRUBFILE): $(BOOTCD)
	@echo "making grubfile ..."
	@cp -a $(GRUBFILE_ORIG) $(GRUBFILE)

CC = gcc
CFLAGS = -O3 -m32 -Wall -ffreestanding -nostdlib -fno-stack-protector
%.o: %.c 
	@$(CC) $(CFLAGS) -c -o $@ $<
%.o: %.S
	@$(CC) $(CFLAGS) -c -o $@ $<

LDFLAGS = -O3 -melf_i386 -e arch_start -Ttext=0x100000
$(BINFILE): hello.o startup.o 
	@echo "making bin file..."
	@ld $(LDFLAGS) startup.o hello.o -o $(BINFILE)	

iso: $(GRUBFILE)
	@mkisofs -J -R -b boot/grub/stage2_eltorito \
		 -no-emul-boot -boot-load-size 4 -boot-info-table -V $(PROJECT) \
		 -A $(PROJECT) -o $(PROJECT).iso $(BOOTCD) 2>/dev/null

all: clean $(GRUBMENU) $(BINFILE) iso
	@echo "making all ..."

clean:
	@-echo "Cleaning ..."
	@-rm -rf *.o *.elf $(PROJECT).iso $(BUILDDIR)
