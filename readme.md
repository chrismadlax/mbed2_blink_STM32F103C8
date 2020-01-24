make mbed offline development environment use mbed-CLI

1. download & install mbed-cli tool from...

	https://github.com/ARMmbed/mbed-cli-windows-installer/releases

2. upgrade python pip manager...

	python -m pip install --upgrade pip

3. make workspace directory...

	ex: "C:\Users\<username>\Documents\mbed2"

4. set GNU ARM compiler path in mbed global value...

	mbed config -G GCC_ARM_PATH "C:\Program Files (x86)\GNU Tools ARM Embedded\6 2017-q2-update\bin"
	
5. clone "mbed2_blink" repository...

	git clone https://github.com/chrismadlax/mbed2_blink_STM32F103C8.git

6. change directory to mbed2_blink_STM32F103C8...

	cd mbed2_blink_STM32F103C8
	
7. deploy mbed tools library...
	
	mbed deploy

	[mbed] Working path "C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8" (program)
	[mbed] Adding library "mbed" from "https://os.mbed.com/users/mega64/code/mbed-STM32F103C8" at rev #8b0b02bf146f
	[mbed] Couldn't find build tools in your program. Downloading the mbed 2.0 SDK tools...
	[mbed] Updating the mbed 2.0 SDK tools...

8. set TOOLchain & TARGET ,set GCC_ARM compiler & use NUCLEO-F103RB as the target name for STM32F103C8 ...

	mbed toolchain GCC_ARM

	[mbed] Working path "C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8" (program)
	[mbed] GCC_ARM now set as default toolchain in program "mbed2_blink_STM32F103C8"
	
	mbed target NUCLEO_F103RB

	[mbed] Working path "C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8" (program)
	[mbed] NUCLEO_F103RB now set as default target in program "mbed2_blink_STM32F103C8"

9. check config set...

	mbed config --list

	[mbed] Working path "C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8" (program)
	[mbed] Global config:
	GCC_ARM_PATH=C:\Program Files (x86)\GNU Tools ARM Embedded\6 2017-q2-update\bin
	
	[mbed] Local config (C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8):
	TOOLCHAIN=GCC_ARM
	TARGET=NUCLEO_F103RB

10. then run mbed compiler...

	mbed compile

	[mbed] Working path "C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8" (program)
	Using targets from C:\Users\chrismadlax\Documents\temp\mbed2_blink_STM32F103C8\mbed\targets\targets.json
	Building project mbed2_blink_STM32F103C8 (NUCLEO_F103RB, GCC_ARM)
	Scan: mbed2_blink_STM32F103C8
	Link: mbed2_blink_STM32F103C8
	Elf2Bin: mbed2_blink_STM32F103C8
	| Module        |     .text |    .data |    .bss |
	|---------------|-----------|----------|---------|
	| [fill]        |    44(+0) |    0(+0) |  11(+0) |
	| [lib]\c.a     | 17049(+0) | 2472(+0) |  89(+0) |
	| [lib]\gcc.a   |  3868(+0) |    0(+0) |   0(+0) |
	| [lib]\misc    |   252(+0) |   16(+0) |  28(+0) |
	| main.o        |    72(+0) |    4(+0) |  28(+0) |
	| mbed\drivers  |   118(+0) |    4(+0) | 100(+0) |
	| mbed\hal      |   404(+0) |    0(+0) |   8(+0) |
	| mbed\platform |  1095(+0) |    4(+0) | 269(+0) |
	| mbed\targets  |  6830(+0) |    4(+0) | 431(+0) |
	| Subtotals     | 29732(+0) | 2504(+0) | 964(+0) |
	Total Static RAM memory (data + bss): 3468(+0) bytes
	Total Flash memory (text + data): 32236(+0) bytes
	
	Image: .\BUILD\NUCLEO_F103RB\GCC_ARM\mbed2_blink_STM32F103C8.bin

11. you get a bin file >> "mbed2_blink_STM32F103C8.bin"
    use j-link or UART to flash program on STM32F103C8 , then press RST button on boards to run new program.
	
enjoy fun :)