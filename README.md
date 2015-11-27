Tiny Bluetooth Library
=============

This project aims to create Bluetooth GATT bindings for C++, Java and other
languages, using BlueZ over DBus. Most of the code is automatically
generated using gdbus-codegen, including a few additions to the default
behaviour, such that it also generates the C++ classes, which wrap the functions
normally generated by gdbus-codegen.

Using TinyB
============

TinyB requires CMake 3.1+ for building and requires GLib/GIO. It also requires BlueZ with GATT profile activated, which is currently experimental, so you might have to run bluetoothd with the -E flag.

~~~~~~~~~~~~~{.sh}
mkdir build
cd build
cmake ..
make
make install
~~~~~~~~~~~~~

The last command will create the include/ and lib/ directories with a copy of
the headers and library objects respectively in your build location. Note that
doing an out-of-source build may cause issues when rebuilding later on.

Our cmake configure has a number of options, *cmake-gui* or *ccmake* can show
you all the options. The interesting ones are detailed below:

Changing install path from /usr/local to /usr
~~~~~~~~~~~~~
-DCMAKE_INSTALL_PREFIX:PATH=/usr
~~~~~~~~~~~~~
Building debug build:
~~~~~~~~~~~~~
-DCMAKE_BUILD_TYPE=DEBUG
~~~~~~~~~~~~~
Using clang instead of gcc:
~~~~~~~~~~~~~
-DCMAKE_C_COMPILER=/usr/bin/clang -DCMAKE_CXX_COMPILER=/usr/bin/clang++
~~~~~~~~~~~~~
Cross-compiling on a different system:
~~~~~~~~~~~~~
-DCMAKE_CXX_FLAGS:STRING=-m32 -march=i586
-DCMAKE_C_FLAGS:STRING=-m32 -march=i586
~~~~~~~~~~~~~

To build documentation run 
~~~~~~~~~~~~~
doxygen Doxyfile
~~~~~~~~~~~~~