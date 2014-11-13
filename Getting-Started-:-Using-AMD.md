### Setting up the Config
When using ScrollMagic make sure the paths to the source files of all dependencies are known.
Usually you may have to define them u sing the requirejs config.
```js
require.config({
    baseUrl: 'js',
    paths: {
        TweenMax: 'lib/greensock/TweenMax',
        TimelineMax: 'lib/greensock/TimelineMax',
        jquery: 'lib/jquery.min',
        ScrollMagic: 'jquery.scrollmagic',
        "ScrollMagic.debug": 'jquery.scrollmagic.debug'
    }
});
```
### Using ScrollMagic with AMD
For AMD __only one object is exported__ containing references to the ScrollMagic controller and the ScrollScene Constructors.
Compared to the browser globals the object looks like this:
```js
{
    Controller: ScrollMagic,
    Scene: ScrollScene
}
```
To use ScrollMagic in your setup you need to use these references as constructors.
Example:
```js
require('ScrollMagic', 'ScrollMagic.debug'], function(ScrollMagic) {
    var controller = new ScrollMagic.Controller({globalSceneOptions: {triggerHook: "onCenter"}});
    var scene = new ScrollMagic.Scene({
            duration: 300,
            offset: 100
        })
        .addTo(controller)
        .addIndicators();
});
```