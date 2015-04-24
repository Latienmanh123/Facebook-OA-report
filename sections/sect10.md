# Facebook OA / AI2 – Week 10 (April 1 – April 8)

This week, I am into my third week resolving the getter / setter bug, and finally managed to solve it!

## The problem

To recap, the setter was working all fine, as the game state was maintained on the Javascript end and altering was simply performed through a one-time function call. However, the getter was slightly different. The event had to be triggered from the Java end, calling a Javascript function and somehow returning a value back to Java, in-order and synchronous. There was no method existing to directly retrieve a Javascript function call's routine directly, so a method had to be devised.

Previously, this was done through an event-driven method. Java would call the Javascript function with a unique UUID as a reference. Upon completing the routine, the Javascript function call another universal Java function to put it into a key-value data structure, using the UUID given. The original Java function would be polling this data structure in the meantime, and upon finding a UUID which matches, would deque the entry, and return the value to the user.

This method did not work! After numerous checks, there was no reason why it should not work and the problem was isolated to a possible way Java webview might have handled the thread calls. Apparently, there was a blocking thread somewhere after the original Java function was called, leading to the game blocking on this thread and hence hanging. Given not much form of debugging and a relatively long build time, this was frustrating and took a long time to trace. But nevertheless fun indeed!

## The solution

In the end, I adopted another alternative (thank God!) that solved the issue. Instead of storing state on the Javascript function, sprite states were also posted frequently (~0.2 secs, any slower would report the wrong value) to the Java end. These reports were stored in Java, and upon requesting for a getter function call, the Java function would return its last reported value back to the program executed. Dirty, quick, and somewhat sounding a little inefficient, but it works!

## TL;DR

This might be getting a little hard to see without visuals, so here is a callback diagram:

![callback-diagram-new][1]

Just to test the piece works, I wrote a program to set the value of a sprite using its getter (which should effectively not hang the game and run as per normal).

Phew. It worked.

For next steps, I will be moving on to adding user interfacing and packaging the game for release to the public.

 [1]: http://res.cloudinary.com/jhtong/image/upload/v1429450614/Selection_291_glmzej.png