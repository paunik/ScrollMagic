**Live Example**

- [Basic Tween w/Multiple Scenes](http://codepen.io/grayghostvisuals/pen/wzFnb/)

**Documentation**
- [TweenMax.to Method](https://greensock.com/asdocs/com/greensock/TweenMax.html#to())
- [ScrollScene Class](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene)
- [setTween Control Method](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#setTween)

**Tutorial**

In order for you to Tween, ScrollMagic requires the use of [GreenSock's Animation Platform (GSP)](https://greensock.com/get-started-js) along with ScrollMagic and jQuery of course. For this tutorial we're specifically using [TweenMax](https://greensock.com/get-started-js).

```html
<script src="path/to/js/jquery.min.js"></script>
<script src="path/to/js/TweenMax.min.js"></script>
<script src="path/to/js/jquery.scrollmagic.min.js"></script>
</body>
</html>
```

Now that our scripts are referenced we can begin to structure our markup by adding our “hooks” to trigger the animation along with animating the target(s) we desire.

```html
<main role="main">
  <section>
    <div>
      <h1>Basic Tweening</h1>
    </div>
  </section>

  <section id="scale-trigger">
    <div id="scale-animation">
      <p>This element will scale down using the scale value of the CSS transform property.</p>
    </div>
  </section>

  <section id="bg-trigger">
    <div id="bg-animation">
      <p>This element will have the background color change</p>
    </div>
  </section>
  
  <section id="yoyo-trigger">
    <div>
      <p id="yoyo-animation">Section Four yoyo Text!</p>
    </div>
  </section>
</main>
```

In the markup above we've included our trigger hooks as the id values and set our items we wish to animate with id hooks as well. When each trigger point is reached in the scroll the associated items will animate or “Tween” as the pros like to say.

The final part of this recipe is setting up the config for the scroll event and animations. To do this we'll create our element's animation using the ``TweenMax.to()`` method, set the scene's triggers and finally add our scenes to the ScrollMagic controller.

```javascript
// Scale Animation Setup
// .to('@target', @length, {@object})
var scale_tween = TweenMax.to('#scale-animation', 1, {
  transform: 'scale(.75)',
  ease: Linear.easeNone
});

// BG Animation Setup
// .to('@target', @length, {@object})
var bg_tween = TweenMax.to('#bg-trigger', 1, {
  backgroundColor: '#FFA500',
  ease: Linear.easeNone
});

// YoYo Animation Setup
// .to(@target, @length, @object)
var yoyo_tween = TweenMax.to('#yoyo-animation', 1, {
  transform: 'scale(2)',
  ease: Cubic.easeOut,
  repeat: -1, // this negative value repeats the animation
  yoyo: true // make it bounce…yo!
});


// init ScrollMagic Controller
controller = new ScrollMagic();


// Scale Scene
var scale_scene = new ScrollScene({
  triggerElement: '#scale-trigger'
})
.setTween(scale_tween);

// Background Scene
var bg_scene = new ScrollScene({
  triggerElement: '#bg-trigger'
})
.setTween(bg_tween);

// YoYo Scene
var yoyo_scene = new ScrollScene({
  triggerElement: '#yoyo-trigger'
})
.setTween(yoyo_tween);

controller.addScene([
  scale_scene,
  bg_scene,
  yoyo_scene
]);
```