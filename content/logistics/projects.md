---
title: "Projects"
draft: false
---
# Projects

## P1: Design and build a new Raspberry Pi Pico accessory

Design a small PCB that can plug into the headers of the [new Raspberry Pi Pico](https://www.raspberrypi.org/documentation/pico/getting-started/) that enhances its capabilities in a new way.

The Pico is brand new (just released on January 21st, 2021), but I ordered enough for everyone in the class to have one. They are now out of stock everywhere I've looked.

![Pile of Raspberry Pi Picos](/img/raspberry-pi-pico.jpg)

It's okay if someone else has made a sort of similar board, but yours should be a new design. For example, there are [9 different boards available from Pimoroni](https://shop.pimoroni.com/collections/pico), but mostly, the field is wide open. Also, there are new sensors and other chips coming out every day. Ask your non-engineer friends what magical device they wish they had; build the closest approximation you can.

In thinking through ideas, you might investigate the Pico's PIO modules. These are special chunks of silicon embedded in the Pico's processor that can be programmed in a 9-instruction assembly language to implement lots of weird digital protocols spoken by different sensors or actuators.

Let's be clear about what the goals are here. If you have never made a PCB before, your goal should be to submit a PCB before the due date where at least the components you think you need can be soldered to the board-- think of it as a first draft. If you have made several PCBs before, you should aim to make something that actually works, though it's hard to get every detail right on the first try.

A few detailed requirements:

* Please use [Kicad](https://www.kicad.org) to design the PCB.
* For fabrication, please use [OSHPark](https://oshpark.com). They're reasonably cheap and have successfully delivered over 100 PCB orders to Tufts with zero mistakes.
* Your PCB should almost certainly use two [1x20, 0.100" pitch header sockets](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PPTC201LFBN-RC/810158). I have ordered a pile of them, so we can get them more cheaply ($0.19 each direct from China via Ebay, instead of more like $1.20, with shipping amortized across 35 people, but we have to wait a few weeks).

A note about programming:

This class will be mostly about programming microcontrollers. But, around 90% of you are really excited to make PCBs that enable new programming opportunities. PCB fabrication takes a while, so we have to get the PCB out the door first. We'll mostly focus on programming after this first project, but we'll also do a second revision of this board as one of the later projects.

