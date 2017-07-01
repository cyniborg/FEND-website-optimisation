# FEND-website-optimisation
Optimize a provided website with a number of optimization- and performance-related issues so that it achieves a target PageSpeed score and runs at 60 frames per second.

## How to use the files on your computer?

1. Clone this repository on your computer by clicking the clone repository button.
1. The *Development* folder contains all the source files, the *Submission Folder* contains all the minified distribution files and the *Original files* folder contains the unmodified files as received for this project.
1. If you wish to edit this project after the changes that I have done, open the *Development folder* and start using the html files that have the *-dev* suffix in its name in a text editor of your choice. For eg. **index-dev.html**. You may open it with any browser you like and use it further as you would use any other website. **_Please note that the process is currently not automated and you will have to make changes to the files manually that do not have the -dev suffix_**
  1. If you are willing to share any changes that you have made to this file. Please fork the repository and share the changes.
1. If you want to tackle the objectives by yourself then access the *Original files* folder. You will have to do all the optimisations from scratch by yourself.
1. If you you just wish to browse the optimised content on your web browser, I recommend you to use the *Submission files* folder for the purpose.
1. **To edit** to edit the files. I recommend the following procedure:
  1. In *Development* folder the root contains the HTML files in which the CSS is inlined. Only the CSS styles for print are stored in the /css folder. Although in the *Original files* folder the CSS files are stored seperately in the /css folder.
  1. To edit the pizzeria page. Navigate to /views in either folder. Here you will find the pizza.html (*pizza-dev.html* in the *Development* folder for the unminified version) which contains the HTML code for the page. Again in the *Development* folder the css is optimised and inlined in the HTML file while in the *Original files* there are used css files in the /views/css folder. Please note that in the *Submission files* folder the /views/css folder doesn't exist. Here the CSS has been optimised and inlined.
  1. To edit the JS in for the pizzeria page navigate to /views/js and open the main.js. Here you will find the js with comments to edit it as per your wish.

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
1. Updated the size of the image as per the original content.

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
1. Updated `document.querySelectorAll` to `document.getElementsByClassName` for faster performance.
1. Corrected the sizing issues which came by due to scaling only the image. Corrected it by changing the width of the container.
