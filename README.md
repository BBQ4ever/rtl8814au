# RTL8812AU/21AU and RTL8814AU linux driver with monitor mode and frame injection
Credit to astsam and ulli-kroll for porting this driver, the guide will help you make the AWUS 1900 Work in Fedora, it might work else where, but i can't garantee it.

https://www.alfa.com.tw/products_show.php?pc=137&ps=246 (is the card, it's a sexy beast of a card)

The chipset driver is RTL8814AU

### for Fedora26
* sudo dnf install elfutils-libelf-devel
* git clone https://github.com/madmantm/rtl8812au
* make RTL8814=1
* sudo make RTL8814=1 install

### for Kali Linux
apt install realtek-rtl88xxau-dkms (which right now works really well)

airmon-ng doesn't work to make the card go in monitor mode you have to do it manually.
you can do the airmon-ng check kill to kill all conflicting processes.

### configure monitormode
* sudo ifconfig wlan0 down
* sudo iwconfig wlan0 mode monitor
* sudo ifconfig wlan0 up


### to make aircrack-ng use the 5ghz bands
sudo airodump-ng -c 149 wlan0 -w psk --band a
