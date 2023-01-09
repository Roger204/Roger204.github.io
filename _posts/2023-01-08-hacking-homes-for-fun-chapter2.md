---
title:  "Hacking Homes For Fun: Chapter 2 - The Alarm Tag"
---

Nowadays most of the home alarms use a contactless tag to activate/deactivate the alarm. Those tags bring cryptographic functionalities; however, I want to verify if they are really used. As an example, the remote control of [Chapter1](hacking-homes-for-fun-Chapter1) had anti-replay capabilities which were not used by the system integrator.

I started analyzing the type of tag of the home alarm, this can be easily done using an NFC enabled smartphone and the [NXP Tag Info](https://play.google.com/store/apps/details?id=com.nxp.taginfolite) application. The tag is an ISO15693 with cryptographic capabilities. 

![TagInfo Image](/assets/images/20230106_TagInfo.png){: width="200" style="display: block; margin: 0 auto"}

NXP Tag Info also indicated that no cryptographic keys were set, therefore, I suspected that the alarm device only checks the UID of the tag. The UID  is a unique identifier which must NEVER be used for security means, as it can be easily replicated.

After the initial analysis, seems clear that it will not be very hard to create a fake tag to deactivate the alarm. To do so I used the Proxmark3 as shown below. Basically, I used a script to use the [standalone mode](https://github.com/RfidResearchGroup/proxmark3/wiki/Standalone-mode) which has two steps:

1. Reader mode, reads a Tag which is approached.
2. Emulation mode, emulates the read Tag.

![Emulating Tag](/assets/images/20230106_122034.gif){: width="200" style="display: block; margin: 0 auto"}

Once the Tag was emulated, I performed a proof of concept to verify that the Alarm Tag could be bypassed, the steps to conduct were:

1. Activate the alarm
2. Once the alarm was activated, use the emulation tag to deactivate it.

The results can be seen below:

![Deactivating alarm](/assets/images/20230106_122254.gif){: width="200" style="display: block; margin: 0 auto"}

As in [Chapter1](hacking-homes-for-fun-Chapter1), although the tag implements cryptographic functionalities, the system integrator chose not to use it, probably for simplicity or lack of security knowledge. 

Even more; after further research I was able to identify that only the 3 last bytes of the UID were checked. The other 5 bytes were ignored:

![Emulating Tag](/assets/images/20230106_UID.png){: style="display: block; margin: 0 auto"}

I already advised both the alarm manufacturer and the system integrator, and they indicated that the security would be enchanced :).