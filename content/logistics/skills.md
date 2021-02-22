---
title: "Skill builders"
draft: false
---

## SB3: learn to use pastebins

* The next time you need to share code, create a gist at https://gist.github.com.
* Try using https://pastebin.com at least once.
* If you do not know how to copy and paste with your terminal program, figure it out using Google.
* For PuTTY: https://www.alphr.com/copy-paste-putty/

## SB2: customize your Pi shell ##

* Install Zsh on your Pi
* Install [Oh-My-Zsh](https://ohmyz.sh/)
* Change the Zsh theme to one you like
* Install at least one plugin

Here are some instructions that explain how to do both tasks together: https://www.seeedstudio.com/blog/2020/03/06/prettify-raspberry-pi-shell-with-oh-my-zsh/

If you are on Windows and using WSL2, you might find this useful: https://blog.nillsf.com/index.php/2020/02/17/setting-up-wsl2-windows-terminal-and-oh-my-zsh/

## SB1: git ##

* Install git on your Raspberry Pi 4
* Make a Github account
* Watch the git video
* Create a repository try to do most of the things that I do in the video.
* See also [the git page](/notes/git/)

<iframe id="kaltura_player" src="https://cdnapisec.kaltura.com/p/1813261/sp/181326100/embedIframeJs/uiconf_id/26203331/partner_id/1813261?iframeembed=true&playerId=kaltura_player&entry_id=1_d9h05lxw&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=1_s90p29of" width="736" height="450" allowfullscreen webkitallowfullscreen mozAllowFullScreen allow="autoplay *; fullscreen *; encrypted-media *" sandbox="allow-forms allow-same-origin allow-scripts allow-top-navigation allow-pointer-lock allow-popups allow-modals allow-orientation-lock allow-popups-to-escape-sandbox allow-presentation allow-top-navigation-by-user-activation" frameborder="0" title="Kaltura Player"></iframe>

## Alternative SB1: Figure out how to compile and run Rust code on the Pico ##

Already familiar with git? Great! Instead, do this:

* Figure out how to cross-compile code written in Rust for the Pico
* Figure out how to load and execute that code on the Pico
* Prepare to explain what a borrow checker is to the rest of the class
* Prepare to explain what Rust does to ensure memory safety, which is absent in C and C++
