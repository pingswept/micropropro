---
title: "Rant: security"
draft: false
---

This is at least as good a time as any for me to summarize the various countermeasures that I have implemented in my life to resist the surveillance state, to the extent that’s possible. Most of these things are actually pretty easy to do, and almost all of them improve your quality of life in the long run, even if some of them are difficult in the short term.

## Countermeasures I have implemented ##

* Deleted Facebook, Instagram, Reddit, Twitter (x2), Flickr, Yahoo, Dropbox, iCloud, Box, LinkedIn and Google accounts (x4). (I do still have one Google account as a  rescue account for my domain registrations, but I rarely log into it. My Twitter accounts still exist, but I haven’t logged in in years.)
* Installed an adblocker (uBlock Origin) on all my browsers. On my phone, AdGuard. Set them to block third-party cookies.
* Switched to Firefox or, in some cases, Chromium, instead of Chrome, Safari, or whatever Microsoft is calling their browser now.
* Signed up for Fastmail as a replacement for Gmail. For a few years, I ran my own mail server on a Raspberry Pi, but it ended up being too irritating to maintain.
* Instead of relying on RCN or AT&T for DNS, signed up for NextDNS and turned on a bunch of their blocklists. This has the nice effect of blocking a lot of ads in apps on my phone, and for my whole family. (Occasionally, it breaks some stupid website that still requires pop-ups.)
* Set up Lastpass as a password manager on my phone, tablet, and PC.
* This next one was huge: made my browser dump cookies every time I close it. This would be really annoying without Lastpass. It is still pretty annoying.
* Convinced my family and a couple of my friends to switch to Signal for encrypted messaging.
* Set up SSL certificates with Let’s Encrypt for all the websites I manage (haven’t gotten to the ME30 one yet).
* Used my wood stove to burn all mail I receive that has even slightly personal information on it.
* For the one sort-of social network I do use, Strava, my account is non-public, under a fake name, and has no pictures.
* Until this whole pandemic thing started, I paid for almost everything that I bought in person with cash.
* As a substitute for Dropbox, I set up an instance of Nextcloud. It has worked quite well.
* I have location services turned off on my phone for all apps. I don’t have any Google or Microsoft apps installed on my phone.
* Deleted my Goodreads account, wrote a Flask app to track all the books I read. Wasn’t actually very successful, but fortunately, since my children arrived, I have very little time to read books, and especially not complex books that I might want to read again.

But I’m still a regular user of Amazon, and I have an iPhone and an iPad. I’m not pure. I’ve been thinking about switching to the Librem 5 for a phone. We’ll see.

I should also say that I am not trying to claim that I have totally escaped surveillance, or even close. For me, this is more of a recreational activity, a fun challenge to see if I can keep using the internet while at least partially confounding surveillance.

One other idea that I haven’t implemented yet is writing a program called Chaffic, a mix of chaff and traffic. The idea is that it’s a daemon that runs in the background on whatever device you have, and it has a list of, say, the 1000 most popular websites. 24 hours a day, it fetches new versions of those popular websites on your behalf. Then, you run a caching proxy like Varnish, so that when you actually want to visit a website, there’s a decent chance that it has already been cached for you. This speeds up your browsing, while also hiding your actual browsing in a sea of generic traffic.

`/rant`, I guess.
