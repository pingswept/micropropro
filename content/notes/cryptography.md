---
title: "Cryptography"
draft: "false"
---

Cryptography is a massive field; one could easily spend an entire semester on the topic, so as you read this page, keep in mind that we're just covering a few of the basics.

## Hashes ##

You may be familiar with the side dish where you chop up some potatoes, fry them in butter, and add salt and pepper. The potatoes get hashed, and then browned, so we call this "hash browns." Note that it is easy to make hash browns, but impossible to turn hash browns back into potatoes.

Just like hashing potatoes, a hash function is a mathematical function that is easy to calculate in one direction, but difficult to reverse.

## A few popular hashes and an example ##

* MD5: "message digest", 128 bits, 2<sup>128</sup> = 3.4 x 10<sup>38</sup>
* SHA-1: "secure hash algorithm", 160 bits, 2<sup>160</sup> = 1.5 x 10<sup>48</sup>
* SHA-256: "secure hash algorithm", 256 bits, 2<sup>256</sup> = 1.2 x 10<sup>77</sup>
* BDH8: "Brandon's dumb hash", 8 bits, 2<sup>8</sup> = 256

The first three are real hashes in actual use around the world. Given the speed of modern PCs, MD5 is now considered broken for password authentication. SHA-1 hash collisions are harder to calculate, but still within the range of state-level adversaries (e.g. the NSA).

The last one, BDH8, is a function that I'm making up just as an example; I define it as just an exclusive-OR (XOR) of each byte with the next one until you get to the end of whatever you're hashing. It is trivially broken, but it has the rest of the attributes of a typical hash function. Specifically, it maps all lists of bytes onto a finite output range. The outputs are evenly distributed, and small changes in the input value create large changes in the output value, on average.

As an example, let's run BDH8 on the string "fun". By checking [asciitable.com](https://asciitable.com), we can figure out that the characters "f", "u", and "n" are represented by the bytes 0x66, 0x75, and 0x6E. In binary, we would represent those as b0110 0110, b0111 0101, and b0110 1110.

If we XOR the first two bytes, we get b0001 0011. Then XOR that with the last byte, and you get the final hash, b0111 1101 = 0x7D.

It's simple to find hash collisions. For example, the string "ven", represented as 0x76, 0x65, 0x6E, has the same BDH8 hash of 0x7D.

## What is a hash for? ##

### Checking for changes to a file ###

Say you download some software, and you want to check that the file is not corrupted or modified by a malicious villain. You can calculate, say, the MD5 hash of the file you downloaded, and then compare it to what the MD5 hash should be. How do you know what the MD5 hash should be? Usually, the people who wrote the software will tell you.

For example, the Raspberry Pi people uses SHA-256 for OS download checks. The version of Raspberry Pi OS Lite from 2021-01-11 has the hash `d49d6fab1b8e533f7efc40416e98ec16019b9c034bc89c59b83d0921c2aefeef`. You could check it by downloading [that version of the OS](https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2021-01-12/2021-01-11-raspios-buster-armhf-lite.zip) and then running a command like `md5sum 2021-01-11-raspios-buster-armhf-lite.zip`.

Similarly, PyPI, the Python software repository, publishes SHA256, MD5, and BLAKE2-256 hashes for its downloads.

### Password authentication ###

When you pick a password for a website, the hash of the password is generated, and the website stores the hash, but not the password itself. Then, when you want to log in again, you hash the password again, and compare it against the stored hash. Nobody else can figure out what password to use to generate that hash, so nobody can log in as you.

(Note: this is how it should work, but some people still store all the passwords in one big file. They are idiots. If a website ever sends you your password, you should realize that they must have been storing your password instead of a hash, and then you should stop trusting that website.)
