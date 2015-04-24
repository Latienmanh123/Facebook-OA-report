# Facebook OA / AI2 - Week 11 (April 8 - April 15)

This week, I spent some time wrapping up the functionality of the SimplePhaser component. To recap, I am developing a component that allows one to easily create games via blocks through the App Inventor framework.

The previous few weeks were intense as the getter code functions refused to work, and was finally narrowed down to a thread issue.

For this week, I worked on adding some touch interactivity to SimplePhaser. Now, there is an integrated event manager(s) for the tracking of swipe (up/down/left/right), in addition to single taps and drags. This was accomplished via HammerJS, and for the record, this added some nice swipe on the Javascript end:

    // for swiping features
    var _bindHammer = function () {
        var ele = document.getElementsByTagName('body')[0];
        var hammertime = Hammer(ele);
    
        hammertime.on('swipeup', function (event) {
            _inputManager.onSwipe('up');
        });
    
        hammertime.on('swipedown', function (event) {
            _inputManager.onSwipe('down');
        });
    
        hammertime.on('swipeleft', function (event) {
            _inputManager.onSwipe('left');
        });
    
        hammertime.on('swiperight', function (event) {
            _inputManager.onSwipe('right');
        });
    
        hammertime.on('swipe', function (event) {
            _inputManager.onSwipe('swipe');
        });
        console.log('--- Attached Hammer.JS ---');
    };
    

![Hammerjs][1]

Also coded this week is the ability to increase world size, and also the ability to move the camera around the world, in addition to being able to track a sprite object with the camera.

## Testing

A small game using the code blocks was written to test the functionality of the game. In this game, rocks fall down from the sky. It is the user's duty to clear the rocks by tapping on the screen, causing them to explode. Bullets in the direction of the user's tap fall from the sky, and are influenced by gravity. The game in action:

<iframe width="420" height="315" src="https://www.youtube.com/embed/4HriQzQxUFs" frameborder="0" allowfullscreen></iframe> 
Here is the program. It also uses another external component, the Timer compoent. The inspiration is that users will mix and match components / sensors in future, to create something interesting! (Proximity?)

![code][2]

## Code base for v0.1-alpha

Code bases have been tagged as v0.1-alpha and released as the following. Still planning to work on a couple of additions / bugs so there might be hotfixes along the way. In either case, this is stable.

*   The Javascript at https://github.com/myrtleTree33/TestBlockly/releases/tag/v0.1-alpha and is hosted on my remote server.
*   The Java at https://github.com/myrtleTree33/appinventor-sources/releases/tag/SimplePhaser-v0.1-alpha .

## Next steps

For the next week, I will concentrate on improving the official documentation. Right now there's still some online proposal going on at https://docs.google.com/document/d/1jcZ3FNsjMZPQVVCyaKAmAktT3MKZLapE3XMJdrMfM9U/edit?usp=sharing , which is targeted as a proposal for features and discussion. The official spec will have information how to properly enforce tasks, for e.g. specifying the correct groups, as well as getting up and running with the game. Hopefully, that can be a testbed to see how quickly users adapt to the SimplePhaser framework, and future adjustments made accordingly.

Also to be added are bux fixtures and introducing this to the community.

## What is implemented

For the record, taken from the release logs, the following are implemented:

    ## Sprites supported:
    
    - Tree
    - Player
    - Rock
    - Sky
    - TiledBackground
    - TilePlatform
    - Platform
    - Bullet
    
    ## Groups supported:
    
    - bullet
    - terrain1
    - terrain2
    - destructibles
    
    
    ## Collision detection handling
    
    ### Bullets 
    
    - terrain1
    - terrain2
    - destructibles
    
    
    ## Camera
    
    - Camera XY setters
    - Camera tracking an object
    
    
    ## User Interaction
    
    - Single Tap / drag
    - Swipe left / right / up / down / general
    
    
    ## Player 
    
    - Ability to change player sprite state (left animation / right animation)
    
    
    ## Features
    
    - Collision detection
    - Automated destruction animation and deletion upon sprite destory
    - Automated destruction of bullets upon hitting object
    - Gravity
    - Getters / Setters
    - Making world larger than screen size
    - Moving camera around world
    - Tracking camera on object
    - Swipe and touch events
    
    
    ## Production-ready URL
    
    - Loaded from a remote server.  To be implemented on device during production.

 [1]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_263/v1429029380/Selection_243_qtf02z.png
 [2]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_600/v1429030916/Selection_241_hsv59g.png