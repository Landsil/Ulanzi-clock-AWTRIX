# Ulanzi-clock-AWTRIX
Those are my config notes for setting up Ulanzi LED clock with AWTRIX host on Raspberry PI

If this page is mostly empty then congratulations, you are waaaay to early. Please come back in a day of two.


## Links
1. [Ulanzi Smart Pixel Clock](https://www.ulanzi.com/products/ulanzi-pixel-smart-clock-2882)
2. [AWTRIX docs](https://awtrixdocs.blueforcer.de/#/en-en/host?id=quickstart)
3. Ulanzi firmware update (not needed but would be nice, ping me if you find it)

# Initial setup
You will need to install a host app on a device. I think hosting is on our PC is not the best idea so  I'm doing Raspberry PI. 
Docker would probably be best but I may not bother with that.

## Raspberry PI setup
1. You can grab official imager from https://www.raspberrypi.com/software/
2. User CTRL + SHIFT + X to get advanced options and configure things like `hostname`, `SSH` and `WiFi` in advance. 
3. grab `Raspberry Pi OS Lite` and instal it all
4. When PI is up and running find in on your local network and give it static IP to avoid issues later.
5. SSH into a pi with credentials you gave it via `ssh [username]@[IP address]`, if you are on Windows just install Linux subsystem :P
   
move to next step

## AWTRIX host setup
This is all done on your PI via SSH
1. run `wget -N https://blueforcer.de/awtrix/awtrix.sh ; sudo sh awtrix.sh`
2. Try to access interface via `http://awtrix_ip:7000`
3. If that works setup up something (add info here)

Move to the next step

## Ulanzi clock setup
Assuming you've read manual for the clock and it's connected to your network.
1. Go to `http://clock.local` to get the local interface (yes, http ;( )
2. Move to 2nd page "Common Settings" and expand "Awtrix Simulator" option
3. Put your Pi's static IP and `7000`, click save.
4. Works?
