# Your First Gulp project with LiveReload 

First things first I'm going on the assumption that you have node installed. If not, this might be a perfect time to do so. I recommend using the package installer on the [node.js](http://nodejs.org/) site as it makes it much easier. I could go into more detail, but for now I'll just say I don't like where the homebrew installer of Node puts certain files 

With node installed via the installer you now should have access to both the node and npm bash commands. We're going to be using npm.

## Setting up our project

The first thing we're going to want to do is create our project directory and change into that directory. We can do this by typing the following into our terminal:

`mkdir gulpreload`

`cd gulpreload`

Next we want to setup Node Package Manager for this project by putting this into the terminal:

`npm init` 

`npm install gulp gulp-livereload --save-dev`

What that last little bit of code did was download the gulp package along with the gulp-reload package, a package that adds so shortcuts for 

##Installing the LiveReload Plugin

There are several ways to set up LiveReload but I think one of the simplist is with a plugin for a chrome browser, [LiveReload Chrome Plugin](https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei?hl=en). Once you install it you should notice a small icon in the right hand corner of your browser window's toolbar. This is where you will be toggling on and off the Plugin.

One **really important** thing to note is that you need to give the plugin some extra access once you've installed it. You can do this by going to **Window > Extensions** in your chrome browser and checking the box **"Allow access to file URLs"** for LiveReload.

## Creating your Gulpfile

The first thing you'll want to do is create a Gulpfile. This is where we tell Gulp what tasks we want run and in what order. I'll explain more about this as we go but for right now type this into your terminal:

`touch gulpfile.js`

Once you've created that file, copy the following code into your **gulpfile.js**:

```
var gulp = require('gulp'),
  livereload = require('gulp-livereload');

gulp.task('watch', function() {
  livereload.listen();
  gulp.watch('app/**').on('change', livereload.changed);
  gulp.watch('README.md').on('change', livereload.changed);
});

gulp.task('default',['watch']);
```

