<!--
    Page : Beta/Installer
    Author : Alexis CONIA
    Latest Update : 30/05/2018
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

This page describes how to install Kickle on a freshly new windows 10 install.

##Requirements

To install Kickle, the following requirements are required:

* **OS** : At least Windows 10 Version 1703, 1709 recommended (Enterprise or Edu)
* **Processor** : Intel i5 or i7 recommended
* **RAM** : At least 4 Gb, 8Gb Recommended
* **Disk** : At least 5Gb free
* Internet Connexion

All these requirements are checked during installation.

##OS Configuration
During installation, the installer will change Windows configuration to offer a "kiosk" experience.
The list below describes all the operation :

* Create an user "Kickle"
* Install Kickle Bootstrap Service
* Install Software requirements (Powershell Modules)
* Install Support Tools
* Configure Auto login with Kickle's credential
* Enable Windows Features : Device Lockdown
* Configure Logon Screen UI
* Configure Firewall
* Configure Keyboard Service
* Configure Custom Shell for Kickle
* Configure Power Settings
* Configure Windows Update
* Add tasks in Tasks Scheduler (Daily Reboot, Kickle Login)
* Hide Kickle User (not listed on login screen)
* Update Rights on Task manager and some others tools to avoid popup on this session.
* Disable First Logon Animation

All these steps are rollback when you uninstall kickle

##Windows Installation

You can start a clean install of Windows. 
The only point to notice and that is particularly important is about default user : Kickle user is creating during installation, so don't create an user with this username to avoid confusion.

You can add Kickle to your domain. Just be sure that your domain GPOs are not overriding the configuration above.

##Kickle Installation

The MSI guides you to each step. Two reboots are necessary during the process.
All components are downloaded and installed automatically after final reboot.

|Steps   |   |
|---|---|
|After Windows installation is terminated, start Kickle's MSI   |   |
|Click on next to validate the welcome menu   |![Step 1](/img/install-1.png)   |
|Requirements checks are done. You can continue, only if the necessary requirements are available.    | ![Step 2](/img/install-2.png)   |
|Validate the license and click on Install  |![Step 3](/img/install-3.png)   |
|The first part will copy files and activate Windows Features  |   |
|A reboot is asked to terminate windows features activation |   |
|After the reboot, log on the session that you used before. Installation will continue automatically |   |
|Final steps are executed. You can click on finish. |   |
|A popup asks you to reboot to terminate Kickle's installation. The system will restart automatically in kiosk mode and on the right user session |   |
|Just after reboot, session starts on cmd windows. After a quick delay, an automatic update is starting to download the latest version |   |

Today, we are not supporting to change the default installation location.

##Troubleshooting
If you encounter an error during installation, the installer will rollback all modifications.
You can also start the installation with logs by using the following command :

``` powershell
msiexec Kickle.deploy.msi /l*v log.txt
```