is project showcases my work optimizing a web site for speed and responsiveness.
# What i learnt from working on this project:
**Using Google Page Speed Insights**

**How to avoid Forced Synchronous Layouts**

# My development environment: LAMP


#### Where to start: 
Load the index.html file in the src and dist folders. The index.html files have links to the other pages.
pizza.html which demonstrates the 60fps scroll and pizza size resizing is the last link.


#### Minifying images

**imageMagick**: I used ImageMagick to compress image files.

**yui-compressor and uglifyjs**: I used yui-compressor and ugilfyjs to minify my Javascript files.

# Changes made to index.html and pizza.html

Added media=print tag for print.css so print.css would not be downloaded when there was no printer connected.

I linked to compressed versions of images.

I used code (linked from page speed insights results) to load the javascript files at he end of the html page to increase page speed score.

# Changes made to main.js

**Changes made on Feb 14, 2016 - These are the most recent changes**

**1.** Removed the use of the calculatePhase function in calculating the movement of the pizza images on scroll. Instead in the DOMContentLoaded listener, the 'left' style property is set using a much simplified function. The transform style property of the moving pizza element is set to translateY(30px).

**2.** Replaced 'querySelector...' calls with getElementById or getElementsByClassName

**3.** Reduced number of moving pizzas to 24.

**4.** Removed call to updatePositions in the DOMContentLoaded listener; instead updatePositions handles the scroll event.

**5.** Modification to updatePositions: set the 'transform' style property for the moving pizza element. When the page is scrolled, the pizza image is moved along the y axis by a hardcoded number of pixels.

**End of changes made on Feb 14, 2016 - What follows below are changes that were present at the time of my first submission.**

**makeRandomPizza** -  remove calls to makeRandom... functions except for selectRandomSauce() and selectRandomCrust() and used ingredientItemizer function.

I directly used indices to access the pizza ingredients array inside makeRandomPizza

**sizeSwitcher** - Modified to return percentage values directly.

**changePizzaSizes** - Modified to call sizeSwitcher outside the pizzaContainers loop.

**calculatePhase** Since there were onyl ten unique phase values needed, i modified
calculatePhase to calculate the phase value like this - phase[i] =  (100 * tempPhaseValue);

**updatePizzaPositions** I removed all calls inside the loop to access style properties and simplified the style value calculations like this -
items[i].style.left = ((i % 8) * 256) + phase[i%10] + 'px';
