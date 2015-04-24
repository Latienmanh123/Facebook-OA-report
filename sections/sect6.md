# Facebook OA / AI2 – Week 6 (March 4 – March 11)

This week, I am down with Dengue, a mosquito-born ailment in Singapore. Hence went slow on coding.

This week, I managed to churn a Gulp script together with Browserify. Previously, the build was a rough sketchup and hence utilized many `<script>` tags. Talk about having multiple scripts, handling dependencies, ensuring that things are called properly and the like. This is my first time using Gulp, and its going pretty well!

Now is is really simple, following NodeJS's pattern.

**Dependencies:** Managed with Bower

**Build:** Gulp

**Minification:** Browserify

So now we can simply do the usual node `require()` and dependencies will be automatically handled across modules.

    require('../bla.js');
    ...
    

For sprites, I have settled on an inheritance pattern enforced by mixins. There will be a basic sprite which handles garbage collection methods in the background. Hence, the idea is that these sprites will feature very high-level methods to the user and will not bother about how to, for example, load a texture for the tree sprite or perhaps even configuring collision and physics behavior for a rock.

So after much experimentation, here is the final pattern for a basic sprite!

    __generators.SimpleSprite = function(name) {
        var _scope = undefined;
    
        var _kill = function() {
        delete this;
        }
    
        var _init = function(scope) {
        _scope = scope;
        ...
        }
    
        /**
         * Override this implementation.
         */
        var init = function() {
        /** Insert code here **/
        /** End insert code here **/
        _init(this);
        }
    
        /**
         * Override this implementation.
         */
        var kill = function() {
        /** Insert code here **/
        /** End insert code here **/
        _kill();
        }
    
        return {
        _init: _init,
        _kill: _kill,
        init: init,
        kill: kill
        }
    }
    

All future sprites implement the kill and init functions, instead of letting the user do so. No need for the user to program an explosion animation, no need to care for mass and etc. Take for example, the rock sprite:

    __generators.rock = function (group, name, x, y, gravity) {
        //var nativeObject = __generators.SimpleSprite('rock1');
        var nativeObject = __generators.SimpleSprite(name);
    
        var init = function () {
        var rock = $blast._groups[group].create(x, y, 'rock1');
        rock.group = group;
        rock.body.gravity.y = gravity;
        rock.body.bounce.y = 0.7 + Math.random() * 0.2;
        rock.outOfBoundsKill = true;
        rock.body.collideWorldBounds = true;
        this.obj = rock; // add to object
        nativeObject._init(this);
        console.debug("Init rock at x=" + x + ',' + y);
        };
    
        var kill = function () {
        console.log("=KILL= I got called");
        __generators.explosion(this.obj.x, this.obj.y);  // plays an explosion
        this.obj.destroy();
        nativeObject._kill();
        };
    
        return _.extend({}, nativeObject, {
        init: init,
        kill: kill
        });
    };
    

Here's a few sprites and the garbage collector dump, just to test things out on the backend:

![enter image description here][1]

Looking good! For next steps, will attempt to link the Java and Javascript sides together.

 [1]: http://res.cloudinary.com/jhtong/image/upload/c_scale,w_826/v1429679591/1_tzidqf.png