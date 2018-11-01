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
cmake ../
make
sudo make install
sudo ldconfig
```
* tutorial for stratux: https://www.reddit.com/r/stratux/comments/3v9vsr/howto_building_stratux_from_source/ (excluding libsrtlsdr part, which points to incorrect repo)
* kiosk mode: ...
