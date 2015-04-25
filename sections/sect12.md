# Facebook OA / AI2 – Week 12 (April 15 – April 22)

The week was spent tidying up SimplePhaser with the master branch for submission. Some comments had to be renamed, accidental indentations had to be removed. The code was not synced with master for a while, and hence needed to be updated with `upstream`.

SimplePhaser is now ready for merging with upstream, as far as the code base is concerned:

![enter image description here][1]

Right now, its mainly tidying up the user API, and convincing users to get aboard the system - simplifying workflows which may have been overlooked, and making it not overtly complex such that a beginner has to read a manual. So its refining the workflow, thinking about what the user would have after viewing the prototype.

> What is a callback?
> 
> What is SimplePhaser?
> 
> what are the sprite groups available and how do I use them?
> 
> How do I create many sprites on the canvas?

This is crucial, as the whole SimplePhaser package features many blocks (due to its nature of being a game creation engine component), and would need a slightly different approach towards user adoption (Users might be overwhelmed by the blocks).

> Follow the principle of least astonishment.

To facilitate user adoption, next steps would fall under two categories:

1.  Empowering the user by providing online tutorials on using SimplePhaser to build games. This could be similar to the videos we have started on App Inventor 2 on the main page:
2.  Providing a community of support. As it is, to ensure that questions on the component by users get answered responsively and without delay. This would require support from the community, which should be easier if this gets through a couple of vetting / refinement prior to release (Releasing suddenly might surprise the community)
3.  Simplifying the workflow of events. This has been considered during the drafting of SimplePhaser in the developer's forum, and should continue to adapt to input based on what the community suggests. More feedback might imply more support from the community.
4.  Renaming SimplePhaser to something which says much about its name. Few outside the Javascript / Game development community might have heard about PhaserIO. Hence, renaming the SimplePhaser component to something like ArcadeGame would help user to be less astonished by the introduction of the component.

Some thoughts to consider for next steps after initial prototyping and development. The next phase would be an interesting one for me, and I am keen to see SimplePhaser being adopted by the community after Facebook OA.

![enter image description here][2]

## Adding double-tap functionality

This week was also spent fixing a couple of undetected bugs, and refining the user interaction manager such that it is able to recognize double taps. This was not as trivial as the double-tap handler would have to wait for a while before it can be sent out, and in the event of not detecting a second tap, would fire a single tap event handler.

As the current user interaction system features inputs that are much richer than that supported by pure PhaserIO (for example, taps, pinches, rotations and swipes / drags), the implementation was a coordination between PhaserIO and Hammer.JS, a popular mobile user input framework. Mutex locks were first considered, however they frequently locked and are not recommended in Javascript. Instead, a timed delay of 5ms was given to avoid race condition between the PhaserIO native input and Hammer.JS's event manager, which worked pretty well.

<iframe width="560" height="315" src="https://www.youtube.com/embed/zZvIM0khw6A" frameborder="0" allowfullscreen></iframe> 
![enter image description here][3]

So yes, Phaser can now swipe left and right! To test the functionality, here is a simple game, which moves a player sprite according to the following moves:

*   Swipe left: Move left
*   Swipe right: Move right
*   Double tap: Jump
*   Tap: trigger App Inventor's text-to-speech component to say "boom!"

Note how the camera locks onto the player during moves.

## TL;DR and next steps

Having seen a component from conceptualization, to grappling with the AI2 framework, to coordinating data synchronization, to the end in a relatively unconventional way (using Java to control Javascript and controlling state!) has been a wonderful experience for me, to challenging things out of the box as well as receiving input from wonderful mentors and the community. The product is done, deliverables submitted, however next steps to its integration would be a different set of learning experiences (less of coding and more of listening and user adoption), which I am keen to continue learning after the completion of the App Inventor program.

 [1]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_700/v1429938023/Selection_300_higoa8.png
 [2]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_500/v1429938019/Selection_301_jhhrye.png
 [3]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_900/v1429938020/Selection_296_oyvqxv.png