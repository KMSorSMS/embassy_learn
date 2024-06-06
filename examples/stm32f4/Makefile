TARGET := blinky

OBJDUMP := rust-objdump --arch-name=arm
OBJCOPY := rust-objcopy --binary-architecture=arm

ENTRY_PA := 0x08000000

$(TARGET): target/thumbv7em-none-eabi/release/$(TARGET)
	$(OBJCOPY) -O binary $< target/thumbv7em-none-eabi/release/$@.bin
debug:
	openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c init -c "halt" -c "flash write_image erase target/thumbv7em-none-eabi/release/blinky.bin 0x8000000"