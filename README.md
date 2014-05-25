# CrossGuid

CrossGuid is a minimal, cross platform, C++ implementation. It uses the best
native GUID/UUID generator on the given platform and had a generic class for
parsing, stringifying, and comparing IDs.

## Building

Each platform has its own build script to create object files and run unit
tests, but the source files (the only ones you need are `guid.h` and
`guid.cpp`) are meant to be incorporated into your own build system. You can
look at the platform build script (eg: `linux.sh` as a reference).

## Linux

**The Linux version uses the proprocessor flag `GUID_LIBUUID`**

On linux you can use libuuid which is pretty standard. On distros like Ubuntu
it is available by default but to use it you need the header files so you have
to do:

    sudo apt-get install uuid-dev

Then you can compile and run tests with:

    ./linux.sh

## Mac/iOS

**The Mac and iOS versions use the preprocessor flag `GUID_CFUUID`**

On Mac or iOS you can use `CFUUIDCreate` from `CoreFoundation`. Since it's a
plain C function you don't even need to compile as Objective-C++. If you have
the command line tools that come with Xcode installed, then you can compile and
run the tests like this:

    ./mac.sh

## Windows

**The Windows version uses the preprocessor flag `GUID_WINDOWS`**

On Windows we just the the built-in function `CoCreateGuid`. There is a Visual
Studio 2013 solution in the `VisualStudio` directory which you can use to
compile and run tests.
