---
title: "Digital filters"
draft: false
---

## Filtering: what is the point?

The filtering problem that I dare say mechanical engineers run into most frequently is that of a noisy sensor. For example, you have an ultrasonic distance sensor that is generally accurate, but the readings it give jump up and down a little. The first thing you might think is, "I know, I'll read the sensor a bunch of times, and then calculate the average value in software." That's a pretty good solution, and it's quick to implement.

What you're doing essentially is creating a simple low-pass filter. "Low-pass" means that low frequencies go through the filter, but high frequencies (all the jittery noise you don't want) get blocked.

## Parks-McClellan filter design

But then you might think, "Could I do better than just averaging the sensor readings?"

If you're going to average the last 4 readings, you could multiply them each by 1/4, and then add them. But if you're trying to track something that is moving, you'd want to put more weight on the most recent readings, and less weight on older readings. But how much less weight? How about 1/2, 1/4, 1/8, 1/8? 

It turns out that some diligent people named Parks and McClellan came up with a method for figuring out a good set of coefficients for such a digital filter. Even better, there's a Python library that will calculate them for you.

## Example

```
from scipy import signal
bpass = signal.remez(72, [0, 0.1, 0.2, 0.4, 0.45, 0.5], [0, 1, 0])
freq, response = signal.freqz(bpass)
import numpy as np
ampl = np.abs(response)

import matplotlib.pyplot as plt
fig = plt.figure()
ax1 = fig.add_subplot(111)
ax1.semilogy(freq/(2*np.pi), ampl, 'b-')  # freq in Hz
plt.show()
```
