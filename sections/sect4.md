# Facebook OA / AI2 – Week 4 (February 18 – February 25)

This week was spent thinking of the possible workflow. I have resolved the multiplexing problem by intending to move the Phasor Blockly IDE into a separate pop-up window. Thus the IDE based as a HTML5 webapp will solely output Javascript. As existing components are available in Blockly, such as the creation of lists and arrays, the task is eased somewhat with the provision of core components.

The whole integration is scratch-padded into a webapp document, with package management by Bower. I am pretty satisfied with the organization and this helps in getting up to speed with development. When ready, it may be possible for this IDE to be contained in a separate module (as per standard, modularized practice) and deployed as an iframe component in App Inventor2. This is still sketchy and the aim is to create a simplified game using a simplified Blocks workflow in AI2 first.

To understand the workflow of components, I have followed a tutorial online to create the game shown below. It is a game to collect stars. In addition, as Phasor IO relies heavily on function chains (and thinking in the line of a beginner programmer), I am adamant that these chains would have have to be simplified. For example, the API call to enable physics on an object is

    rock.physics.enableBody = true; 
    rock.body.gravity = 300;
    

which probably does not make sense to a beginner programmer! So the Blockly equivalent should be instead should be instead look like

![enter image description here][1]

I will be suggesting these to Jose for consideration. We can hopefully move forward with our project next with the creation of a few varying blocks.

Right now, the current mock framework spews out PhaserIO Javascript which can be embedded into a template file. I will look into embedding these live, such that the game can be previewed live as we code.

The next phase of development is to get basic generator going, which can be embedded as a module the App Inventor’s repository later.

 [1]: http://res.cloudinary.com/jhtong/image/upload/v1429710019/Selection_298_ndvual.png