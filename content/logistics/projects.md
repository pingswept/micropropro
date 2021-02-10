---
title: "Projects"
draft: true
---
# Projects

## P2: Figure out how to hide this project from Jeremy

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

## P2: Program an oscilloscope puzzle for the Pico

ME 30 is the electronics course that every mechanical engineering junior takes at Tufts. Next year, it will have a new challenge called "the oscilloscope puzzle." The goal is to teach ME 30 students how to use an oscilloscope, which is a device that measures voltage like a multimeter, but shows you a graph of voltage over time, rather than just a single instantaneous reading. The ME 30 students, hereafter called "the detectives," will have to use an oscilloscope to find signals on the Pico's pins, interpret them, and then follow whatever directions they find to advance through the puzzle.

There's another goal too, which is to get you all to learn how to program a Pico, and especially how to implement a state machine.

I created the original version of this back in 2017 for an EN 1 course, but it had a fundamental problem, which is that once one detective solves the problem, the secret is out. Now, with the 32 of you, we can make 32 different puzzles that appear the same from the outside, but have different solutions. Your brain is like the salt in our password hash.

A few detailed requirements:

* The puzzle should have 4 states: ONE, TWO, THREE, and SOLVED. During the numbered states, the Pico's onboard LED should blink as many 200 ms pulses as the state name every  second, so the detectives can track what state they are in.

* Here's some ASCII art that shows what the pulses should look like. Each asterisk is a 200 ms pulse; each underscore is a 200 ms gap. 

```
STATE ONE:    *_________*_________*_________
STATE TWO:    *_*_______*_*_______*_*_______
STATE THREE:  *_*_*_____*_*_*_____*_*_*_____
STATE SOLVED: *_*_*_*_*_*_*_*_*_*_*_*_*_*_*_
```

* The Pico should start in state ONE upon power up.
* In each of the first three states, the Pico should emit some kind of electrical signal that encodes (in a short, simple way!) instructions that describe an action the detectives should take to make the Pico advance to the next state.
* In the SOLVED state, the Pico should send a message out its USB port at 115200 bps that says, "PUZZLE SOLVED! Secret key: " followed by a SHA-256 hash that will be described in class. (Yes, a shrewd detective might try to extract the binary from the Pico and find the hash in the binary. Assuming you have deployed no countermeasures, it might even work, but then the detective is getting practice with reverse engineering, which is still good.)
