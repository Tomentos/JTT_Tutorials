# Networking 103 - I know where your PC lives
43.19346307029371, -88.2664612175454

---

**Please read Networking 101 and Networking 102 before trying to understand anything in here**

## Table of contents
- Network Addressing Systems
- The Binary System
- IPv4 Address Ranges
- Subnets and Hosts
- Network Address
- Broadcast Address
- Network-ID

---

## Network Addressing Systems
Back in the day, when Networks were new to the average family household, there were multiple different Network communication systems that were competing with each other. The most popular example today is Apples solution for Apple devices, called AppleTalk. In 1981 the global standard for Networking was set into stone and the IPv4 protocol became the norm for the OSI Networking Layer. Other Addresses like the MAC-Address also exist, but this example exists as the Norm for the OSI Data Link Layer. 

Shorty after the IPv4 protocol became the norm, it's limitations already started as computers became more and more affordable and popular for the averade household. In 1992 the first description of the IPv4 address exhaustion was publicly made. The IPv4 protocol consists of 4 octaves, which all consist of 8 bits (hence the name octave). A bit is a value that can either be *one* (1) or *zero* (0), genererally describing the *On* and *Off* state. These 8 bits are then converted into the decimal system. Since each number is a representation of a binary octave, the highest number possible for each of these numbers in 255, with a total amount of 256 different numbers (because *zero* (0) counts as well). That leaves us with a total of 32 bits, with each bit having 2 different possible states. So the total number of IPv4 Addresses is `2^32`. Or if you want to represent it as the 4 different numbers, it's `256^4`. The result being `4,294,946,296` different IPv4 addresses.

4 billion addresses might sound like a lot, but in reality it is not at all, with many of these addresses not being able to be used. The entire space of 127.xxx.xxx.xxx being reserved for the localhost, and every single network having the Network Address and Broadcast Address, which are both fixed in place and have to exist. Now to put into perspective how many devices we already all have that all connect to the internet, take a look at this picture.

![Over 3 billion devices run java](/Networking_103/img/java.png)

*The java installer has been telling you 3 billion devices since decades by the way, the actual number is likely tenfold or higher.*

This shortage of IPv4 addresses started showing just 10 years after it became the norm. The shortage was dubbed the IPv4 exhaustion problem, and it was the main reason as to why the IPv6 protocol was developed in 1995. It's counter to this problem was extending the amount of number segments from 4 to 8. Each of these number segment no longer use 8 bits but 4 hex character instead. Hex character are representing numbers but are ranging from 0 to F instead, giving you the option of displaying 16 different numbers in just one character. This amounts to 4 quartets of bits and a total of 16 bits per number segment. This puts the total of IPv6 addresses to `16^32` or `2^128`. This gives us the total amount of IPv6 addresses, which is: `340,282,366,920,938,463,463,374,607,431,768,211,456`. I am not describing this number in words, read it yourself.

Now you might asking, *"How can it be then, that we still use mainly IPv4 to this day?"* Well, this is a question for the chapter after the next chapter. I'll describe the reasons for that in *IPv4 Address Ranges*.

---

## The Binary System
Explaining what the binary system is, doesn't take very long. Displaying information with only *ones* (1) and *zeores* (0). How to read it, convert it and use it however, that's a different question with a different answer.

IPv4 Addresses builds up on the principle of Binary. Unlike the MAC-Address and IPv6 Addresses, which both build upon the Hexadecimal system. Now first we need to understand how exactly this system uses Binary. I already said above that it consts of 4 number segments, also called octaves, which in turn then consist on 8 bits, which are just binary characters. So each of these numbers can only go as high as 8 binary characters can go, which is 255. If we spread these 8 bits out, the leftmost bit has the lowest value. The value then doubles with every bit we add to the left. This tables attempts to visualize that to create a better understanding.

