---
title: "Bluetooth"
draft: true
---

## Classic Bluetooth vs BLE

Bluetooth is a short-range radio protocol used for communicating between devices. The first 3 versions are called "BR/EDR" for "Basic Rate/Enhanced Data Rate."

Versions 4 and 5, known as "Bluetooth Low Energy," or BLE, broke hardware compatibility with classic Bluetooth, but increased the data rate while lowering energy consumption, crucial for battery-powered devices like phones. As of 2020, the latest release of Bluetooth is release 5.2.

BR/EDR and BLE use the same physical antenna at 2.4 GHz, and both use FHSS (frequency hopping spread spectrum), but with different allocations of frequency bands.

BR/EDR used 79 channels, each 1 MHz wide, but BLE uses 40 channels, each 2 MHZ wide.

Both versions use frequency shift keying, which means that bits are encoded with two nearby frequencies.

![Frequency shift keying](/img/frequency-shift-keying.png)

BLE uses Gaussian frequency shift keying, which is similar, but the transistions between frequencies are less abrupt, which spews less noise at other frequencies.
