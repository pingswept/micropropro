---
title: "Compilation example"
draft: false
---

## Example of compiling C code ##

Suppose you want to compile a short C program into machine code, the bits that your microcontroller can execute.

Let's start with a stupidly simple program, called `simple.c`.

```
void main() {
    int x = 255;
    x = x + 0xAAAA;
}
```

On a Raspberry Pi, I could compile that like this: `gcc simple.c`.
