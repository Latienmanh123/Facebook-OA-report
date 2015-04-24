# Facebook OA / AI2 – Week 9 (March 25 – April 1)

For this week, I added new components to the game. One of these components is a flexible platform.

Recalling our previous implementation of platform, there was no support for custom-sized platforms. In the latest iteration however, this is possible.

I also added a couple of animated sprites to control the user animations. However, instead of dealing with the low-end Blockly code, it is possible to change the state of the player sprite (running / moving / left / right) via a simple function call. Phaser already does some of the heavy-lifting (For example, cutting up the spritesheet into the various frames), however this is not intuitive and may be too slow for the novice user if it were implemented through blocks.

So here is the game in action, with a couple of new sprites:

![game in action][1]

Oh and, you could change the texture of the custom platform!

**And the blocks:**

### Create a user:

![block-1][2]

### Ever wanted the user to turn left? No problem!

![changeState][3]

### And the custom platform block:

![blocks-3][4]

For next steps, I am debugging the getter function. Right now the issue with the getter is, synchronizing a bi-directional callback between the Java and Javascript endpoints. Its using an event-driven callback, and while it seems alright, the game somehow hangs every time. Debugging it for next week! (Pressing issue).

 [1]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_879/v1429451559/Selection_213_c1qozj.png
 [2]: http://res.cloudinary.com/jhtong/image/upload/v1429451720/Selection_259_we10yb.png
 [3]: http://res.cloudinary.com/jhtong/image/upload/v1429451738/Selection_277_xtkayl.png
 [4]: http://res.cloudinary.com/jhtong/image/upload/v1429451698/Selection_262_vyu8hm.png