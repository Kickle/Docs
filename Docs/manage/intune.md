<!--
    Page : Manage/Manage Kickle with Microsoft Intune
    Author : Alexis CONIA
    Latest Update : 02/11/2017
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

Kickle is based on Windows 10 IoT Enterprise (formerly embedded). We update OS regularly.
We recommend also managing Windows on your side, particularly the updates.
If you have an internal WSUS server, you can integrate Kickle to AD ([more details](ad.md)) and apply updates automatically.
You can also use Microsoft Intune to facilitate remote management:

1. Start Kickle unit in [admin mode](admin-mode.md).
2. Start explorer and download Intune Agent from the portal [https://manage.microsoft.com](https://manage.microsoft.com).
3. Install agent from the administrator session and restart.
4. You can now manage updates and viruses from the portal.