# Raspberry-Pi-Headless-Setup-via-Network-Manager

WiFi Configuration via Network manager on RPi

## Installation

1. Update your sources.

   ```
   $ sudo apt update & sudo apt upgrade
   ```

2. Install NetworkManager,This will install a number of other packages as well.

   ```
   $ sudo apt install network-manager
   ```

3. Remove these packages as suggested here:

   ```
   ### https://raspberrypi.stackexchange.com/a/73816
   Otherwise the wifi device appears as unavailable to nmcli.

   $ sudo apt purge openresolv dhcpcd5
   ```

4. Reboot, sudo reboot now.

   ```
   $ sudo reboot
   ```

5. Check network connection status and verify that the inet addr is empty.
   ```
   $ ifconfig wlan0
   ```

## Usage:

Start using nmcli by scanning the manual, man nmcli.

```
$ nmcli dev help.
```

Displays a table. Notice that wlan0 is disconnected

```
$ nmcli dev status
```

Displays a table of available wifi access points

```
$ nmcli dev wifi
```

Connect to a WiFi network.

```
$ nmcli device wifi connect <SSID> password <Secrete>
```

Connects may be added using nmcli, for example nmcli con add con-name HOMEOFFICE ifname wlan0 type wifi ssid MYSSID, but I prefer to use nmtui.

Provides a text user interface that allows easy creation of wifi connection.

```
$ sudo nmtui
```

Edit a connection. Add  wifi.
Give your connection a name and set the fields needed for your access point.
If you provided all the settings correctly and set the connection to connect automatically, it might already have connected. Check with ifconfig wlan0.

Notice the changed out put from nmcli dev status and nmcli dev wifi.

Show active connections with nmcli con show -a.

Take down a connection with sudo nmcli con down connection_name and bring it back up with sudo nmcli con up connection_name.
