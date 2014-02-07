# ChangeLog

The following are lists of the notable changes included with each release.
This is intended to help keep people informed about notable changes between
versions as well as provide a rough history.

#### Next Release

#### v1.0.0

This release doesn't include any new changes. It is simply here to signify
that the public interface for the application is now at a stable place and
shouldn't be changing in ways that would break existing functionality.

#### v0.2.0

* added -P, --pattern options to over the test file search pattern as well as
  a default test file search pattern when not given an explicit file or
  directory path.

#### v0.1.12

* add the --color, --no-color, --colour, --no-colour, and -c option to
  enable/disable color output

#### v0.1.11

* fixed issue where junit formatter was outputing multiple xml docs.

#### v0.1.10

* added --format junit switch to make it output JUnit format for CI servers
* added -v and --version switches to notify users of the version
* added -h and --help switches to notify users of the proper usage

#### v0.1.9

* fixed bug preventing require\_relatives with no tailing whitespace from being
  detected ([\#20](http://github.com/reachlocal/snapdragon/issues/20))
* eliminated duplicate requires
  ([\#17](http://github.com/reachlocal/snapdragon/issues/17))

#### v0.1.8

* removed debug puts statements that were left in
* added the Jasmine license info to LICENSE since we package Jasmine

#### v0.1.7

* made require_relative directives work inside of required files
  ([\#15](http://github.com/reachlocal/snapdragon/issues/15))

#### v0.1.6

* snapdragon_server when given `some/spec.js:344` now opens the browser to the
  correctly filtered URL
  ([\#3](http://github.com/reachlocal/snapdragon/issues/3))
* snapdragon_server now finds new files/specs on browser refresh
  ([\#1](http://github.com/reachlocal/snapdragon/issues/1))
* Stack traces are now exclude jasmine.js lines
  ([\#10](http://github.com/reachlocal/snapdragon/issues/10))
* Added stack traces to the output of failed expectations
  ([\#14](http://github.com/reachlocal/snapdragon/issues/14))
* Moved from inline code loading to external script tag sources
  ([\#13](http://github.com/reachlocal/snapdragon/issues/13))

#### v0.1.5

* Jasmine runner now hosts files in CWD under `/:path`
  ([\#12](http://github.com/reachlocal/snapdragon/issues/12))

#### v0.1.4

* Resolved some path expansion issues

#### v0.1.3

* Made Capybara wait for test output to finish before killing session

#### v0.1.2

* Reworked styled and colored output to work with Jasmine v1.3.1
* Switch to include latest stable Jasmine v1.3.1

#### v0.1.1

* Added jasmine-core to gemspec to resolve epic failure when running
  `snapdragon` or `snapdragon_server`

#### v0.1.0

* Provided initial README.md for documentation
  ([\#2](http://github.com/reachlocal/snapdragon/issues/2))
* Added styled and colored output matching RSpec style output.
* Added latest master branch of Jasmine as the included test framework
* Added support for spec.js file arguements to `snapdragon` &
  `snapdragon_server`
* Added support for spec directory arguements to `snapdragon` &
  `snapdragon_server`
* Added support for spec.js:line_number arguements to `snapdragon` &
  `snapdragon_server`
* Added `// require_relative()` directive to load required dependencies
* Added the basic `snapdragon` command line tool
* Added the basic `snapdragon_server` command line tool

