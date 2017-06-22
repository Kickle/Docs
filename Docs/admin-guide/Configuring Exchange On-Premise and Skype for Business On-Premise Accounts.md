<!--
    Page : Administration/On Prem
    Author : Alexis CONIA
    Latest Update : 14/04/2017
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

### Creating and Configuring a Room Exchange On-Premise Account

!!! important "Important"
    This paragraph applies to Exchange On-Premise infrastructures only. If you are using an Exchange Online solution (Office 365), please skip to section **Configuring Exchange Online and Skype for Business Online (Office 365) accounts**.

#### Starting Exchange Shell Management

Start Exchange Management Shell from your Exchange On-Premise server.
For more information, refer to:

  ***<https://technet.microsoft.com/en-us/library/bb123778%28v=exchg.150%29.aspx>***

#### Using an Existing Room Exchange account as On-Premise

If you are already using an Exchange Room Mailbox account for the KICKLE room, you can follow the steps below. However, we recommend that you delete the account and then recreate it. You can create an Exchange Room Mailbox using Exchange Management Shell (PowerShell) or Exchange Management Console (EMC). The steps below are based on Exchange Management Shell (PowerShell).

To use an existing Exchange Room Mailbox (KICKLE01 in the example below), run the EMC cmdlet as follows :

``` powershell
Set-Mailbox –Name ‘KICKLE01’ –Alias ‘KICKLE01’ -Room -EnableRoomMailboxAccount $true –RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

#### Creating a new Exchange Room Mailbox

In the example below, an Active Directory account is created at the same time as the Room Mailbox. The RoomMailboxPassword field is the account's password.To create a new Room Mailbox (KICKLE01 in the example below),run the following EMC cmdlet.

``` powershell
New-Mailbox -UserPrincipalName KICKE01@mycompany.com -Alias KICKLE01 -Name "KICKLE01" -Room -EnableRoomMailboxAccount $true –RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

#### Configuring the Exchange Room Mailbox Account

The cmdlet below will configure the Exchange account to accept or refuse meeting notifications automatically based on whether the room is available.

``` powershell
Set-CalendarProcessing -Identity KICKLE01 -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –DeleteSubject $false -RemovePrivateProperty $false –DeleteAttachments $false
```

#### Configuring MailTip

The MailTip reminds the organizer that the room is equipped with a KICKLE videoconferencing system. The user must click on the “Skype for Business Meeting” button if he or she wishes to use KICKLE.

``` powershell
Set-Mailbox -Identity KICKLE01@mycompany.com -MailTip "This room is equipped with a KICKLE videoconferencing system. Click on the Skype for Business Meeting button if you wish to use KICKLE.
```

You can also use the following cmdlets to adapt the message according to the exact location of the room.

``` powershell
$Temp = Get-Mailbox KICKLE01@mycompany.com
```

``` powershell
$Temp.MailTipTranslations += "ES: Esta sala de reuniones tiene una solución KICKLE
```

``` powershell
Set-Mailbox -Identity KICKLE01@mycompany.com -MailTipTranslations $Temp.MailTipTranslations
```

#### Configuring the Message Received When a KICKLE Room is Booked

You can configure the message that the meeting organizer will receive when booking the room by running the following cmdlet:

!!! Tip "Configuring the message received when a KICKLE room is booked :"
    Set-CalendarProcessing -Identity KICKLE01@mycompany.com –AddAdditionalResponse $TRUE –AdditionalResponse “If the meeting has been refused, it is because the meeting room is not available at the time specified.```<br><br>```If the meeting is accepted, congratulations! You have planned your KICKLE meeting successfully.```<br<br>```Do not forget that KICKLE should not wait in the waiting room. To check, open the KICKLE meeting and then click on Meeting Options. Check that not guest is waiting in the waiting room. Also check that KICKLE is the organizer.”

#### Activating the account

The previously created Room Mailbox account can be disabled in Active Directory. The account must be enabled so that KICKLE may use Exchange Web Services.
You can check this in the Active Directory Users and Computers console. Also make sure that the password for the user is blank.
To enable the account, run the following cmdlet:

``` powershell
Set-ADAccountPassword –Identity KICKLE01
```

``` powershell
Enable-ADAccount –Identity KICKLE01
```

#### Allowing a person outside the company to schedule a meeting

If you wish to enable the use of KICKLE in "Planned Meeting" mode by somebody who does not belong to the company, run the command below:

``` powershell
Set-CalendarProcessing KICKLE01@mycompany.com –ProcessExternalMeetingMessages $true
```

Companies who want to use your KICKLE must add your domain as a RemoteDomain.**The following commands must be executed on the Skype for Business infrastructure of your partner.**

``` powershell
New-RemoteDomain –DomainName mycompany.com –Name mycompany.com
```

``` powershell
set-RemoteDomain mycompany.com –TNEFEnabled $true
```

#### Configuring Skype for Business On-Premise Accounts

This paragraph applies to Skype for Business On-Premise infrastructures only. If you are using a Skype for Business Online (Office 365) solution, please skip to 4 Configuring Exchange Online and Skype for Business Online (Office 365) accounts.
Once you have configured the Room Mailbox accounts for use with KICKLE, use Skype for Business Server Management Shell to enable the Skype for Business account using the cmdlet below.

``` powershell
Enable-CsMeetingRoom -SipAddress "sip:KICKLE01@mycompany.com" -domaincontroller DC-ND-001.company.com -RegistrarPool SKYPE FOR BUSINESSPool15.company.com -Identity LRS01
```

!!! note
    Skype for Business Server Management Shell is automatically installed on each Standard Edition Server or frontend Enterprise Edition Skype for Business Server. For more information, please refer to:***<https://technet.microsoft.com/fr-fr/library/gg398474.aspx>.***



