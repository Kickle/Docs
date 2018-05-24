<!--
    Page : Administration/Network
    Author : Alexis CONIA
    Latest Update : 24/05/2018
    Confidential : No
	Partner : No
	Public : Yes
    Version : 1.1
-->

Kickle is always in conference mode. This table describes all the scenarios about codec and bitrate.
You can modify the bitrate for audio, video and sharing by using the cmdlet "[Set-csconferencingpolicy](https://docs.microsoft.com/en-us/powershell/module/skype/set-csconferencingpolicy?view=skype-ps)"
All figures are not fixed and depend on media's activities


##Audio

| Audio Codec  |Audio payload bit rate (Kbps)   | Bandwidth (Kbps)   |
|---|---|---|
| G.722   | 64.0  | 159.6  |
| G.722 Stereo   | 128.0  | 223.6   |
| G.711    | 64.0  | 156.0   |
| Siren  | 16.0  | 63.6   |

##Video
Video is linked to : the number of videos and the size (full screen or preview).

Skype for business is using H264 SVC since Lync 2013.
The maximum for all the video streams in conference is 8015 kbps.
Please refer to the link at the bottom of this page to get more details.

##Sharing
Kickle doesn't support VBSS so far (https://docs.microsoft.com/en-us/skypeforbusiness/manage/video-based-screen-sharing)
Bandwidth for sharing depends on screen resolution that is shared.

| 1080p Content  | RDP Average   | RDP Peak  |
|---|---|---|
| PPT   | 200kbps   | 12mbps  |
| CAD   | 3mbps  | 7mbps   |
| Video    | 5mbps  | 7mbps   |

For more information, please refer to the following TechNet article:

***<https://docs.microsoft.com/en-us/skypeforbusiness/plan-your-deployment/network-requirements/network-requirements>.***
