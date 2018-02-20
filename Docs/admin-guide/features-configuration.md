<!--
    Page : Administration/Features Administration
    Author : Alexis CONIA
    Latest Update : 27/06/2017
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

####Manage Attachments

Kickle is able to manage attachments. If a user attaches a file to an invitation, it will automatically be included in the workspace.
By default, room mailbox deletes attachment. You can use this cmdlet to avoid suppression.

``` powershell
Set-CalendarProcessing –Identity KICKE01@mycompany.com -DeleteAttachments $false
```