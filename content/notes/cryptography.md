---
title: "Cryptography"
draft: "false"
---

Cryptography is a massive field; one could easily spend an entire semester on the topic, so as you read this page, keep in mind that we're just covering a few of the basics.

## Hashes ##

You may be familiar with the side dish where you chop up some potatoes, fry them in butter, and add salt and pepper. The potatoes get hashed, and then browned, so we call this "hash browns." Note that it is easy to make hash browns, but impossible to turn hash browns back into potatoes.

Just like hashing potatoes, a hash function is a mathematical function that is easy to calculate in one direction, but difficult to reverse.

## A few popular hashes ##

* MD5: "message digest", 128 bits, 2<sup>128</sup> = 3.4 x 10<sup>38</sup>
* SHA-1: "secure hash algorithm", 160 bits, 2<sup>160</sup> = 1.5 x 10<sup>48</sup>
* SHA-256: "secure hash algorithm", 256 bits, 2<sup>256</sup> = 1.2 x 10<sup>77</sup>
* BDH8: "Brandon's dumb hash", 8 bits, 2<sup>8 = 256

The first three are real hashes in actual use around the world. Given the speed of modern PCs, MD5 is now considered broken for password authentication. SHA-1 is harder to reverse, but still within the range of state-level adversaries (e.g. the NSA).

The last one is a function that I'm making up just as an example. It is trivially broken, but it has the rest of the attributes of a typical hash function.
