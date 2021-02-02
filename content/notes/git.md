---
title: "Git"
draft: false
---

## Git and Github ##

Git is a program for tracking changes to software in a fancy structure of files called a repository. Tracking changes to software is called `version control`. Git is a `DVCS`, for "distributed version control system." It is by far the most popular DVCS. On a Raspberry Pi, you can install git with a command like this: `sudo apt install git`

Github, owned by Microsoft, is a website for hosting git repositories. There are lots of competing options, like Gitlab or Sourcehut, but Github is the dominant player. You can also store git repositories on your own computer; they're just a collection of files in a folder.

## What is this "distributed" stuff? ##

In the past, version control systems used a central server. This works fine for small groups of harmonious individuals, but for large groups, it's a mess. In a distributed system like git, no repository has primacy over any other; there is no central server.

<iframe id="kaltura_player" src="https://cdnapisec.kaltura.com/p/1813261/sp/181326100/embedIframeJs/uiconf_id/26203331/partner_id/1813261?iframeembed=true&playerId=kaltura_player&entry_id=1_d9h05lxw&flashvars[streamerType]=auto&amp;flashvars[localizationCode]=en&amp;flashvars[leadWithHTML5]=true&amp;flashvars[sideBarContainer.plugin]=true&amp;flashvars[sideBarContainer.position]=left&amp;flashvars[sideBarContainer.clickToClose]=true&amp;flashvars[chapters.plugin]=true&amp;flashvars[chapters.layout]=vertical&amp;flashvars[chapters.thumbnailRotator]=false&amp;flashvars[streamSelector.plugin]=true&amp;flashvars[EmbedPlayer.SpinnerTarget]=videoHolder&amp;flashvars[dualScreen.plugin]=true&amp;flashvars[Kaltura.addCrossoriginToIframe]=true&amp;&wid=1_s90p29of" width="736" height="450" allowfullscreen webkitallowfullscreen mozAllowFullScreen allow="autoplay *; fullscreen *; encrypted-media *" sandbox="allow-forms allow-same-origin allow-scripts allow-top-navigation allow-pointer-lock allow-popups allow-modals allow-orientation-lock allow-popups-to-escape-sandbox allow-presentation allow-top-navigation-by-user-activation" frameborder="0" title="Kaltura Player"></iframe>

## The 7 most useful git commands ##

```
git clone
git pull
git status
git add .
git commit -m "Prevent ARP cache poisoning"
git diff --staged
git push
```
![Git's conceptual structure](/img/git-conceptual-structure.jpg)
