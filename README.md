# Static Assets Manager
#### A Webpack configuration to manage your assets

This package is an assembly of different components and plugins for Webpack that allows to have a good basic structure for the management of static assets within a project (js, css, images, fonts).

If you use it, here's what it will do **automatically**:

This is an overview of the features, see below for details on how to use them.

1) CSS Minify
1) Automatic css prefixes if needed to increase browser compatibility
1) JS Minify
1) ES6 Compilation
1) Automatic Sprites generator
1) Automatic fonts generator starting from SVG
1) Automatic TinyPNG and TinyJPG on images (you need an API Key here)
1) PHP Manifest generator with the mapping of all the css and js compiled

## How to use it

####General Concept

Simply, I thought of this package to be the content of the *assets* folder of my projects.

####Setup:

```
npm install
```

**Entry Point**

The entry point to manage all the code that will be generated is configured as:
```
src/index.js
```

####CSS (really, we will use SCSS)

```
src/scss/
```

Create the scss as you want inside the *src/scss* folder.  
Once you have created your scss, you must insert the instruction to include it in the entry point (*index.js*).
Eg. if your file is called *src/scss/main.scss*.  
In the entry point enter:

```
import './scss/main.scss';
```
Webpack will generate the css files and will minimize them.

####JS

In the entry point file (*index.js*), you can insert the javascript code as you would in any javascript file.  
Just be aware to enter the code below any "*import*" or "*require*" statement.  
The ES5 or ES6 code compilation is already provided so feel free to enter ES6 code without problems.

The current configuration is made in such a way that after compiling your javascript code is divided from the one relative to the "vendors" (eg bootstrap, jquery etc ...).

Webpack will handle all the needed compilations and will create the necessary js files.

####Sprites


Sprites are a great Best Practice and you should use it.
It is about bringing together all those medium/small sizes images into a single image, so as to reduce the HTTP calls made and optimize.

Insert the individual images in the *src/sprites/* folder and the **Static Assets Manager** will automatically create the files:

```
src/images/sprites.png
 ```
and
```
src/scss/sprites.scss
```

The CSS classes for each image within the *sprites.scss* will be called based on the filename with an "*ico-*" prefix.

Example, if your files are called "*icon.png*" and "*logo.png*" two classes will be created called "*ico-icon*" and "*ico-logo*".

##### Using Sprites:

- In the entry point (*index.js*) enter:
```
import './scss/sprites.scss';
```

- In your HTML code, enter, for example:
```
<i class="ico ico-logo"></i>
```

__Currently only *.png* files are supported.__

####Icon Fonts

Using icon fonts is another Best Practice that you should use if possible.
It's about converting SVG to Fonts so you can take advantage of some advantages like the ability to change color and size.

Copy the individual SVG files in the *src/ico-font/* folder and the **Static Assets Manager** will automatically create 
the fonts and the css to use.

The CSS classes for each image within the *sprites.scss* will be called based on the filename with an "*icofont-*" prefix.

Example, if your files are called "*barcode.svg*" and "*envelop.svg*" two classes will be created called "*icofont-barcode*" and "*icofont-envelop*".

##### Using Icon Fonts:

- Above, in the entry point (index.js) enter:
```
require('./../ico.font');
```
- In your HTML code, enter, for example:
```
<i class="icofont-barcode icofont"></i>
```



