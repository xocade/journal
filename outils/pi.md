# Setting Up Raspberry Pi for iPad Through USB-C

1. [Download](https://www.raspberrypi.com/software/) Raspberry Pi OS
   `sudo apt install rpi-imager` 

2.  Hostname: F5920

3. ssh to the Raspberry Pi.

## Ethernet Over USB-C
4. Adjust `/boot/config.txt`  file. Add this line at the bottom:
   ```shell
   dtoverlay=dwc2,dr_mode=peripheral
```

5. Adjust the `/boot/cmdline.txt` file. Add a new line below `console=serial0`
   ```shell
   modules-load=dwc2,g_ether
```

### USB-C Network Configuration
6. Create a file:
   ```bash
   sudo nvim /etc/network/interfaces.d/usb0
```

Fill the `usb0` file with the following:
```bash
auto usb0
allow-hotplug usb0
iface usb0 inet static
        address 10.55.0.1
        netmask 255.255.255.248
```

### Handing of IP Address
7. Install dnsmasq:
```bash
sudo apt install dnsmasq
```

8. Create `/etc/dnsmasq.d/usb0` with the following content:
```bash
interface=usb0
dhcp-range=10.55.0.2,10.55.0.6,255.255.255.248,1h
dhcp-option=3
leasefile-ro
```

9. Add the line `denyinterfaces` at the bottom of `/etc/dhcpcd.conf`.
10.  Shutdown the Pi and connect to iPad.


Sources:
1. https://www.hardill.me.uk/wordpress/2019/11/02/pi4-usb-c-gadget/ 