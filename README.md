Intel® XDK IoT Node.js\* Analog Pin Read App
============================================
See [LICENSE.md](LICENSE.md) for license terms and conditions.

This sample application is distributed as part of the
[Intel® XDK](http://xdk.intel.com). It can also be downloaded
or cloned directly from its git repo on the
[public Intel XDK GitHub\* site](https://github.com/gomobile).

For help getting started developing applications with the
Intel XDK, please start with
[the Intel XDK documentation](https://software.intel.com/en-us/xdk/docs).

App Overview
------------
A simple Node.js application that reads an onboard analog input (an AIO input),
on select Intel IoT development boards, and displays the result of that read on
the console log.

The app initializes a single pin to analog input mode, so it can be read;
samples that analog input at a regular basis; and prints the result of each
read to the console. The specific pin that is read is configured in
`cfg-app-platform.js` and can be identified by looking for lines similar to the
following line of code, in the `cfg.init` method:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    io = opt.altPin ? io : 0 ;              // use alternate pin?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the example shown above, analog "pin 0" will be used for the analog input.
Note that on some boards the analog pin number does not correspond to the 
header number, like it does for other I/O pin numbers.

**IMPORTANT:** the pin that is configured by the sample is a function of the
detected board. You **must** inspect the code to determine which pin is being
configured for use on your board!!

Once you have identified the AIO pin that is being read, you can use a jumper
wire to change the input value of that analog input by connecting one end of the
jumper wire to the initialized analog input and the other end of the jumper to
the various voltage pins or GND point on your board's header. Most boards have
a +3.3V and a +5V pin, some also have a +1.8V pin; all can be used for a quick
simple test of the analog input. A greater range of input voltages can be
sampled by using an I/O mezzanine or "shield" that fits your board and an
appropriate potentiometer.

Most boards have multiple pins that can be configured for use as a analog input.
The `cfg-app-platform.js` module has been designed so you can override the pin
that is used, by passing it an alternate pin during the init call (see the module
documentation). Or, you can simply modify the code to change the default value.

Important Sample App Files
--------------------------
* main.js
* package.json

Important Sample Project Files
------------------------------
* README.md
* LICENSE.md
* project-name.xdk
* project-name.xdke

Tested IoT Node.js Platforms
----------------------------
* [Intel® Galileo Board](http://intel.com/galileo)
* [Intel® Edison Development Platform](http://intel.com/edison)
* [Intel® Joule™ 570x Developer Kit](http://intel.com/joule)
