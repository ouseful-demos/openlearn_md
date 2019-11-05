# Session 11: Network principles



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/11_abstract_digital_network_image.tif)

From your earlier work on domestic networks you should already have a broad understanding about how data is transmitted across networks and the role of IP addresses and subnet masks. In this session you will be revising and deepening your existing knowledge on these topics. 

By the end of this session, you will be able to:

* explain the need for encapsulation of IP dataexplain the need for encapsulation of IP data

* understand the relationship between the TCP/IP protocol suite and the Open Systems Interconnection modelunderstand the relationship between the TCP/IP protocol suite and the Open Systems Interconnection model

* configure and test a simple network using PT Anywhereconfigure and test a simple network using PT Anywhere

* appreciate the need for IPv6 addressing and identify some of its main characteristics.appreciate the need for IPv6 addressing and identify some of its main characteristics.


## 11.1 Data transmission


Modern communication systems are the result of a gradual evolution from earlier systems, each bringing its own legacy of diverse technologies and infrastructure that need to be integrated for effective transition. An important task is to ensure that the content of messages is not compromised during the process, and this has led to the development of protocols whose role is to ensure that the message can be conveyed by various networking technologies in a way that is independent of message content. This has led to the development of protocols that work for almost any of the standard data transmission media and almost any kind of content, whether text, audio, video or whatever.

In this section you will revisit some of the concepts of data transmission introduced earlier in this course, keeping an eye on the historical journey that brings us to where we are.

Watch the video below (which is about 5 minutes long). This video considers the influence of the historical development of data transmission on the technologies used today.


### Data transmission

         ##-- MEDIACONTENT
        
Using the analogy of shipping containers, Session 1 introduced you to the idea of a layered approach to data transmission where each layer is responsible for a different aspect of the transport and delivery of the data. The important concept to take away from this is that the message content is completely independent of the mode of transport used and the services associated with it.

In Session 1 you were also introduced to the four layers of the TCP/IP protocol stack, which is the suite of protocols used on the internet and most other computer networks. In Session 3 you learned that the data created by the users at the Application layer is sent down the stack to the next layer, the Transport layer, where it is segmented into chunks of the same size called data units before being passed down the stack to the next layer. Each layer adds some information that enables it to do its job. This is called encapsulation. The Internet layer is responsible for getting data units across networks – sometimes via many different networks. The information that’s added here includes the IP addresses and subnet masks of the source and destination networks. Routers work at this level and use IP addresses and subnet masks to get information from network to network.

But why do we need to go to all this trouble of encapsulation? Why don’t we just launch data units out onto ‘the internet’, with the IP address uppermost, and have them successfully delivered? To answer this, we need to think about what the internet is. You might have heard it described as a ‘network of networks’ which makes it easier to understand.

The Internet is made up by interlinking many different sorts of networks – so many that it is impossible to draw a full map of them. The network technologies work together to cross geographical, system and ownership boundaries.

For example, the telecomms companies had nationwide and international high speed packet-based networks back in the sixties and seventies. These used addressing systems and technologies that were particular to that industry. Offices and businesses in the early 80s had small networks to join computers to each other, to printers and to storage devices using protocols like AppleTalk, Ethernet and token ring. Often companies would link their own remote offices and sites with networks connected together through leased lines that used different technologies. All these networks were like islands where different languages were spoken. There was no obvious way to get data from one such network to another, because initially people didn’t see the need for data to go outside its local network.

What IP addressing and routers give us are a way of getting data from one such ‘island’ to another. But on the island itself, data has to be carried by the local form of transport. That’s why IP data has to be encapsulated, and the outer layer of the encapsulation has to use whatever addressing system is particular to the network the data is being carried across. This is why we speak of ‘lower-level’ and ‘higher-level’ networks and addressing. The lower-level addressing is meaningful only on a local network, whereas the higher-level addressing has to be interpretable on external networks. By the way, a ‘local network’ isn’t necessarily a small one.

