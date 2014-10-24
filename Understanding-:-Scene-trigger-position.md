If you're wondering how to set a scene's trigger position or in other words, the point of execution, then you're in the right place.

A scene's trigger position is controlled via the [ScrollScene](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) Class. A ScrollScene defines where the controller should react and how.

To begin we create a variable called “scene” and initiate a new ``ScrollScene()`` class.

```javascript
var scene = new ScrollScene();
```

Inside this ScrollScene class we can pass an object of key/value pairs that are provided to us per the [docs](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene).

```javascript
var scene = new ScrollScene({
  triggerElement: '#scroll-trigger' // point of execution
});
```

As you can see in the example above we've used the ``triggerElement`` property option provided by ScrollMagic. The value for ``triggerElement`` will be a selector, DOM object or jQuery Object that defines the start of the scene. If undefined the scene will start right at the start of the page (unless an offset is set). In our case we use the id value of a DOM node.

We can also do more with our trigger like controlling duration, offset, triggers for scroll direction and much more. Refer to the [docs](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) for further investigation.