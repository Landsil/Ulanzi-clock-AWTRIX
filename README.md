# Ulanzi-clock-AWTRIX
Those are my config notes for setting up Ulanzi LED clock with AWTRIX host on Raspberry PI

## Links
1. [Ulanzi Smart Pixel Clock](https://www.ulanzi.com/products/ulanzi-pixel-smart-clock-2882)
2. [AWTRIX docs](https://awtrixdocs.blueforcer.de/#/en-en/host?id=quickstart)
3. Ulanzi firmware update (not needed but would be nice, ping me if you find it)

# Initial setup
You will need to install a host app on a device. I think hosting is on our PC is not the best idea so  I'm doing Raspberry PI. 
Docker would probably be best but I may not bother with that.

## Raspberry PI setup
1. You can grab official imager from https://www.raspberrypi.com/software/
2. Use CTRL + SHIFT + X to get advanced options and configure things like `hostname`, `SSH` and `WiFi` in advance. (or click settings button)
3. grab `Raspberry Pi OS Lite` and instal it all
4. When PI is up and running find in on your local network and give it static IP to avoid issues later.
   1. You can do this on PI but it may conflict with other settings.
5. SSH into a pi with credentials you gave it via `ssh [username]@[host].local`, if you are on Windows just install Linux subsystem :P
   1. You can also ask PI for it's current IP via `hostname -I`
6. `sudo apt-get update` & `sudo apt-get upgrade`
   
move to next step

## AWTRIX host setup
This is all done on your PI via SSH
1. run `wget -N https://blueforcer.de/awtrix/awtrix.sh ; sudo sh awtrix.sh`
   1. This will take some time
2. Get IP via `hostname -I` if you haven't already.
3. Try to access interface via `http://awtrix_ip:7000`
   1. You may want to add password right away at `http://awtrix_ip:7000/pages/hostsettings.html`

Move to the next step

## Ulanzi clock setup
Assuming you've read manual for the clock and it's connected to your network.
1. Go to `http://clock.local` to get the local interface (yes, http ;( )
2. Move to 2nd page "Common Settings" and expand "Awtrix Simulator" option
3. Put your Pi's static IP and `7001`, click save. (yes, `7001`, not `7000`)
4. This should now work


## Bonus - add 2nd WiFi via SSH
1. `sudo nano /etc/wpa_supplicant/wpa_supplicant.conf`
2. add
```bash
network={
    ssid="network name"
    psk="wifi password"
    }
```
3. Exit with  `CTRL + X` and then chose `Y`, `Enter`
