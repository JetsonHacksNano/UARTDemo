# UARTDemo
UART Demo Code

This is currently a simple Python 3 script to interface with the UART on the J41 header of the NVIDIA Jetson Nano Developer Kit.

<h4>Before You Start</h4>
The stock Jetson Nano starts a console on the ttyTHS1 serial port at startup through a service. The script that starts the service is nvgetty.sh which launches getty. The script is located in /etc/systemd. While this does not conflict with the script presented here, consider disabling the console if you are using the serial port to avoid conflicts. Note that normal udev rules will be overridden by the console while the service is running. To disable the console:

```
$ systemctl stop nvgetty
$ systemctl disable nvgetty
$ udevadm trigger
# You may want to reboot instead
```

<h4>The Demo Script</h4>

The script opens up the serial port ( /dev/ttyTHS1 ), writes a simple header on the serial port, and then will echo any characters it receives from the serial port back. When the script is terminated with ^C, the script will close the port.

One easy way to use the script is to connect the Jetson Nano to a PC/Mac/Linux box via a TTL to USB cable. The Jetson Nano signal is 3.3V. Run a serial tty program on the PC to interface with the serial port, and then interact with the Jetson Nano.

The script requires py-serial. To install py-serial:

```
$ sudo apt-get install python3-serial

```
Then to run the script:

```
$ sudo python3 uart_example.py

```

<h3>Notes</h3>

<b>Initial Release October 2019</b>
<ul>
  <li>L4T 32.2.1/JetPack 4.2.2</li>
  <li>Python 3</li>
  </ul>

