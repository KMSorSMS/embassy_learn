TARGET := embassy-stm32f401re-examples

OBJDUMP := rust-objdump --arch-name=arm
OBJCOPY := rust-objcopy --binary-architecture=arm

ENTRY_PA := 0x08000000

bin: $(TARGET)
	@echo "Build done"

$(TARGET): target/thumbv7em-none-eabi/release/$(TARGET)
	$(OBJCOPY) -O binary $< target/thumbv7em-none-eabi/release/$@.bin
debug:
	openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c init -c "halt" -c "flash write_image erase target/thumbv7em-none-eabi/release/${TARGET}.bin 0x8000000"
download:
	openocd -f interface/stlink.cfg -f target/stm32f4x.cfg -c init -c "halt" -c "flash write_image erase target/thumbv7em-none-eabi/release/embassy-stm32f401re-examples.bin 0x8000000" -c "reset" -c "shutdown"