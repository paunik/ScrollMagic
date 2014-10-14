## Description
This error occurs when two tweens animate the same property of an element and are triggered in short succession.

A common example for this is using one scene to fade an element in and another to fade it out.  
If the user scrolls very fast past them or uses the `home` and `end` keys to jump past them, visual errors occur like the element being stuck at 10% opacity.

The phenomenon was first adequately discussed in [Issue 145](https://github.com/janpaepke/ScrollMagic/issues/145).

## Explanation
In GSAP a tween will overwrite any previously running tween, as soon as it is triggered and has conflicting parameters. This is default behavior due to the setting of [`TweenLite.defaultOverwrite`](http://greensock.com/docs/#/HTML5/GSAP/TweenLite/defaultOverwrite/).  
Since the first tween usually has already entered render state and rendered its first frame, when the second is triggered, this will be the faulty start position for our second tween (and the explanation for the 'stuck at 10% opacity' behavior).

Using `fromTo` does not resolve the problem, because a tween that is overwritten and has no more properties to tween, will be killed.

## Solution
There are three possible approaches to resolve this issue:

### A: Giving the scenes a duration
This issue only occurs if the scenes have no duration and the tweens are just played.  
So the easiest way to resolve it is by giving the scenes a duration and thus binding the animation to the scroll position.  
To see it in action, click here: http://jsfiddle.net/1Lfqqbx0/

This is not always the desired behavior, so you'll have to check out __B__ or __C__.

### B: Disabling overwrite and using `fromTo()`
For this solution the overwrite behavior needs to be disabled so tweens that are overwritten and only have one property aren't completely destroyed.  
This can be done globally using `TweenLite.defaultOverwrite = false;` or individually by supplying the `overwrite` option to the tween (see example).  
It is also important that all but the first tween get the option `immediateRender: false` so it will be the only one that is set to its start position upon init.  
Here's an example:
```js
var scene1 = new ScrollScene({
        offset: 10,
        duration: 30
    })
    .setTween(TweenMax.fromTo($s, 0.2, {opacity: 0}, {opacity: 1}))
    .addTo(ctrl);

var scene2 = new ScrollScene({
        offset: 100,
        duration: 30
    })
    .setTween(TweenMax.fromTo($s, 0.2, {opacity: 1}, {opacity: 0, immediateRender: false}))
    .addTo(ctrl);
```
You can check it out in detail here: http://jsfiddle.net/pv5tnymx/

### C: Using `to()` inside of event listeners based on `scrollDirection`
With this solution we actually take advantage of GSAP's overwrite functionality. Instead of defining a tween and playing it forward or reverse, we just create a new one everytime we hit the trigger position.  
The one that is currently running will be overwritten and stopped.  
Unlike with solution __B__ the animation will always start from the current value.  
Here's an example
```js
$s.css("opacity", 0); // starting value
var scene1 = new ScrollScene({
        offset: 10
    })
    .on("start", function (e) {
        TweenMax.to($s, 0.2, {opacity: e.scrollDirection === "FORWARD" ? 1 : 0});
    })
    .addTo(ctrl);

var scene2 = new ScrollScene({
        offset: 50
    })
    .on("start", function (e) {
        TweenMax.to($s, 0.2, {opacity: e.scrollDirection === "FORWARD" ? 0 : 1});
    })
    .addTo(ctrl);
```
To see it in action, click here: http://jsfiddle.net/L7qm9c8o/

## How to decide
The solution to chose much depends on the visual outcome you are trying to achieve.
- Use __A__ if you don't care if the animation just plays or is bound to scroll position and want the easiest possible fix.
- Use __B__ if you want the animations always to be played from a certain start or end point.
- Use __C__ if you want the animations always to be played from the current start or end point.