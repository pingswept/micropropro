---
title: "Embedded idioms"
draft: false
---

## Idioms in embedded programming ##

Bitmasks

### Setting bits high and low

|=
&=

```
#define BIT0_HIGH 0x01
#define BIT7_HIGH 0x80

#define BIT0_LOW 0xFE
#define BIT7_LOW 0x7F
```
