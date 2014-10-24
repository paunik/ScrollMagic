### How does ScrollMagic work?
The principle design pattern of ScrollMagic is a __controller__[1] that has arbirtary number of __scenes__[2] attached to it.
 1. There is one __controller__ for each scroll container. In most cases there is only one controller object and the scroll container is the browser window. But you can also use DIV elements for scrolling and even have multiple containers on your page. The controller also defines which direction should be scrolled (horizontal or vertical) and is responsible for keeping all scenes updated.
 2. A __scene__ defines what should happen when, meaning at which scroll position. It can trigger animations, pin an element, change element classes or anything else you might desire.

### Defining the Controller

As mentioned above in most cases the scroll container is the browser window. To create a ScrollMagic controller with the default settings we use the main [`ScrollMagic()`](file:///Users/janpaepke/Desktop/ScrollMagic%20Project/ScrollMagic/docs/ScrollMagic.html#ScrollMagic) class.
We create a new instance of it and assign it to a variable, so we can reference it later:
```
var controller = new ScrollMagic();
```
That's it! Now for the more interesting part:

### Defining Scenes

Scenes are created by using the [``ScrollScene()``](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) class. A ``ScrollScene`` defines where the controller should react and how.
Here we define a variable called “scene” and we'll create a new ``ScrollScene()`` instance.

```javascript
var scene = new ScrollScene();
```

Inside ``ScrollScene`` we can place an [object](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) of associated properties and values that are made available according to the [docs](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene)…  
These options describe the behavior of our Scene and in order to figure out what value has what effect you can play around in the [Scene Manipulation Example](http://janpaepke.github.io/ScrollMagic/examples/basic/scene_manipulation.html)

```javascript
var scene = new ScrollScene({
  triggerElement: '#pinned-trigger1', // starting point of the scene
  duration: 400 // pin the element for 400px of scrolling
})
```
### Adding Scenes to Controller

In order to have the scenes react to the scrolling of the container we have to add our scene to the controller we defined at the very beginning…

```javascript
var scene = new ScrollScene({
  triggerElement: '#trigger1', // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin('#pinned-element1'); // the element we want to pin

// Add Scene to ScrollMagic Controller
controller.addScene(scene);
```

If you desire multiple scenes at once you can pass them to the controller just as the example shows below:

```javascript
// Add Scene to ScrollMagic Controller
controller.addScene([
  scene1,
  scene2,
  scene3
]);
```

Instead of telling the controller what scenes to add you can also tell the scene to be added to a certain controller:

```javascript
var scene = new ScrollScene({
  triggerElement: '#trigger1'
})
.addTo(controller); // Add Scene to ScrollMagic Controller

var scene2 = new ScrollScene({
  triggerElement: '#trigger2'
})
.addTo(controller); // Add Scene to ScrollMagic Controller
```

In the above example we're using a technique called ”chaining” with the [``addTo()``](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#addTo).
If no Semicolon ends the line, we can continue adding `ScrollScene` methods and ”chain” them together.

Next let's start adding some animation to our scenes in the next Chapter: [[Tweens]]