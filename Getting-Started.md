### Getting All The Files
We will need the necessary files for ScrollMagic, GSAP and jQuery.
If you are using [bower](bower.io) you should be advanced enough to download all the necessary files.
Here we will describe how to download them manually.
 - download ScrollMagic [here](https://github.com/janpaepke/ScrollMagic/archive/master.zip)
 - download GSAP [here](http://greensock.com/forums/files/getdownload/84-html5js-gsap/)
 - download jQuery [here](http://jquery.com/download)

### Preparing Our Project

We will assume an `index.html` file in the root folder of our project.
Create folders for your CSS and Javascript files, like `/js` and `/css`.
The Download package of ScrollMagic also contains the full documentation and all examples.
The files that are relevant to us are located inside the `/js` folder. These files are:
 - jquery.scrollmagic.js<br>
 - jquery.scrollmagic.min.js<br>
 - jquery.scrollmagic.debug.js<br>

Copy all the above files into the javascript folder of your project. Do the same with the GSAP and jQuery files.

### Initial Setup
To get started you'll need to reference GSAP, jQuery and the ScrollMagic library in your HTML. 
It has been common practice to add JS files just before the closing ``<body>`` tag, so they don't block the loading of the rest of your page.
```markup
<script src="path/to/js/jquery.min.js"></script>
<script src="path/to/js/jquery.scrollmagic.min.js"></script>
<script>

</script>
</body>
</html>
```