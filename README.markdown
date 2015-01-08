# Snapdragon

**A command-line [Jasmine](http://jasmine.github.io) (JavaScript) test runner built with developer workflow in mind.**

## Installation

Add this line to your application's Gemfile:

```
gem 'snapdragon'
```

And then execute:

```text
$ bundle
```

Or install it yourself as:

```text
$ gem install snapdragon
```

## Install PhantomJS

You need at least [PhantomJS](http://phantomjs.org) 1.8.1. There are no other
external dependencies (you don't need Qt, or a running X server, etc.)

### Mac OS X

I recommend installing [PhantomJS](http://phantomjs.org/) using
[Homebrew](http://mxcl.github.io/homebrew/) on Mac OS X. Using
[Homebrew](http://mxcl.github.io/homebrew/) it can be installed as easily as
running the following command:

```text
$ brew install phantomjs
```

## Quick Start Guide

If you are a visual learner Brian Miller and I have put together a Free
[Snapdragon Screencast](http://codebreakdown.com/screencasts/7) at [The Code
Breakdown](http://codebreakdown.com).

[![It in Action](http://media.codebreakdown.com/thumbnails/tcb-0007-thumbnail-400x225.png)](http://codebreakdown.com/screencasts/7)

For those of you that like to jump right in and start playing with new tools
follow the steps below to get started.

1. Install [Snapdragon](http://github.com/reachlocal/snapdragon) and
   [PhantomJS](http://phantomjs.org/) as outlined above.

2. Create a simple [Jasmine](http://jasmine.github.io) spec file
   `example/spec/hoopty_spec.js` with the following content. Note: the
   `// require_relative()` directive at the top of the file. This tells
   [Snapdragon](http://github.com/reachlocal/snapdragon) what
   implementation file(s) it needs to run the specs in this file.

    ```javascript
    // require_relative('../src/hoopty.js')

    describe("Hoopty", function() {
      describe(".hello", function() {
        it("says hello there", function() {
          var f = new Hoopty();
          expect(f.hello()).toBe("Hello There");
        });
      });
    });
    ```

3. Create the implementation file for the spec file `example/src/hoopty.js`
   with the following content.

    ```javascript
    var Hoopty = function() {
      this.hello = function() {
        return "Hello There";
      }
    };
    ```

4. Run your spec file with the following command:

    ```text
    $ snapdragon example/spec/hoopty_spec.js
    ```

    You should see output that looks similar to the following.

    ```text
    Running examples...

    Finished in 0.001 seconds
    1 example, 0 failures
    ```

Thats it, you now have [Snapdragon](http://github.com/reachlocal/snapdragon)
running a [Jasmine](http://jasmine.github.io) spec.

## Usage (snapdragon)

The *snapdragon* command allows you to run your
[Jasmine](http://jasmine.github.io) specs from the command-line just
as you would with RSpec and other testing tools. The following are some usage
examples.

#### Run a specific describe/it block

The following runs the describe or it block that corresponds to line number
*23* in the *spec/javascript/foo_spec.js* file.

```text
$ snapdragon spec/javascript/foo_spec.js:23
```

#### Run an entire spec file(s)

```text
$ snapdragon spec/javascript/foo_spec.js spec/javascript/bar_spec.js
```

#### Run an entire directory of spec files

The following recursively explores the given directories contents for
files that end in `spec.js` or `Spec.js` and runs the tests in the identified
spec files.

```text
$ snapdragon spec/javascripts
```

#### Run combination of files and directories

```text
$ snapdragon spec/javascript custom_js/tests/foo_spec.js custom_js/test/bar_spec.js
```

#### Run test files matched by default pattern (`spec/**/*_spec.js`)

```text
$ snapdragon
```

#### Run test files matched by custom pattern

The following is an example command that specifies a custom pattern to use to
match test files to run. Please note the double quote marks around the
pattern. These are necessary as without them most shells will try and resolve
the pattern for you. Further details on the glob syntax can be found
[here](http://ruby-doc.org/core-2.0.0/Dir.html#method-c-glob).

```text
$ snapdragon -P "spec/assets/javascripts/foo/*_spec.js"
```

#### Output Usage Details/Help

```text
$ snapdragon --help
```

## Usage (snapdragon_server)

The *snapdragon_server* command allows you to run your
[Jasmine](http://jasmine.github.io) specs in your browser. When this
command is run it will launch the *snapdragon_server* and open your default
browser to the proper URL to run your specified test suite. This is especially
useful if you want to debug some JavaScript as your browser most likely has a
JavaScript debugger built into it. A few examples of this commands usage
follow.

#### Run a specific describe/it block

The following runs the describe or it block that corresponds to line number
*23* in the *spec/javascript/foo_spec.js* file.

```text
$ snapdragon_server spec/javascript/foo_spec.js:23
```

#### Run an entire spec file(s)

```text
$ snapdragon_server spec/javascript/foo_spec.js spec/javascript/bar_spec.js
```

#### Run an entire directory of spec files

The following recursively explores the given directories contents for
files that end in `spec.js` or `Spec.js` and runs the tests in the identified
spec files.

```text
$ snapdragon_server spec/javascript custom_js/specs
```

#### Run combination of files and directories

```text
$ snapdragon_server spec/javascript custom_js/tests/foo_spec.js custom_js/test/bar_spec.js
```

#### Run test files matched by default pattern (`spec/**/*_spec.js`)

```text
$ snapdragon_server
```

#### Run test files matched by custom pattern

The following is an example command that specifies a custom pattern to use to
match test files to run. Please note the double quote marks around the
pattern. These are necessary as without them most shells will try and resolve
the pattern for you. Further details on the glob syntax can be found
[here](http://ruby-doc.org/core-2.0.0/Dir.html#method-c-glob).

```text
$ snapdragon_server -P "spec/assets/javascripts/foo/*_spec.js"
```

#### Output Usage Details/Help

```text
$ snapdragon_server --help
```

### Additional Options

Below is a listing of the various options that can be passed to either the
`snapdragon` or `snapdragon_server` commands.

#### Version (`-v`, `--version`)

When given this option it will output the version that you are using
and exit without running any tests.

#### Help (`-h`, `--help`)

When given this option it will output basic usage summary and exit without
running any tests.

#### Format (`-f FORMAT`, `--format FORMAT`)

This option allows you to specify the output format of the tests. By default
it outputs using the `console` format. This option is extremely useful when
you would like to use `snapdragon` inside of a CI process because you can
instruct it to output in other formats such as `junit` which CI services
can parse.

The following are the currently supported `FORMAT` values.

* `console` (default)
* `junit`

#### Color (`--no-color`, `--no-colour`)

If you would like to disable ANSI color output which is enabled by default,
include either the `--no-color` or `--no-colour` option.

#### Pattern (`-P PATTERN`, `--pattern PATTERN`)

When this option is not given and no file or directory paths are given it
uses the default pattern `"spec/**/*_spec.js"`.

When given this option without any explicit file paths or directory paths it
will use the provided glob pattern to identify which test files to run. Any
example usage of this option can be seen above in the *Run test files matched
by custom pattern* section. For more details on the glob pattern syntax please
refer to the [Ruby
Dir.glob](http://ruby-doc.org/core-2.0.0/Dir.html#method-c-glob)
documentation.

## // require_relative() directive

Snapdragon also provides a `// require_relative()` directive that the
Snapdragon preprocessor looks for to identify the necessary implementation
files that need to be loaded for the spec files to run. This directive should
define the relative path to associated implementation files needed for a spec,
relative to that spec file. The following is an example spec and implemantion
file.

*example/src/hoopty.js*

```javascript
var Hoopty = function() {
  this.hello = function() {
    return "Hello There";
  }
};
```

*example/spec/hoopty_spec.js*

```javascript
// require_relative('../src/hoopty.js')

describe("Hoopty", function() {
  it("exists", function() {
    var f = new Hoopty();
    expect(f).not.toBe(undefined);
  });

  describe(".hello", function() {
    it("says hello there", function() {
      var f = new Hoopty();
      expect(f.hello()).toBe("Hello There");
    });
  });
});

```

## The ChangeLog

Information on notable changes in each release can be found in the
[ChangeLog](http://github.com/reachlocal/snapdragon/blob/master/ChangeLog.markdown).

## IRC Channel

We have a persistent IRC channel (**#snapdragon-js**) on
[freenode](http://freenode.net/). Feel free to join it and ask questions, make
suggestions, talk with developers, or just hang out.

## The Back Story

If you have ever used [Jasmine](http://jasmine.github.io) for your
JavaScript BDD style testing framework I am sure you have run into the
following issues just as I have.

1. Getting up and running with [Jasmine](http://jasmine.github.io) is
   quite a pain and the examples of how to setup your SpecRunner.html are
   sparse.
2. Having to manually add the dependency files and spec files to the
   SpecRunner.html is a huge pain in the ass.
3. Limiting a test run to a specific spec file is near impossible with the
   only solution being to comment out script tags in your SpecRunner.html.
4. Limiting a test run to a specific *describe* or *it* block is near
   impossible because the only way to do it is with the *spec* query param that
   matches the full description of the *describe* or *it* block including all
   its parents. This can be very long and very prone to typos if you try to
   do this.
5. Oh, and did I mention that you have to do all of this in a browser with the
   SpecRunner.html loaded which is not where you actually write your code.

The above issues created a horrible development workflow. Especially
since I came from the world of RSpec where the above issues are non-existent
and it is easily run from the command line and integrated into most editors.

Snapdragon is my preferred solution to the above listed issues.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Write your tests & dev your feature using BDD/TDD with RSpec.
4. Commit your changes (`git commit -am 'Add some feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create new Pull Request