So, you’ve met the TCP/IP protocol suite, but there is another layered model that is commonly referred to in data networks. This is known as the Open Systems Interconnection model, abbreviated to OSI. In this model, seven layers are defined and, though the model is only conceptual, you will often encounter network functions being identified with OSI layers instead of TCP/IP layers. The OSI model is much more detailed. For example, the Physical layer (layer 1) deals with whether the physical medium is cable, optical fibre or wireless. The Data Link layer (layer 2) deals with the switching of data in the local network and the Network layer (layer 3) deals with routing data across the internet.

Fortunately there is quite a straightforward mapping between TCP/IP and OSI as you can see here. So when you come across functions identified as occurring at layer 3 of the OSI model, this is actually referring to the Network layer (or the Internet layer in the TCP/IP model).

Switches operate at the Network Access layer of the TCP/IP stack and the Data Link layer (layer 2) of the OSI model. Their purpose is to connect devices within a local network. Routers operate at the Internet layer of the TCP/IP stack and the Network layer (layer 3) of the OSI model. Their function is to connect networks. You can think of a router as being a gateway from one network to another. Within the network itself the router doesn’t really have any function related to delivery. That’s handled by the switch, and it’s why you can ping from one computer to another on the same network even if the computers aren’t configured to know about the router. Routers, therefore, continually direct incoming packets to other routers until a packet arrives that is destined for the local network that the router is a gateway to. Also, packets on the local network come to the router when their destination is outside the originating local network.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/63_data_transmission.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Think about


#### Question

*5 minutes*

Write two or three sentences to briefly explain the process of encapsulation of data units and why it is needed.


#### Discussion

Here’s one possible answer.

During transmission, a message is likely to be carried over a variety of communication networks using different methods and processes. Encapsulation of data units is the process of successively adding delivery information relevant to the protocol being used at a particular point in the journey.




### Activity 2 Test yourself


#### Question

*5 minutes*

1.

Network Access

Which layer of the TCP/IP protocol suite do switches operate at?

Data Link

Which layer of the OSI model do switches operate at?

Internet

Which layer of the TCP/IP protocol suite do routers operate at?

Network

Which layer of the OSI model do routers operate at?


#### Question

2. Select the true statements from the options below.

Without a router in a local network, it is not possible for two network devices to ping each other.

OSI stands for Organised System Information.

Encapsulation is the process of adding protocol information to a data unit.

Both the OSI model and the TCP/IP protocol suite have a layer called ‘Application’.




## 11.2 Routers and IP addresses


You’ve learned about IP addressing and subnet masks in earlier sessions. This section serves as a brief reminder of your earlier work and provides an opportunity to practise and test your understanding of subnetting.

Watch the video below, which is about 1.5 minutes long.


### Routers and IP addresses

         ##-- MEDIACONTENT
        
Routers use IP addresses to direct packets. IP addressing has been covered very thoroughly in earlier sessions so you are already familiar with the host portion, network portion and subnet masks.

An IP address can identify an individual computer device (known as a host) or it can identify a network. The network address is always the lowest address in the network, which in binary will end in a zero, though it may not in dotted decimal. I’ll demonstrate this by using the IP address 192.168.1.0 with a /28 subnet mask. This means that the last four bits are the host part.

The first subnet would have addresses from 192.168.1.0 to 192.168.1.15, and the network address is 192.168.1.0, as expected. The second subnet goes from 192.168.1.16 to 192.168.1.31. The network address is now 192.168.1.16.

This looks anomalous until we look at the binary rendering of the last octet, which is 0001 0000. Here the host part (i.e. the last four bits) is all zeros, as befits a network address; but this is obscured in the decimal representation, which is 16, because this represents the entire octet, not just the host part.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/64_routers_and_ip_addresses.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 3 Test yourself


#### Question

*5 minutes*

1. How many IP addresses can be assigned to hosts on a subnet with a subnet mask of 255.255.255.240?

13

14

15

16

Addresses with a subnet mask of 255.255.255.240 will run from XXX.XXX.XXX.240 to XXX.XXX.XXX.255. This provides 16 possible addresses. The lowest of these (XXX.XXX.XXX.240) will be assigned to the network address and the highest (XXX.XXX.XXX.255) is the broadcast address, leaving 14 addresses for the hosts.


