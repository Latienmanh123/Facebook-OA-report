# Facebook Open Academy: A Summary

12 weeks have passed since my involvement in App Inventor 2, and while it has been a while of a time, it was a really enjoyable one and fulfilling experience - something that cannot just be learnt through books alone.

Being attached to a large code base, and having credits to do that is a rare opportunity, and I am thankful for it. If you're thinking of going for Facebook Open Academy, well, go for it! Here are pointers I have learnt from a somewhat Git-ignorant, Java newbie to someone more comfortable with handling these tools after this semester.

![][1]

## Listen, listen, listen.

Listening is an important skill in any field - and this includes coding. I found this topic resonant throughout the duration of Facebook Open Academy. Code is cheap, but it may not be necessarily so that the code written is useful to others. Learn to listen to them, learn to engage with the community, and implement code that people will use. This is something I am trying to learn still.

In all things, ask the community for their ideas. Find out what is needed from the developers, from the people, and the things they would like to see.

This really struck me during my discussions with my mentor Jose, a key contributor / maintainer of the project. Originally, I had in mind a rough sketch of what the component should look like and proceeded to implement parts of it. However, throughout this process, Jose encouraged me to relook at the process by engaging the community with a proposal. He encouraged me to put a proposal out there with SimplePhaser. While the idea was to implement most parts of Phaser.IO, we eventually restrained it to what the user really needed - building an Arcade game, using high-level blocks that a new beginner programmer would like to use. And we did that.

A proposal was put in place, and there was some feedback gathered. Having to discuss ideas and discuss why some features were needed was a constructive part of the discussion - something that was revisited time and again during the duration of SimplePhaser. Additionally for blocks, we moved away from the notions of low-level code and attempted to offer something new to the table - being motivated to create a Mario-style game with high-level behavior and blocks that a novice user would understand. And it worked - both for the implementation (it appears), as well as for the community and us.

We will still continue in that direction for the next phase of user adoption.

## Implement first, think later. Think out of the box.

During the duration of the project, I was stuck for three weeks on a bug which appeared trivial - retrieving a sprite's property through getters. Recalling the blog post, it was not trivial as it involved calling a Javascript function, and awaiting the value of its callback on the Java end - all without direct support of retrieving the return value of the named Javascript function.

Three weeks were spent debugging this issue. The initial implementation was to implement an event-driven framework, whereby the said values would be identified by UUIDs in a key-value Java store. However, in every single instance where the getter was called, the program would hang! There was no idea where it would hang - it just did.

As there was not much form of debugging - there was not much of a debugger in place, and compiling the Java end would take around 7 minutes - leading to 4 changes an hour, debugging was tedious, sometimes tiring and at times painful. Throughout the whole process, I kept with the event-based protocol, having ruled out that constantly parameter polling would be too intensive and inefficient.

Finally, there was some progress after 2.5 weeks and it appeared that while there did not seem to be a bug with the code, it might be possible that there was an issue with how Javascript's webview functions were called and it appeared while they could be called simultaneously out-of-order, somewhere there was a thread pending internally with the first Javascript call (even thought it appeared calls were out of order).

Whichever the case, things did not seem pretty, and I eventually became open to the method of passing the keystore as a JSON continuously between the Java and Javascript ends, at an interval of 0.2 seconds.

It worked! (With not as much lag, but this remains to be seen with more sprites of course).

## Be flexible.

I was hesitant at first contributing to a large code-base, in Java, having come from a C / NodeJS background with little experience in the Java world. IntelliJ was something new to me - what is IntelliJ? Oh and Java - is it inefficient? Why is it using Ant?! The usual stereotypes.

![explanation of how to properly use Git by Jose at Facebook OA][2]

But over time and with prayer, it got better and the more we put our practice into it, the better it became. I was thankful for a good mentor who shared advice on working with App Inventor, getting into Java development in IntelliJ (made the switch from Eclipse and loving it), and even getting up and running with Git through a graphical explanation by my mentor (which I realized, I was using wrongly). Read more books, learn the shortcuts, practice with empty Git repositories, read Stack Overflow, and pray.

Be not afraid to ask, to practice, and learn. It will get better.

## Maintaining a large code base isn't that hard.

Prior to AI2, I have never touched a large code base, only started mini-projects / coded stuff in my spare time / did work for school projects. Maybe because there was not a need, but perhaps because it appeared intimidating. Too many lines. Hard to build. How do I navigate / where do I start?! With practice, it got better.

Somehow, IntelliJ helped (especially with the CTRL + SHIFT + N quick navigation keys, and the target buttons), and being exposed to the code base proved helpful. What really helped though was keeping in touch with my mentor, and discussing with him problems which seem to crop up.

A word of advice: If the docs do not seem too informative, and you tried, approach the community online for help! It really helps when you do, and especially when someone can help you navigate through things.

## TL;DR

Contributing to the MIT App Inventor 2 codebase under the Facebook Open Academy Program in Winter 2015 was a really enjoyable experience. What worked was having a great mentor, and coding something that we really believed in, and enjoyed doing. A new component was drafted, and we had the opportunity to learn things outside the box and would love to see this project to fruition - adoption to the community at large is another phase of learning.

Gained more confidence with contributing to Open Source? Yes I did. Will do it again? Yes, sure will!

And, thank God for a wonderful semester.

 [1]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_400/v1429805702/1888986_10152698445177825_3675151375444878955_o_pb5b8q.jpg
 [2]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_200/v1429805338/IMG_20150201_135722_arjxxn.jpg