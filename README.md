# NanoBootloaderBurner
 Hardware programmer for programming (bootloader to) Arduino Nano compatible development board
 Purpose of this repository is to share the design files for board shown in my YouTube video: [https://youtu.be/Mxi_6IfEGUE](https://youtu.be/Mxi_6IfEGUE)
 
 Holes for the target Nano have been increased to 1.1mm, which should allow using cheap pogo-pins instead of female headers. This modification hasn't been tested yet.
 
 This programmer is ment to be super simple and it works in it's current form. Possible "bug fixes" may be committed at some point, but otherwise this project is considered finished.
 
## Firmware
 For firmware, you can use "ArduinoISP" -example sketch that comes with the Arduino IDE. 
 Pin configuration is following (Can be found around line 75 in example sketch, edit if needed):
 * RESET = 10
 * LED_ERR = 7
 * LED_PMODE = 8
 
 Bare ATMega328p doesn't have bootloader in it from the factory, so you need to use another ISP programmer to program either that ArduinoISP -sketch or Arduino bootloader into the chip. If you decide to program bootloader, you can then use the USB-port to program the actual firmware to the chip. Bootloader method allows updating the firmware via USB-port and external programmer is only needed for initial bootloader programming.
 
## USAGE
 Keep in mind, using any ISP programmer can and will probably erase everything on the microcontroller that is being programmed. This has potential of bricking the microcontroller, making it unusable, unless one has a more expensive programmer to fix it. Use at your own risk.
 
 Once the onboard ATMega328p has the ArduinoISP running, you can use this device to program bootloaders to Arduino Nano -compatible boards using Arduino IDE.
 Make following selections in the Arduino IDE:
 * Tools->Board->Arduino Nano
 * Tools->Processor->ATmega328p (Or ATmega168p, if your Nano has that MCU)
 * Tools->Programmer->"Arduino as ISP"
 * Tools->Port-> The com port of the programmer
 
 Then you can plug the Nano to the programmer, and select Tools->"Burn bootloader" in Arduino IDE to program the fresh bootloader to your Nano.
 