all: annoy-o-tron.hex

annoy-o-tron.elf: annoy-o-tron.c
	avr-gcc -mmcu=atmega328 -DF_CPU=20000000 -std=c99 -Wall -Wextra -Werror -Os -o $@ $^

annoy-o-tron.hex: annoy-o-tron.elf
	avr-objcopy -j .text -j .data -O ihex annoy-o-tron.elf annoy-o-tron.hex
	avr-size annoy-o-tron.elf

install: annoy-o-tron.hex
	sudo avrdude -p atmega328 -c avrispmkII -U flash:w:$^:a

clean: clean_cscope
	rm -rf annoy-o-tron.elf annoy-o-tron.hex

cscope:
	cscope -Rb

clean_cscope:
	rm -rf cscope.out

.PHONY: all clean clean_cscope cscope install