#### Question

2. Which of the following correctly describes the IP address 192.168.2.32/27?

It is a subnet network address.

It is a subnet host address.

It is a subnet broadcast address.

With a subnet mask of /27 the last five bits are the host part. The binary equivalent of 32 is 100000 so this subnet has the addresses from 192.168.2.32 to 192.168.2.63. Therefore 192.168.2.32, being the lowest address, is the network address of this subnet.




## 11.3 Configuring a network


In this section you will configure and test a simple network using Packet Tracer Anywhere.

First watch the video below, which is about 5 minutes long. This video reminds you of the need for IP addresses and demonstrates how to configure a simple network using Packet Tracer Anywhere.


### Configuring a network

         ##-- MEDIACONTENT
        
I’m now going to look at an example of two networks joined by a router which is, as yet, unconfigured.

When you’re configuring a network it’s always useful to construct a table giving the IP addresses you intend to use. From my table you can see that PC0 and PC1 are in the network 192.168.1.0/24 and PC2 and PC3 are in the network 192.168.5.0/24.

You already know that switches operate at the Network Access layer of the TCP/IP stack (or the OSI layer 2), whereas IP addresses are used at the Internet layer of the TCP/IP stack (or the OSI layer 3).

So why do we need to give the PCs an IP address? In the early days of local networks, when they just carried local data, IP addresses wouldn’t have been needed, just MAC addresses. But a MAC address is meaningless on an external network, so we need an addressing system that will at least deliver inward traffic from external networks to the correct destination network. Unlike the MAC address (or any other form of address that has only local significance), the IP address and the subnet mask are meaningful on external networks.

The subnet mask isolates that bit of the address that relates to the network, and is all that’s needed to get the data across other networks to the destination network. At the destination network, though, the host part of the IP address is unique to the receiving device, but there has to be a look-up table from which the corresponding MAC number can be read off; we will look at in the next session. Similarly, outbound data from a network needs to be directed at the router, because that’s the gateway out of the local network.

So now I’ll configure the network. I’m using Packet Tracer Anywhere for this demonstration. First I’ll configure the PCs with the IP addresses identified in the table. I’ll start with PC0 which needs an IP address of 192.168.1.2.

I will now click PC0 and click ‘Edit device’ and click the ‘Interfaces’ tab, leaving the default interface as FastEthernet0 and editing the address and the subnet mask. Now I’ll do the same for PC1 to give it the IP address 192.168.1.10. Again, I’m leaving the default gateway unchanged. In the same way I’ll configure the IP addresses on PC2 and PC3, but I won’t demonstrate that here. I’ll just jump forward to the next stage.

I can check I’ve correctly configured the PCs by opening the command line and typing the command `ipconfig`. Here you can see the correct IP address has been set for PC0.

Leaving the command line open for PC0 I’m going to ping PC1. Here you can see the ping has been successful.

What will happen if I try to ping PC2, which is in a different network? Let’s give it a try. You can see that the ping has failed. That’s not surprising as it’s in a different network and I haven’t yet configured the router. I’ll do that next.

I will now click on the router. Then click on the menu item ‘Open console’ to show the command line of the router. I need to answer ‘no’ at the first prompt ‘Continue with configuration dialog’ and then Return. I’ll type `en` to enable the privileged exec mode. I now need to type `conf t` to enter the configuration mode of the router. To configure the interface G0/0 I first need to enter the command `int g0/0`. This enters the interface configuration mode.

Next I type `ip add 192.168.1.1 255.255.255.0`. And you mustn’t forget to add `no shut` to activate the interface. Now I’ll go through the same process to configure interface G0/1 on the router, this time giving it the IP address 192.168.5.1.

So now I’ll try to ping again from PC0 to PC2. It still doesn’t work, but that’s because I still need to configure the default gateway settings on each PC. I have included the `ipconfig`command to show the IP settings. Each PC needs to be configured with the IP address of the router’s Gigabit Ethernet port that connects to that network. For PC0 and PC1 the default gateway is the router port G0/0, which for this network is the address 192.168.1.1. So I’ll edit the settings for PC0 accordingly.

