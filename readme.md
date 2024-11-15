### Installation

This one package will let you use `jquery` and `jquery-ui` *(v.1.12.1, for jQuery1.7+)* in your project.  
Use `npm install webpack-jquery-ui` instead of installing all dependencies and loaders separately.


### Configuration

##### your `webpack.config.js` file
* set the following loaders and plugins that are necessary to support `jquery`
```javascript
const path = require('path');
const webpack = require('webpack');
module.exports = {
  entry: {
    index:'./src/index.js'
  },
  output: {
    filename: 'bundled.js',
    path: path.resolve(__dirname, 'dist'),
    publicPath:'dist/'
  },
  module: {
    rules: [
      {
        test: /\.css$/,
        loaders: ["style-loader","css-loader"]
      },
      {
        test: /\.(jpe?g|png|gif)$/i,
        loader:"file-loader",
        options:{
          name:'[name].[ext]',
          outputPath:'assets/images/'
          //the images will be emited to dist/assets/images/ folder
        }
      }
    ]
  },
  plugins: [
    /* Use the ProvidePlugin constructor to inject jquery implicit globals */
    new webpack.ProvidePlugin({
        $: "jquery",
        jQuery: "jquery",
        "window.jQuery": "jquery'",
        "window.$": "jquery"
    })
  ]
};
```

##### your entry `index.js` file

To load **all** `jquery-ui` **features** with its **basic css theme** use:
```javascript
require('webpack-jquery-ui');
require('webpack-jquery-ui/css');  //ommit, if you don't want to load basic css theme
```

To load **only** `jquery-ui` **interactions** or **widgets** or **effects** [\[list of features\]](http://jqueryui.com/download/) use:
> don't worry about jquery-ui **core files**. All neccessary dependencies are automatically loaded
```javascript
require('webpack-jquery-ui/interactions');
require('webpack-jquery-ui/widgets');
require('webpack-jquery-ui/effects');
```

To load **only particular interactions** [\[list of interactions\]](http://jqueryui.com/download/) use:
> don't worry about jquery-ui **core files**. All neccessary dependencies are automatically loaded with chosen interaction feature
```javascript
require('webpack-jquery-ui/draggable');
require('webpack-jquery-ui/droppable');
require('webpack-jquery-ui/resizable');
require('webpack-jquery-ui/selectable');
require('webpack-jquery-ui/sortable');
```
To load **only particular widgets** [\[list of widgets\]](http://jqueryui.com/download/) use:
> don't worry about jquery-ui **core files**. All neccessary dependencies are automatically loaded with chosen widget
```javascript
require('webpack-jquery-ui/accordion');
require('webpack-jquery-ui/autocomplete');
require('webpack-jquery-ui/button');
require('webpack-jquery-ui/checkboxradio');
require('webpack-jquery-ui/controlgroup');
require('webpack-jquery-ui/datepicker');
require('webpack-jquery-ui/dialog');
require('webpack-jquery-ui/menu');
require('webpack-jquery-ui/progressbar');
require('webpack-jquery-ui/selectmenu');
require('webpack-jquery-ui/slider');
require('webpack-jquery-ui/spinner');
require('webpack-jquery-ui/tabs');
require('webpack-jquery-ui/tooltip');
```
To load **only particular effects** [\[list of effects\]](http://jqueryui.com/download/) use:
> don't worry about jquery-ui **core files**. All neccessary dependencies are automatically loaded with chosen effect
```javascript
require('webpack-jquery-ui/blind-effect');
require('webpack-jquery-ui/bounce-effect');
require('webpack-jquery-ui/clip-effect');
require('webpack-jquery-ui/drop-effect');
require('webpack-jquery-ui/explode-effect');
require('webpack-jquery-ui/fade-effect');
require('webpack-jquery-ui/fold-effect');
require('webpack-jquery-ui/highlight-effect');
require('webpack-jquery-ui/puff-effect');
require('webpack-jquery-ui/pulsate-effect');
require('webpack-jquery-ui/scale-effect');
require('webpack-jquery-ui/shake-effect');
require('webpack-jquery-ui/size-effect');
require('webpack-jquery-ui/slide-effect');
require('webpack-jquery-ui/transfer-effect');
```

### Links

* [jQuery-UI docs](https://learn.jquery.com/jquery-ui/environments/bower/)
* [jQuery docs](http://jquery.com/download/)

### See also
* [styles-loader](https://www.npmjs.com/package/styles-loader)
* [webpack-icons-installer](https://www.npmjs.com/package/webpack-icons-installer)
* [webpack-karma-jasmine](https://www.npmjs.com/package/webpack-karma-jasmine)