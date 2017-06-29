# FEND-website-optimisation
optimize a provided website with a number of optimization- and performance-related issues so that it achieves a target PageSpeed score and runs at 60 frames per second.

## The index.html page changes:
1. Compressed the images
1. The css was small so inlined it for reducing the render path.
1. Utitlised the [Optimised CSS delivery](https://developers.google.com/speed/docs/insights/OptimizeCSSDelivery) as explained in the Google developer notes to defer the loading of google fonts.
1. Added alt tags to the img attributes to make it more user friendly.
1. Moved the script tags to the end of the page and added async to load the file asynchronously.
1. Edited and compressed the thumbnail image for Cam's pizzeria link.
1. Added `media = "print"` to the print.css file to avoid any blocking while loading the page.
1. Also researched and added a .htaceess file but could not see any caching happening.
1. Minified the HTML

*Mobile psi = 94/100*
*Desktop psi = 96/100*

## pizza.html page changes:
1. Used unCSS to scan through and remove unused css classes and ids from bootstrap-grid.css
1. Inlined all the css due to small size achieved after the said process.
1. Edited and compressed and the pizza-img.png to optimise the images.
1. Changed the pizzeria.jpg and inlined it with the HTML to avoid extra network roundtrips.
1. Added an extra class pizza-img to facilitate the change of pizza image when choosing the pizza size via transform to avoid repainting.
1. Minified the HTML
1. Deferred the JS and moved the script tag to the end of the body.

*Mobile psi = 73/100*
*Desktop psi = 85/100*

## main.js changes for smooth 60fps animations

1. Removed all the animations happening via width changes and made it happen through transform.
1. Cached the results of `document.querySelectorAll("class")` into a variable to access them in a loop.
1. Cached the length of the same in a variable to be accessed in for loops.
1. The function `updatePositions()` now uses `translate` to make the background animate avoiding time costly repaint.
1. The function `changePizzaSizes(size)` now uses `transform: scale(value);` to change the pizza sizes according to choice
1. Used the code by [KIM S. TEEPLE](http://www.developerdrive.com/2012/03/coding-vendor-prefixes-with-javascript/) to ensure that the transform property has the correct vendor prefix when used.
1. Removed the determineDX function and added the size calculation inside the `changePizzaSizes(size)` function to avoid uneccesary calls to external function.
1. Minified main.js