I’ll do the same for PC1, but won’t show it in this demonstration. For PC2 and PC3 the default gateway is the router port G0/1, which for this network is 192.168.5.1. Again, I’ll set this for both PCs, but won’t show it in this demonstration. Instead I’ll jump straight to the fully configured network. I have included the `ipconfig`command to show the IP settings. Now I’ll try and ping again from PC0 to PC2. And this time it is successful.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/65_configuring_a_network.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Sort it out


#### Question

*15 minutes*

1. Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt11.3) in a new tab or window so you can read these instructions.

In this scenario, two networks – each comprising a switch and two PCs – are joined by a router. PC0, PC1 and the router interface G0/0 are already configured. A ‘spare’ PC is provided at the bottom for use in step 6 of this activity.

2. Configure PC2, PC3 and the router interface G0/1 with the following:
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>IP address</th>
<th>Subnet mask</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC2</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.2</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC3</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
</tr>
</tbody>
</table>

(Hint: don’t forget to configure the default gateway on each PC.)

3. Can you ping PC0 from PC3? (Hint: you will need to find out the IP address of PC0.)

4. Check the configuration of PC0. Is the default gateway configured? Is it correct? (Hint: check the IP address of the network’s router interface.)

5. Can you ping PC0 from PC3 now?

6. Add another PC to the network 192.168.2.0 and configure it with the IP address 192.168.2.15/255.255.255.0. For this step of the activity, use the ‘spare’ PC provided at the bottom.

7. Can you ping each of the other four PCs from this PC?

In step 3 the ping from PC0 to PC3 would have failed. When you checked the configuration of PC0 you should have discovered that its default gateway was incorrectly set to 192.168.1.0. PC0 is connected via a switch to router interface G0/0 which has an IP address of 192.168.1.1 so PC0 was unable to send a reply to the ping. Once you corrected PC0’s default gateway to 192.168.1.1, the ping should have been successful. When you added the additional PC you should have set its default gateway to 192.168.2.1 to match the IP address of router interface G0/1. You should have found that you could then ping each of the other PCs with the exception of PC1, which also has an incorrect default gateway set.




## 11.4 Introduction to IPv6


Though the use of the IPv4 addressing scheme has been extended by the adoption of subnet masks and Network Address Translation (NAT), there still aren’t enough IPv4 addresses to satisfy current, let alone future, needs. To overcome this problem, IPv6 (Internet Protocol version 6) has been developed.

Watch the video below, which is about 5 minutes long. This video provides a brief introduction to IPv6.


### Introduction to IPv6

         ##-- MEDIACONTENT
        
In this video I’m going to give a very brief introduction to IPv6. Up to now we’ve only been looking at IPv4 addresses and you may remember from earlier sessions that we’re running out of them. Despite the introduction of NAT and subnetting there still aren’t enough public addresses to meet all current and future needs and this is the main reason that IPv6 was developed.

You should recall that  IPv4 has address that use 32 bits, which provide over 4 billion addresses. An IPv6 address has 128 bits, which doesn’t sound that much bigger but if you try raising 2 to the power of 128 you’ll find that in decimal it produces a number that’s too big to say with ease. It’s usually referred to as ‘around 340 undecillion’. The IPv6 address space is so big that according to one well-used quotation ‘we could assign an IPv6 address to every atom on the surface of the Earth, and still have enough addresses left to do another 100+ Earths.’

An IPv6 address is written as eight groups of 4 hexadecimal numbers, each group separated by a colon. (You were introduced to hexadecimal in an earlier session.) Long strings of numbers like this are very difficult for humans to read, even when separated by colons. But there is a way of shortening them, which simply involves removing some of the zeros. This is done by a two-stage process. First, completely removing any leading zeros at the start of each block. Next, replace any consecutive zero blocks by double colons – though this can only be done once. If there is an additional consecutive zero block, this has to remain. Can you think why?

