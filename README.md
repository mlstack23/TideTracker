# TideTracker
Track tides and weather at local beach

![B1D97707-9A84-400F-BD0E-3E7C76CE60D2_1_201_a](https://user-images.githubusercontent.com/25852077/117740617-ce73b180-b1ce-11eb-9f86-58120becb931.jpeg)

For the full story and build, visit https://www.hackster.io/ssbaker/e-ink-tide-and-weather-tracker-21447b 


## Requirements

### Enable SPI
`sudo raspi-config`

Navigate to Interface-->SPI and enable SPI, then reboot

### Install System Dependencies
`sudo apt-get install libatlas-base-dev python3-pip libxslt-dev libopenjp2-7 libtiff5`

### Install Python Dependencies
`pip3 install -r requirements.txt`

### Setup systemd service

Create the file at `/etc/systemd/system/tidetracker.service` with the following contents
```
[Unit]
Description=tidetracker.service
After=network.target

[Service]
WorkingDirectory=/home/pi/TideTracker/
User=pi
ExecStart=/usr/bin/python3 /home/pi/TideTracker/TideTracker.py
Restart=always

[Install]
WantedBy=multi-user.target
```

### Enable systemd service
`sudo systemctl enable tidetracker.service`

### Reboot