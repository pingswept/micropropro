---
title: "I2C"
draft: false
---
# I<sup>2</sup>C: a digital communication protocol

I<sup>2</sup>C is a digital communication protocol that uses 3 wires to talk between up to 112 different hosts in its basic addressing mode. Each host is connected to three wires:

 1. A clock line, SCK
 2. A data line, SDA
 3. Ground, GND

![I2C schematic](/img/i2c-schematic.png)

## Open drain outputs and pull-up resistors

If you have a whole bunch of chips connected to the same three wires, there's a decent chance that one of them might starting to transmit at the same time as another. If one of them sends a high signal while the other is trying to send a low signal, this is like shorting power to ground, so one or both of the chips burns out.

Chips that implement I<sup>2</sup>C avoid this by using special piece of hardware called an "open drain output." Instead of having two stacked transistors inside the chip to connect to emit either a high or low signal, an open drain output has only one transistor, the source of which is connected to ground. The gate is connected to control circuitry inside the chip, and the third terminal, the drain, is left open. (See, open drain?) This means that each chip can pull the clock or data lines low, but none of them can pull the lines high, so they can never burn each other out.

Here's a comparison of a normal push-pull output, which can go high or low, and an open drain output, which can only pull low.

![open drain output](/img/i2c-open-drain.png)

If you want to know more about I<sup>2</sup>C, it's not crazy to try reading [the 64-page specification](/pdf/i2c-specification-UM10204.pdf) that NXP has released. (That *is* crazy for something like Bluetooth Low Energy. I just checked; the BLE 5.2 specification is 3256 pages long.)

<iframe id="kaltura_player" src="https://cdnapisec.kaltura.com/p/1813261/sp/181326100/embedIframeJs/uiconf_id/26203331/partner_id/1813261?iframeembed=true&playerId=kaltura_player&entry_id=1_zqozv6fh&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=1_yfhf0mos" width="736" height="450" allowfullscreen webkitallowfullscreen mozAllowFullScreen allow="autoplay *; fullscreen *; encrypted-media *" sandbox="allow-forms allow-same-origin allow-scripts allow-top-navigation allow-pointer-lock allow-popups allow-modals allow-orientation-lock allow-popups-to-escape-sandbox allow-presentation allow-top-navigation-by-user-activation" frameborder="0" title="Kaltura Player"></iframe>

You might also like to look at (this video from BlueDot)[https://www.youtube.com/watch?v=RPHP4fAisz8] about I2C.
