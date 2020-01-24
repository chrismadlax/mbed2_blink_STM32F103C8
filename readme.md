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

8. set TOOLchain & TARGET ,set GCC_ARM compiler & use NUCLEO-F103RB as the target name for STM32F103C8 ...

	mbed toolchain GCC_ARM

	mbed target NUCLEO-F103RB

9. check config set...

	mbed config --list
	
10. then run mbed compiler...

	mbed compile

11. you get a bin file >> "mbed2_blink_STM32F103C8.bin"
    use j-link or UART to flash STM32F103C8move , then press RST button on boards to run new program.
	
enjoy fun