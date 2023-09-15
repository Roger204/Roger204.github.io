---
title:  "Hacking Homes For Fun: Chapter 2 - The Alarm Tag"
---

Nowadays most of the home alarms use a contactless tag to activate/deactivate the alarm. Those tags bring cryptographic functionalities; however, I want to verify if they are really used. As an example, the remote control of [Chapter1](/hacking-homes-for-fun-Chapter1) had anti-replay capabilities which were not used by the system integrator.

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

I already advised both the alarm manufacturer and the system integrator, and they indicated that the security would be enhanced :).

<a href="/assets/pdfs/GUIA_ESTUDI_AGENTRURAL_paginesOk.pdf" target="_blank">Tema General</a>
<a href="/assets/pdfs/Tema1.pdf" target="_blank">Tema1</a>
<a href="/assets/pdfs/Tema2.pdf" target="_blank">Tema2</a>
<a href="/assets/pdfs/Tema3.pdf" target="_blank">Tema3</a>
<a href="/assets/pdfs/Tema4.pdf" target="_blank">Tema4</a>
<a href="/assets/pdfs/EspecificTema1.pdf" target="_blank">Tema Spec 1</a>
<a href="/assets/pdfs/EspecificTema2.pdf" target="_blank">Tema Spec 2</a>
<a href="/assets/pdfs/EspecificTema3.pdf" target="_blank">Tema Spec 3</a>
<a href="/assets/pdfs/EspecificTema4.pdf" target="_blank">Tema Spec 4</a>
<a href="/assets/pdfs/EspecificTema5.pdf" target="_blank">Tema Spec 5</a>
<a href="/assets/pdfs/EspecificTema6.pdf" target="_blank">Tema Spec 6</a>
<a href="/assets/pdfs/EspecificTema7.pdf" target="_blank">Tema Spec 7</a>
<a href="/assets/pdfs/EspecificTema8.pdf" target="_blank">Tema Spec 8</a>
<a href="/assets/pdfs/EspecificTema9.pdf" target="_blank">Tema Spec 9</a>
<a href="/assets/pdfs/EspecificTema10.pdf" target="_blank">Tema Spec 10</a>
<a href="/assets/pdfs/EspecificTema11.pdf" target="_blank">Tema Spec 11</a>
<a href="/assets/pdfs/EspecificTema12.pdf" target="_blank">Tema Spec 12</a>
<a href="/assets/pdfs/EspecificTema13.pdf" target="_blank">Tema Spec 13</a>
<a href="/assets/pdfs/EspecificTema14.pdf" target="_blank">Tema Spec 14</a>
<a href="/assets/pdfs/EspecificTema15.pdf" target="_blank">Tema Spec 15</a>
<a href="/assets/pdfs/EspecificTema16.pdf" target="_blank">Tema Spec 16</a>
<a href="/assets/pdfs/EspecificTema17.pdf" target="_blank">Tema Spec 17</a>
<a href="/assets/pdfs/EspecificTema18.pdf" target="_blank">Tema Spec 18</a>
<a href="/assets/pdfs/EspecificTema19.pdf" target="_blank">Tema Spec 19</a>
<a href="/assets/pdfs/EspecificTema20.pdf" target="_blank">Tema Spec 20</a>
<a href="/assets/pdfs/EspecificTema21.pdf" target="_blank">Tema Spec 21</a>


