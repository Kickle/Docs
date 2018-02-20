<!--
    Page : Administration/Requirements
    Author : Alexis CONIA
    Latest Update : 27/03/2016
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

Kickle was developed based on Microsoft Skype for Business APIs and is thus reliant on the Skype for Business infrastructure in place. Kickle requirements include:

- An Exchange room mailbox account associated with a Windows account to handle how meetings should be accepted or refused.
- A Skype for Business account linked to the Windows account.
- The autodiscover service should be activated on Exchange.
- Wired connection to the dhcp network for the first install.
- A screen with a hdmi connection.
- Ideally, a “CEC over HDMI” compatible screen.
- A “1366 x 768 pixels” minimal screen resolution.
- [Protocols and ports requirements](protocols and port requirements.md).

Kickle is compatible with:

- All Skype for Business architectures (online, on-premises, hosted).
- All Skype for Business server 2013 architectures (online, on-Premises, hosted).
- All Exchange 2013 (individual-forest) or later (individual or multi-forest) architectures (online, on-premises, hosted).

The following licenses are required for use with Kickle:

- Skype for Business client access license (CAL): CAL Skype for Business / Skype for Business for on-premises architectures or P2 for Skype for Business online / office 365.
- Kickle does not require an Exchange license (room mailboxes do not require a license).
- Kickle does not require a Windows IOT license (the Windows IOT license is dealt with by the Kickle Company directly.