If you're wondering how to set a scene's trigger position or in other words, the point of execution, then you're in the right place.
The trigger position is basically the specific scroll offset where the respective scene takes effect.

There are three parameters that in combination make up this "starting position": `offset`, `triggerElement` and `triggerHook`.

Let's go through them one by one.

To begin we create a variable called “scene” and initiate a new ``ScrollMagic.Scene()`` class.

```javascript
var scene = new ScrollMagic.Scene();
```

Inside this ScrollScene class we can pass an object of key/value pairs that are provided to us per the [docs](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene).

```javascript
var scene = new ScrollMagic.Scene({
  triggerElement: '#scroll-trigger' // point of execution
});
```

As you can see in the example above we've used the ``triggerElement`` property option provided by ScrollMagic. The value for ``triggerElement`` will be a selector, DOM object or jQuery Object that defines the start of the scene. If undefined the scene will start right at the start of the page (unless an offset is set). In our case we use the id value of a DOM node.

[NOTE: incomplete article]

To learn more about this subject have a look at this great article:
https://ihatetomatoes.net/svg-scrolling-animation-triggered-scrollmagic/