|                   | Bit #8 | Bit #7 | Bit #6 | Bit #5 | Bit #4 | Bit #3 | Bit #2 | Bit #1 |
|:------------------|-------:|-------:|-------:|-------:|-------:|-------:|-------:|-------:|
| **Binary Value**  | 1      | 1      | 1      | 1      | 1      | 1      | 1      | 1      |
| **Decimal Value** | 128    | 64     | 32     | 16     | 8      | 4      | 2      | 1      |

If we now add all the decimal values, you would get the number 255. Meaning that the Binary number of `11111111` equals to the decimal number `255`. I will now have a table below where not every binary position is 1 as an example for how the number would change.

|                   | Bit #8 | Bit #7 | Bit #6 | Bit #5 | Bit #4 | Bit #3 | Bit #2 | Bit #1 |
|:------------------|-------:|-------:|-------:|-------:|-------:|-------:|-------:|-------:|
| **Binary Value**  | 1      | 1      | 0      | 0      | 1      | 0      | 1      | 0      |
| **Decimal Value** | 128    | 64     | 0      | 0      | 8      | 0      | 2      | 0      |

Every column in which the binary number is *zero* (0), the decimal number also turns into *zero* (0) as it is only a decimal representation. If you now add all these numbers together, you get 202. Meaning that the Binary number `11001010` equals to the decimal number `202`.

If you understand why and how these 8 digits interact and influence each other, you understand the binary system. To understand the IPv4 addressing system, you only need to understand the Binary system up to 8 binary numbers. If you have trouble understanding it, feel free to reach out or @ me on the server so I can help you with it.

---

## IPv4 Address Ranges
I hinted at the fact that a lot of the Addresses in the IPv4 Protocol cannot be used. Of course, the Network Address, which is the address of the network itself, and the Broadcast Address, which is used to send something to every single used Address in the Network, are part of those unusable addresses, but they can't be considered a *range*.

With a range, an actual static range of IP Addresses is meant. I already mentioned the Localhost range. The localhost range is simply every single address in which the first octave is `127`. You could technically specify it to the point of saying *"From the address of 127.0.0.0 to 127.255.255.255"* but..., come on. What's easier to remember. I'm putting my hand on *"First octave is 127"*. It's simply easier to remember and the other 3 octaves just really don't matter.

When it comes to everything else, we have something called *Private Ranges* and *Public Ranges*.
Private addresses are what your are using right now. I'm putting money on that fact. There's only *three* (3) different private ranges and they aren't that large.

| Network         | Lowest IP Address in range | Highest IP Address in range |
|:----------------|:---------------------------|:----------------------------|
| 10.0.0.0 /8     | 10.0.0.0                   | 10.255.255.255              |
| 172.16.0.0 /12  | 172.16.0.0                 | 172.31.255.255              |
| 192.168.0.0 /16 | 192.168.0.0                | 192.168.255.255             |

These are all the ranges there are. These ranges are not directly connected to the internet, but are a part of a network, managed by at least one larger one. Public IP Addresses are at this point in time all managed by big companies who are strategically handing them out to ISPs and corporations to make sure there is no monopoly for public IP Addresses. These private IP Addresses are also the reason why we are still able to use the IPv4 protocol to this day. I've mentioned the IPv4 Address Exhaustion problem. But what I didn't mention was that there also was a second solution apart from the IPv6 protocol. These private ranges were introduced and standardized as a direct result of it. Back in the day large companies used to have all their systems hooked up to a public IP address. The concept of the internet hooking every device together directly was taken way more literal back in the day. But after the IPv4 Address Exhaustion problem became more apperant, and the security risks of having every single device directly exposed to the public internet, had these private ranges way more utilized very soon. With these ranges you can have one centralized point in the network which has a public IP Address, and every subsequent device can use a private one. This way the risk is minimized and IP addresses are also way more available again. The best part, these IP Addresses can be reused by anyone. As long as no two IP Addresses exist in the same network, you can reuse them in a different Network. This is also why most of the Networking work that the average System Engineer deals with, is within these private ranges.

### Classes
Of course those aren't the only ranges there are, because there is a second, completely seperate set of ranges. This one is called classes. Certain ranges are dubbed classes as well and you gotta know them at least a little to understand what's coming, so here's a table of what they are. Please not that again, only the first octave matters, the rest *could* be considered important too, but they're really not as the first octave tells you everything you need to know.

