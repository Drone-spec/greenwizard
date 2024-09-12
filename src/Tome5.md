# DellserverGPUfanissue
Read my story to fix your issue.

Sorry for the wizard fun but I hate dry write ups and you can just copy paste and ignore my rambling. 

## Chapter 1, The problem
---
Welcome fellow techno sewergoblin. If you found this then you too have put an unsuppored GPU inside of that wonderful dell server you are about to commit unholy sins against in the persuit of the perfect homelab. 

The bad news. That fan sucks mega butts contantly trying to take off with its fans spinning at like 75 to 85 percent for NO REASON.. Well as it turns out there is a reason and I had to ponder some Old arcane tomes to understand the issue.


## Chapter 2, Pondering old orbs
---
Deep in the back pages of spiceworks fourms. In the year of our lord 2023 I stumbled into this.

https://community.spiceworks.com/topic/613098-dell-poweredge-server-r7xx-series-fan-speed-with-gpu

Full of wizard sharing in their woes as one mighty hero would deliver us from our struggles. SUFFER NO MORE this hero said. *alexrozentuller* you mighty wizard! I salute you.

```
Dell traced the issue back to a setting for how they handle unmatched devices.  They were able to run the following IPMI command on my 730's to resolve the issue:

ipmitool.exe -H 172.16.171.21 -U root -P calvin raw 20 30 0x00 ce 0 0x16 5 0 0 0 5 0 1 0 0    > Set Unmatched Logic Disabled

*** USE AT YOUR OWN RISK ***﻿

﻿Dell was very hesitant to provide me with the above command, so it is not official by any means.  I forwarded the details to Teradici under ticket reference: #15134-33400.  ﻿I would give them a ring first.

If that doesnt get you anywhere, i provided my Dell ticket in an earlier post: SER# 81901735650.﻿  See if you can reference that with Dell directly.

Good Luck!

```
As we gaze at this script of old we find the command and values we need.

```
ipmitool -I lanplus -H <IP of the IDRAC> -U <user> -P <password> raw 0x30 0xce 0x00 0x16 0x05 0x00 0x00 0x00 0x05 0x00 0x01 0x00 0x00
```

Ah and here we have a great example of PRIME magic, This is undistilled wizard juice. The good stuff.

## Chapter 3, Tapping ancient power
---

With our new found words of power we must build our foundation.

Step 1. Log into your dell IDRAC

Step 2. Once Logged in on the left hand side under IDRAC Settings, click on User Authentication

Step 3. Make a user with a password containing no symbols, Down one box should be IPMI USSER PRIVILEGES, set Maximum LAN User Privilege Granted to Administrator.

Step 4. Hit APPLY

Step 5. On the Far Left hand side under iDRAC SETTINGS, Select Network, Scroll to the bottom and located the IPMI Settings, check the box for Enable IPMI Over LAN

Step 6. Hit APPLY

We have now pregamed the server for IPMI wizard magic. Let us now begin the incantation.

## Chapter 4, Activating ancient power
---

I am using Endevour OS, so let me tip my wizard hat because I used arch BTW.

```
yay ipmitool  < yay wizards

apt-get install ipmitool < Normal Linux users
```
if you want to self compile
https://github.com/ipmitool/ipmitool

For all my powershell surfers here is the windows Dell support pack 
https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=w9nmr

once you have ipmitools let me give a rundown on the actual command, You could spare me this pain and read the man page or the -h but here it is anyway

ipmitool -I lanplus -H <IP of the IDRAC> -U <user> -P <password> raw 0x30 0xce 0x00 0x16 0x05 0x00 0x00 0x00 0x05 0x00 0x01 0x00 0x00

-I is the interface method 
-H is the ip of your iDrac 
-U is the user with ipmi permissions
-P is password
Raw is the data type

0x30 0xce 0x00 0x16 0x05 0x00 0x00 0x00 0x05 0x00 0x01 0x00 0x00
This above is Set Third-Party PCIe Card Default Cooling Response Logic To Disabled

Mad shout out to *mikemattran* for the Disable, Enable, and Status codes

```
Set Third-Party PCIe Card Default Cooling Response Logic To Disabled

ipmitool -I lanplus -H -U -P raw 0x30 0xce 0x00 0x16 0x05 0x00 0x00 0x00 0x05 0x00 0x01 0x00 0x00 

Set Third-Party PCIe Card Default Cooling Response Logic To Enabled

ipmitool -I lanplus -H -U -P raw 0x30 0xce 0x00 0x16 0x05 0x00 0x00 0x00 0x05 0x00 0x00 0x00 0x00 

Get Third-Party PCIe Card Default Cooling Response Logic Status

ipmitool -I lanplus -H -U -P raw 0x30 0xce 0x01 0x16 0x05 0x00 0x00 0x00 

The response data is:

16 05 00 00 00 05 00 01 00 00 (Disabled)

﻿16 05 00 00 00 05 00 00 00 00 (Enabled)
```

Once the dust settles and peace returns to your wizard homelab. We can all take a deep breath as we are free from the loathsum Dell GPU fan curse.
