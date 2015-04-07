### Getting all the Files
We will need the necessary files for ScrollMagic, GSAP and jQuery.  
If you are using [bower](bower.io) you should know how to download all the necessary files.
Here you can download them manually:  
 - download ScrollMagic [here](https://github.com/janpaepke/ScrollMagic/archive/master.zip)
 - download GSAP [here](http://greensock.com/gsap)
 - download jQuery [here](http://jquery.com/download)

### Preparing the Project

We will assume an `index.html` file in the root folder of our project.  
Create folders for your CSS and Javascript files, like `/js` and `/css`.  
The Download package of ScrollMagic also contains the full documentation and all examples.  
The files that are relevant to us are located inside the `/js` folder. These files are:

 - __jquery.scrollmagic.js__<br>This is the main file for ScrollMagic. It is used during the development phase of your project, so it can give you helpful debugging information.
 - __jquery.scrollmagic.min.js__<br>After we finished the development we can replace the main ScrollMagic file with this minified version. It is lighter and thus loads faster.
 - __jquery.scrollmagic.debug.js__<br>This file is needed to help you visualize where your scenes are triggered. For more information see [Debugging](./Understanding-:-Debugging)

Copy all the above files into the javascript folder of your project. Do the same with the GSAP and jQuery files.

### Initial Setup
To get started you'll need to reference GSAP, jQuery and the ScrollMagic library in your HTML.  
It has been common practice to add JS files just before the closing ``<body>`` tag, so they don't block the loading of the rest of your page. If you prefer to have them in your `<head>` section this would work just as well...
```html
<script src="path/to/js/gsap/TweenMax.min.js"></script>
<script src="path/to/js/jquery.min.js"></script>
<!-- should be replaced with minified version when development is finished -->
<script src="path/to/js/jquery.scrollmagic.js"></script>
<!-- should be removed when development is finished -->
<script src="path/to/js/jquery.scrollmagic.debug.js"></script>
<script>
   // this is where our code will go
</script>
</body>
</html>
```
Now we're ready to start! Continue with the [Basics of ScrollMagic](./Getting-Started-:-How-to-use-ScrollMagic).