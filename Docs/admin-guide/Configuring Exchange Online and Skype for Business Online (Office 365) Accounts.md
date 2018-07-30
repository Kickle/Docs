<!--
    Page : Administration/Online
    Author : Alexis CONIA
    Latest Update : 27/03/2016
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->
### Creating and Configuring a Room Mailbox Account for Exchange Online (Office 365)

!!! Info "Info "

    - This paragraph applies to Exchange Online and Skype for Business Online (Office 365) infrastructures only. If you are using an Exchange On-Premises or Skype for Business On-Premises solution, please refer to the section: [Configuring Exchange On-Premises](Configuring Exchange On-Premise and Skype for Business On-Premise Accounts.md).
    - You must have sufficient rights to access your Office 365 using Exchange PowerShell remotely.

#### Starting PowerShell

The following commands are PowerShell commands. To launch PowerShell, simply search for PowerShell in the Search field in Windows 7 or Windows 8.Start PowerShell with the option Run as an administrator.

![Power-Shell] (/img/power-shell1.png)
![Power-Shell] (/img/power-shell2.png)

For more information, please refer to the following TechNet article:

***<https://technet.microsoft.com/fr-fr/library/bb978526.aspx>.***

#### Logging on to Exchange Online

To use an existing Room Mailbox account (Kickle01 in the example below), run the PowerShell cmdlet below to log in to Exchange Online:

``` powershell
$UserCredential = Get-Credential
```

Enter an Exchange Online username / password with administrator privileges. Then, run the cmdlet below to connect to your Exchange Online.

``` powershell
$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
```

Run the cmdlet below to import your session so you can run Exchange commands in your Exchange Online.

``` powershell
Import-PSSession $Session
```

#### Creating a New Exchange Room Mailbox

Follow the steps below to create a new Room Mailbox account for Kickle. To use an existing Room Mailbox account, you can skip this and read Using an existing Room Mailbox account in Exchange Online (Office 365).
However, we recommend that you create a new Room Mailbox account (delete the existing one and then recreate it).To create a new Room Mailbox account (Kickle01 in the example below), run the cmdlet below:

``` powershell
$rm="Kickle01@mycompany.com"
```

``` powershell
$newpass='pass@word1'
```

``` powershell
New-Mailbox -MicrosoftOnlineServicesID $rm -room -Name "Kickle Room" -RoomMailboxPassword (ConvertTo-SecureString $newpass -AsPlainText -Force) -EnableRoomMailboxAccount $true
```

#### Using an Existing Room Mailbox Account in Exchange Online (Office 365)

If you are already using a Room Mailbox account for the Kickle room, you can follow the steps below. However, we recommend that you delete and then recreate the account.
To use an existing Exchange account (Kickle01 in this example), execute the following cmdlet:

``` powershell
$rm="Kickle01@mycompany.com"
```

``` powershell
$newpass='pass@word1'
```

``` powershell
Set-Mailbox -MicrosoftOnlineServicesID $rm -room -Name "Kickle Room" -RoomMailboxPassword (ConvertTo-SecureString $newpass -AsPlainText -Force) -EnableRoomMailboxAccount $true
```

#### Configuring the Exchange Room Mailbox Account

The cmdlet below will configure the Exchange Online account to accept or refuse meeting notifications automatically based on whether the room is available.

``` powershell
Set-CalendarProcessing -Identity $rm -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –DeleteSubject $false -RemovePrivateProperty $false
```

#### Configuring MailTip

![mail-tip] (/img/mail-tips.png)

!!! Tip "Configuring MailTip:"
    Set-Mailbox -Identity $rm -MailTip "This room is equipped with a Kickle videoconferencing system. Click on the Skype for Business Meeting button if you wish to use Kickle."

You can also use the following cmdlets to adapt the message according to the exact location of the room.

``` powershell
$Temp = Get-Mailbox $rm
```

``` powershell
$Temp.MailTipTranslations += "ES: Esta sala de reuniones tiene una solución Kickle"
```

``` powershell
Set-Mailbox -Identity $rm -MailTipTranslations $Temp.MailTipTranslations
```

#### Configuring the Message Received When a Kickle Room is Booked

