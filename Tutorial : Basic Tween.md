**Live Example**

- [Basic Tween w/Multiple Scenes](http://codepen.io/grayghostvisuals/pen/wzFnb/)

**Documentation**
- [TweenMax.to Method](https://greensock.com/asdocs/com/greensock/TweenMax.html#to())
- [ScrollScene Class](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene)
- [setTween Control Method](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#setTween)

**Tutorial**

In order for you to Tween, ScrollMagic requires the use of [GreenSock's Animation Platform (GSP)](https://greensock.com/get-started-js) along with ScrollMagic and jQuery of course. For this tutorial we're specifically using [TweenMax](https://greensock.com/get-started-js).

```markup
<script src="path/to/js/jquery.min.js"></script>
<script src="path/to/js/TweenMax.min.js"></script>
<script src="path/to/js/jquery.scrollmagic.min.js"></script>
</body>
</html>
```

Now that our scripts are referenced we can begin to structure our markup by adding our “hooks” to trigger the animation along with animating the target(s) we desire.

```markup
<main role="main">
  <section>
    <div>
      <h1>Basic Tweening</h1>
    </div>
  </section>

  <section id="scale-trigger">
    <div id="scale">
      <p>This element will scale down using the scale value of the CSS transform property.</p>
    </div>
  </section>

  <section id="bg-trigger">
    <div id="background">
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