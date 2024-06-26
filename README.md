The program works in the AnotherTerm application on the Android platform. The program creates a virtual serial port in the /port folder, which can be referenced by programs capable of handling serial ports available in the proot system. The program is under development, so errors may occur. Currently, these devices are supported:

FTDI (Tested and working)

PL2303 (Tested and working)

CH341 (Tested and working)

CP210X (Tested and working)

CDC-ACM (Tested and working)

https://green-green-avk.github.io/AnotherTerm-docs/installing-linux-under-proot.html#main_content

The program was developed on the Kali Linux distribution, so it is most reliably run on this system.

The modified libusb is essential for operation:

https://green-green-avk.github.io/AnotherTerm-docs/installing-libusb-for-nonrooted-android.html#main_content

Two files were created: one is vserial, and the other is serial_ioctl_wrapper.so.

The vserial works on its own, for example, with screen or minicom programs.

The serial_ioctl_wrapper.so is necessary if we want to use programs that attempt to write or read serial port settings via ioctl, for example, any program written with the pyserial module.

Copy the vserial program to the /usr/bin folder.
Copy the serial_ioctl_wrapper.so file to the /usr/lib folder.

For easier operation, modify the ~/.bashrc file by adding this line:

export LD_PRELOAD=/usr/lib/serial_ioctl_wrapper.so

If we start the vserial program with the "vserial &" command, we can still use the given terminal window, and we can also manage the ttyUSB0 created in the /port folder from other terminal windows while the program is running. To stop the program, use the "killall vserial" command or in the terminal window where it is running, press CTRL+C after the "fg" command.


The pogram in action:



https://github.com/9hm2/AnotherTerm_SerialDriver_ttyLike/assets/25800553/8eb0258d-4cab-486d-9056-be84e9875a65





I am developing the program for my own use. I welcome feedback and suggestions, but I have minimal time for development.

