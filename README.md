# Raspberry with Stratux 

Used tutorials:

* standard installation of Raspbian with X11 (ssh and vnc enabled, connected to home wifi)
* go installation: https://gist.github.com/simoncos/49463a8b781d63b5fb8a3b666e566bb5
* two new lines added manually to ~/.profile

```
export PATH=$PATH:/usr/local/go/bin
export GOROOT=/usr/local/go
```

* librtlsdr installation: 
https://github.com/cyoung/stratux/issues/628 (solution from comment: scottbyrns commented on 25 Jun)
https://github.com/jpoirier/librtlsdr
```
sudo apt-get install gqrx-sdr
sudo apt-get purge librtlsdr0 librtlsdr-dev gr-osmosdr
git clone https://github.com/jpoirier/librtlsdr.git
cd librtlsdr/
mkdir build
cd build
cmake ../ -DINSTALL_UDEV_RULES=ON -DDETACH_KERNEL_DRIVER=ON
make
sudo make install
sudo ldconfig
```
* wiringPi (using for as original repo does not allow to build static)

```
git clone https://github.com/BPI-SINOVOIP/BPI-WiringPi2
cd WiringPi/wiringPi 
make static 
sudo make install-static
```


* tutorial for stratux: https://www.reddit.com/r/stratux/comments/3v9vsr/howto_building_stratux_from_source/ (excluding libsrtlsdr part, which points to incorrect repo)
```
export CGO_CFLAGS_ALLOW=-L/root/stratux
```

* kiosk mode: https://blog.gordonturner.com/2017/07/22/raspberry-pi-full-screen-browser-raspbian-july-2017/
```
apt-get install hostapd
apt-get install dhcpd
```

* single dongle config: /etc/stratux.conf (disabled uat)
```
{
  "UAT_Enabled": false,
  "ES_Enabled": true,
  "Ping_Enabled": false,
  "GPS_Enabled": true,
  "BMP_Sensor_Enabled": true,
  "IMU_Sensor_Enabled": true,
  "NetworkOutputs": [
    {
      "Conn": null,
      "Ip": "",
      "Port": 4000,
      "Capability": 5,
      "MessageQueueLen": 0,
      "LastUnreachable": "0001-01-01T00:00:00Z",
      "SleepFlag": false,
      "FFCrippled": false
    }
  ],
  "SerialOutputs": null,
  "DisplayTrafficSource": false,
  "DEBUG": false,
  "ReplayLog": false,
  "AHRSLog": false,
  "IMUMapping": [
    -1,
    0
  ],
  "SensorQuaternion": [
    0,
    0,
    0,
    0
  ],
  "C": [
    0,
    0,
    0
  ],
  "D": [
    0,
    0,
    0
  ],
  "PPM": 0,
  "OwnshipModeS": "F00000",
  "WatchList": "",
  "DeveloperMode": false,
  "GLimits": "",
  "StaticIps": [],
  "WiFiSSID": "stratux",
  "WiFiChannel": 1,
  "WiFiSecurityEnabled": false,
  "WiFiPassphrase": ""
}
```
