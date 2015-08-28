---
title:  "Let's Automate! Pt. 1"
date:   2015-08-26 17:40:00
---

I just got two Particle Photon dev boards in the mail.

![Particle Photons]({{site-url}}/assets/images/automation/photon-unboxing.jpg)

Let's see if I can get them to replace my janky old Arduino setup, which not only involves hard wires the whole way, but also includes a full sized tower PC running 24/7. Good riddance to this piece:

![Arduino Setup]({{site-url}}/assets/images/automation/old-arduino.jpg)

P.S. yes those are nails attaching the microcontroller and relay.

I'm gonna live blog this for grins (read: for the github commit log karma)

__5:40__ Download IDE, start reading docs. Seriously starting from dead scratch here.

__5:45__ Particle's board only supports wireless b and g, so I had to switch to a downgraded router channel. I am not complaining, because they put wifi on a chip smaller than my Shift key for $19, but man, this download is going slow.

__5:59__ Bad news: Past Rick used industrial strength double sided tape to attach a $2 breadboard to a piece of pallet wood, and the whole thing ripped in half when I took it off. Good news: I put every single piece back together. Gonna take more than that to stop the IoT train. This calls for a beer.

![Fuck]({{site-url}}/assets/images/automation/breadboard-broken.jpg)

__6:09__ Forked the "[blink LED over web](https://docs.particle.io/guide/getting-started/examples/photon/#control-leds-over-the-39-net)" code and accompanying html file. Flashing to the board now. We'll see...

![Lit Photon]({{site-url}}/assets/images/automation/photon-lit.jpg)

__6:11__ It's restarted twice now... still connecting to the internet... uhoh.

<iframe src="//gfycat.com/ifr/DearestOrneryCatbird" frameborder="0" scrolling="no" width="540" height="540" style="-webkit-backface-visibility: hidden;-webkit-transform: scale(1);" ></iframe>

__6:13__ Success! Time to break out the relay and see if we can just bolt it directly on. Where's that pin sheet.....

__6:18__ Found [the pin sheet](https://docs.particle.io/assets/images/photon-kit-new.jpg). 

__6:21__ Pins connected. Tested. Power is go, but pin 0 doesn't seem to be doing much. Pin sheet says it can put 4.8 out, that should be sufficient.

__6:25__ Took it apart and put it back together. It works now. These things happen. Probably had some wires switched, since I only had red wires when I soldered this thing.

![Relay Connected]({{site-url}}/assets/images/automation/relay-connected.jpg)

__6:33__ I'm searching everywhere, but no light bulbs! I'm about to run downstairs to the liquor store and see if they have light bulbs. I wanna hit this one hour mark!

<iframe src="//gfycat.com/ifr/ImmaculatePreciousAmericanwigeon" frameborder="0" scrolling="no" width="540" height="540" style="-webkit-backface-visibility: hidden;-webkit-transform: scale(1);" ></iframe>

__6:37__ DONE!! I found a bulb in an old moving box. Just in time. Now for the dweet part.

__6:41__ This calls for a beer. Obviously.

__6:45__ I actually don't know shit about sending POST requests. Also, I don't think I even need dweet.io anymore. This is simultaneously awesome and sad, because their service is genuinely great. Good F'ing riddance to having to run a node server, though.

__6:48__ Oh, there's a [jQuery.post](https://api.jquery.com/jquery.post/). Walp. That's that. Big ups John Resig! Let's write some jQuery.

__6:50__ I may have spoken too soon about not needing Dweet. Looking at my old automation app code, half of what dweet does is send instructions, but the other half is loading the past feed to accurately present the current state of the apartment when the app loads. I don't know if I can query state with Photon, so that dweet code might have to stay if only to keep track of the past.

__6:53__ I think I'm wildly wrong about that last bit. Looks like Particle has an entire metrics GUI and everything, and Spark.publish() does the eqivalent of dweeting.

__7:04__ This third beer and the unexpected complexity of Particle's webhook system are coming together in a way that isn't awesome.

__7:07__ I'm just gonna wing it, start publishing empty events, and see what happens.

__7:12__ In addition to writing to the LEDs, I'm now also issuing a `Particle.publish("demo", command);` call. What will that look like? Who knows.

__7:14__ The dashboarding tracking looks good. But does it persist when I close the dashboard? Apparently this is an in-progress feature. (Read: it doesn't exist yet) Shit!

__7:36__ Again in the nick of time! We have liftoff. New Particle API calls have been added to the old home automation app. It's still sending Dweet calls when the Particle API calls succeed, so that it can keep track of its state the way it always has. Overall, a very smooth refactoring.

Aaaaand that's all for now. Just under 2 hours - I'm very happy with that number. In part 2 I'll go into more detail about exactly how this thing is put together, and probably give away the web code. For now, I'm super busy building [Dash](https://getdash.io/).