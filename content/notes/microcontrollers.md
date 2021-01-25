---
title: "Microcontrollers"
draft: false
---

## Microcontroller vs. microprocessor

Both microcontrollers and microprocessors are small chunks of silicon encased in black plastic with little wires or metal balls sticking out of them. They both act like little brains. The difference is that microcontrollers have memory and other circuitry embedded on the same silicon chip that can do stuff like talk to a USB port or send pulses to motor. Unfortunately, virtually all microprocessors now have at least some memory caches embedded in them, and they get additional peripherals added constantly.

In practice, people use the words interchangeably, but the ones that are small, cheap, and not in a desktop, laptop, tablet, or phone, people tend to call microcontrollers. As mechanical engineers, you'll probably use microcontrollers to build small electromechanical systems. For example, as a mechanical engineer, you might be asked to work on

 * a test chamber that has a temperature sensor in it, with a microcontroller that monitors the temperature and runs a fan if it gets too hot inside
 * a pump controller that regulates fuel pressure in a booster rocket
 * an gearbox that includes an encoder that displays the velocity of the output shaft on an LCD

## Two big categories of microcontroller

### Category 1: no operating system

The most ubiquitous small microcontroller in the last decade is the Arduino. It has no operating system. When you power up an Arduino out of the box, it has a simple program called a bootloader on it that just does this: it checks the USB port to see if any computer is waiting to send it new code. If there's no new code, it runs whatever code was last sent to it. That's it. Everything else you want it to do, you either have to write yourself, or you have to use a library that somebody else wrote.

Here's what an Arduino Uno looks like.

![Arduino Uno blinking its LED](/img/arduino-uno-blink.gif)

### Category 2: has an operating system

The Raspberry Pi is even more widespread than the Arduino, but it's more of a small computer than just a microcontroller. When you power up a Raspberry Pi, it also runs a bootloader, but that bootloader loads an operating system, usually Linux, from a microSD card on the Pi. The operating system does all sorts of stuff for you: gives you a filesystem, sets up network connections, allows the CPU to switch back and forth so lots of different programs can run at the same time. The Pi also comes preloaded with a ton of software.

## Choosing a microcontroller

Let's suppose you need to choose a microcontroller. There are something like 100 different companies that make microcontrollers (and probably more if you include specialized chips that contain microcontrollers, but are not intended for general purpose use, like chips used in cameras or cell phones). However, most of those companies will not actually do business with you unless you are working for a large company that might plausibly place an order for 100,000 chips. Realistically, as a college student, or even an engineer working at most startups or most smallish companies, you are limited to ordering a chip from one of the large electronics distributors in the US: Digikey, Mouser, Newark, Arrow, or Avnet. If you try to call a microcontroller manufacturer like Microchip or Cypress, they will refer you their local sales office. That sales office will ask you how many parts you expect to order per year, and when you say a number like "Uh, I don't know, maybe 1000?" they will refer you to Digikey.

That actually makes your job a little easier, because the distributors are dominated by 10 companies. If, near the start of 2021, you judge their popularity by the number of different part numbers they sell, averaged across Digikey and Mouser, you come up with this list.

| Manufacturer    | Parts on Mouser | Parts on Digikey | Part share |
| --------------- | --------------- | ---------------- | ---------- |
| Microchip/Atmel |           23450 |              643 |        21% |
| Cypress         |            3489 |            13164 |        10% |
| NXP/Freescale   |            8589 |             3209 |         8% |
| Renesas         |            6291 |             3756 |         7% |
| ST              |            3878 |             3720 |         5% |
| TI              |            4610 |             1795 |         4% |
| Silicon Labs    |            4027 |             1120 |         4% |
| Zilog           |             965 |             2264 |         2% |
| Infineon        |             700 |              591 |         1% |
| Analog Devices  |             681 |              308 |         1% |
| Nordic          |              98 |              131 |         0% |
| Espressif       |              17 |                0 |         0% |




