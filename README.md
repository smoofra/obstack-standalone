
obstack-standalone
==================

This is just a standalone, portable version of [`obstack.h`][obstack] from the GNU C library.

## How to build

* Install [CMake][cmake] for your platform.   Probably this is `brew install cmake`, or `apt install cmake`, or something like that.

* build and install it

        cmake . -DCMAKE_INSTALL_PREFIX=/usr/local
        make
        make install

see also: [CMAKE_INSTALL_PREFIX][prefix]

## Or just compile it.

It's only one source file and one header.

    gcc -I. obstack.c tst-obstack.c -o tst-obstack

[obstack]: https://www.gnu.org/software/libc/manual/html_node/Obstacks.html
[cmake]: https://cmake.org/
[prefix]: https://cmake.org/cmake/help/latest/variable/CMAKE_INSTALL_PREFIX.html