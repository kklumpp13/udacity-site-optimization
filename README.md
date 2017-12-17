## Website Performance Optimization portfolio project

The goal of this project was to optimize the starter portfolio project site that was [provided](https://github.com/udacity/frontend-nanodegree-mobile-portfolio). We needed meet the following requirements:
* The ```index.html``` page must achieve a PageSpeed Insights score of at least 90 for Mobile and Desktop
* The ```views/pizza.html``` page must render with a consistent frame-rate at 60fps when scrolling
* The time to resize pizzas is less than 5 ms when using the pizza slider on the ```views/pizza.html``` page (the time in shown in the browser developer tools)

### Getting started

1. Clone the repository
1. Navigate to the root directory and start a web server

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

1. Copy the public URL ngrok gives you and run it through PageSpeed Insights.


### Optimizations Performed

#### Requirement 1: Improve PageSpeed Insights score for index.html
* CSS was minified using the npm package [minifier](https://www.npmjs.com/package/minifier)
* Critical CSS was inlined
* Instructions were added to only download the print stylesheet when necessary
* HTML was minified using the npm package [html-minify](https://www.npmjs.com/package/html-minify)
* All ```<script>``` tags were moved to the bottom above the closing ```<body>``` tag and ```async``` was added to them where appropriate
* The Web Font Loader was used to improve the font loading
* Images were compressed with [TinyPNG](https://tinypng.com/)

#### Requirment 2: Remove Jank and reduce time to resize pizzas
* Changed ```querySelector()``` to ```getElementById()```
* Changed ```querySelectorAll()``` to ```getElementsByClassName()```
* Reduced number of pizzas from 200 to 40
* Removed switch statements where possible
* Extracted variables from loops to prevent unnecessary DOM calls on each iteration
* Pulled out the ```items``` variable so that it was only called once
* Added ```randomPizzaContainer``` variable to reduce code duplication
