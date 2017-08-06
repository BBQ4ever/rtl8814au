# RTL8812AU/21AU and RTL8814AU linux driver with monitor mode and frame injection
Credit to astsam and ulli-kroll and the kali linux folks for porting this driver, the guide will help you make the AWUS 1900 Work in Fedora, it might work else where, but i can't garantee it.

### The drivers work and can capture WPA handshakes, which the previous one didn't work on my setup, i hope this helps others.

https://www.alfa.com.tw/products_show.php?pc=137&ps=246 (is the card, it's a sexy beast of a card)

The chipset driver is RTL8814AU

### for Fedora26
* sudo dnf install elfutils-libelf-devel
* git clone https://github.com/madmantm/rtl8814au
* make RTL8814=1
* sudo make RTL8814=1 install
* sudo modprobe 8814au

plug your adapter and everything should work.

### for Kali Linux
apt install realtek-rtl88xxau-dkms.

### configure monitormode
Note : airmon-ng doesn't work to make the card go in monitor mode you have to do it manually.

* sudo airmon-ng check kill
* sudo ifconfig wlan0 down
* sudo iwconfig wlan0 mode monitor
* sudo ifconfig wlan0 up


### to make aircrack-ng use the 5ghz bands
sudo airodump-ng -c 149 wlan0 -w psk --band a