| Class Name | Starting Address | Ending Address |
|:-----------|:-----------------|:---------------|
| Class A    | 1.x.x.x          | 127.x.x.x      |
| Class B    | 128.x.x.x        | 191.x.x.x      |
| Class C    | 192.x.x.x        | 223.x.x.x      |
| Class D    | 224.x.x.x        | 239.x.x.x      |
| Class E    | 240.x.x.x        | 255.x.x.x      |

As you can see in the above table, Class A ranges all the way to 127. But please never forget that even though 127 is technically still Class A, it being localhost most often nullifies anything a class can influence. The only time I had to specify the class of localhost was in a theoretical test at school and even then the correct answer included reminding the teacher of it's localhost property. Apart from that, there really is not much more to them. There are 5 classes in total, ranging from Class A to Class E. However, Class D and Class E really don't matter and are often lumped in with Class C. So that's what I'm going to to as well. From this point forward, Class D and Class E won't be mentioned anymore and are used synonimous with Class C.

---

## Subnets and Hosts
I have mentioned networks and their size before. Just above in the table describing the private IPv4 Address Ranges, I used a slash with a number to indicate the network size, but how is any of that actually calculated? How do you look at that number and think "Ah yes, Network *big*". For that we need to recap the Binary Chapter. So if you didn't understand that yet, good luck ahead buddy.

We've discussed that an IP Address consists of 32 bits, seperated into 4 octaves, so there's 4 times 8 bits. The Slash and the number is what we call a Subnet Mask, and it is basically another IP Address, all though it works very differently. An IP Address can have any value from *zero* (0) to 255. A Subnet mask can have only 8 values per octave and a total of 32 values in general. That is because it is filled up from the left to the right.

| Subnet Mask Binary | Subnet Mask Decimal |
|:-------------------|---------------------|
| `00000000`         | 0                   |
| `10000000`         | 128                 |
| `11000000`         | 192                 |
| `11100000`         | 224                 |
| `11110000`         | 240                 |
| `11111000`         | 248                 |
| `11111100`         | 252                 |
| `11111110`         | 254                 |
| `11111111`         | 255                 |

These are all possible values any octave can have. But of course, there's another limitation to that. The one thing all of these Binary values have in common, all the bits to the left, have to have the value *one* (1). This rule takes over into the other octaves as well. So let's say that my third octave of my Subnet Mask is `11111000`. That would mean that my entire Subnet Mask would have to look like this: `11111111.11111111.11111000.00000000`, which correlates to `255.255.248.0`. As said, every single bit before the last *one* (1). Also has to be set to *one* (1). That also means that every single one afterwords has to be *zero* (0).

Now how does this tell us the size of our Network? Well, we can use this binary sequence sort of like a lock comparison. If we also write out our IP Address in binary, we would only be able to manipulate the bits that correlate to a *zero* (0) in the Subnet mask.

```
IP Address: 192.168.10.100
Subnet Mask: 255.255.224.0

IP Address Binary:  11000000.10101000.00001010.01100100
Subnet Mask Binary: 11111111.11111111.11100000.00000000
```

In the above example you should be able to see exactly on which bits the Subnet Mask is set to *one* (1). If you overlap these binary strings with each other, you can only manipulate the bits in the IP Address that correlate to a *zero* (0) in the Subnet Mask. This is going to become incredibly important again later so keep that in mind.

Again here, I know this is a very complex topic and I can only explain so much and give so many examples. So if there is confusion going on here with a will to learn more, @ me on the server and I'll help out to my best ability.

### Hosts
The Amount of Hosts in a Network is calculated rather simply. If we take the example from abox again, with the Subnet Mask of `255.255.224.0`, specifically the Binary Version of it, we only need to count the amount of *zeroes* (0) in it. in this case that would be 13. We have 13 zeroes in the binary version of our Subnet Mask. Now we can use that number as the power of *two* (2) and subtract *two* (2) from the result. So we calculate `2^13-2`.

