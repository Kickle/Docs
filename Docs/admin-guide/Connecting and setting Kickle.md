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

Each Kickle embed its own website and settings GUI. First, ensure that Kickle is on a DHCP network. Then, make sure that your computer is on the same sub-network.

- Connect KICKLE to the screen's HDMI port.
- If the screen is a touchscreen, connect the touchscreen source to Kickle via USB. If not, connect an USB mouse.
- Connect the camera and the microphone to USB ports **at the back of Kickle**.
- Start KICKLE by pressing the power button.

#### Setting Up Kickle Using First Time Configuration

Before starting the configuration, make sure Kickle requirements are met.

To start configuration, press the configuration icon.

![fisrtconfig] (/img/1stConfig1.png)

First, you'll need to choose your preferred language setting, keyboard language layout and Kickle's time zone.

!!! Information

    - Kickle provides 3 differents languanges (English, French and German).

    - The next button will turn bold once you have selected all the informations.

![firstconfig] (/img/1stConfig2.png)

Second step, you can select the network configuration, you can set **dynamic** or **static** connection.

!!! Information
    If you set it as a static connection, be sure the ip address allows to connect to the internet.

![firstconfig] (/img/1stConfig3.png)

Here, if your internet connection requires a proxy, you can enable this feature.

!!! Information
    We strongly recommend you to bypass your proxy with a specific rule. Proxy configuration is very complex within a Skype for Business infrastructure.

![firstconfig] (/img/1stConfig4.png)

Here, you must fill out Skype authentication. Skype default setting is Office 365, but if you need to configure it with an on-prem account, be sure to uncheck **SKYPE is Office 365**.

!!! Information
    Press the **Test** icon to process test connections. If the test fails, we advise you to check the authentication account whether it has been activated or not and we also suggest that to check network connection.

    Once you have **OK connection**, press the next button to continue.
![firstconfig] (/img/1stConfig5.png)

!!! Information

    - Office 365 EWS URL address:
      Type or Copy--> https://outlook.office365.com/EWS/Exchange.asmx <--end of copy.

    - How to find EWS URL address on on-premise server :
      Open the Exchange Management Shell on the Exchange server
      Type or copy--> ***Get-WebServicesVirtualDirectory |Select name, *url* | fl*** <--end of copy.
![firstconfig] (/img/1stConfig6.png)

Here, you can select the display scaling that your kickle screen use and turn screen off features. 

!!! Information

    - Kickle is compatible with any kind of screen whether if this touchscreen panel or non touchscreen panel. The best configuration is full-HD or 4K touchscreen

    - The default value of turn screen off features is 0.

![firstconfig] (/img/1stConfig7.png)

Here, you can add local NTP server and enable icmp request for your Kickle device.

![firstconfig] (/img/1stConfig8.png)

Here, you can customize the mail invitation template.

![firstconfig] (/img/1stConfig9.png)

**Congratulation!**

To complete the configuration, press the reboot icon to apply the changes.

![firstconfig] (/img/1stConfig10.png)

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