# Raspberry with Stratux 

Used tutorials:

* standard installation of Raspbian with X11 (ssh and vnc enabled, connected to home wifi)
* go installation: https://gist.github.com/simoncos/49463a8b781d63b5fb8a3b666e566bb5
* two new lines added manually to ~/.profile

```
export PATH=$PATH:/usr/local/go/bin
export GOROOT=/usr/local/go
```

* librtlsdr installation: http://podtynnyi.com/2015/10/11/installing-rtlsdr-on-raspberry-pi-2/
* tutorial for stratux: https://www.reddit.com/r/stratux/comments/3v9vsr/howto_building_stratux_from_source/ (excluding libsrtlsdr part)
* kiosk mode: ...
