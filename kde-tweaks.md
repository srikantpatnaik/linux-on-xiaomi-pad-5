# Tuning the Plasma Desktop 

*  Wait around 80s for the touch to work then try clicking the session selector 
   and change it to `Plasma X11`. The default `Wayland` session tend to crash the plasmashell and it
   also has touch issues.

* Connect a bluetooth keyboard(recommended) and mouse as soon as you login, connect to Wifi, change the date to fetch from NTP

* Change the default password

* Change the system font size to 13 or so, increase the display scaling to 125%, and change the theme to Dark (as you may like)

* Create profile in Konsole and change the font, size, background etc 

* Change the sleep time to 1 min in power settings to save as much power as possible

* Edit the repositories `sudo vi /etc/apk/repositories` and comment the postmarketos, change the aplinelinux repositories
  to v3.18.
  ```
  http://dl-cdn.alpinelinux.org/alpine/v3.18/main
  http://dl-cdn.alpinelinux.org/alpine/v3.18/community
  ```
* `sudo apk update && sudo apk upgrade`

* Now install your favorite packages, say
  `sudo apk add htop vim git chromium`

