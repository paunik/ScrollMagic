Hi there, and welcome to the Scrollmagic **Get Started** guide where you'll learn the basics of working with ScrollMagic to create scroll-based animated websites.

In this first section we're going to cover the setup of our page. To create our animations, we are going to rely on two things : building the animations to play and defining when to play them. There are several different options when deciding the tool to use for the first, ScrollMagic on the other hand is responsible for the second one. I hope that makes sense.

Through out this guide I'll focus on working with GSAP, as I believe it to be the most flexible solution (more on that later), however please note that ScrollMagic can also work with other animation libraries, including the well-known, fast Velocity.js library.

Okay, now that we're all clear let's see what we need to get started.

# Basic HTML Page

Because we're building web pages, we'll have to start with an HTML page.

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="utf-8">
        <title>ScrollMagic #1 Setup</title>
    </head>
    
    <body>
        This is my page
    </body>
    </html>

Hopefully this all makes sense to you. Let's move forward and load ScrollMagic and its dependencies now.

# ScrollMagic and dependencies

We'll start with jQuery. While it's not required since the launch of the v2, jQuery is still tremendously helpful and will help when dealing with our DOM, so let's start with that, we'll place it (along with the other scripts we'll load) in the `<head>` of our page :

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="utf-8">
        <title>ScrollMagic #1 Setup</title>

        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
    </head>
    
    <body>
        This is my page
    </body>
    </html>

Okay, cool, now let's load GSAP. If you've never heard of it before, GSAP is one of the JavaScript Animation libraries that work well with ScrollMagic. Most of its functionnalities are contained in a single script, we have to load it to and it will enable us to have a lot of control over the animations we'll play later. Let's go!

    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="utf-8">
        <title>ScrollMagic #1 Setup</title>

        <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
        <script src="http://cdnjs.cloudflare.com/ajax/libs/gsap/1.14.2/TweenMax.min.js"></script>
    </head>
    
    <body>
        This is my page
    </body>
    </html>

Now that we have those two, we can pull ScrollMagic in and let the fun begin, we'll need 3 files :

* `ScrollMagic.js` for all the logic and functionnalities
* `/plugins/animation.gsap.js` that will act as a bridge between SM and GSAP
* `/plugins/debug.addIndicators.js` which is a debug tool we'll look into really soon !

Let's load all these files from a CDN :

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

And that would be it !

Let's do a quick recap to make sure you can do it from memory, it's not so much really, here's what we've done :

1. Create a basic HTML page
1. Load jQuery, that's optional but quite handy in my opinion
1. Load GreenSock Animation Platform (or GSAP) which we'll use to create our animations
1. Load ScrollMagic to get the SM functionnalities
1. Load the bridge between ScrollMagic and GSAP
1. Load the debug file to get some visual cues when creating our animations

All good ? Great, then we'll be able to go to our next step soon, creating a **Tween** ! It's okay if you have no idea what that is, don't worry.