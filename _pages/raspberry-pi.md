---
title: "Setup on a Raspberry Pi"
permalink: /raspberry-pi/
excerpt: "Setup on a Raspberry Pi"
last_modified_at: 2020-05-05T14:00:00+01:00   #Please Update, The +00:00 is the Time Zone difference
redirect_from:
  - /theme-setup/
toc: true

# Date formatting & Date Parsing - Let formatting and parsing date expressed in ISO8601 format.
# Can be obtained from https://dencode.com/en/date
# ---- Defined ----
# YYYY-MM-DD'T'hh:mm:ssTZD (e.g. 2015-12-11T20:28:30+01:00)
# YYYY = four-digit year
# MM = two-digit month (01=January, etc.)
# DD = two-digit day of month (01 through 31)
# hh = two digits of hour (00 through 23) (am/pm NOT allowed)
# mm = two digits of minute (00 through 59)
# ss = two digits of second (00 through 59)
# TZD = time zone designator (Z or +hh:mm or -hh:mm)
---

## Setup on a Raspberry Pi
We recommend to initially run your bot in a local environment on your laptop before you run the translator on a Raspberry Pi. The local setup allows you to get familiar with the setup and the settings.

The following description allows a headless configuration. Only a network connection is required. This description is explicitly for running the bot on a Raspberry Pi 4, but the setup should be similar for earlier version.

Recommendation: run it locally first before putting the code on pi. Easier to ensure that .env variables are setup correctly.

#### 1. Write Raspbian on your SD card
Download the minimal image of Raspbian (https://www.raspberrypi.org/downloads/raspbian/). This setup is based on Raspbian Buster Lite, July 2019.

Use balenaEtcher(https://www.balena.io/etcher/) to write the image on your SD card.

For more Information: See https://www.raspberrypi.org/documentation/installation/installing-images/README.md

#### 2. Enable SSH
Enable SSH by placing a file named “ssh” (without any extension) onto the boot partition of the SD card.

#### 3. Start and Login
* Pop your prepared SD card, power and a network cable into the Pi.
* Find your Pi's IP Address. Check your Router's DHCP allocation table or use a mobile app like Fing (https://play.google.com/store/apps/details?id=com.overlook.android.fing) to find the IP of Pi.
* Install WinSCP and Putty on your Laptop.
* Start Putty and login into your Pi. Username: pi, PW: raspberry. Change your password with 'passwd'.

#### 4. Initial Setup
* Type `raspi-config` and change your locales
* Update the package lists from repositories: `sudo apt-get update`
* Update your repositories: `sudo apt-get dist-upgrade`

#### 5. Install node and npm
The fastes way to install the current node and npm versions (https://nodejs.org/en/download/) was to follow the description from nodesource (https://github.com/nodesource/distributions/blob/master/README.md):
* Get the source: `curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`
* Install: `sudo apt-get install -y nodejs`
* Check version: `node -v` and `npm -v`

#### 6. Get the code
It is recommend to install git and pull from your fork or main:
* Install git: `sudo apt-get install git`
* Create the folder for the source: `mkdir Rita`
* Clone the repository: `git clone https://github.com/ZyC0R3/RitaBot.git`
* Checkout the branch you need: `git checkout --track origin/1.1.7`

Alternative: move the source code with WinSCP from your local environment to the Pi.

#### 7. Install the database
Install sqlite3 with `sudo apt-get install sqlite3`.

Create an empty database file (`sqlite3 database.db`)and call `.tables`)

#### 8. Copy your .env
Use WinSCP to copy your .env file from your local environment to the Pi.

#### 9. Run the code
* Install gulp is installed: `sudo npm install -g gulp` (not sure if still necessary)
* Make sure you are in the Rita folder
* Get and install all packages of RITA: `npm install`
* Build the code: `npm run-script build`
* Start the bot: `npm run-script start`

#### 10. Autostart
There are different ways to make the bot initialize at startup. The following description is based on `init.d` and `update-rc.d`:
* Create a `init.d` script: Edit the script template in `.pi/translate_bot` if necessary and copy it to the folder `/etc/init.d/` with `sudo mv .pi/translate_bot /etc/init.d/.`
* Make the file executable: `sudo chmod +x /etc/init.d/translate_bot`
* Update the system script links: `sudo update-rc.d translate_bot defaults`
* Now, you can interact with the bot service with commands `sudo service translate_bot start`,  `sudo service translate_bot status` and `sudo service translate_bot stop`
* The logging will be in `/var/log/translate_bot.err` and `/var/log/translate_bot.log`
* Reboot and hope everything is running smooth: `sudo reboot`
* Enjoy (or return to step 4 in [Setting up a New Bot](#new-bot) if you haven't done yet)

