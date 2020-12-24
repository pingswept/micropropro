---
title: "Computer architecture"
draft: false
---

## Instruction set architecture ##

Each kind of microprocessor uses a different instruction set architecture, or ISA. Here are some ISA's you may have heard of: ARM, x86, RISC-V, AVR.

## CISC vs RISC ##

20 or 30 years ago, when ISA's like x86 and 8051 were dominant, CPUs that could execute more complicated instructions were popular. These were called CISC machines, for "Complex Instruction Set Computer."

At some point, computer architects realized that there are some advantages to RISC ("Reduced Instruction Set Computer) machines. Now, it looks like RISC will win.

## The winner so far: ARM ##

As cell phones and tablets rose in popularity between 2005 and the present, energy consumption became a major driver in processor selection. A British company, ARM, took an unusual approach. (Originally, ARM stood for "Acorn RISC Machines," then "Advanced RISC Machines;" now they have the gall to claim ARM doesn't stand for anything and is written in all lower case, like "arm." Ow, my arm.) Anyway, ARM designed chips, but produced no silicon of their own. They license their designs to other companies, who then make the chips.

Additionally, they optimized their ISA (and their chip architecture more broadly) for low energy consumption. The result of that, to a first approximation, was that every mobile phone uses an ARM processor. The chips are made by many different companies, but the designs are all licensed from ARM. The Raspberry Pi 4, for example, uses a Broadcom BCM2711, which is a quad-core ARM Cortex-A72. (The Pi could just as well have used an NXP Layerscape LS1046A, another quad-core ARM Cortex-A72. Both use the ARMv8-A architecture, but have different peripherals built in.)

## References ##

A few useful tables and details about recent (2020) ARM stuff

 * [List of ARM microarchitectures](https://en.wikipedia.org/wiki/List_of_ARM_microarchitectures)
 * [Comparison of ARMv8-A cores](https://en.wikipedia.org/wiki/Comparison_of_ARMv8-A_cores)
 * [AArch64, the 64-bit version of the ARM architecture](https://en.wikipedia.org/wiki/AArch64)
