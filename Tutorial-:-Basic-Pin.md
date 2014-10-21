**Live Examples**
- [Basic Pin Demo](http://codepen.io/grayghostvisuals/pen/f1d7268c88fd6011ba113ae93adf45f7): Using multiple scenes and full viewport height for each section. This is the demo referenced for the explanation below.
- [Official ScrollMagic Basic Pin Example](http://janpaepke.github.io/ScrollMagic/examples/basic/simple_pinning.html)

**Exaplanation**

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
      <h1>Basic pinning.</h1>
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

One your script is referenced you can begin to structure your project and set the trigger points. In this example below  we initiate the controller and then set property values for each scene defined.
```javascript
// init controller
controller = new ScrollMagic();

// Assign handler1 and add it to the Controller
var scene = new ScrollScene({
  triggerElement: "#pinned-trigger1", // point of execution
  duration: $(window).height()/2
})
.setPin("#pinned-element1") // the element we want to pin
.addTo(controller);

// Assign handler2 and add it to the Controller
var scene2 = new ScrollScene({
  triggerElement: "#pinned-trigger2", // point of execution
  duration: 400
})
.setPin("#pinned-element2") // the element we want to pin
.addTo(controller);

controller.addScene([
  scene,
  scene2
]);
```

If you notice I used ``$(window).height/2`` as a duration value. This means once we reach our trigger point keep the element fixed for 1/2 the window height. You could even use the offset values of elements as your points of execution. Be creative!