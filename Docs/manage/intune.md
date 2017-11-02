<!--
    Page : Manage/Manage Kickle with Microsoft Intune
    Author : Alexis CONIA
    Latest Update : 02/11/2017
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

Kickle is based on Windows 10 IoT Enterprise (formerly embedded). We are updating OS regularly.
We recommend to also manage Windows on your side and more precisely updates. 
If you have an internal WSUS server, you can integrate Kickle to AD ([more details](ad.md)) and apply updates automatically.
You can also use Microsoft Intune to facilitate remote management :

1. Start Kickle in [admin mode](admin-mode.md)
2. Start explorer and download Intune Agent from the portal [https://manage.microsoft.com](https://manage.microsoft.com)
3. Install agent from administrator session and restart.
4. You can now manage updates and virus from the portal