You can configure the message that the meeting organizer will receive when booking the room by running the following cmdlet:

!!! Tip "Configuring the message received when a Kickle room is booked:"
    Set-CalendarProcessing -Identity $rm –AddAdditionalResponse $TRUE –AdditionalResponse “If the meeting has been refused, it is because the meeting room is not available at the time specified.```<br><br>```If the meeting is accepted, congratulations! You have planned your Kickle meeting successfully.```<br><br>```Do not forget that Kickle should not wait in the waiting room. To check, open the Kickle meeting and then click on Meeting Options. Check that no guest is waiting in the waiting room. Also check that Kickle is the organizer.”

The message received by the organizer will be as follows:

![MeetingAccepted] (/img/MeetingAccepted.png)

#### Allowing a Person Outside the Company to Schedule a Meeting

If you wish to enable the use of Kickle in "Planned Meeting" mode by somebody who does not belong to the company, run the command below:

``` powershell
Set-CalendarProcessing $rm –ProcessExternalMeetingMessages $true
```

Companies who want to use your Kickle must add your domain as a RemoteDomain.***_The following commands must be executed on your external collaborator's Office 365 infrastructure_***.

``` powershell
New-RemoteDomain –DomainName mycompany.com –Name mycompany.com
```

``` powershell
Set-RemoteDomain mycompany.com –TNEFEnabled $true
```

#### Creating The Skype for Business Online (Office 365) Account

Once the Room Mailbox account for Exchange Online is created, it must be associated with a Skype for Business Online account.The steps below are the same for a new account or an existing account.

#### Assigning Skype for Business Online licenses

Log on to the Office 365 administration portal at <https://portal.office.com> and choose the “administrator” portal.

![Office365] (/img/Office36501.png)

Then, assign the corresponding license (P2, P3 or E1, E3, E4 license)

![Office365] (/img/Office36502.png)
![Office365] (/img/Office36503.png)

Once the license has been assigned, check that the Skype for Business account works as intended by logging on to a Skype for Business client with this account.

#### Update the Password Expiry Policy

In Office 365, the default password expiry policy is 90 days. For Kickle, however it is imperative to change this to “Password Never Expires”. Follow the following procedure step by step.</>
**Install Microsoft Online Services Sign-In Assistant for IT Professionals RTW.**

![Office365] (/img/miconlineserv.png)

Finally, install **Azure Active Directory Module for Windows PowerShell (64-bit version)**

![Microsoft Azure] (/img/azure.png)

#### Launch PowerShell

Start PowerShell with the option **Run as an administrator**.

![power-shell1] (/img/power-shell1.png)

![power-shell2] (/img/power-shell2.png)

For more information, please refer to the following TechNet article:

***<https://technet.microsoft.com/fr-fr/library/bb978526.aspx>.***

Run the following cmdlet:

``` powershell
Import-Module LyncOnlineConnector
```

``` powershell
$cred=Get-Credential
```

Enter an Exchange Online username / password with administrator privileges.

``` powershell
$cssess=New-CsOnlineSession -Credential $cred
```

``` powershell
Import-PSSession $cssess -AllowClobber
```

#### Password Expiration Policy

Run the following cmdlet :

``` powershell
Connect-MsolService -Credential $cred
```

``` powershell
Set-MsolUser -UserPrincipalName Kickle01@mycompany.com -PasswordNeverExpires $true
```

Refer to ***<http://technet.microsoft.com/en-us/library/dn362831.aspx>*** for more information.

#### Office 365 Consent

This paragraph applies to **Exchange Online and Skype for Business Online (Office 365) infrastructures only.**
Kickle uses Office 365 APIs. By default third party applications are not authorized to authenticate your office 365 tenant. The following procedure authorizes Kickle to connect to your office 365 APIs.
Go to <https://auth-online.Kickle.com/> and enter your office 365 domain name.

![Office 365 Consent1] (/img/consent01.png)

Authenticate with an office 365 administrator account:

![Office 365 Consent2] (/img/consent02.png)

Click on **Accept**.

![Office 365 Consent3] (/img/consent03.png)

![Office 365 Consent4] (/img/consent04.png)