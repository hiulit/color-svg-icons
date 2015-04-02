# grunt-color-svg-icons

> Color svg icons.

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-color-svg-icons --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-color-svg-icons');
```

## The "color_svg_icons" task

### Overview
In your project's Gruntfile, add a section named `color_svg_icons` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  color_svg_icons: {
    svg_options: {
      options: {
        colors: {
          red: '#ff0000',
          blue: '#0000ff'
        }
      },
      files: {
        'dest': ['src/svgs/*']
      }
    }
  }
});
```

### Options

#### options.colors
Type: `Object`

Properties of the colors object will be used to get the value of color to set the svg icon to and name will be used as a prefix to resulting files.

```js
options: {
  colors: {
    red: '#ff0000',
    blue: '0000ff'
  }
}
```

So the resulting files would be `red_whatever-icon.svg` and `blue_whatever-icon.svg`.

##### Reserved words and link states (:hover, :active, etc)

You can use the **reserved** color name **"base"** to set a default color. This color name won't be outputted.

You can also use **"hover"** as a color name, as well as **"active"** and **"focus"**. These will be outputted just like any other color.

```js
options: {
  colors: {
    base: '#ff0000',
    hover: '0000ff'
  },
  preprend: false
}
```

So the resulting files would be `whatever-icon.svg` and `whatever-icon_hover.svg`.

_Notice the usage of `prepend: false`. See below._

This is pretty useful when using in conjunction with a spriting plugin, such as [grunt-dr-svg-sprites](https://github.com/drdk/grunt-dr-svg-sprites), which creates CSS classes from the files names.

So, with the given options above, the CSS result would be:

```css
.whatever-icon {
  background-position: 0 0;
  height: 20px;
  width: 20px;
}

.whatever-icon:hover {
  background-position: 20px 0;
  height: 20px;
  width: 20px;
}
```

#### options.prepend
Type: `Boolean` Default: `true`

You can choose to append (use as a suffix) the color's name instead of prepending it, which is the default behaviour.

Just add:

```js
options: {
  prepend: false
}
```

This way you can have BEM style names

### Usage Examples
In this example `SVGO.optimize` will be run on all svgs in the `src/svgs/*` path, then color will be set to given CSS hex value, and this result saved in dest folder with property name as the prefix.

```
grunt.initConfig({
  color_svg_icons: {
    svg_options: {
      options: {
        colors: {
          red: '#ff0000',
          blue: '#0000ff'
        }
      },
      files: {
        'dest': ['src/svgs/*']
      }
    }
  }
});
```

## Contributing
In lieu of a formal style guide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
_(Nothing yet)_
