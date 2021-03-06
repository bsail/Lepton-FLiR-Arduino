C Library for the Lepton FLiR Thermal Camera Module.
===============

[![Build Status](https://img.shields.io/travis/bsail/flir-lepton-command-c/master.svg)](https://travis-ci.org/bsail/flir-lepton-command-c)
[![Coverage Status](https://img.shields.io/coveralls/github/bsail/flir-lepton-command-c/master.svg)](https://coveralls.io/github/bsail/flir-lepton-command-c?branch=master)

Library to control a Lepton FLiR (forward looking infrared) thermal camera module.
Licensed under the non-restrictive MIT license.

Created by NachtRaveVL, August 1st, 2016.

Forked by Nikolay Nerovny, BMSTU, 2018.

This library allows communication with boards running a Lepton FLiR thermal camera module. It provides a wide range of functionality from adjustable memory footprint size, adjustable temperature display mode to exposing the full functionality of the thermal camera itself.

Parts of this library are derived from the Lepton FLiR software development SDK, Copyright 2011,2012,2013,2014 FLIR Systems - Commercial Vision Systems.

Fork of original library by [NachtRaveVL](https://github.com/NachtRaveVL/Lepton-FLiR-Arduino).
This version differs from original version: it was ported to plain C to allow usage in wider range of architectures. We also removed the support of VoISP communication, it has only command and control interface.

[Latest version of the library](https://github.com/bsail/flir-lepton-command-c)

Library Setup
---------------

User must create additional header file "lepton-config.h" and put it somewhere in the include search path outside of this library.
This header file should include several declarations that control the behaviour of the library.
The example header file may by found in `test/support` directory.

```C
// Uncomment this define if wanting to exclude extended i2c functions from compilation.
// #define LEPFLIR_EXCLUDE_EXT_I2C_FUNCS   1

// Uncomment this define if wanting to exclude SYS functions from compilation.
// #define LEPFLIR_EXCLUDE_SYS_FUNCS   1

// Uncomment this define if wanting to exclude VID functions from compilation.
// #define LEPFLIR_EXCLUDE_VID_FUNCS   1

// Uncomment this define if wanting to exclude AGC functions from compilation.
// #define LEPFLIR_EXCLUDE_AGC_FUNCS   1

// Uncomment this define if wanting to exclude misc. functions from compilation.
// #define LEPFLIR_EXCLUDE_MISC_FUNCS   1

// Explicitly suppress warning about LEPFLIR_EXCLUDE_MISC_FUNCS
// #define LEPFLIR_EXCLUDE_MISC_FUNCS_SUPPRESS_WARNING 1

// Uncomment this define if wanting to exclude image statistics functions from compilation.
// #define LEPFLIR_EXCLUDE_IMAGE_FUNCS   1

/* Do not use locking instruction in case of single threading */
// #define LEPFLIR_EXCLUDE_LOCKING

// Uncomment this define to enable debug output functions.
#define LEPFLIR_ENABLE_DEBUG_OUTPUT     1
```

Tests are always built with maximum included functions.

Development
---------------

For developers looking to extend, bug fix, build, and test this library with dependencies and test infrastructure included in the source tree.


Setup Environment - Ubuntu 16.04/18.04
---------------------------------

```bash
sudo apt install build-essential git ruby
sudo gem install ceedling
```

Get Code
-----------------

```bash
mkdir lepton
git clone https://github.com/bsail/flir-lepton-command-c lepton
ceedling upgrade lepton
cd lepton
```

Tests
---------------

Build & Run Unit Tests

```bash
ceedling test:all
```

You may use and create additional tasks for Ceedling build system. Please refer to the documentation in the `vendor/ceedling/docs`.
