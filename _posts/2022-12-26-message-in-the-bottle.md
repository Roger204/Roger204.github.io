---
title:  "Message to the Future beings"
---

Have you ever though to send a message for the future beings? No matter who would read it? The requirements are to generate a message that will be stored forever but than only be read in the future...

![Message in Bottle](/assets/images/20221225_message-bottle.jpg){: width="250" style="display: block; margin: 0 auto"}

Let's see how you can do it. Let's build a message which can be read but not understood... wait! What? Let's see how real crypto, not the crypto bro's crypto can help us:

1. Generate a plain message.
2. Generate a random number of 16 bytes.
3. Encrypt the message with this key.
4. Delete this key and do not write it down.
    - Optionally you can just show some bytes to "regulate" the future time in which could be read.

The result could be something like this:
![Message Future Beings](/assets/images/20221226_MessageFutureBeings.png){: width="500" style="display: block; margin: 0 auto"}

It includes the encrypted message, and a flag for the decryption with a text in plain and its encryption to help the future reader :) . Finally we should store it in a permanent not mutable storage, and nothing more than the [ipfs](https://ipfs.tech/).

I already [did it](https://ipfs.io/ipfs/QmPgW7xu522Dy91xPg9nH5ZVGwxgd5G55BWwRj5Qbxc28v?filename=LetterForFutureBeings.pdf).