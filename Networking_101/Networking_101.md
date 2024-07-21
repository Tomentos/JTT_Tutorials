# Networking 101 - The basics

You want to learn networking? Then you gotta start at the bottom. Bottom meaning how a network is built, physically and what that even is would be good to know too.

Warning. This is a Tutorial meant for absolute beginners - hence the *101* and the title *The fucking basics* - so everything here is very simplified to make it more understandable. So anyone commenting "Uhm, well acktually, tere is no 8th network layer 🤓☝" will get fucking boarded by me if I come across them in real life.

## Content Table
- [Definition - What is a Network](#Definition)
- [Theory - How does a Network work](#Topologies)
- [Topologies - How a Network is built](#Theory)
- [Routing - How multiple Network interact](#Routing)

---

## Definition
What is a network. I want you to think about this and make a guess. After that uncensor the below message and see yourself.

A Network is two or more electrical devices communicating with each other

That's it. That's the most basic description of a network. No fancy Gigabit Fiber Modems (Yes I'm mad about that), No High Speed 5G Wireless Connections, matter of fact, no internet at all. The Internet and Networks aren't necessary intertwined. Your TV Remote sending a signal to your TV is already a network. A so called one sided one because the TV doesn't send any signals back to the remote, but it's a network none the less.

Of course, over the past decades, we made our networks fancier to the point where I dare you to find anything in your room that isn't somehow part of a network. Your light bulb doesn't count, even though half of those are already smart, meaning they're part of a network now days.

---

## Topologies
A network can - matter of fact - be heavily influenced by how you plug what into what. This is called a topology. These things are mostly controlled by your ISP or IT department in a company, so the end user doesn't really notice it, nor do they have a really good chance of fucking anything up by plugging the wrong things together. However, there's still different topologies used to this day. 

Here you have a few of them listed:
![Network Topologies](./img/topologies.png)

Every single dot in this image represents a node (basically a plug on a device). In the past our devices weren't as well managed as today though, so there was no central managing service giving internet to everyone through a carefully planned and structured connection. Back in the day, we hooked every single device together directly - like the Fully connected topology.

The Mesh, Ring and Line topology are similar to the Fully Connected topology, however in them, not every single device is connected with each other, if you wanted to send something to a device, not directly hooked up to yours, you would send that something *through* another device. Basically, a computer took the role of a switch.

Now the big question though is, how did people access the internet then? Easy! You would directly connect every single device to the open internet! Yes, we used to do that. If you've see the 1995 Movie Hackers featuring Angelina Jolie, you may remember them hacking actual companies by connecting their computers to a public phone. This is exactly why that worked. Devices were directly hooked to the internet, exposing them to connections from any device directly hooked onto the internet.

The Bus topology is very similar to that, yet a bit different. It does have a central managing point. It also has one main line of connection that every device, including the managing point, is connected to. That allows every single device in the network to directly talk to the central managing point.

The Star and Tree topology are inherently the same. The difference is that the tree topology is just multiple star topologies hooked together. They use multiple central management points. Each and every one managing a small group of devices. Then they report back to an even centraller point, which manages all the central points.

Can you guess which of these topologies are still commonly used today?
ALL OF THEM! YES THAT'S RIGHT. Of course, some of them are more outdated than others, but that doesn't change the fact that some objectively unnecessary ones are still being used in some small network somewhere. Be it to save cost, because it's faster or lord knows why.
The more common ones though are definitely using a Tree/Star topology. But you might still find a few Buy topologies. These would be more common in buildings though, like an automated blind system, or an old, non-smart LED controller.

---

## Theory
To the different devices a network consists of, we've come up with a neat little model. Every single device that can communicate, can be classified using that model. It's called the OSI-Layer model.

| Layer | Name          | Examples                  | Function                                                                  |
|:----- |:------------- |:--------------------------|:------------------------------------------------------------------------- |
| 7     | Application   | MS Office, Web Browser    | Applications and services used by the user to view, create and send data  |
| 6     | Presentation  | ASCII, XML, JSON          | Decompressing, Decryption, Formatting the data to make it readable        |
| 5     | Session       | Firmware, Driver          | Opening a session enabling requesting and responding with specific nodes  |
| 4     | Transport     | TCP, UDP                  | Transporting data and recognizing errors in transmission                  |
| 3     | Network       | Router, IP                | Enabling communication through the transfer and routing of packages       |
| 2     | Data Link     | Switch, Bridge            | Linking interfaces / nodes together using their physical address          |
| 1     | Physical      | Cable, Plug, NIC          | The physical hardware connecting different interfaces                     |

The ones who read the whole introduction already know about the mysterious 8th Layer. The secret of said layer, you will have to find out yourself once you are comfortable enough in Networking and IT as a whole.

Back to topic; The OSI-Layer model is incredibly important in understanding how a network is working. I'm not saying you need to understand every single Layer and it's exact purpose - hell, even I had to look some things up when writing this - but it is important in remembering the 7 steps, understanding that they all build upon each other and understanding how many parts there are to get a network working.

I will explain how all the layers are related shortly here.

| Layer     | Example                                                                                                                                   |
|:--------- |:----------------------------------------------------------------------------------------------------------------------------------------- |
| Layer 1   | You have a laptop and you plug in your cable into a nearby network port.                                                                  |
| Layer 2   | The port recognized something being plugged in. Your device is sending a request to be part of the network.                               |
| Layer 3   | Your device receives it's Address and is nor registered in the network.                                                                   |
| Layer 4   | Your device is receiving packages and can connect to the network.                                                                         |
| Layer 5   | You open a website on your laptop, sending a signal to the website, requesting the data to load it.                                       |
| Layer 6   | The device received the data required to load the website. The data is processed to a readable form.                                      |
| Layer 7   | Your web browser displays the readable data to you.                                                                                       |
| Layer 8   | Fuck you stupid ass this is why I hate myself                                                                                             |

---

## Routing

This I will have to keep very short. The topic of routing is so incredibly big, I could probably write the entirety of Networking 102, 103 and 104 just about it.

Networks have certain IP-Addresses that are reserved. That means, no single system can use it or everything will fucking die. The very first and very last IP-Address of any network are reserved for the Network-ID and the Broadcast-ID. The Network-ID is used to identify the network itself. The Broadcast-ID is used to send a signal to every single device in the network. Then, every single Network needs a routing master. I use this term to describe the device responsible to communicate with other networks and distributing packets from outside the network to every device. This device is always occupying either the first, or the last usable IP-Address in a network. This master device is often separated into multiple different devices, especially in corporations. There's a Gateway, DHCP, DNS, Firewall, Modem, Access Points, in a business also an AD. Many businesses separate these into their own servers because if enough people are working, one single server cannot handle all the resources. At your home, the modem you received from your ISP is probably handling all of those things at the same time.

I just threw a lot of buzzwords at you. But I am going to do the YouTuber Outro here. If you like this topic, if this seems interesting to you, if you want to know what these buzzwords mean, you need to ask for the 102 tutorial. I will probably focus on all the different devices and servers that are in a network today, and how they work. I do not know how long that will turn out to be,but if it's not too long, I will throw IP-Addresses as a whole in there as well. But that will most likely be Tutorial 103. Feel free to request another topic as well for the next Networking tutorials if that interests you.
