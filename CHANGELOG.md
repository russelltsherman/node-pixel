# node-pixel changelog

### 0.8.2

* Fixes to testing setup - thanks @reconbot

### 0.8.1

* Put in error check to make sure the firmata firmware is capable of doing
node-pixel stuff. Fixes [#74](https://github.com/ajfisher/node-pixel/issues/74)
* Put in I2C write check to deal with specifically time outs on high bandwidth
writes that appear to happen on RPi. Fixes [#71](https://github.com/ajfisher/node-pixel/issues/71)
and
* Added `.off()` option to individual pixels. Completed: [#61](https://github.com/ajfisher/node-pixel/issues/61)

### 0.8.0

* Moved all strip manipulation up to the level of the ws2812 library
in order to consolidate into a single array. This means that the `Strips` are now
relatively dumb and just operate on the array they are passed which is ripe
for further consolidation down the line. ( = more memory for pixels - YAY!)
* Added a SHIFT operation to the protocol per [#32](https://github.com/ajfisher/node-pixel/issues/32)
which is what required this large refactor above.
* Begun deprecation of `strip.stripLength()` and move to `strip.length` as the
more logic alternative. 0.8 generates warning, 0.9 will throw error, 0.10 will
have function removed
* Added example `examples/repl` that exposes `strip` object so you can manipulate
it from a repl environment

### 0.7.1

Thanks to @stevemao for the following:

* Updated strip color to consistently take arrays for the rgb model
* Made `Strip.off()` behaviour intuitive so it latches as soon as it's set
and turns the strip off.
* Updated package file to be able to run `npm test`

## 0.7.0

* updated packages to bring dependency list up to scratch.
* removed es6-collections shim YAY ES6.
* Updated node-pixel-firmata with latest version of StandardFirmata (v2.5.3)
* Updated lib to use new color string api.
* Resolved issue with an osx segfault when trying to write too quickly after
firmware returns
* Update to grunt file to now build and compile hexes to target MCU architecture
* Manifest file for interchange to be able to install to targets.
* Update of examples as needed.

### 0.6.1

* Fixed some default I2C address issues - thanks @frxnz

## 0.6.0

* Added `strip.off()` functionality and tests - thanks again @noopkat

### 0.5.2

* Documentation fixes around syntax highlighting thanks to @noopkat

### 0.5.1

* Modified maximum firmata to 192 pixels after profiling and lack of memory issue

## 0.5

* Strip multipin! You can now use and define multiple strips on different pins
in the firmata and I2C backpack versions of node-pixel.
* Tests are starting to be laid in for any development. New features
require tests to be built out as well from now on.
* Removed the AdaFruit lib and switched to lightweight lib with a number of
modifications from https://github.com/cpldcpu/light_ws2812 (mostly removals
of things we don't need because the JS side will take care of it).
* Added protocol changes to set the colour order of the strip so that you can
use different types of pixels
* Added protocol changes to define multiple strips of varying legnths
* Interface to the virtual strip is singular and the C lib takes care of the mapping
to the actual pixel required.
* Added `set_off()` in order to rapidly and efficiently wipe an entire strip of
values back to zero in the firmware.
* Implemented error checking for too many strips and too many pixels that would 
exceed memory limits in the firmware.
* Updated new examples and updated examples documentation properly incuding the
updates to the master readme and installation guides. All examples have code in
them as well as proper wiring diagrams.
* Package dependencies updated to bring into line.
* New tests for pixel lengths, strip maximums, ensuring calculations are correct.

### 0.4.1

* Fixed bug in backpack firmware that meant it was doing full scale serial debugging
by default.

## 0.4

* Major refactor to deal with install and symlinking issues. Updates mean a Grunt
task which is used to build the destination trees properly so the firmware can be
compiled. This means better cross-platform support as well as no symlinking when
npm installed the package. More details here
[https://github.com/ajfisher/node-pixel/issues/34](https://github.com/ajfisher/node-pixel/issues/34)
* New documentation added and installation instruction fixed.
* Grunt file used to do all building operations from a source tree to produce the
relevant files in the right place for building
* renamed the examples to be more sensical.

### 0.3.3

* @pierceray contributed two examples porting "rainbow" behaviour with a static
rainbow effect and a dynamic moving one.

### 0.3.2

* Various documentation updates to clean up errors.
* npm installation fixes - thanks @frxnz

### 0.3.1

* Documentation updates and bug fixes around Baudrate on backpack for RPi installation
* Thanks to @frxnz


## 0.3.0

* Added pin selection to the constructor in order to be able to set which pin
you are using for the strip.
* Added custom I2C controller in pixel.js
* added custom I2C Backpack firmware.
* Removed ATTIny85 support due to bugginess.
* Updated all documentation including firmware install support etc.


### 0.2.3

* Restructure of the firmware folder ahead of providing backpack and native
firmata controllers.
* Updated all of the package versions.


### 0.2.2

* Migration of all protocol messages to use firmata SYSEX commands with custom
command set that will be viable when moving to I2C / SPI.
* Updates to Pixel lib to talk this protocol
* Optimisation of the SYSEX commands to ensure high bitrate (now at 150fps on test rig - up from 18)
* Removal of all the string processing code which drops hex file size from 20K to 11K
* documentation of protocol as it's being created.


### 0.2.1

* First implementation of Pixel library on JS side against firmata API
* big restructure of entire code base to work properly in ino and arduino

## 0.2.0

* Removal of 95% of all custom firmata messages and compression of existing
messages in order to speed things up.
* Entire restructure of code library including ino support and structure to
support no-dependency firmware compilation.

## 0.1.0

* Firmata only implementation
* Specific implementation in firmata to provide functions
* Naive implementation against Adafruit NP library.
* Initial build of library

