<!--
    Page : Beta/Installer
    Author : Alexis CONIA
    Latest Update : 30/05/2018
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

This page describes how to install Kickle on a newly windows 10 install.

##Requirements

To install Kickle, you must check off the following requirements:

* **OS** : At least Windows 10, Version 1703 (1709 recommended), either Enterprise or Edu
* **Processor** : Intel i5 (i7 recommended)
* **RAM** : At least 4 GB (8GB recommended)
* **Disk** : At least 5GB of available space
* Internet Connexion

All of these requirements are verified during installation.

##OS Configuration
During installation, the installer will change the Windows configuration to offer a "kiosk" experience.
The list below details the entire operation :

* Create user: "Kickle"
* Install Kickle Bootstrap Service
* Install Software requirements (Powershell Modules)
* Install Support Tools
* Configure auto login using Kickle's credential
* Enable Windows Features : Device Lockdown
* Configure Login Screen UI
* Configure Firewall
* Configure Keyboard Service
* Configure Custom Shell for Kickle
* Configure Power Settings
* Configure Windows Update
* Add tasks in Tasks Scheduler (Daily Reboot, Kickle Login)
* Hide Kickle User (not listed on login screen)
* Update Rights on Task manager as well as several others tools to avoid popups during the session.
* Disable First Login Animation

All of these steps are rolled back when you uninstall kickle

##Windows Installation

You may start a clean install of Windows. The only point to keep in mind, which is of particular importance, concerns the default user: a “Kickle” user is created during installation, so be sure not to create another user with this same username in order to avoid confusion.

You may add Kickle to your domain. Just be sure that your domain’s GPOs are not overriding the above configuration.

##Kickle Installation

The MSI guides you through each step. Two reboots are necessary during this process. 
All components are automatically downloaded and installed following the final reboot.

|Steps   |   |
|---|---|
|After the Windows installation has completed, you can start the MSI for Kickle.   |   |
|Click on “Next” to validate the welcome menu.   |![Step 1](/img/install-1.png)   |
|Requirement checks are completed. You can only continue if the necessary requirements are confirmed.   | ![Step 2](/img/install-2.png)   |
|Validate the license and click “Install”.  |![Step 3](/img/install-3.png)   |
|The first part will copy the files and activate Windows Features.  |![Step 4](/img/install-4.png)    |
|You will be prompted to reboot in order to complete activation of the Windows features.|![Step 5](/img/install-5.png)     |
|After rebooting, log into the same session you used previously. Installation will continue automatically. |   |
|The final steps are executed. You can click on “Finish”. |![Step 6](/img/install-6.png)     |
|You will be prompted by a popup message to reboot again in order to complete the installation of Kickle. The system will restart automatically in kiosk mode and logged into the correct user session. |![Step 7](/img/install-7.png)    |
|Right after the reboot, the session will open and check updates. After a brief delay, an automatic update will begin downloading the latest version.| ![Step 8](/img/updates.png)  |

As of today, we are not supporting a change to the default installation location.

##Troubleshooting
If you encounter any error during installation, the installer will roll back all modifications. 
If necessary, you can also start the installation with logs by using the following command:

``` powershell
msiexec Kickle.deploy.msi /l*v log.txt
```