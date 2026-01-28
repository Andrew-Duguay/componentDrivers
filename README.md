# componentDrivers
This repo contains baremetal-c drivers to operate external components such as OLED displays or joysticks.
The supporting drivers are lightweight, custom drivers and can be found here:
https://github.com/Andrew-Duguay/stm32drivers

## ssd1306
The configuration and control of the ssd1306 chip in the OLED screen is in accordance with direction from the reference manual here:
https://cdn-shop.adafruit.com/datasheets/SSD1306.pdf
The init function uses a hard-coded sequence of commands to configure the OLED screen as directed on section 3 of the Application note (found PDF page 64)

1. Contains a wrapper API to use I2C communications to send data to the SSD1306 GDDRAM.
2. Additional files add functionality for graphics and text
3. Config header allows key values to be changed to adjust driver to different screen sizes.
4. Required peripherals: PB8, PB9, I2C1
5. Requires 1KB RAM for GDDRAM buffer

## joystick
Uses ADC driver init ADC pin and to convert jostick potentiometer voltage. Also configures registers for a GPIO pin to read the SW button.

1. Initializes ADC module on pa1 to read 1 axis of joystick movement
2. Initializes general input mode using internal pull-up resistors on pa0 to read the built in joystick switch.
3. automatically debounces switch press using timer drivers.
4. Required peripherals: timer1, adc1, pa0 and pa1

