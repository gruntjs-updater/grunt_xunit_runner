# grunt-xunit-runner

> Grunt task for running multiple xunit dlls with all the options that xunit console provides. Also totals the results from each dll at the end

## Getting Started
This plugin requires Grunt `~0.4.2`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-xunit-runner --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-xunit-runner');
```

## The "xunit_runner" task

### Overview
In your project's Gruntfile, add a section named `xunit_runner` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  xunit_runner: {
    options: {
      // this is the exe that I use.  but there seem  to be a couple of runners in the xunit bin
      // your options here are to either have xunit in your path or provide a
      // workingDir for xunit.
      // WARNING
      // IF you provide the workingDir you MUST make your path/to/my/test_dll.Test1.dll RELATIVE to the working dir!
      xUnit : "xunit.console.clr4.exe"
    },
    // two forms use either or
    files:{
        dlls: [
            'path/to/my/test_dll.Tests1.dll ',
            'path/to/my/test_dll.Tests1.dll ',
            'path/to/my/test_dll.Tests1.dll ',
            'path/to/my/test_dll.Tests1.dll '
        ]
    }
    TestAndConfig:[
        {
            file:'path/to/my/test_dll.Tests1.dll ',
            config:'path/to/my/test_dll.Tests1.dll.config'
        }
  }
});
```

### Options
    stdout: true,
    stderr: true,
    workingDir:'',
    xUnit: "xunit.console.exe",
    silent:'true',
    teamcity:'false',
    trait:'',
    notrait:'',
    noshadow:'',
    xml:'',
    html:'',
    nunit:''

// the options should follow the following format
// workingDir:'../../where_my_xUnit_exe_is'  // relative to current dir
// silent: 'true'
// teamcity: 'false'
// trait: 'mytrait=myvalue'
// notrait: 'mytraittoexclude=myvalue'
// noshadow: 'true',
// xml: 'myxmlfile.xml'
// html: '../../somedir/myhtml.xml' // I believe this works, if not, sorry :(
// nunit: 'mynunit.txt' //?



## Contributing
I started with cs_xunit the looked at msbuild and ended up with this.
I'm sure there are a) better ways to do some algorithms and b) more standard ways of doing some parts.
Please feel free to inform me of these as I am kind of new to some of this stuff.

## Release History
0.1.4 made task fail if any tests fail. (duh)

0.1.5 moved async from devDependencies to dependencies courtesy of jgillich
made path to xunit fully resolve

0.1.6 Ok this time the path to xunit should actually resolve. I screwed it up last time and I apologize.

1.7 cleaned up implementation a little bit logging is still probably terrible.
added ability to list file and config incase your dll needs a config file

1.8 fixed bug when not using config