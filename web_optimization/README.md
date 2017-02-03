## Portfolio Project - Performance Optimization

1. Optimized fonts using ``` @font-face ``` css rule to include the fonts. Reference:[Web Font Optimization ] (https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/webfont-optimization).
2. Made all the CSS styles as inline styles in ``` index.html ``` to reduce critical resource.
3. HTML and CSS are validated by [HTML Validator](https://validator.w3.org) and [CSS Validator] (https://jigsaw.w3.org/css-validator/). Found no issues.
4. Using ```async``` attribute some JavaScripts are loaded Asynchronously.
5. **PageSpeed Insights Scores**
    * Mobile: 93/100
    * Desktop: 95/100

=============================================================================

## Pizza Project - Performance Optimization

1. Made all the CSS styles as inline styles in ```pizza.html``` to reduce critical resource.
2. HTML and CSS are validated by [HTML Validator](https://validator.w3.org) and [CSS Validator] (https://jigsaw.w3.org/css-validator/). Found no issues.
3. The frame rate for ```pizza.html``` is rendered at **_60fps_**.
4. **Change Pizza Size Optimization**
    * ```determineDx()``` function has been removed from ```resizePizzas()``` function which causes Layout event to run again and again.
    * The new width of the pizza is calculated in ```changePizzaSizes()``` function itself. It uses a switch case where the width of the new pizza is determined and it has been assigned to the pizza element's style property.
    * ```document.querySelectorAll(".randomPizzaContainer");``` has been moved out of the for loop and a new variable is used to store the ```.randomPizzaContainer``` element and this variable is in turn used in the for loop. Which means the ```.randomPizzaContainer``` element is read only once and then start to write rather than reading and writing in each iteration. This process avoids **Forced Synchronous Layout(FSL)**.
5. **Page Scroll Event Optimization**
    * During the scroll event ```updatePositions()``` function. This function reads the ```scrollTop``` property of the body inside a for loop which is a overdo thing. So this ```document.body.scrollTop;``` is moved out of the for loop and assigned to a variable and this variable is used inside the for loop, which means the ```scrollTop``` property is read once and then the read process starts. This process reduces the **Forced Synchronous Layout(FSL)** and avoids simultaneous painting & rendering process.
6. **PageSpeed Insights Scores**
    * Mobile: 73/100
    * Desktop: 90/100

#### How to run this project?

1. Download and extract this repository.
2. Find the ```index.html``` file and open that in a web browser to run the project.
3. By clicking on ```Cam's Pizzaria``` link in the homepage takes you to a simulated online pizzaria application where you can see large collections of pizzas.

### How to calculate Google's PageSpeed Insights score?

1. Check out the repository
2. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

3. Open a browser and visit localhost:8080
4. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

4. Copy the public URL ngrok gives you and try running it through [Google Pagespeed Insight](https://developers.google.com/speed/pagespeed/insights/)!


### Extra

1. Adding new layers to the moving pizzas(background) by adding ```will-change:transform``` style property to all the ```<img class='.mover'>``` image elements. Here each pizza element is promoted to its own layer which enhances the animation performance and avoids paint issues.
2. ```document.getElementById("randomPizzas");``` element is used to append the randomly generated pizzas. This property has been used inside the for loop which creates **Forced Synchronous Layout(FSL)**. So to avoid that this element is moves outside the for loop and assigned to a variable. And in turn this variable is used inside the for loop where the element is read only once and write process stated respectively. This enhances the performance.
3. ```document.querySelector("#movingPizzas1");``` element is moved outside the for loop to reduce the **Forced Synchronous Layout(FSL)** as this element is read once and then the write process is started.


=============================================================================

## GUIDE TO GET STARTED WITH THIS PROJECT

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository and inspect the code.

### Getting started

####Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js. 

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>