The reason is that the original address is recovered by reinserting the zeros until there are again 8 blocks of 4 hexadecimal numbers. If you were to remove more than two consecutive blocks of zeros, wewouldn’t know how many blocks to reinsert for each double colon.

Next we’ll look at the IPv6 address format. Like IPv4 it has two components: one that identifies the network – called the network prefix or ID – and one that identifies the host – called the interface ID. Note the different terminology used here: IPv4 refers to a host portion while IPv6 refers to an interface portion. The IPv6 terminology is much more correct as a network device can have a number of different interfaces, each with its own IP address. For example, think of a router with its multiple interfaces, or a laptop, which typically has an interface for its wired connection and a Wi-Fi interface. Each with its own IP address, if they are used simultaneously.

In IPv4 both address portions have variable lengths but in IPv6 these lengths are fixed, both being portions of 64 bits.

In earlier sessions you learned that the highest IPv4 network address was reserved for broadcasting to all devices on the same network. In IPv6 there is no broadcast transmission, but there are three other modes that are available. Unicast for transmissions from one interface to another – these addresses are what most of us use most of the time for sending and receiving emails or web browsing; multicast for transmissions from one interface to multiple other interfaces; and anycast for transmission from one interface to one other from a list of multiple interfaces. Each of these three address modes has a specified address structure to identify what type of address it is, but I won’t go into that here as this is just a general introduction to IPv6.

The increased address space of IPv6 gives it its main advantage over IPv4, but there are other benefits too. I’ll briefly identify them, but it’s beyond the scope of this course to explain them. IPv6 results in more efficient routing by using a hierarchical addressing structure. Its packet header structure is simpler than IPv4’s. The increased address space means there is no need for NAT in an IPv6-only network. IPv6 packets have a larger payload giving improved throughput and efficiency. IPv6 is more secure than IPv4.

It’s never been suggested that one day we will switch off IPv4 and everybody will start using IPv6. This is because there are ways of handling both IPv4 and IPv6 over the same network. This, coupled with the development of subnetting and NAT, helps to explain why the uptake of IPv6 has been gradual. When I checked this Google page in April 2019, it told me that only 27% of its users were connected over IPv6. You might like to check this out for yourself to see how it has changed since then.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/66_introduction_to_ipv6.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 5 Test yourself


#### Question

*5 minutes*

1. How many bits are there in an IPv6 address?

32

64

128

256


#### Question

2. IPv6 addresses are organised into groups of how many bits?

4

8

16

32


#### Question

3. Select the transmission modes of IPv6.

Anycast

Broadcast

Duplicast

Multicast

Singlecast

Unicast




## 11.5 Summary of Session 11


In this session you have seen how today’s data transmission technologies are the result of an evolutionary process and why the encapsulation of data units enables a message to be carried over a variety of different networks. You have revisited IP addressing and subnet masks, and you have practised configuring and testing a simple network using Packet Tracer Anywhere.

---


### Commands

In this session you have used the following commands.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Command</th>
<th>Result</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`configure terminal`</td>
<td class="highlight_" rowspan="" colspan="">Enter global configuration mode</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`enable`</td>
<td class="highlight_" rowspan="" colspan="">Enter privileged execution mode</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`interface *&lt;interface ID&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Enters into interface configuration mode</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`ip address*&lt;IP address&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Configure an IP address and subnet mask on an interface</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`no shutdown`</td>
<td class="highlight_" rowspan="" colspan="">Restarts the interface</td>
</tr>
</tbody>
</table>

---

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
anycast
</td>
<td class="highlight_" rowspan="" colspan="">
Data transmissions from one host to selected others.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Open Systems Interconnection (OSI) model
</td>
<td class="highlight_" rowspan="" colspan="">
A conceptual model that defines a 7-layer framework for the implementation of networking protocols.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
multicast
</td>
<td class="highlight_" rowspan="" colspan="">
Data transmissions from one host to multiple others.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
unicast
</td>
<td class="highlight_" rowspan="" colspan="">
Data transmissions from one host to one other host.
</td>
</tr>
</tbody>
</table>

---

