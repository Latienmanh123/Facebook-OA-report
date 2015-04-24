# Facebook OA / AI2 – Week 8 (March 18 – March 25) - Added a collision manager!

For this week, I have successfully implemented the collision manager. It builds on top of PhaserIO's collision manager, which already supports some basic collision handling across groups.

Triggering an event in PhaserIO can be done through the following:

    _game.physics.arcade.collide(__._groups.destructibles, __._groups.bullet, function () {
        console.log("triggered!")
    }, null, this);
    

Helpful, but too low-level in my opinion for our needs of code blocks.

Our idea was to make it really easy for the user to write code, certain objects (bullets) have automatic collision behavior embedded in them. For example, bullets should blow up when coming into contact with a sprite group.

So here is the new block!

![enter image description here][1]

So, when Sprite A collides with Sprite B, we worked this event to fire, on the Java end, behind the scenes. It it works fine!!

Below shows 2 different scenes in action (one in the browser, the other a native app created through the code blocks.)

![enter image description here][2] ![enter image description here][3]

It comes with a nice destruction animation, upon being destroyed.

## Implementation

Behind the scenes, a centralized collision manager handles the collisions between sprites. If you recall, we decided upon setting SimplePhaser to utilize fixed groups, instead of letting the user control the collision groups (doing otherwise would be really messy and too low-level setting up collisions, as users would have to tweak a little of the low-level code, at least 3 to 4 steps before doing anything. By attaching pre-defined collision hooks to these sprites in a given fashion, we avoid having to attach collision callbacks for every single sprite to every other sprite in the world.

As it is, this is pretty heavy in SimplePhaser and here is how it looks like:

            // collision detection
            /** terrain 1 **/
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.terrain1);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.terrain2);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.powerups);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.destructibles);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.player1);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.player2);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.enemy1);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.enemy2);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.enemy3);
    
            /** Terrain 2 **/
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.terrain2);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.terrain1);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.powerups);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.destructibles);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.player1);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.player2);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.enemy1);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.enemy2);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.enemy3);
    
            /** Bullet **/
                //__._game.physics.arcade.collide(__._groups.bullet, __._groups.destructibles);
                //__._game.physics.arcade.collide(__._groups.bullet, __._groups.terrain1);
                //__._game.physics.arcade.collide(__._groups.bullet, __._groups.terrain2);
            __._game.physics.arcade.collide(__._groups.destructibles, __._groups.bullet, _collisionManager, null, this);
            __._game.physics.arcade.collide(__._groups.terrain1, __._groups.bullet, _collisionManager, null, this);
            __._game.physics.arcade.collide(__._groups.terrain2, __._groups.bullet, _collisionManager, null, this);
    

All the unified collision manager has to do now is to send the signal over to Java, and raise an event:

        if (hasAndroid) {
            Android.onCollision(spriteA.name, spriteA.obj.group, spriteB.name, spriteB.obj.group);
        }
    

## Other blocks

In addition, I have added deletion, setting the XY coordinates of a sprite, this week.

## Next steps

Next steps will be adding getters and setters to sprite blocks.

 [1]: http://res.cloudinary.com/jhtong/image/upload/v1429608356/Selection_250_pz1kef.png
 [2]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_200/v1429608513/2_yl6ci2.png
 [3]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_200/v1429608513/3_en5qhh.png