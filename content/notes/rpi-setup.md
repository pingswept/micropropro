---
title: "Raspberry Pi setup"
draft: true
---
# Setting up a Raspberry Pi Zero W

## Stuff you need

*   Raspberry Pi Zero W
*   2x20 0.100" pitch male header pins to solder into the R. Pi
*   micro SD card
*   micro USB cable for power
*   USB-serial adapter
*   mini USB cable for USB-serial adapter
*   3 female-female jumper wires

## Setup checklist

*   <input type="checkbox"> Download OS image
*   <input type="checkbox"> Burn image to micro SD card with Etcher
*   <input type="checkbox"> Edit config.txt on micro SD card to include: `enable_uart=1`
*   <input type="checkbox"> Solder in pins
*   <input type="checkbox"> Connect RPi to laptop with serial adapter, mini-USB cable, and 3 jumper wires
*   <input type="checkbox"> Put micro SD card in slot of Pi
*   <input type="checkbox"> Connect mini USB cable between PWR IN on Pi and a USB power adapter
*   <input type="checkbox"> Open Putty (Windows) or Terminal (macOS)
*   <input type="checkbox"> Start a session at 115200 bps to the Pi
*   <input type="checkbox"> Log in with username `pi` and password `raspberry`
*   <input type="checkbox"> To enable wireless, figure out the Pi's MAC address with ifconfig
*   <input type="checkbox"> Register MAC address with Tufts IT
*   <input type="checkbox"> Wait a few minutes for MAC address permissions to propagate to local wireless access point
*   <input type="checkbox"> Add network information to `/etc/wpa_supplicant/wpa_supplicant.conf`
*   <input type="checkbox"> Reboot Pi

## FAQ

**What OS image should I use?**

Unless you have a good reason not to, you should start with [Raspberry Pi OS](https://www.raspberrypi.org/downloads/raspbian/). Previously called Raspbian, the OS should be based on Debian Buster or newer (as older versions will not work with a Pi 4). If you are unsure what this means, go ahead and get the `
Raspberry Pi OS (32-bit) with desktop and recommended software` version.

**How do I figure out what name is assigned to the USB-serial adapter when I plug it in?**

On Windows 10, it's usually `COM3` (but it is not uncommon to have a different number). You can check for sure in the Device Manager control panel under Ports (COM & LPT)

On macOS, it's called `/dev/tty.usbserial-123456`, but the numbers at the end change. You can check it by running `ls /dev` in Terminal.

On Linux it's called `/dev/ttyACM0`, but the number will depend on how many USB devices are plugged in. As with macOS, you can check by running `ls /dev` in Terminal.

**When I open config.txt with Notepad, the lines all run together. How do I fix this?**

Use a better text editor, like [Sublime Text](https://www.sublimetext.com/), [Textmate](https://macromates.com/), or [Notepad++](https://notepad-plus-plus.org/). You could also try Wordpad.

**What network settings do I need for the Tufts wireless network?**

<pre class="code">network={
    ssid="Tufts_Wireless"
    key_mgmt=NONE
}
</pre>

**What about Tufts Secure?**

<pre class="code">network={
    ssid="Tufts_Secure"
    key_mgmt=WPA-EAP
    pairwise=CCMP
    eap=PEAP
    identity="Nolop_IOT"
    password="YOU PUT THE PASSWORD HERE IN QUOTES"
    phase2="auth=MSCHAPV2"
}
</pre>

**How do I control pins on the Raspberry Pi?**

Here's an example Python script that sets a pin high.

<pre class="code">import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BOARD)   # use the BOARD pin-numbering system
GPIO.setup(16, GPIO.OUT)   # like pinMode(16, OUTPUT)
GPIO.output(16, GPIO.HIGH) # like digitalWrite(16, HIGH)
</pre>

Here's another script that checks the state of a pin.

<pre class="code">import time
import RPi.GPIO as GPIO
GPIO.setup(16, GPIO.IN)       # like pinMode(16, INPUT)
while(1):                     # do this forever
    if(GPIO.input(16)):       # like digitalRead(16)
        print("Pin is high.")
    else:
        print("Pin is low.")
    time.sleep(0.5)           # sleep for 0.5 s
</pre>

**Where can I find that code you showed us in class that turned pins on and off through a web browser?**

Right here:

<pre class="code">from flask import Flask
app = Flask(__name__)

import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BOARD)

@app.route('/')
def hello_world():
    return 'Hello, World!'

@app.route('/pinon')
def pin_on():
    GPIO.setup(16, GPIO.OUT)   # pinMode(16, OUTPUT)
    GPIO.output(16, GPIO.HIGH) # digitalWrite(16, HIGH)
    return 'I turned on the pin.'

# Make sure the line below has the correct angle brackets in it.
@app.route('/digital/write/<pin_name>/<state>')
def digital_write(pin_name, state):
    pin = int(pin_name)
    if state.upper() in ['1', 'ON', 'HIGH']:
        GPIO.setup(pin, GPIO.OUT)   # pinMode(pin_name, OUTPUT)
        GPIO.output(pin, GPIO.HIGH) # digitalWrite(pin_name, HIGH)
        return 'Set pin {0} to HIGH'.format(pin_name)
    elif state.upper() in ['0', 'OFF', 'LOW']:
        GPIO.setup(pin, GPIO.OUT)   # pinMode(pin_name, OUTPUT)
        GPIO.output(pin, GPIO.LOW)  # digitalWrite(pin_name, LOW)
        return 'Set pin {0} to LOW'.format(pin_name)
    return 'Something went wrong'
</pre>

You also need to install [Flask](https://pypi.org/project/Flask/) for this to work.

**Wait, how do I install Flask?**

Switch to the Tufts_Guest wifi network, so your Pi's HTTP requests won't be redirected by Tufts' network. Then, install Flask:

<pre class="code">sudo apt-get install python-pip
sudo pip install flask
</pre>

Then, start the server (assuming your code is in a file called `server.py`):

<pre class="code">export FLASK_APP=server.py
python -m flask run --host=0.0.0.0
</pre>

By default, Flask will listen on port 5000, so check `http://your.rpi.ip.address:5000` to see if it worked.

**That's cool, but how do I get Flask to start itself when the Pi boots?**

For that, you want to install [Supervisor](http://supervisord.org).

<pre class="code">sudo apt-get install supervisor
</pre>

Check that Supervisor is installed properly and running.

<pre class="code">pi@raspberrypi:~$ sudo supervisorctl
supervisor> status
supervisor> exit
</pre>

Tell supervisor that you want it to run Flask for you by adding something like the lines below to `/etc/supervisor/supervisord.conf`

<pre class="code">[program:flask]
directory=/home/pi
environment=FLASK_APP="server.py"
command=python -m flask run --host=0.0.0.0
</pre>

Then, make Supervisor read the config file.

<pre class="code">sudo supervisorctl
supervisor> update flask
flask: stopped
flask: updated process group
supervisor> status
flask                            RUNNING   pid 14183, uptime 0:00:09
</pre>

If Supervisor can't start Flask for whatever reason, it will write error messages in the log files, which you can find in `/var/log/supervisor/`. In general, it's probably a better idea to debug your Flask code pretty thoroughly before you start using Supervisor, but if bugs come up, the log files are your best hope. You can also just stop Flask under Supervisor and going back to running Flask from the console yourself.

**What do the pin numbers correspond to?**

All the most recent Pi's share a standard pin format. Below is a handy guide. [This site](https://pinout.xyz/) is also an excellent resource for reference.

<p align="center">
  <img src="/img/raspberry-pi-pinout.png" />
</p>
