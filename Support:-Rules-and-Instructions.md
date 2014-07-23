Got stuck with your ScrollMagic page and don't know what went wrong?  
Don't worry - here's how you get help and solve your issues.

## 1. Make sure your console is clean.
ScrollMagic posts a lot of useful debugging information to the console of your browser.
So make sure to check it first, when looking for the problem.  
In Chrome the console is opened by clicking "View -> Developer -> JavaScript console".

If no errors appear make use of ScrollMagic's debugging capabilities.
Both the [controller class](http://janpaepke.github.io/ScrollMagic/docs/ScrollMagic.html#ScrollMagic) as well as the [scene class](http://janpaepke.github.io/ScrollMagic/docs/ScrollScene.html#ScrollScene) offer the `loglevel` option, which, when set to 3 will output even more useful information.  
Does the controller update, when you scroll?  
Is your scene object behaving correctly?

To get visual help you can also include the ScrollMagic debugging extension.  
Include the file into your html like this:
```html
<script type="text/javascript" src="js/jquery.scrollmagic.debug.js"></script>
```
And then use `scene.addIndicators()` to get visual indicators for where your scene should start and stop.

## 2. Tweens don't work as expected? Make sure it's a ScrollMagic issue!
With most tween-related problems the issue lies with CSS, TweenMax or a misuse thereof.
A best practice is usually to create your tweens but **do not** add them to the ScrollScene object using `setTween`.
Now look at your site and see if the animation plays out the way you wanted to.
If it doesn't the problem is obviously not with ScrollMagic.

Check out the [Greensock Forums](http://forums.greensock.com/forum/11-animation-tweening-js/) to get help using TweenMax.

Only once the animation plays like you want it to add it to the ScrollScene.

_**TIPP:** If your animation is further down in the DOM and you can't reach it before it plays, make use of the `delay` option of TweenMax. Just don't forget to remove it once everything animates like you want it to._


## 3. Isolate the problem
A lot of times problems are caused by other elements or overlapping scenes on the page. Try to make a seperate test-page containing only the respective scene. This will also help you with step 5 (posting the issue).

## 4. Search for similar issues
Chances are someone already ran across something similar to what you are experiencing.
Make sure to use the [GitHub search](https://github.com/janpaepke/ScrollMagic/search) at the top of the page to find out.

## 5. Post your question in the issues section
Once you completed steps 1 to 4. post your question [in the issues section](https://github.com/janpaepke/ScrollMagic/issues) and we'll be happy to help you with your problem.  
But in order for us to be able to do that and also for future users to benefit from the solution we ask you to abide by these rules:
 - **Focus**: Only one issue per post, please.
 - **Caption**: Try to find a title that help other people to see what the post is about and avoid titles like "Problem with Scrolling" that really won't help anyone...
 - **Description**: Try to describe your problem as simple as possible and always keep in mind that the people reading it have no idea of your project and it's parameters. How would you explain it to someone who doesn't even know ScrollMagic?
 - **Format**: Use Paragraphs and structure your text using all the great features of [GitHub markdown](https://help.github.com/articles/github-flavored-markdown). pay special attention to the tripple ticks (```) followed by a language name to ensure syntax highlighting.
 - **Code**: In almost all cases help can only be provided if the question is accompanied by the respective code. The VERY best way to do this is using [jsfiddle](http://jsfiddle.net/), [codepen](http://codepen.io/) or [Plunker](http://plnkr.co/edit). It provides an isolated showcase of the issue (which you already created in Step 3) and gives everyone else the opportunity to play around with the code to find out the problem. If feel you HAVE to post a link to your own environment, please make sure it's a special URL and try to keep it live even after development has finished. This way it will be available for future users with the same problem.

Thank you for helping me maintain this project by abiding by these rules.

**Please avoid**:
- Hitting reply in the GitHub notification email and leaving the original message in. If you love to use the direct email reply feature, please make sure to delete the original.
- Posting links to your website and removing them after the issue is solved. This takes away the possibility to learn for future users.