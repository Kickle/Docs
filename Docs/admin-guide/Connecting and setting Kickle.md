<!--
    Page : Administration/KICKLE Configuration
    Author : Alexis CONIA
    Latest Update : 14/04/2017
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

### Connecting KICKLE

Each KICKLE is embedded with its own website and settings GUI. First, ensure that KICKLE is on a DHCP network. Then, make sure that your computer is on the same sub-network.

- Connect KICKLE to the screen's HDMI port.
- If the screen is a touchscreen, connect the touchscreen source to KICKLE via USB. If not, connect a USB mouse.
- Connect the camera and the microphone to the USB ports **at the back of KICKLE**.
- Start KICKLE by press the power button.

#### Setting Up KICKLE

The embedded website of KICKLE starts automatically.

Ask KICKLE support team to get the admin account and the password <http://support.KICKLE.com>.

You can change the password at any time (see chapter 10).

You can also browse to your KICKLE website (http://ip-address-of-KICKLE) from another computer on the same sub-network.

![Setting up 1] (/img/setting-up1.png)

Reconnect using the administrator account. Then, complete the fields in the Web GUI:

- The **username** is the SIP address.
- The **login** is the associated AD account.(if you use Skype for Business Online / Office 365, username and login are the same).
- The Exchange login is the associated AD account.(if you use Skype for Business Online / Office 365, leave these fields blank).
- The **Exchange login** is the associated AD account.(if you use Skype for Business Online / Office 365, leave these fields blank).

![Setting up 2] (/img/setting-up2.png)

Specify the type of network connection:

DHCP or fixed IP.

![Setting up 3] (/img/setting-up3.png)

!!! warning "Caution"
    If you choose fixed IP, you must ensure that KICKLE remains accessible. Changing the IP address takes effect immediately.

Type the **Exchange webservice** URL.

![Setting up 4] (/img/setting-up4.png) 

Configure proxy settings, if applicable.

![Setting up 5] (/img/setting-up5.png)

!!! note "Note"
    We strongly recommend you to bypass your proxy with a specific rule. Proxy configuration is very complex within a Skype for Business infrastructure.

Type the **NTP servers** if needed.

![Setting up 6] (/img/setting-up6.png)

You can change size of text, apps and other items and  event change KICKLE background picture.

![Setting up 7] (/img/setting-up7.png)

You will need to **Reboot** the KICKLE to apply the new configuration settings.

![Setting up 8] (/img/setting-up8.png)