That calculation is basically the same as the one that gives us the total amount of IP Addresses that exist. But only limited to the 13 zeroes in the subnet mask that we can manipulate in our Network. Then we subtract two because every Network has a Network Address and a Broadcast Address that we cannot use. That leaves us with the total amount of usable IP Addresses in our Network, which are also called Hosts.

---

## Network Address
The Network Address is always the lowest possible Address in any Network. It is used to identify the very Network itself, hence the name Network Address. I would like to remind you of a previous chapter now. The **IPv4 Address Ranges**. In the three examples I have listed there, for every one of them, the Network Address is the lowest possible Address which was listed.

Now it's easy to look at the and think *I understand* but actually calculating it from an IP Address and Subnet Mask might not be. This and the Broadcast Address, which will follow this chapter, have been the one thing I always struggled to explain to others. I promise you that it's not that hard once you get it, but you can't explain it in a very straight forward way.

Now I'd like to remind you of another previous chapter, **Subnets and Hosts**. In that chapter I have said, *"you can only manipulate the bits in the IP Address that correlate to a zero (0) in the Subnet Mask*". What you need to do is set every single one of those manipulatable bits to a zero. I will copy the exact IP Address from that chapter to explain it better.

```
IP Address: 192.168.10.100
Subnet Mask: 255.255.224.0

IP Address Binary:      11000000.10101000.000|01010.01100100
Subnet Mask Binary:     11111111.11111111.111|00000.00000000
                                             |
Network Address Binary: 11000000.10101000.000|00000.00000000
```

So in this example, the Network Address then translates back to *192.168.0.0*. This then results in the lowest IP Address in the entire Network and one of the two we subtraced in the Hosts calculation.

---

## Broadcast Address
The use of the Broadcast ID is also very straight forward. Anything that goes through this ID, will be send to every single client which is connected to the Network. It's used to broadcast messages throughout the Network. The Broadcast Address is calculated very similairly to the Network Address. The only difference is that the manipulatable bits are set to *one* (1) instead of *zero* (0). I wont dance around a redundant explaination too long and directly show you the above example again.

```
IP Address: 192.168.10.100
Subnet Mask: 255.255.224.0

IP Address Binary:        11000000.10101000.000|01010.01100100
Subnet Mask Binary:       11111111.11111111.111|00000.00000000
                                               |
Broadcast Address Binary: 11000000.10101000.000|11111.11111111
```

In this case the Broadcast Address translates back to *192.168.31.255*. This is the higest possible IP Address in that Network. It is also the second IP-Address that we subtract from the Hosts calculation.

---

## Network-ID
The Network-ID is a weird one. It exists. I have never in my entire career seen the Network-ID used even once outside of a theoretical test. It is calculated by subtracting the Network Address from the IP Address.

```
IP Address:      192.168.10.100
Network Address: 192.168.0.0

Network-ID:      0.0.10.100
```

You can think of the Network-ID as a localized Address inside of the Network. If you are inside of the *192.168.0.0* network, and you are talking to another client, you don't need to specify the *192.168.0.0* part. You can just identify yourself as *0.0.10.100* (or just *10.100*). At least that's what I believe what the idea of this ID is. In practice, it only creates confusion by obscuring details about the Network and even in the Backend of any program, the entire IP Address has to be spelled out because the IPv4 protocol doesn't work with half sized Addresses.

My tip is, forget about it if you can. It creates more confusion than anything else. If you are in a course or in school and are required to know about it. Remember how to calculate it, but you don't need to remember the function of it. It doesn't really have any in practice.

---

## Outro
That might have been quite a lot to process. I don't blame anyone who had problems understanding this. The IPv4 protocol is incredibly complex and these are just the basics of it. Next up would be Network Dimensioning. I have serious doubts if it'd even be worth it writing another Tutorial on how to do that. If you want to see that, let me know but also remember that I might switch it up entirely for my next tutorial.

If there are any questions that I failed to answer, please @ me on Discord and I'll be happy to answer them. If no one does, I will think I did a good job here.
