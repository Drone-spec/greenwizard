# Running a train with the homies.

Wizard Groups in attendance: The Cyber Threat Emulators wizard court, And my current home which I shall dub the Contractor wizard court.


This is my first venture into the ugly world of ICS on mobile metal boxes. While my fellow wizard homies made it quite apparant that our hexes and incantations have inflicted havoc before on ICS of a more static variety. This was to be my very first venture into this dark and dank world. ICS is often spoken of in hushed tones full of woe and dispare among cyber wizards. Many of our kind tell harrowing tales of encountering machines beyond time and space. Networks of old held together by the most archaic networking magics. I am filled with hope and youthful energies at the chance to see such great works. This shall be my recording of these events.


Preparing for an odyssey.
---

We must prepare as we have been given our topics.

1. Python(requests, scapy, pyrtlsdr, pyshark, BACpypes)
2. Network Recon(nmap, masscan)
3. Wireless Surveys(Kismet, Airodump-ng)
4. Payload Building(msfvenom, empire, veil)
5. PCAP Analysis (Wireshark, Tcpdump)
6. Vulnerability Scanning(OpenVAS, Nessus, nmap NSE Scripts, openscap, lynis)
7. SQL Injection(sqlmap, OWASP ZAP)

As a small court of wizards the time to start researching and obsessing over trains like true enlightened individuals had begun. We searched all over the internet for videos related to train control systems. Abusing the usual suspects we got a ton of important information in relation to most of the ICS environments. FCC submittions and documentation proved to be very eye opening into the way that these systes act and work. We learned critical frequency channels, methods of communication, and how the system should work. We know from many many lectures and talks on the matter that safety is number one. Which means the systems should default to a safe standby. While I always want a secure first approach in the matter of public transit the idea of safety should come first. This does however leave us with issues we must talk about. 

## Saftey first

The concept of saftey above all means security will take a backseat. This backseat is going to be in the form of in an unsure situation a train must come to a stop. This is to ensure human life is the most protected asset. Avoid harm at all costs. This puts into my mine the concept of any method that might be used to alert the trains to situations must by the above issue be robust and simple. Less parts i the system would translate into easy of use and less prone to faults. 

## Public transparancy

The public always has a right to know and understand the methods and processes behind the means to transportation we trust our lives with. The concept of hiding information is a valid one for many systems and methods. Not letting the public know how certain critical infrastructure works to prevent abuse by outside actors has a lot of validity. However as a saftey first mentality we must release the methods and systems. The release of this critical information is a danger due to the ability of someone with malicious intent or simulated intent can as we showcase make use of this public information to cause failures in a system resulting in some very bad times for a sensative system.

## Private and public sector forced co-operation

While I do not accept any private company telling me they are working with my best intrest in mind. I do however understand that given enough fee's and jail time a company might act in my intrest only due to state applied pressure. The private sector will abuse a system as much as they can. Sorry if this sounds like a rant but it does apply. In our research you will begin to find a lot of workers in the rail industry talking about automation and the lay-offs happening even now. At the Hack The Railroad 2023 event the leaders of these companies even talk joyfully about a full automation solution. However as a security-mancer and or wizard I see this as a perfect system for abuse. No human intervention is a very fast and dangerous route to embark on. Once an exploit is found and used the time it would take to correct a fault like that would be fatal to an automated system that relys on perfect timing. Imagine stopping a train in the middle of some far off woods far from human interaction. I pale at the thought of someone first finding the issue, sending a team to investigate, begining the process of trying to clear the fault or whatever, getting the system back into a working state. With human operators being present you can perform the onsite triage. 

Oh uh, yeah anywho long story short, a lack of humans is a very bad time when you have a system that could be attacked and left unattended. Even tho most industrial processes can and have been automated we still have humans very near to prevent some kind of critical failure.


# When wizards meet

As we made our way to the event. I connected with some friends who also planned on attending. Hard cut to us breaking out a HackRF and other SDR solutions we went to all learning how Radio Frequency works and the technology behind a lot of that type of magic. We had two plans, Running a couple of trains with the wizards court and fining out how drunk the apprentence mages could get. (They had added four new mages to the team in my absence) 

So as the moon greeted our arcane shinanigans and teaching the apprentence mages about alcohol based potion crafting our chaos was palpable. Our night concluded and the dawn was soon approaching.

# Beasts of Iron and Heat

Making our way to DreamPort we did the usual sign in and grabbing badges. Making our way past all the non-technical speeches I quickly went to the practical area. Now side note this is a great example of social engineering. Tables had name plates on them. Now we had been told that the event had run out of room for any more groups showing up. So I decided I had driven too far and prepare too much to be told no. So I dropped my stuff and acted like I was a helper. Noticed that all the people helping had merch jackets. So off to the shop I went. Got a cheap jacket and now I fit right in. Locating my old wizard groups table I notice two tables right next to them so I just moved the name plate to a empty table and began moving my stuff into the 
