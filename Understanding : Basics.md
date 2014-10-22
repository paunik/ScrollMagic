To get started you'll need to reference jQuery and the ScrollMagic library from your HTML doc just before the closing ``<body>`` tag. Each project will have at least one call to the ``ScrollMagic()`` class which is the main class needed once per scroll container. Refer to the code block below for an example of the said setup.

### Initial Setup
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

In this case we've defined a var called “scene” and now we will give it a value which is init a new ScrollScene class.

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
