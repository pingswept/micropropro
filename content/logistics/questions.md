---
title: "Crucial questions"
draft: false
---

## Crucial questions for the semester  
We'll choose a question from this list to generate the Video Response prompt for each week.  

1. If we're trying to light up an LED with a 5 V supply, why do we need a resistor in series?
2. How much power can 5 V drive into a 100 ohm resistor? Could the resistors in your project kit handle that?
3. Does a motor get hotter when it's going fast or slow? Why?
4. Can you store more energy in a 100 uF capacitor or in a lithium ion battery of the same volume?
5. Why are extension cords rated for a certain voltage and current? How is a cord with higher ratings different?
6. Using the stuff in your project kit, devise a few different ways to overload your voltage regulator circuit and tell us which one would dissipate the most power, and why.
7. How much energy is there in an AA battery? In a 9V battery? Which has higher energy density by volume, and why?
8. Compared to the N-channel set-up, what would you need to do differently to use a P-channel MOSFET to switch your 12-V DC gearmotor on and off? 
9. What would be the advantages of using the P-channel as a high-side driver instead of a low-side driver?
10. How would you select an appropriate motor for a robot elbow?


## Learning objectives

1.	Complete four hands-on circuit design projects:
    a.	  Build a prototype and PCB of a breadboard power supply that accepts power from a 12 V wall supply and emits 12 V, 5 V, and 3.3 V at the same time.
    b.	  Build a prototype and PCB of an H-bridge motor controller to make a motor spin both ways.
    c.	  Build an electromechanical game including microcontroller, moving mechanical element, and user input.
    d.	  Build a node including both sensor(s) and actuator(s) in an internet-connected, electronic system.
2.	Distinguish between voltage and current and apply working definitions of voltage and current to explain energy transfer in simple circuits. 
3.	Describe the relationships among voltage, current, resistance, and power. 
4.	Gain proficiency with breadboard prototyping.
5.	Turn a breadboard prototype into a printed circuit board using PCB design software.
6.	Explain how to use transistors to control high power with low power.
7.	Compare and contrast different types of motors (DC, stepper, and servo) and build circuits incorporating each kind.
8.	Explain how an H-bridge motor controller works.
9.	Learn the basic code/upload/test/debug cycle for Arduino. 
10.	Gain basic familiarity with microcontroller hardware.
11.	Gain familiarity with incorporating microcontroller hardware peripherals into circuit designs, including the i2C module, PWM module, and serial port module.
12.	Gain enough familiarity with C programming to code an electromechanical game controlled by an Arduino.
13.	Describe how the internet works.
14.	Gain familiarity with Linux basics and explain how they relate to the functioning of a Raspberry Pi. 
15.	Identify the main components and functions of the Raspberry Pi.
16.	Describe the basics types of control in the context of the motor(s) used in course projects, and Arduino or RPi.
17.	Become familiar with the frequency domain and digital filters.
18.	Reflect on strengths and weaknesses of one’s project management approach in an open-ended design project. 
19.	Gain exposure to managing a bill of materials, supply chain, and verification vs validation.
20.	Build engineering ethics fluency by exploring the impact of internet-connected electronic technologies on various stakeholders, including in environmental and societal contexts.
21.	Define discriminatory design, explain a case where it has occurred, and identify an approach to avoid it.

## Video Response 5 (due Mon., Oct. 12, 11:59pm)
*This Video Response prompt has more text than can fit in Flipgrid, so we are posting the details here.*  

We are moving on to microcontrollers! We’ll begin with the Arduino.  Here are the steps for Video Response #5, due a few hours later than usual: 11:59pm Monday, Oct. 12.  

**VR 5 Part I: Reflection on the first 5 weeks of ME 30**

Reflect for a few minutes on your work and learning in ME 30 so far this semester. Here’s a prompt to guide your reflection:
* You’ve probably done a bunch of different things for ME 30 so far (e.g., going to office hours, asking friends how things work, asking questions in pods, reading the website notes and watching its videos, building circuits, breaking components, debugging, Googling, reading the textbooks, making video responses, posting to Slack, etc.)    
* Which of the things you’ve done for ME 30 has been most useful for your learning? What do you think might happen if you put all your effort into that thing and ignored everything else?    
* Jot down some thoughts and save them for your video response (see Step 6 below).  

**VR 5 Part II: Arduino prep**  

(1) If you are a complete newcomer to the Arduino, consider attending one of the special office hour tutorials in which we will walk you through the steps outlined below. Those tutorials are happening Thurs., 10/8 (3pm and 3:45pm), Sun., 10/11 (8pm and 9pm), and Mon., 10/12 (3:30pm and 4:15pm).

(2) Skim the ME 30 website notes [on microcontrollers](http://andnowforelectronics.com/notes/microcontrollers/), the [Arduino MKR Wifi 1010](http://andnowforelectronics.com/notes/arduino-mkr-wifi-1010-hardware/), and [Arduino programming](http://andnowforelectronics.com/notes/arduino-programming/). (You'll want to read them in more depth later on; for now, just get a sense for what's there.)  

(3) Install the Arduino IDE, Desktop version, version 1.8.13, from Arduino’s downloads page: https://www.arduino.cc/en/Main/Software
**We’ll be using the desktop IDE, NOT the web editor.** (The acronym IDE means integrated development environment, which is software that gives computer programmers a single graphical user interface for the different tasks involved in writing programs.)

(4) Follow the directions for adding the Arduino SAMD core to the Boards Manager on the Desktop IDE. These directions are on the website, https://www.arduino.cc/en/Guide/MKRWiFi1010, in the lower section titled “Use your Arduino MKR WIFI 1010 on the Arduino Desktop IDE,”  Make sure you are NOT using the earlier sections on using the IoT cloud or the Web IDE.  In ME 30 we’ll be using the Desktop IDE.

(5) Complete the following two initial Arduino programming tasks:

a. Make your Arduino run the "Blink" example. You can find the "Blink" code and instructions [here](https://www.arduino.cc/en/Tutorial/BuiltInExamples/Blink).  
b. Make your Arduino flash an LED so there are 2 flashes per second, controlled by pin D7. See information about Arduino pins [here](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalwrite/).

**(6) Fligrid posting - Make and post a [Flipgrid](https://flipgrid.com/me30) video that shows us you can do these two Arduino programming tasks, and that shares your reflection thoughts from Part I.**

