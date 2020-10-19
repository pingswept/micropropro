---
title: "The Internet"
draft: false
---

## The Internet: how does it work?

Suppose you're sitting in your apartment, watching some crazy person on Zoom tell you about this new website about electronics that everybody is talking about. She says that the name of the website is [andnowforelectronics.com](http://andnowforelectronics.com), and she pastes a link to the site into the chat window. What happens when you click on the link?

## First, name resolution

First, your computer sends a universal datagram packet (UDP) to port 53 on a domain name system (DNS) server somewhere on the internet. The job of a DNS server is to look up the IP address of the website you're looking for in the distributed global database of domain names.

If you have wireless where you live, the server that your computer targets is probably your wireless router. If you're using your phone, it's a server that's run by AT&T, Verizon, or some phone company like that, and your phone was told where to find it when it connected to the cellular network. You could also be using a public server; for example, Google runs two public DNS servers at the weird IP addresses 8.8.8.8 and 8.8.4.4.

So your computer sends off the UDP packet saying, "Hey, where can I find [andnowforelectronics.com](http://andnowforelectronics.com)?" Despite the site's worldwide popularity, your wireless router probably has no idea, so it makes a request like yours to the DNS server run by whoever sells you an internet connection, like RCN or Comcast.

But again, despite the site's worldwide popularity, Comcast has no idea where to find it, so it makes a request to the authoritative name server for all the domain names that end in .com. If Comcast's server didn't know where to find that server, it could ask one of the 13 root name servers; those servers' addresses are hard-coded into the Comcast server's memory, but Comcast has seen bajillions of requests for .com addresses before, so it surely has the .com name server address cached.

Finally, the .com server sends Comcast over to the authoritative server for andnowforelectronics.com, which is a server run by a domain name registrar in Paris, France, called gandi.net. Their name server, ns1.gandi.net, at long last, answers the question! They do this because I paid them to register the domain name and provide these DNS services, and they know the right IP address because I typed it into their website last summer.

Here's what the Gandi name server sends back:

    id 65452
    opcode QUERY
    rcode NOERROR
    flags QR RD RA
    ;QUESTION
    andnowforelectronics.com. IN A
    ;ANSWER
    andnowforelectronics.com. 10799 IN A 23.239.11.134
    ;AUTHORITY
    ;ADDITIONAL

That IP address, 23.239.11.134, gets passed back to your web browser, and all the DNS servers along the way cache the answer, in case someone else wants to know where to find the site.

## Second, connect to the webserver

Now your computer knows the IP address of the webserver you're targeting. The server is one at a datacenter in New Jersey, owned by a company called Linode. I pay them $5/month, and they let me use their server. The server is almost certainly a multi-core behemoth that is running lots of virtual servers in parallel using a hypervisor, but as far as I can tell, it's just like any other Linux server. My best guess is that the server is in the Cologix data center in Cedar Knolls, NJ: https://goo.gl/maps/J5UagBYytmXPBHRz8

The next step is that your computer sends out a TCP packet to start a connection to the server at 23.239.11.134. Your computer only knows the IP address of your wifi router, so it sends the first packet to that address and hopes it gets there. Your router has no idea how to connect to a server in New Jersey, so it sends the packet upstream to a router at Comcast (or Tufts, or wherever you're getting your internet connection). Your packet will be passed along from router to router. The routers along the way don't know where to find your server, but they each contain a huge table that lists how to get to different networks.

If we use a tool called `traceroute`, we can see the steps that our packet takes to get to the server. From my house in Somerville, here's the path it takes. (The path might be slightly different each time.)

```
Tracing route to andnowforelectronics.com [23.239.11.134]
over a maximum of 30 hops:

  1    <1 ms    <1 ms    <1 ms  192.168.1.1
  2     2 ms     1 ms     1 ms  192.168.0.1
  3    11 ms    11 ms    12 ms  10.23.192.1
  4    39 ms    11 ms    13 ms  bdle1-sub212.aggr1.bos.ma.rcn.net [146.115.22.195]
  5    13 ms     9 ms    10 ms  hge0-0-0-10.core1.sth.ma.rcn.net [207.172.19.191]
  6     9 ms    10 ms    10 ms  207.172.18.70
  7    19 ms    33 ms    15 ms  et-0-0-13.cr1-bos1.ip4.gtt.net [69.174.18.121]
  8    15 ms    14 ms    14 ms  ae10.cr3-nyc3.ip4.gtt.net [89.149.140.182]
  9    17 ms    30 ms    15 ms  ip4.gtt.net [173.205.38.198]
 10     *        *        *     Request timed out.
 11     *        *        *     Request timed out.
 12     *        *        *     Request timed out.
 13    16 ms    19 ms    18 ms  li688-134.members.linode.com [23.239.11.134]

Trace complete.
```

## Third, we ask the server for the webpage

stuff about HTTP, maybe HTTPS?

Should also add stuff about ports, NAT, and port forwarding
