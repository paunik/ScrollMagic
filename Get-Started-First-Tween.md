Okay, it's time to do some real coding now... Well almost, we just need to do a very few things before we can do our first Tween.

# But what's a Tween

In Animation *jargon* a Tween is a transition. It's going from one state to another. In our example, we'll build a simple Tween that will make an element go from no background color to a red background color.

# Minimum CSS

Now that this is clarified, let's prepare the page we created in our first step, here's what our code looks like so far :

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="utf-8">
        <title>ScrollMagic #1 Setup</title>

        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
        <script src="http://cdnjs.cloudflare.com/ajax/libs/gsap/1.14.2/TweenMax.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.3/ScrollMagic.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.3/plugins/animation.gsap.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.3/plugins/debug.addIndicators.js"></script>
    </head>
    
    <body>
        This is my page
    </body>
    </html>

In order to work properly and give beautiful results, ScrollMagic requires some CSS to perform well. For the sake of simplicity, we'll simply create a `<style>` element in our `<head>` with the minimum code :

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="utf-8">
        <title>ScrollMagic #1 Setup</title>

        <style>
        html, body {
            height: 100%;
            margin: 0;
            padding: 0;
        }
        </style>

        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
        <script src="http://cdnjs.cloudflare.com/ajax/libs/gsap/1.14.2/TweenMax.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.3/ScrollMagic.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.3/plugins/animation.gsap.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/ScrollMagic/2.0.3/plugins/debug.addIndicators.js"></script>
    </head>
    
    <body>
        This is my page
    </body>
    </html>

This ensures our pages is the minimum height so the debug indicators ScrollMagic provides us with are placed properly and that our animation calculations are on the whole page, not just the used space.

Okay cool, let's add some content in our page now, along with very minimal styling too :

    <div id="container">
        <div id="block">
            Hi there !
        </div>
    </div>

And let's style that too, here's the CSS I add :

    #container {
        margin: 55vh 0;
        padding: 50px;
        outline: 1px dashed orange;
    }
    
    #block {
        padding: 10px;
        border: 1px solid black;
        font-family: Helvetica;
    }

This is all very basic. You might not know the vh unit, it stands for Viewport Height and is quite useful if you want to make your elements's sizes relative to the whole page. But anyway, not the subject of this lesson, let's get back to the real coding, we're about to write our first lines of JavaScript !

# The JavaScript

There we are, finally !

First, we need to add a `<script>` tag at the bottom of our `<body>` to hold our JS code.

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="utf-8">
        <title>ScrollMagic #1 Setup</title>

        <style>
        ...
        </style>

        ...
    </head>
    
    <body>
        <div id="container">
            <div id="block">
                Hi there !
            </div>
        </div>
    
        <script>
        // Our code goes here
        </script>
    </body>
    </html>

Now let's get to the good stuff.

### The Controller

Like I said in the first step, ScrollMagic is responsible for triggering our animations at the right time, based on the scroll position. It acts like some kind of glue. What holds the animations and the scroll positions together is called the **Controller** so let's start by creating one :

    $(function() {
        var controller = new ScrollMagic.Controller();
    });

We wrap it inside a jQuery `onReady` so it doesn't play too soon and we're good to go.

You don't need to understand what the Controller does, all you need to know is that what's attached to the controller gets played, the rest is ignored, so it's important even though all we'll do is create it and, in a few seconds, attach an animation to it.

### The Tween

We said we'd create our first Tween, so let's do it ! Right after we instanciate our Controller, let's create a GSAP Tween :

    var blockTween = new TweenMax.to('#block', 1.5, {
        backgroundColor: 'red'
    });

Okay let's take a closer look there.

1. First we create a variable called `blockTween`, in which we store our Tween so we can reference it later
1. We Create a new `TweenMax.to` object. That's how we define our Tween, our transition if you prefer
1. `'#block'` is the selector that matches the element we want to set a Tween on. It's the "Hi there !" with the black border onr our example page
1. Then comes `1.5` that's the duration of our animation, in seconds, so here's it'll play for a second and a half
1. Then we define the new styles we want our element to have when the transition ends, here we want the background-color to become red

We'll see other ways to define our Tweens later on, like I said, GSAP is quite a powerful tools and provides us with many different solutions to create more complex animations but it's our first one, let's keep it simple so we understand what's going on.

### The Scene

We have our Controller, we now have our Tween, but like I said, we need another thing : a way to bind the Tween and some scroll position in some way. That's where Scenes come in.

A Scene basically defines when (or more precisely where in term of scroll position) a Tween must be played, along with various nice options (again, more on that later, simplicity for now).

Let's take a look :

    var containerScene = new ScrollMagic.Scene({
        triggerElement: '#container'
    })
    .setTween(blockTween)
    .addIndicators()
    .addTo(controller);

That seems like a lot but it's not that diffcult, let's dive it.

1. First we create a variable called `containerScene` to hold our Scene
1. There we create a `ScrollMagic.Scene` object
1. `triggerElement` is the selector that matches a DOM element, here our container with orange borders dashed.
1. We use `setTween` to bind the Tween we created earlier, using the variable we'd created to bind Tween and Scene together
1. We `addIndicators()` for some debug visual help
1. We `addTo` the Controller using the `controller`variable we created earlier

Now, if you refresh your page, you should see something like this : 

<iframe height='268' scrolling='no' src='//codepen.io/justinmarsan/embed/XbWNmm/?height=268&theme-id=0' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/justinmarsan/pen/XbWNmm/'>XbWNmm</a> by Justin Marsan (<a href='http://codepen.io/justinmarsan'>@justinmarsan</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

### The Thicks

You'll notice (if everything worked properly) the "start 1" and "trigger 1" thicks on the right side of the page. Those come from the addIndicators.js file we've included and the `.addIndicators()` call we made on our Scene. They provide visual cues to understand what's going on, really useful to fine tune or debug our animations.

# The result

Now, if you scroll, you'll notice that once the "trigger" thick reaches the "start" one, our block becomes red. Tada !

In other words, when the middle of our pages (shown as the "trigger") reaches the top of the `triggerElement` of our Scene, it plays the `blockTween` associated to it.

Neat right ? Cool, in the next chapter we'll take a look at Pins, it'll be great too, you'll see.