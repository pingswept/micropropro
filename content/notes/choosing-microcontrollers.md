---
title: "Choosing microcontrollers"
draft: false
---

## Choosing a microcontroller ##

First off, there are two ways to buy a microcontroller. If you work at a large company, or at an engineering consulting firm, you can call any of the large microcontroller manufacturers, and they will be happy to send a salesperson to your office. They will give you free chips for testing and help you understand the different chips they sell. They do this because they expect that you will place an order of at least 100,000 chips.

If you are not in the situation where you can convince someone that you might place an order for 100,000 chips, you will need to get a chip from a distributor, like Digikey, Mouser, or Newark. They sell chips from 10 major players.

## The major players ##

* Microchip: PIC12, 16, 18, and 24
* Atmel (owned by Microchip since 2016)
* NXP
* Analog Devices
* Silicon Labs
* Freescale (formerly Motorola, owned by NXP since 2015)
* Infineon
* Cypress
* ST: STM32 ARM Cortex series
* Renesas
* Texas Instruments

There are two other manufacturers to keep in mind: Espressif and Nordic Semiconductor.

Espressif makes the ESP8266 and ESP32 series, which are frightenly cheap and popular among hobbyists.

Nordic makes the nRF52 series of Cortex M4 microcontrollers, which have embedded Bluetooth modules. They're probably the cheapest way to mess around with Bluetooth. Digikey sells their demo board as 1490-1073-ND for $10.00.

## Peripherals

Next, you can narrow your search down by what peripherals you need. Peripherals are hardware modules that are built into the chips. Examples include:
* UART
* SPI
* I2C
* PWM
* A/D
* DAC
* CAN
* USB
* BLE
* Wifi

Obviously, if you need 3 UARTs, 2 I2C ports, and a USB controller built-in, that narrows down your choices substantially.

## 8-bit vs 32-bit

Microcontrollers consume data and instructions in either 8 bit or 32 bit chunks. (There are also lots of weird microcontrollers, like the irritatingly named PIC16 series, which uses a 14-bit address bus, or others that use 16 or 24 bits.)

Fortunately, this choice is getting easier every day as the price of 32-bit parts is dropping rapidly. Right now, for a given clock speed, 8-bit devices are slower, but cheaper, while 32-bit devices are faster, but more expensive. Soon, 32-bit devices may be both cheaper and faster. Unless you are designing a high-volume product where price is crucial, you should lean toward a 32-bit part.
