### How does ScrollMagic work?
The principle design pattern of ScrollMagic is a __controller__[1] that has arbirtary number of __scenes__[2] attached to it.
 1. There is one __controller__ for each scroll container. In most cases there is only one controller and the scroll container is usually the browser window. But you can also use DIV elements for scrolling and even have multiple containers on your page. The controller also defines which direction should be scrolled (horizontal or vertical) and is responsible for keeping all scenes updated.
 2. A __scene__ defines what should happen when, meaning at which scroll position. It can trigger animations, pin an element, change element classes or anything else you might desire.

### Defining the Controller

As mentioned above in most cases the scroll container is the browser window. To create a ScrollMagic controller with the default settings we use the main [`ScrollMagic()`](file:///Users/janpaepke/Desktop/ScrollMagic%20Project/ScrollMagic/docs/ScrollMagic.html#ScrollMagic) class.
We create a new instance of it and assign it to a variable, so we can reference it later:
```
var controller = new ScrollMagic();
```
That's it! Now for the more interesting part:

### Defining Scenes

Scenes are created by using the [``ScrollScene()``](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) class. A ``ScrollScene`` defines where the controller should react and how. To create a scene we must create a variable:

```javascript
var scene;
```

In this case we've defined a variable called “scene” and now we'll give it a value that will initialize a new ``ScrollScene()`` class.

```javascript
var scene = new ScrollScene();
```

Inside ``ScrollScene`` we can place an [object](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) of associated properties and values that are made available according to the [docs](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene)…

```javascript
var scene = new ScrollScene({
  triggerElement: '#pinned-trigger1', // point of execution
  duration: 400 // pin the element for a total of 400px
})
```

### Scene Control Methods
Setting up the scene is great and all, but now we need to get down to business and control it. This is where ScrollMagic's [Scene Control Methods](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#toc3) come into play. We can add these control methods to our scene's individually like so…

```javascript
var scene = new ScrollScene({
  triggerElement: '#pinned-trigger1', // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin('#pinned-element1'); // the element we want to pin
```

In the example above we're using a technique called ”chaining” with the [``setPin()``](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#setPin) method in order to add it to our ``ScrollScene()`` class. In this case the value passed in quotes as a string is the id of the element we wish to pin on scroll.

### Adding Scenes to Controller

In order to tell ScrollMagic what we want to do we have to add our scene and it's logic to the controller we defined at the very beginning…

```javascript
var scene = new ScrollScene({
  triggerElement: '#pinned-trigger1', // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin('#pinned-element1'); // the element we want to pin

// Add Scene to ScrollMagic Controller
controller.addScene([
  scene
]);
```

If you desire multiple scenes you can pass them to the controller just as the example shows below:

```javascript
// Add Scene to ScrollMagic Controller
controller.addScene([
  scene1,
  scene2,
  scene3
]);
```

Since we're using the var we defined for the ``ScrollMagic()`` class called “``controller``,” ``addScene([])`` will help insert the scenes we've defined. You could also chain instead using the ``addTo()`` method on ``ScrollScene`` like so…

```javascript
var scene = new ScrollScene({
  triggerElement: '#pinned-trigger1', // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin('#pinned-element1') // the element we want to pin
.addTo(controller); // Add Scene to ScrollMagic Controller

var scene2 = new ScrollScene({
  triggerElement: '#pinned-trigger2', // point of execution
  duration: 600 // pin the element for a total of 400px
})
.setPin('#pinned-element2') // the element we want to pin
.addTo(controller); // Add Scene to ScrollMagic Controller
```