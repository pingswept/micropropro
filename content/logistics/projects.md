---
title: "Projects"
draft: false
---
# Projects

## Project #3: Build an electromechanical game

Your task is to build a game with the following characteristics:

*   It is controlled by a microcontroller like an Arduino or Raspberry Pi. (Choose the Arduino unless you're a Pi zealot.)
*   It has at least one electromechanical element that moves, like a motor or a solenoid.
*   It has some kind of user input, like buttons, knobs, joysticks, sensors, or the like.
*   It is at least sort of fun to play. A blinking LED is not a game.
*   (It does not need to have a custom PCB, but it can if you want. If it has a custom PCB, you must make a working prototype first.)

**Midway milestone: Build a [prototype](https://canvas.tufts.edu/courses/22096/assignments/107781): Wednesday, October 21, 11:59 PM**

**Final due date: Monday, November 2, 11:59 PM**

Plan to demo your playable game in pods on November 3rd and 5th.

### More details for project #3

If you need parts (like a sensor or a certain kind of motor), we're happy to order them for you.

## Project #2: Build an H-bridge motor controller

The second project is to build a motor controller with the following characteristics:

*   It consists of a PCB with screw terminals for power and control lines.
*   It also accepts power from a 2.1 x 5.5 mm plug from a 12 V wall adapter.
*   It has a power LED that lights up when motor power is available.
*   It can make a DC motor spin in both directions.
*   The motor current traces can handle 12 V and 5 A continuously without melting.
*   It can be controlled by logic signals from an Arduino (but later, not as part of what you submit for P2).  


<iframe id="kaltura_player" src="https://cdnapisec.kaltura.com/p/1813261/sp/181326100/embedIframeJs/uiconf_id/26203331/partner_id/1813261?iframeembed=true&playerId=kaltura_player&entry_id=1_708qmkve&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=1_mtijm1x6" width="400" height="285" allowfullscreen webkitallowfullscreen mozAllowFullScreen allow="autoplay *; fullscreen *; encrypted-media *" sandbox="allow-forms allow-same-origin allow-scripts allow-top-navigation allow-pointer-lock allow-popups allow-modals allow-orientation-lock allow-popups-to-escape-sandbox allow-presentation allow-top-navigation-by-user-activation" frameborder="0" title="Kaltura Player"></iframe>  



**Due date for prototype: Wednesday, September 30, 11:59 PM**

To get started building your prototype H-bridge, review the [Low Power/high power](http://andnowforelectronics.com/notes/low-power-high-power/) and the H-bridge(http://andnowforelectronics.com/notes/h-bridge/) pages, including their mini-lecture videos on BJT and MOSFET transistors. After that, if you're stuck, consult the [H-bridge testing](http://andnowforelectronics.com/notes/demo-videos/) demo video.  Note that this video is not intended to give you step-by-step building or testing instructions, but rather to give you a feel for the kind of approach you might take to building and testing this circuit. If your H-bridge prototype isn't working by the deadline for this prototype, don't worry!  Just submit to Canvas a photo of what you have, working or not.  

**Due date for PCB submission: Wednesday, October 7, 11:59 PM**

When your design is ready, you should [submit it to the fabricator](https://oshpark.com/), OSH Park. It will cost you around $10\. After you submit it, take a screenshot of your order confirmation and upload it to the Project 2 PCB assignment on Canvas. That will serve as proof that you submitted your project on time.

## Project #1: Build a breadboard power supply

The first project is to build a power supply with the following characteristics:

*   It consists of a PCB that plugs directly into a breadboard.
*   It accepts power from a 2.1 x 5.5 mm plug from a 12 V wall adapter.
*   It emits 12 V, 5 V, and 3.3 V (at the same time).

**Due date (for PCB submission): Wednesday, September 16, 11:59 PM**

When your design is ready, you should [submit it to the fabricator](https://oshpark.com/), OSH Park. It will cost you around $10\. After you submit it, take a screenshot of your order confirmation and upload it to the Project 1 PCB assignment on Canvas. That will serve as proof that you submitted your project on time.

### More details for project #1

First of all, we're not trying to build anything revolutionary in this project. None of you have ever made a PCB before, so the point is to make something fairly simple to get comfortable with the process. If you search Amazon for "breadboard power supply", you'll see that you can buy various versions of things like this, though none with a 12 V passthrough, so far as I'm aware.

Here's what a typical one of these things looks like.

![breadboard power supply](/img/breadboard-power-supply-from-amazon.jpg)

The image below shows the rough mechanical constraints for the PCB. You can make a board of whatever dimensions you want, but it needs to plug into the breadboard, so you probably want to follow the pin location dimensions shown below. You don't have to have pins where all of the 8 red dots are-- you could get by with just 4, but 8 will make the board stay in place a little more securely.

![](/img/breadboard-supply-mechanical-design.png)

In your project kit, you'll find all the components you'll need to build a prototype of your power supply on a breadboard. You build the prototype and make sure that you've got the wiring right. Then, make the PCB with the same connections. Finally, when your PCB arrives in the mail, you can reuse the prototype components on your PCB.

To improve heat dissipation, you will want to use your PCB as a heatsink for the regulators. The TA from 2018, Dominic Guri, has made a [KiCAD PCB footprint for the TO-220 package](/to-220-horizontal-footprint.kicad_mod) to help with that. You should put it into a folder called `volt-reg.pretty`, or something like that. (The ending `.pretty` is what matters to KiCAD.)

Put that folder in C:\Program Files\KiCad\share\kicad\modules on Windows or /Library/Application Support/kicad/modules on MacOS. Then, you can add that library to Kicad using Preferences > Footprint Libraries in the footprint association window.

{{< hint danger >}}
**Important note #1: the pins on the two regulators are not in the same order!**
{{< /hint >}}

Check the datasheets for the components to see which pin is the input pin, which is the output pin, and which should connect to ground.

{{< hint danger >}}
**Important note #2: the pins on the power jack are weird! More details below.**

There's a cryptic diagram in the datasheet for the PJ-102AH power jack, shown below.

![power jack pinout](/img/power-jack-pinout.jpg)

One part is obvious: the pin in the middle is connected to pin 1.

But what is that little arrow/bump thing with pins 2 and 3?

That's trying to tell you that when the jack is empty (i.e. no plug inserted), pins 2 and 3 are connected together. When you insert the plug, the barrel pushes on the bump at the end of the pin 2 contact, which bends it away from the pin 3 arrow, breaking the connection to pin 3. It's so that you can detect whether there's a plug inserted or not, which can be useful for battery-powered systems. You don't need to implement that feature on your regulator board.
{{< /hint >}}
