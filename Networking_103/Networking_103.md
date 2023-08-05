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

Every column in which the binary number is *zero* (0), the decimal number also turns into as it is only a decimal representation. If you now add all these numbers together, you get 202. Meaning that the Binary number `11001010` equals to the decimal number `202`.

If you understand why and how these 8 digits interact and influence each other, you understand the binary system. To understand the IPv4 addressing system, you only need to understand the Binary system up to 8 binary numbers. If you have trouble understanding it, feel free to reach out or @ me on the server so I can help you with it.

---

## IPv4 Address Ranges
