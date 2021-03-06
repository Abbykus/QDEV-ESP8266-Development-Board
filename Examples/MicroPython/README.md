## MicroPython ON THE ESP8266

The QDEV-ESP8266 is capable of running the MicroPython interpreted language. 
MicroPython is a compact Python interpreter that can run on embedded platforms with very limited memory. Using the familiar Python programming language you can talk to hardware and control it, much like controlling hardware with an Arduino or other embedded boards. The QDEV ESP8266 board makes it easy to get started using MicroPython and thanks to recent contributions to MicroPython, you can turn a QDEV-ESP8266 into a MicroPython device.

Please read [MicroPython language and implementation](https://docs.micropython.org/en/latest/reference/index.html) for more information.

### INSTALL MICROPYTHON 

To install MicroPython firmware on the QDEV-ESP8266 board see [Quick reference for the ESP8266](https://docs.micropython.org/en/latest/esp8266/tutorial/intro.html#intro).

Also see [MicroPython for the ESP8266](http://www.micropython.org/download/?port=esp8266) for the latest firmware release.

Once you have installed MicroPython on the QDEV ESP8266 board you can connect to the board via the Serial monitor in your development environment or a serial terminal emulator such as [screen](https://linuxhint.com/screen-linux/) for Linux. You should expect to see a '>>>' prompt indicating the interactive mode where you can enter MicroPython commands or entire scripts manually.

### INSTALL AMPY
To aid script development for the QDEV ESP8266 module, you can install the AdaFruit MicroPython Tool ***ampy*** on your host PC which is a utility to interact with a MicroPython board (QDEV ESP8266) through the serial connection.

***Ampy*** is a simple command line tool to manipulate files and run code on a MicroPython board. With ***ampy*** you can send files from your computer to the board's file system, download files from a board to your computer, and even send a Python script to a board to be executed.

Visit [AdaFruit Ampy](https://pypi.org/project/adafruit-ampy/) for instructions on installation and use of ***ampy***. 

### RUN A PYTHON SCRIPT
Using the above utility ***Ampy*** you can execute python scripts from the host PC.
A very simple script to blink the on-board LED can be run as follows:
- Copy the main.py and blink.py files to a folder on the host PC. 
- Open a terminal on the host PC and navigate to the above folder.
- Type one of the following (depending on your OS):

***ampy --port /dev/ttyUSB0 run blink.py***   *(Linux or MacOS)*

***ampy --port COM5 run blink.py***   *(Windows)*

**NOTE:** Your USB Serial port may be different than shown.

Now you should see the ESP-12F LED blink once per second for 30 seconds.

### AUTO-RUN PYTHON SCRIPTS
Python scripts can be automatically executed after Micropython boots.
MicroPython executes two files after booting:
- ***boot.py***   This file contains setup information and normally does not need modification.
- ***main.py***   If this file exists it will be executed after boot.py. 

Your Python application code should be placed in the ***main.py*** file

Use ***Ampy*** to transfer main.py to the MicroPython board:

***ampy --port /dev/ttyUSB0 put main.py***    *(Linux / MacOS)*

***ampy --port COM5 put main.py***    *(Windows)*

To confirm that the file has been saved to the MicroPython board type:

***ampy --port /dev/ttyUSB0 ls***   *(Linux / MacOS)*

***ampy --port COM3 ls***   *(Windows)*

Now when the board is powered up or reset, the Python script in *main.py* file will be executed.

You can remove the *main.py* by typing:

***ampy --port /dev/ttyUSB0 rm main.py***

## microPy-IDE
As an alternative to running the command line *Ampy* please see the **microPy-IDE** in the Abbykus repositories. This development tool is specifically designed to create and test microPython scripts on various boards that support microPython.






