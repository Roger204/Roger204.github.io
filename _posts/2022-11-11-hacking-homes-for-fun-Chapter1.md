---
title:  "Hacking Homes For Fun: Chapter 1 - The Awning"
---

Once upon a time, I challenged myself to hack devices of ¿my? home. I decided to start with ¿my? Awning as I expected that it would be be the easiest one... And I wasn't wrong at all :). 

The awning moves thanks to an embedded engine which is controlled by a remote control:

![Cherubini remote control](/assets/images/20221111_RemoteControl.jpg){: width="250" style="display: block; margin: 0 auto"}

Even though the specifications of the device claim that it implements the *Rolling code* mechanism (used to prevent Replay attacks), seems that the awning installer understood that using this protection was not necessary... That's bad...

The result is that after spending approximately 30 minutes I could hack very easily the awning, just conducting a replay attack of the signals generated by the 3 switches of the remote control. The following image shows the signal profile of one of the switches:

![Signal profile](/assets/images/20221111_SignalProfile.png){:style="display: block; margin: 0 auto"}

This sadly means that a script kiddie could play with ¿my? awning just for fun... Should I complain to the technician who installed it?

**Details** <br /> Equipment used:
* [HackRF](https://greatscottgadgets.com/hackrf/)
* [URH software](https://github.com/jopohl/urh)

Steps:
* Activate the awning with the remote controller and sniff the signal.
* Resend the same signal.

It wasn't necessary to modify the signal or adjust the equipment, not bad for the first chapter...