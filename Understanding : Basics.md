### Initial Setup
To get started you'll need to reference jQuery and the ScrollMagic library from your HTML doc just before the closing ``<body>`` tag. Each project will have at least one call to the ``ScrollMagic()`` class which is the main class needed once per scroll container. Refer to the code block below for an example of this setup.

```markup
<script src="path/to/js/jquery.min.js"></script>
<script src="path/to/js/jquery.scrollmagic.min.js"></script>
<script>
$(document).ready(function() {
    // init ScrollMagic Controller
    controller = new ScrollMagic();
});
</script>
</body>
</html>
```

### Defining Scenes

Scenes are created by using the [``ScrollScene()``](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) class. A ``ScrollScene`` defines where the controller should react and how. To create a scene we must first create a variable:

```javascript
var scene;
```

In this case we've defined a variable called “scene” and now we'll give it a value which is init a new ScrollScene class.

```javascript
var scene = new ScrollScene();
```

Inside ``ScrollScene`` we can place an [object](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) of associated properties and values available to us…

```javascript
var scene = new ScrollScene({
  triggerElement: "#pinned-trigger2", // point of execution
  duration: 400 // pin the element for a total of 400px
})
```

### Scene Control Methods
Setting up the scene is great and all, but now we need to get down to business and control it. This is where ScrollMagic's [Scene Control Methods](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#toc3) come into play. We can add these control methods to our scene's individually like so…

```javascript
var scene = new ScrollScene({
  triggerElement: "#pinned-trigger2", // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin("#pinned-element1"); // the element we want to pin
```

In the example above we're using a technique called ”chaining” with the [``setPin()``](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#setPin) method in order to add it to our ``ScrollScene()`` class.

### Adding Scenes to Controller

In order to tell ScrollMagic what we want to do we have to add our scene and it's logic to the controller we defined at the very beginning…

```javascript
var scene = new ScrollScene({
  triggerElement: "#pinned-trigger2", // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin("#pinned-element1"); // the element we want to pin

// Add Scene to ScrollMagic Controller
controller.addScene([
  scene
]);
```

In the example above we're using the var we defined for the ScrollMagic class called “``controller``” and using ``addScene([])`` to helps us insert our required scenes. You could also chain this using the ``addTo()`` method like so…

```javascript
var scene = new ScrollScene({
  triggerElement: "#pinned-trigger2", // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin("#pinned-element1") // the element we want to pin
.addTo(scene); // Add Scene to ScrollMagic Controller
```