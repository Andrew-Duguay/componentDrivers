# ComponentDrivers | Bare-Metal C Library

A collection of lightweight, zero-dependency (CMSIS-only) C drivers for interfacing STM32 microcontrollers with external peripherals. Designed for high-performance robotics and embedded systems.

## 🛠 Dependencies
This library requires my core STM32 peripheral drivers for I2C, ADC, and Timers:
👉 [stm32drivers Repository](https://github.com/Andrew-Duguay/stm32drivers)

---

## 📺 SSD1306 OLED Driver (I2C)
A memory-efficient driver for 128x64 or 128x32 OLED displays based on the SSD1306 chipset.

### Key Features
* **Optimized Buffer:** Implements a 1KB local GDDRAM buffer for fast frame updates.
* **Extended Graphics:** Includes a custom graphics library for primitive shapes and text rendering.
* **Configurable:** Display dimensions are adjustable via `ssd1306_conf.h`.

### Requirements
* **Peripherals:** I2C1 (PB8/PB9)
* **Memory:** 1KB RAM for display shadowing.
* **Documentation:** [SSD1306 Datasheet](https://cdn-shop.adafruit.com/datasheets/SSD1306.pdf)

---

## 🕹 Analog Joystick Driver
A robust driver for 2-axis analog joysticks with integrated pushbutton support.

### Key Features
* **Non-Blocking Read:** Uses ADC1 to sample potentiometer voltages.
* **Hardware Debouncing:** Implemented via Timer1 interrupts to ensure clean switch transitions.
* **Pull-up Config:** Internal pull-up resistors configured for the SW pin (PA0) to minimize external component count.

### Requirements
* **Pins:** PA1 (ADC), PA0 (GPIO Input)
* **Peripherals:** ADC1, TIM1
