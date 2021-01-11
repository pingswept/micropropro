---
title: "Shells"
draft: false
---

## What is a shell? ##

A shell is the program that generates the terminal prompt that you see when you log in to a Raspberry Pi. The shell receives your commands and executes them for you. 

It's part of a kind of weird metaphor: the core of an operating system is called the kernel, and the shell is the layer of software wrapped around it that protects it from the outside world. It's like the operating system is a nut: the kernel is the squishy part in the middle of the nut that you eat, and the shell is hard outer layer that you peel off and leave on the table in the makerspace.

The basic shell that all Unix systems have is called `'/bin/sh`, or "the Bourne shell," because a person named Bourne wrote it. Most Linux systems also include the C shell (`/bin/csh`), its improved derivative, `/bin/tcsh`, and the GNU Bourne Again Shell, `/bin/bash`. Debian, and its major derivative, Ubuntu has switched to the Debian Almquist shell (`/bin/dash`, but also now `/bin/sh` by default).

In the big picture, it doesn't really matter what shell you use, but the newer shells tend to be easier to use, more powerful, and a little more pleasant to look at.

## List of shells you might want to know about ##

* sh
* csh
* tcsh
* bash
* ksh
* dash
* zsh
* fish
* ion

## Zsh ##

`Zsh` is a particularly fine modern shell. On a Raspberry Pi, you can install it like this: `sudo apt install zsh`

After you install it, you can test it out by running the command `/bin/zsh`

If it works, you can make it your default shell using `chsh -s /bin/zsh`

(`chsh` means "change shell.")

## Oh-My-Zsh ##

https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH
