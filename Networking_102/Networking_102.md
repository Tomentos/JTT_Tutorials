# Networking 102 - The necessities
Joyce said no 😔😔😔

---

**Please read Networking 101 before reading this Tutorial**

I promised and I decided to not wait 3 months this time. The Networking 101 lesson got incredibly positive reactions and I also got requests for the second lesson already. So here I am. This lesson will focus on every device / service in a modern network. This also includes IP Addresses.

---

## Content Table
- The Must haves
    - DHCP
    - DNS
    - Gateway
- Routing

---

## The Must Haves
Every network requires multiple services in order to be operational. If you read this and go "nO i DoN't HaVe AnY oF tHeSe" then tell me how exactly you are supposed to be reading this right now.

If you open a Command line Window (cmd) and type `ipconfig` you should see multiple things next to your IP-Address. The Subnet mask is not important right now, I'll get to that later. The thing I'm talking about is the "Default Gateway" address. This thing is responsible for hooking your network up to the actual internet.

Since most of you are reading this from home, or from a smart device or simply don't know a lot about networks yet, this might seem like something expendable. But the gateway is, in most cases, handling everything required to make a network actually work.

The three things I'm taking about are, the **Gateway**, the **DNS** and the **DHCP**.

### DHCP
Short for *Dynamic Host Configuration Protocol*. The DHCP Server is responsible for handing out IP-Addresses in a local Subnet. This is a service to make device usability for the end user as painless as possible. Without this server, you would need to keep track of every IP-Address in your entire network. You would need to keep track of which ones are used by someone and which ones are free. Every time someone new would connect to your network, you would need to manually enter the IP-Address assigned to the device into it's configuration just so they could connect to the Network.

With this server, the device could send a request for an IP-Address, and the server would automatically check which ones are free to use and send one to your device. Your device would then automatically assign the address to itself and you are free to use the network. All of this happens every time you restart your computer. Within a few milliseconds of time.

### DNS
Short for *Domain Name System* or *Domain Name Server* or *Domain Name Service*. Yes is has three different names.

When you open a web browser and type `google.com` into the URL bar, how does your computer know where to go? We established very well that networks use IP-Addresses, so how exactly can your system connect to such a *name* all of a sudden? The answer is, it doesn't. When you tell your system to connect to `google.com`, you system then takes that name and passes it to the DNS. The DNS then checks the worldwide database of domain name collections just to find out to which IP-Address is behind that name. After that, the IP-Address is given back to your system.

You can actually test this out by going back to your Command line Window (cmd) and type `nslookup google.com`. This command is short for *Name Server Lookup*. This also pretty much describes what a DNS does. When you press enter, it shouldn't take long for the IP-Address to pop up. The IP-Address you see there is the exact one your computer connect to every time you visit `google.com`. Try pasting that IP-Address into the URL bar of your browser and see where it takes you.

Now that your system knows where to connect, how does it connect? The Google servers surely aren't in your basement, so they are not in your network. How does your computer connect to the Google servers?

### Gateway
This IP-Address that your computer ends up with is then passed to the gateway. A gateway is most often responsible for more than one network. The gateway is basically the master of the network. It's the device that created the network and it can always create more than one network. If that is the case, it will check if the requested IP-Address is somewhere inside the networks that it is managing. If it is not, the Gateway will then pass the IP-Address to *its* gateway. The next gateway will then do the same and then its Gateway will to the same etc. etc...

Once this request has reached the gateway that is responsible for the IP-Address it will pass the request to that IP-Address. The server with that IP-Address with answer it or drop it depending on a multitude of factors. For example if your IP-Address has been banned by that server, it will not bother to answer to you anymore. This is what we call *dropping a request*. When your browser opens the website you requested, that means, the server behind it has *answered your request*.

Now there might be one glaring question you might have. Clearly it seems like there are hunders of Gateways that such an address has to travel through before it reaches Googles servers. How does a Gateway know that none of the Gateways below it have that IP-Address? The answer is actually quite simple. You can calculate if any of the devices below the Gateway are even able to have that IP-Address. How...? Find out in Networking 103! Explaining this would be a whole other topic in and of itself, one that I **will** discuss in Networking 103 (hopefully).

---

## Routing
Not gonna lie, a good part of Routing has already been explained by the Gateway explanation that came in the chapter before. That would have been how your computer connects to an IP-Address *outside* of the current Network. But what if you try to connect to an IP-Address within the current Network?

There isn't really a realistic way to track where every single device physically is in your network. So to accurately locate a device within a network every single time, you need to ask every single device who they are, every time. I am not kidding with that. You can also not remember which device was plugged in where because that can be different with every single request.

So what happens is that the request goes from your device to probably a switch first. That switch will then ask every other device that is plugged into it if they are the requested device. If one of the devices plugged into the switch is another switch, that switch will ask every device plugged into it if they are the device. This, similarly to the Gateway, goes on and on and on until one of two things happens.

One scenario is that the requested device has been found. It will generate an answer that will be send back to your device *directly*. No more asking every device, the response goes back the exact way it came from, immediately. This is also the reason why you can't quickly switch ports on a switch without a short delay on your PC. There are dozens of requests going around every single seconds. When you quickly switch ports, at least a few of them will be lost because the requesting device isn't where it was when the request was started.

The other scenario is a timeout. Every request has multiple settings to it. One of those settings is the TTL (short for time to live). The TTL is given in milliseconds. If your device does not receive a response within the given TTL, the request is disregarded, or *timed out* as your PC will say it.

---

## Outro
So that is pretty much it for now. I tried to focus on Routing and required services in a Network for this Tutorial. It turned out a bit shorter than I expected it to. That is mainly because the next Tutorial is going to be IP-Addresses and combining Routing with those will be a huge Tutorial. So I rather wanted it in two separate parts.

If there are any questions that I failed to answer, please @ me on Discord and I'll be happy to answer them. If no one does, I will think I did a good job here.
