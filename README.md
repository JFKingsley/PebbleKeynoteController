libpebble
=========
Interact with Keynote using your Pebble from OSX.

## Warning and Complications

* Supported OSes are OSX 10.8 and 10.7
* Detailed Lightblue-0.4 installation instructions for earlier version of OSX (10.6) and other OSes can be found [here](http://lightblue.sourceforge.net/#downloads)


##1. Install Dependencies

You will require `python 2.7` to operate libpebble. It can be installed [here](http://www.python.org/download/releases/2.7/)
* `Pyserial`will also be required, is can be installed via [pip](https://pypi.python.org/pypi/pip)

###a. Additional Dependencies

Installing Lightblue-0.4 in OSX will require the following be installed:
* `PyObjC` which can be installed via [pip](https://pypi.python.org/pypi/pip)
* `Xcode 2.1 or later` to build LightAquaBlue framework
* Note that you may have to run libpebble as root with `sudo python pebble.py` in Debian


##2. Install Libpebble and Lightblue

* To install libpebble, clone the current libpebble with lightblue support from `git@github.com:pebble/libpebble.git` to a location of your choosing
* To install lightblue clone `lightblue-0.4` from `https://github.com/pebble/lightblue-0.4` and then:
    * `cd lightblue-0.4`
    * `sudo python setup.py install`


##3. Testing the Connection
Note: you should have your bluetooth module enabled before continuing

###a. OSX
When using libpebble on OSX, it is recommended that `--lightblue` be utilized.

#####Using libpebble with --lightblue on OSX
* First install the OSX dependencies, general dependencies and lightblue
* From the `libpebble` folder, execute the following: `./p.py --lightblue --pair get_time keynote`
* Note that if no `--pebble_id` is specified before the command, you are provided with a GUI selection tool.
* Note that if a MAC address is supplied, initialization time is reduced. 
    * For example:  `./p.py --pebble_id 00:11:22:33:44:55:66 --lightblue get_time keynote`
      where `00:11:22:33:44:55:66` is the Pebble's MAC Address, viewable on the Pebble from `settings`-->`about`
* You can obtain your pebble's MAC address after a successful connection in the libpebble stdout debug logs
* The `--pebble_id` can also be the 4 letter friendly name of your pebble but this will require that the Pebble is broadcasting.
* It is also possible to set the PEBBLE_ID environment variable as well:

      export PEBBLE_ID="00:11:22:33:44:55:66"
      ./p.py --lightblue get_time keynote

#####Using libpebble without --lightblue on OSX (MAY CAUSE KERNEL PANICS)

* Pair your Pebble to your computer and make sure it's setup as a serial port. For example it could be exposed as `/dev/tty.Pebble123A-SerialPortSe`. You can accomplish this by using OSX's pairing utility in `System Preferences` --> `Bluetooth` -> `+` --> selecting your pebble `Pebble XXXX` then confirming the pairing code on the Pebble.
* Once you're paired and the serial port is setup, you can execute commands without the `--lightblue` flag, just ensure that the `--pebble_id` is the 4 letter friendly name of your Pebble, `123A` for example.
* A command to get the time might be: `./p.py --pebble_id 123A get_time keynote`

Functionality
-------------

The following are currently supported:

* Sends your pebble a notification when it connects.
* Can go forwards and backwards in slides.
* Shows details on the slides in the Music app.
* To use it you must have the music app open.
* The middle button (play/pause) will act as an escape key from the presentation
* In the Music app you can see your presentations Title, Author, and what slide you are currently on.