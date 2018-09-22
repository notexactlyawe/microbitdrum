Preparing Ubuntu for micro:bit C/C++ development
======================================

Pre-requisites
-------------

Following the instructions from the [Yotta docs](http://docs.yottabuild.org/#installing-on-linux), do the following:

```
sudo apt update && sudo apt install python-setuptools cmake build-essential ninja-build python-dev libffi-dev libssl-dev && sudo easy_install pip

pip install yotta
```

You then need to install `SRecord`, updated instructions [here](http://srecord.sourceforge.net/download.html):

```
sudo apt install srecord
```

The page linked tells you to add a repository from which to install `srecord` but that wasn't necessary for me. Of course, at the linked page there is also the option of building from source.


Setting up a project
--------------------

```
mkdir my_project
cd my_project
yotta init
```

This will then ask you a series of questions about the project that you are creating. You then need to configure the created project for micro:bit development as Yotta can be used for many different types of project.

```
yotta target bbc-microbit-classic-gcc
yotta install lancaster-university/microbit
```

The first line tells Yotta what platform and compiler we are using while the second downloads the `microbit` library from GitHub which makes using the hardware much easier.


Building
---------

If everything is set-up correctly and you have written some code inside the `source` directory, then you should be able to run:

```
yotta build
```

This will produce a `MYPROJECT-combined.hex` file in `my_project/build/bbc-microbit-classic-gcc/source`. The micro:bit has a nice feature where it emulates a USB drive when plugged into your computer. If you then drag this `.hex` file to the micro:bit "folder" it will flass your program to the board.

--------------

These instructions were heavily based off [this article on i-programmer.info](https://www.i-programmer.info/programming/hardware/9654-offline-cc-development-with-the-microbit-.html).  
The [micro:bit runtime docs](https://lancaster-university.github.io/microbit-docs/) are really good.
