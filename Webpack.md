Webpack is a static module bundler for javascript applications.

Consider a web application that uses a bunch of third party modules, along with having several files that import/export modules (React Components etc) from other files in your project. In other words your project has several files with incoming and outgoing dependencies. 

Once you run  your project through webpack, it will create dependency graph from one or more entry points in your project, and combine then into one or more bundles. These bundles are the static assest from which your app will be served.

The benefit here is that you don't have to keep a track of your JS dependencies in your HTML file and don't have to worry about the order as well. Webpack can also create a dev-server which doesn't even create a physical bundle file and instead serves your application directly from the memory. This allows you to have a very snappy local development experience.

Webpack can also integrate and call babel on your react project to compile your React/ES6 code to JS.

In order to use webpack, install it as a dependency on your project: `yarn add webpack`, and then create a `webpack.config.js` file in the root of your project. This file is a standard javascript file which defiles a `module.exports` with configs for several tasks that webpack performs. A sample config file is shown below with important properties.

```
const path = require('path');

module.exports = {
	// following properties define the entry point to the application for webpack, as well the output bundle file
	entry: './src/app.js',
	output: {
		path: path.join(__dirname, 'public'),
		filename = 'bundle.js'
	}
	
	// following object defines the rules for loaders for compilers and preprocessors (for ex babel)
	module: {
		rules: [{
			loader: 'babel-loader', // defines which loader to use
			test: /\.js$/, // regex for the files to be processed by loader
			exclude: /node_modules/ // regex for files to be excluded
		}]
	}
	
	// following property defines the tool to create source maps. This allows us to retain the original files that create the bundle, so we can use them in debugging
	devtool: 'cheap-module-eval-source-map'
	
	// following object defines the config for webpack-dev-server command, mostly issued from a script in package.json
	devServer: {
		contentBase: path.join(__dirname, 'public')
	}
}
```

Once you have the above config in place, you can have build scripts in package.json that call either webpack or webpack-dev-server to create a bundle or server application directly from memory, respectively.

```
"scripts": {
	"build": "webpack",
	"dev-server": "webpack-dev-server"
}
```