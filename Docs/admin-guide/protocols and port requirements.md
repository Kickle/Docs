<!--
    Page : Administration/Network
    Author : Alexis CONIA
    Latest Update : 07/07/2017
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.1
-->

!!! note
    We are not listing all the basics ports that are mandatory to communicate, such as dns or dhcp.

### Skype for Business On-Premises and Exchange On-Premises

The following table lists the protocol and port requirements for a Skype for Business On-Premises and Exchange On-Premises infrastructure.
You need to adapt the list based on the location of the Kickle unit (if it's internal or external access)

!!! note
    These ports and protocols are the standard ports and protocols of a Skype for Business and Exchange infrastructure. If you have custom ports for Edge access, the list below is not exactly the same.
    If Kickle is installed in your internal network, you should install the root certificate on Kickle to trust SSL connections

|From   |To   | Protocol and Port   |Comments   |
|---|---|---|---|
| Kickle  | Skype for Business Infrastructure  | TCP/HTTPS (443)  | Autodiscover and Skype for Business Web APIs  |
| Kickle  | Skype for Business Infrastructure  | TCP (PSOM/TLS) (443)  | For External user access to web conferencing sessions |
| Kickle  | Skype for Business Infrastructure  | TCP (STUN/MSTURN) (443)  | Edge Server STUN / TURN for external access  |
| Kickle  | Skype for Business Infrastructure  | UDP (STUN/MSTURN) (3478)  | Edge Server STUN / TURN for external access  |
| Kickle  | Skype for Business Infrastructure  | TCP/UDP (1024-65535 )  | Audio, Video and Desktop Sharing Range. It must be updated based on your internal policies|
| Kickle  | Exchange  | HTTP (80)  | Exchange Web Service      |
| Kickle  | Exchange  | HTTPS (443)  | Exchange Web Service    |


!!! note
    Skype for Business HTTP/HTTPS Destination can be your front-end(s), a director server or your reverse proxy.
    Exchange HTTP/HTTPS can be your internal server(s) or your reverse proxy

For more information, please refer to the following TechNet article: ***<https://technet.microsoft.com/en-us/library/gg398833.aspx>.***

### Skype for Business Online and Exchange Online

The following table lists the protocol and port requirements for a Skype for Business Online and Exchange Online infrastructure:

|From   |To   | Protocol and Port   |Comments   |
|---|---|---|---|
| Kickle  | Office 365  | UDP (3478)  | Skype for Business Audio, Video and Desktop Sharing  |
| Kickle  | Office 365  | UDP (3479)  | Skype for Business Audio, Video and Desktop Sharing  |
| Kickle  | Office 365  | UDP (3480)  | Skype for Business Audio, Video and Desktop Sharing  |
| Kickle  | Office 365  | UDP (3481)  | Skype for Business Audio, Video and Desktop Sharing  |
| Kickle  | Office 365  | TCP/UDP (50000-59999)  | [This range is now optional for Skype for Business Online.](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Simplified-port-requirements-for-Skype-for-Business-Online/ba-p/77094)  |
| Kickle  | Office 365  | HTTPS (443)  | Exchange and Skype for Business Web Services,Azure AD for Authentication    |
| Kickle  | Office 365  | HTTPS (443)  | Exchange and Skype for Business Web Services,Azure AD for Authentication    |

For more information and details (on URLs and IPs), please refer to the following articles: 

*   <a href="https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US&fromAR=1#bkmk_portal-identity" target="_blank">Shared Services</a>
*   <a href="https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US&fromAR=1#bkmk_lyo" target="_blank">Skype for Business Online</a>
*   <a href="https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US&fromAR=1#bkmk_exo" target="_blank">Exchange Online</a>

### Hybrid Configuration

As you probably know, Hybrid configuration is composed by on-premises and online servers. You need to configure your network based on the location of the Kickle unit and your configuration.

You can find more information via these links:

* Skype for Business Hybrid Configuration : https://technet.microsoft.com/en-us/library/jj205403.aspx
* Exchange Hybrid Configuration : https://technet.microsoft.com/en-us/library/hh534377(v=exchg.150).aspx

### Kickle

Kickle uses several specific ports to communicate with our cloud platform.

|From   |To   | Protocol and Port   |Comments   |
|---|---|---|---|
| Kickle   | cloud.kickle.com   | HTTPS (8705)  | Authentication. Only for versions below 2.0.17317.02  |
| Kickle  | cloud.kickle.com  | HTTPS (8432)  | Updates. Only for versions below 2.0.17317.02  |
| Kickle   | *.kickle.com   | HTTPS (443)  | Authentication, Updates, Portal   |
| Kickle  | Any  | HTTP (80)  | Quick Assist, Internet Navigation  |
| Kickle  | Any  | HTTPS (443)  | Quick Assist, Internet Navigation  |

!!! Info "Info"
    From version 2.0.17317.02 through the latest releases, we are now using only HTTPS(443)
    The best option is to configure a wildcard. All URLs are: api.kickle.com, auth.kickle.com, hub.kickle.com, portal.kickle.com

### MirrorOP / Wireless

MirrorOP is the software/technology that Kickle uses for wireless display. MirrorOp uses the following ports:

|From   |To   | Protocol and Port   |Comments   |
|---|---|---|---|
| Sender (PC, Mobile)   | Kickle  | TCP (443)  | Command   |
| Sender (PC, Mobile)   | Kickle  | TCP (3268)  | Command  |
| Sender (PC, Mobile)   | Kickle  | TCP (389)  | Command  |
| Sender (PC, Mobile)   | Kickle  | TCP (8080)  | Data  |
| Sender (PC, Mobile)   | Kickle  | TCP (31865)  | Data  |
| Sender (PC, Mobile)   | Kickle  | TCP (515)  | Data  |
| Sender (PC, Mobile)   | Kickle  | TCP (1688)  | Audio  |
| Sender (PC, Mobile)   | Kickle  | UDP (1047)  | Device Discovery  |
| Sender (PC, Mobile)   | Kickle  | UDP (1048)  | Device Discovery  |
| Sender (PC, Mobile)   | Kickle  | UDP (1049)  | Device Discovery  |