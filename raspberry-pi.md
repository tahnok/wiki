# Headless Setup

Download latest image: https://www.raspberrypi.org/downloads/raspbian/

Flash image (Etcher seems to work nicely)

Create a file in boot called `wpa_supplicant.conf` with network info like

```
network={
    ssid="SSID"
    psk="password"
    key_mgmt=WPA-PSK
}
```

Create an empty file called `ssh`

## Webcam setup

Using the `motion` package from here: https://learn.adafruit.com/cloud-cam-connected-raspberry-pi-security-camera/dropbox-sync

