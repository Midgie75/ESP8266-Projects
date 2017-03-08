# Compile-Mongoose-for-ESP8266 [DRAFT]

Following steps are run in a Ubuntu Yakkety Virtual Box on a Windows 10 host.

1. Follow https://github.com/pfalcon/esp-open-sdk
2. Clone https://github.com/espressif/ESP8266_RTOS_SDK
3. Clone https://github.com/cesanta/mongoose
4. export SDK_PATH=/path/to/ESP8266_RTOS_SDK
5. export BIN_PATH=./bin
6. export PATH=/path/to/esp-open-sdk/xtensa-lx106-elf/bin:$PATH
7. https://github.com/cesanta/mongoose/tree/master/examples/ESP8266_RTOS
8. correct Makefile: LINKFLAGS -lgcc_sdk ---> -lgcc
9. run ./gen_misc.sh 
10. git clone https://github.com/espressif/esptool
11. sudo apt install python-pip
12. pip install esptool
13. sudo apt install arduino
14. complete shutdown of Vbox and restart -> FTDI231x now on /dev/ttyUSB0
15. change esptool.py: ESP_RAM_BLOCK   = 0x180
16. esptool.py --port /dev/ttyUSB0 --baud 115200 write_flash --flash_mode=dio --flash_size=detect 0x00000 ${BIN_PATH}/eagle.flash.bin 0x20000 ${BIN_PATH}/eagle.irom0text.bin 0x7e000 ${SDK_PATH}/bin/esp_init_data_default.bin
