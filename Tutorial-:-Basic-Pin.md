**Live Example**

- [Basic Pin Demo](http://codepen.io/grayghostvisuals/pen/f1d7268c88fd6011ba113ae93adf45f7): Using multiple scenes and full viewport height for each section. This will be the demo referenced for the explanation below. Please make sure you have read and/or understand the basics of ScrollMagic in our [Basics](https://github.com/janpaepke/ScrollMagic/wiki/Understanding-:-Basics) section of this WIKI before going any further.

**Documentation**

- [ScrollMagic.Scene Class](http://janpaepke.github.io/ScrollMagic/docs/ScrollMagic.Scene.html#constructor)
- [setPin Control Method](http://janpaepke.github.io/ScrollMagic/docs/ScrollMagic.Scene.html#setPin)

**Tutorial**

To start our example we're going to create the markup. Take note of the id values used as these will correlate to our points of execution and the elements we desire to pin.

```html
<main role="main">
  <section>
    <div>
      <h1>Basic Pin</h1>
    </div>
  </section>

  <section id="pinned-trigger1">
    <div id="pinned-element1">
      <p>This element will be pinned for the half the window height</p>
    </div> 
  </section>

  <section id="pinned-trigger2">
    <div id="pinned-element2">
      <p>This element will be pinned for a duration of 400px</p>
    </div>
  </section>
  
  <section>
    <div>
      <p>Section Four!</p>
    </div>
  </section>
</main>
```

Now that we have our markup in place we can begin to structure the project and set our trigger points. In the example below we initiate the ScrollMagic controller with a variable called “controller”, set property values for each scene and finally add them to the ``ScrollMagic()`` class controller.
```javascript
// init ScrollMagic Controller
var controller = new ScrollMagic.Controller();

// Scene Handler
var scene = new ScrollMagic.Scene({
  triggerElement: "#pinned-trigger1", // point of execution
  duration: $(window).height() - 100, // pin element for the window height - 1
  triggerHook: 0, // don't trigger until #pinned-trigger1 hits the top of the viewport
  reverse: true // allows the effect to trigger when scrolled in the reverse direction
})
.setPin("#pinned-element1"); // the element we want to pin

// Scene2 Handler
var scene2 = new ScrollMagic.Scene({
  triggerElement: "#pinned-trigger2", // point of execution
  duration: 400 // pin the element for a total of 400px
})
.setPin("#pinned-element2"); // the element we want to pin

// Add Scenes to ScrollMagic Controller
controller.addScene([
  scene,
  scene2
]);
```

If you notice I used ``$(window).height - 100`` as a duration value. This means once the trigger is reached we keep the element fixed for whatever the ``window height - 100`` result is. You could even use the offset value of other elements as your points of execution. Be creative! Refer to the documentation above to fine tune your controlling of the pinned element and scene.