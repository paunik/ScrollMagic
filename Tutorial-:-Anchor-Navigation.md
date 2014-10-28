**Live Example**

- [Anchor Navigation](http://codepen.io/grayghostvisuals/pen/EtdwL)

**Documentation**

- [ScrollScene](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene)
- [GreenSock ScrollToPlugin](https://greensock.com/docs/#/HTML5/GSAP/Plugins/ScrollToPlugin)

**Tutorial**	
As we learned in [Getting Started](https://github.com/janpaepke/ScrollMagic/wiki/Getting-Started-:-First-Steps) about including the TweenMax library we also need to include GreenSock's **ScrollToPlugin**.

```html
<script src="TweenMax.js"></script>
<script src="ScrollToPlugin.js"></script>
<script src="ScrollMagic.js"></script>
</body>
</html>
```

Our anchor tag's ``href`` attributes for the navigation will contain the hash or in other words, the id of the sections our anchors will correlate to.

```html
<header role="banner">
  <nav role='navigation'>
    <a href="#section-1">Section 1</a>
    <a href="#section-2">Section 2</a>
    <a href="#section-3">Section 3</a>
  </nav>
</header>
<section id="section-1"></section>
<section id="section-2"></section>
<section id="section-3"></section>
```

Now that our anchors match to the id of our sections we can begin setting up the JavaScript for the action itself. First we'll initialize the ScrollMagic class along with chaining our controller with the [scrollTo](http://janpaepke.github.io/ScrollMagic/docs/ScrollMagic.html#scrollTo) control method.

```javascript
var controller = new ScrollMagic();
controller.scrollTo(function(target) {});
```

The scrollTo control method allows a function to be passed as an argument. This function will be used as a callback for future scroll position modifications providing a way for you to change the behavior of scrolling and adding new behavior like animation. The callback receives the new scroll position as a parameter and a reference to the container element using ``this``.

Inside the scrollTo control method we'll add ``TweenMax`` to the function body. Using ``TweenMax.to()`` we pass the GSAP ScrollToPlugin and it's custom options.

```javascript
// Init controller
var controller = new ScrollMagic();

// Change behavior of controller
// to animate scroll instead of jump
controller.scrollTo(function(target) {

  TweenMax.to(window, 0.5, {
    scrollTo : {
      y : target, // scroll position of the target along y axis
      autoKill : true // allows user to kill scroll action smoothly
    },
    ease : Cubic.easeInOut
  });

});
```

The GSAP ScrollToPlugin allows ``TweenLite`` and ``TweenMax`` to animate the scroll position of either the window (like doing ``window.scrollTo(x, y)``) or a DOM element's content (like doing ``myDiv.scrollTop = y; myDiv.scrollLeft = x;``). The value reflected as ``0.5`` relates to the scroll speed. We suggest you adjust to fit your needs and taste along with the easing option chosen as these properties can impact the end result.

The final piece we need to setup is the actual event (i.e. the anchor click event) so that we can tell ScrollMagic which elements we would like to serve as our triggers. Using jQuery we bind the click event to any anchor tag with an ``href`` attribute beginning with a ``#`` sign.

```javascript
//  Bind scroll to anchor links
$(document).on("click", "a[href^=#]", function(e) {});
```
At this stage we can add logic to the function body so that the event actually does something. First we create a variable that will contain the ``href`` attribute value when an anchor is clicked.

```javascript
//  Bind scroll to anchor links
$(document).on("click", "a[href^=#]", function(e) {
  var id = $(this).attr("href"); // grab the href attribute value
});
```

To ensure we don't click on empty ``href`` attributes we make sure the length is greater than 0. We'll also prevent the default behavior of links for our anchor nav items.

```javascript
//  Bind scroll to anchor links
$(document).on("click", "a[href^=#]", function(e) {
  var id = $(this).attr("href"); // grab the href attribute value

  if($(id).length > 0) {
    e.preventDefault(); // prevents default behavior of links.
  }
});
```

Within the ``if`` conditional block we just created we'll trigger the controller's ``scrollTo()`` method and pass the id or the ``href`` attribute of the link as an argument.

```javascript
//  Bind scroll to anchor links
$(document).on("click", "a[href^=#]", function(e) {
  var id = $(this).attr("href"); // grab the href attribute value

  if($(id).length > 0) {
    // prevents default behavior of links.
    e.preventDefault();
    
    // trigger scroll
    controller.scrollTo(id);
  }
});
```

For the final touches we can use [``window.history``](https://developer.mozilla.org/en-US/docs/Web/API/Window.history) to update the url when the anchors are clicked. This means our URL will append the hash value to the end of the URL like this… ``theurl.com?#section-1``. ``window.history.pushState`` pushes the given data onto the session history stack with the specified title and, if provided, URL.


```javascript
//  Bind scroll to anchor links
$(document).on("click", "a[href^=#]", function(e) {
  var id = $(this).attr("href");

  if($(id).length > 0) {
    e.preventDefault();

    // trigger scroll
    controller.scrollTo(id);

    // If supported by the browser we can also update the URL
    if (window.history && window.history.pushState) {
      history.pushState("", document.title, id);
    }
  }

});
```