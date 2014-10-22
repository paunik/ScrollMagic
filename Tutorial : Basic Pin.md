**Live Examples**
- [Basic Pin Demo](http://codepen.io/grayghostvisuals/pen/f1d7268c88fd6011ba113ae93adf45f7): Using multiple scenes and full viewport height for each section. This is the demo referenced for the explanation below.
- [Official ScrollMagic Basic Pin Example](http://janpaepke.github.io/ScrollMagic/examples/basic/simple_pinning.html)

**Documentation**
- [ScrollScene Class](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene)
- [setPin Control Method](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#setPin)

**Tutorial**

To get started you'll need to reference jQuery and the ScrollMagic library from your HTML doc just before the closing body tag like so…

```markup
<script src="path/to/jsfolder/jquery.min.js"></script>
<script src="path/to/jsfolder/jquery.scrollmagic.min.js"></script>
</body>
</html>
```

Now we can create our markup. Take note of the id values used as these will correlate to our points of execution and the elements we desire to pin.

```markup
<main role="main">
  <section>
    <div>
      <h1>Basic Pinning.</h1>
      <p>Durations are pinned for their respective pixels set as the duration value and released again.</p>
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

One your scripts are referenced and markup is in place you can begin to structure your project and set the trigger points. In this example below  we initiate the ScrollMagic controller, set property values for each scene and finally add them to the ScrollMagic controller.
```javascript
// init ScrollMagic Controller
controller = new ScrollMagic();

// Scene Handler
var scene = new ScrollScene({
  triggerElement: "#pinned-trigger1", // point of execution
  duration: $(window).height() - 100, // pin element for the window height - 100
  triggerHook: 0, // don't trigger until #pinned-trigger1 hits the top of the viewport
  reverse: true // allows the effect to trigger when scrolled in the reverse direction
})
.setPin("#pinned-element1"); // the element we want to pin

// Scene2 Handler
var scene2 = new ScrollScene({
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