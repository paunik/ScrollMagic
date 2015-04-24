Now that's we're all set and have discovered how ScrollMagic and GSAP can interact to create Tweens, it's time to dig into **Pins**.

If you know the `position: fixed` attribute, it's should make sense as it looks kind of the same way, we're pinning an element to its place so the scroll of the page continues, but the element remains at the same place.

Alright, let's get to it

# The Markup

To code our first Pin we'll just reuse the markup from our previous example, removing the JS code that took care of the Tween. HTML and CSS stay the same and this is what our script tag contains :

    $(function() {
        var controller = new ScrollMagic.Controller();
        
    });

Okay so, unlike Tweens, Pins don't need GSAP or any kind of object to work, we just create a Scene, set the element to pin and that's it. Well almost :

    $(function() {
        var controller = new ScrollMagic.Controller();
        var containerScene = new ScrollMagic.Scene({
            triggerElement: '#container',
            duration: 500
        })
        .setPin('#block')
        .addIndicators()
        .addTo(controller);
    });

So let's see what we added there.

The `containerScene` is a Scene just like the one we did in the previous lesson, and the `triggerElement` is on the `#container` element, just like before.

The first thing that is new is the `duration` option, which is set to 500. It means that our Scene now lasts for 500 pixels of scroll. It's going to enable us to have our Pin stop at some point, or it'd just stay fixed forever...

Then, unlike earlier, we don't use the `setTween` method (because we don't want any Tween there)  but the `setPin` method, which takes a selector as an element : the selector of the block we want to have fixed.

We add the indicators for clarity, we of course add the Scene to the Controller or nothing would happen. Now we refresh : [Here's the result](http://codepen.io/justinmarsan/pen/vOYPaq).

# Important things to note

There are a few things that need to be understood to work with Pins and Scenes in general that we can clearly see here.

The first one is the "end" thick that's new, it's placed exactly 500 pixels below the "start" thick, that's the duration we've set. While not required, the duration is useful in most cases, especially with Pins but even with Tweens.

The second thing to note is that our orange bordered container has been resized so the padding are correct at the top and the bottom. There are a options to disable that but most of the time it's actually what we want and a really useful functionnality. This also means that everything below our Pin would have gotten pushed as needed so the Pin can happen without overlapping with the content beneath. Quite neat if you ask me.

The last thing : if you remove the duration option, its default value is 0, which both means forever in terms of Pin. I encourage it to try and removing it, youy'll see that the Pin stays fixed until the bottom of the page is reached, but you'll also see that the container isn't extended anymore.

The duration parameter has some effects on Tweens as well, we'll discover them in later lessons, for now let's celebrate our first Pin. Congratulations, you know the main parts of ScrollMagic already. In the next lessons we'll discover more about specific options and what they do, and see some GSAP functions that are quite handy.