<!--
    Page : Beta/Boila
    Author : Alexis CONIA
    Latest Update : 19/03/2018
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.0
-->

#Voila

Voila is a project that we are working on for a few months now. 
Our goal is to create a great experience with kickle, locally in the meeting room.

We are really excited to release it! It is part of our beta release.

##Features
We will launch some features gradually. Today we limit the version to : 

* Local Sharing
* Windows Sender

##Architecture
The sender is connected directly to the receiver on Kickle. At this time, Kickle should be reachable by the sender on the local network.

![Voila](../img/VOILA.png)

##Network Requirements

###Ports

|From   |To   | Protocol and Port   |Comments   |
|---|---|---|---|
| Sender (PC)   | Kickle  | TCP (443)  | Commands   |
| Sender (PC)   | Kickle  | UDP (1024-65535)* | Media |

*Of Course, we are working hard to limit this ports range. It will also be configureable by IT Administrators

