# grunt-sencha-build

> Grunt plugin to use as a wrapper to Sencha CMD.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-sencha-build --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-sencha-build');
```

## Sencha CMD
Sencha CMD is required for this plugin.  In most cases it's installed as the command line app 'sencha'.  For more details on Sencha CMD, visit http://docs-origin.sencha.com/cmd/3.1.2/#!/guide/command

## Supported Commands
Currently only 'sencha app build' and 'sencha compile' are supported via specific targets.  You can use the generic 'sencha' task to run any task and pass in command details via the command array ( see below ).  More specific commands are coming and if there are some in particular you have use for, please let me know and I'll add them.

## The "sencha_app_build" task

### Overview
In your project's Gruntfile, add a section named `sencha_app_build` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  // Simple Example
  sencha_app_build: {
    testing_build: {
    	environment: 'testing'
	}
  }
  // Full Example
  sencha_app_build: {
  	options: {
  		cwd: 'your app path',
  		cmdPath: 'path to Sencha CMD executable'
  	}
  	testing_custom_build: {
  		environment: 'testing'
  		commandOptions: '-d somefolder'
  	}
  }
})
```

### Options

#### options.cwd
Type: `String`
Default value: ``

The path to your app you want to work with, defaults to the current directory

#### options.cmdPath
Type: `String`
Default value: `sencha`

The full path to the Sencha CMD executable, defaults to 'sencha'

### Properties

#### environment
Type: `String`

The type of build environment to use, options are production|testing|native|package

### Usage Examples

#### Simple Package Example
Builds app in current directory using the testing environment
```js
grunt.initConfig({
  sencha_app_build: {
    testing_build: {
		environment: 'testing'
	}
  }
})
```

#### Build different directory with different output directory
Package up the /myappdir into /webroot using the production environment
```js
grunt.initConfig({
  sencha_app_build: {
    options: {
    	cwd: '/myappdir'
    },
    custom_build: {
		environment: 'production'
        commandOptions: '-d /webroot'
	}
  }
})
```

## The "sencha_compile" task

### Overview
In your project's Gruntfile, add a section named `sencha_compile` to the data object passed into `grunt.initConfig()`.  This task will run the sencha cmd compile target.  See the Sencha CMD documentation for additional options.

```js
grunt.initConfig({
  // Simple Example
  sencha_compile: {
    testing_build: {
        params: [
            "page -i index.html -o output.html"
        ]
	}
  }
})
```

### Properties

#### params
Type: `Array`
Default value: ``

An array of parameters.  If you prefer you can also just make them as one string in the array like above.

## The generic "sencha" task

### Overview
Any task that Sencha CMD supports can be achieved by this grunt task. It just takes the command from grunt's config.

```js
grunt.initConfig({
  // Simple Example
  sencha: {
    concat: {
        command: [
            "fs concat -to=output.js input1.js input2.js input3.js"
        ]
	}
  }
})
```

### Properties

#### command
Type: `Array`
Default value: ``

An array of command lines.  If you prefer you can also just make them as one string in the array like above.

