---
title:  "Let's Automate! Pt. 1"
date:   2015-08-26 17:40:00
---

Let's Automate!

I just got two Particle Photon dev boards in the mail.

Let's see if I can get them to replace my janky old Arduino setup, which not only involves hard wires the whole way, but also includes a full sized tower PC running 24/7. Nope!

I'm gonna live blog this for gris (read: for the github commit log karma)

5:40 Download IDE, start reading docs. Seriously starting from dead scratch here.

5:45 Particle's board only supports wireless b and g, so I had to switch to a downgraded router channel. I am not complaining, because they put wifi on a chip smaller than my Shift key for $19, but man, this download is going slow.

5:59 Bad news: Past Rick used industrial strength double sided tape to attach a $2 breadboard to a piece of pallet wood, and the whole thing ripped in half when I took it off. Good news: I put every single piece back together. Gonna take more than that to stop the IoT train. This calls for a beer.

6:09 Forked the "blink LED over web" code and accompanying html file. Flashing to the board now. We'll see...

6:11 It's restarted twice now... still connecting to the internet... uhoh.

6:13 Success! Time to break out the relay and see if we can just bolt it directly on. Where's that pin sheet.....

6:18 Found the pin sheet. 

6:21 Pins connected. Tested. Power is go, but pin 0 doesn't seem to be doing much. Pin sheet says it can put 4.8 out, that should be sufficient.

6:25 Took it apart and put it back together. It works now. These things happen. Probably had some wires switched, since I only had red wires when I soldered this thing.

6:33 I'm searching everywhere, but no light bulbs! I'm about to run downstairs to the liquor store. I wanna hit this one hour mark!

6:37 DONE!! I found a bulb in an old moving box. Just in time. Now for the dweet part.


