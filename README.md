# Udacity ND001 Front-end web development
## P4: Website performance optimization portfolio project

### Running instructions

The final and optimized code is stored in the folder **production code/**.
Some useful tips to help run the websites:

#### Desktop

Open index.html to get access to the portfolio. From there, links are provided to all the other parts and sections of the project. Simply navigate from here or open a respective part of the website directly from the html file. The files for the pizza project are stored in the folder **views/**.

#### Mobile

1. To inspect the site on a phone, download the repository and run a local server

  ```bash
  $> cd /path/to/project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080

### Part 1: Optimization steps for index.html (PageSpeed >90)

* Download thumbnail images for index.html and reduce file size
* Compress img file size for all integrated images (using Photoshop and PageSpeed Insights)
* Minify HTML, CSS and JS files (using SublimeText Plugin Minify)
* Add media queries to CSS integration in index.html
* Inline minified CSS for screen display
* Excluded web font
* Added asynchronous loading of Google Analytics JS

### Part 2: Optimization steps for pizza.html (FPS 60)

#### Improve FPS
* Moved the layout read (document.body.scrollTop) out of the loop for the style changes to remove forced synchronous layout (FSL) problem.
* Inside of updatePositions() instead of selecting all the DOM elements every time the page is updated, the global pizzaArray variable is accessed to improve scripting speed.
* Inside of updatePositions() transform: translateX() is implemented instead of left() to reduce layout time.
* Added will-change: transform property to moving pizza objects to reduce paint time by moving the objects to their own composite layer.
* The number of pizzas needed to fill the screen is now dynamically computed, by checking the window size, computing the number of rows and then multiplying this number with the number of columns.

#### Improve Pizza resizing
* determineDx() was removed due to inefficiency
* Instead of calculating new widths in pixels, a percentage based approach is performed directly in changePizzaSizes().
* The collection of nodes is stored in pizzaNodes to eliminate repetition.
* To collect all the elements for pizzaNode, the document.getElementsByClassName() Web API call was implemented because it is faster than document.querySelectorAll().
* Finally, only the style change is kept in the loop to eliminate FSL effects.
