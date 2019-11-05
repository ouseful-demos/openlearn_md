# Session 5: Dynamic configuration



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/05_digital_computer_data.tif)

This session considers some of protocols used to configure small networks such as those found at home. Dynamic Host Configuration Protocol (DHCP) makes it much easier to manage networks that devices may join and leave. Network address translation (NAT) makes it possible to use private addresses and still communicate with the internet. 

By the end of this session, you will be able to:

* 
understand how DHCP configures host devices automatically


* 
understand how NAT operates and helps reduce demand for IP addresses


* 
set up DHCP on a domestic gateway and configure host devices to obtain network configuration using DHCP.



## 5.1 Dynamic Host Configuration Protocol (DHCP)


In this section you will see how networks can be configured so that new devices can join automatically and not have to be configured manually.

Mobile devices such as laptops and smartphones may leave and join different networks frequently: for example, you may use the same device at home and work, and also on the bus or in a café. A mobile device needs a different configuration for each network; it would be annoying and error-prone if the user had to do this manually. Other networked devices, such as security cameras or central heating thermostats, have no keyboard or screen, so they must connect automatically.

Dynamic Host Configuration Protocol (DHCP) is used to configure network devices automatically. DHCP is specifically designed for networks where the connected devices (hosts) change frequently, using a protocol to achieve a correct configuration.

Now watch the video below, which is about 5 minutes long. It shows how new devices are configured as they join a network.


### DHCP in action

         ##-- MEDIACONTENT
        
So let’s see how it works. Here’s my ‘Home’ network over here on the left. I’ve also got ‘Work’ network on screen as well, but I’ll talk about that in a minute. Let’s focus our attention on the ‘Home’ network here on the left, where I have a typical small domestic router. It happens to be a Wi-Fi access point as well, but I’m going to start just using wired connections, but actually everything will work just the same because DHCP will work across different transport layers.

So let’s see what happens if I bring my laptop into the network; let’s say I’ve just bought myself a new laptop, which will need configuring. So I’m going to click on it to configure it. But instead of typing in an IP address as we’ve done previously, I’m just going to click ‘DHCP’ and allow it to get configuration automatically. Nothing is going to happen until I actually connect it though, so let’s get a cable and connect from the laptop Ethernet port to the router – pick a free Ethernet port – and then I need to sit back and wait for the configuration to take place. So DHCP is a protocol that means a conversation, an exchange of messages between the devices – the laptop and the router – until they’ve between them sorted out what the correct configuration is. So I need to be patient while those messages are exchanged. And this is Packet Tracer and that is simulating all that exchange of messages, so I need to wait for that to happen. The lights have now gone green, so hopefully I can just check that the configuration is what I expect and I now have some values in here. And if I open a command prompt I can type in `ipconfig` and check to see what my configuration is. So this laptop has been given a configuration. It’s been given an IPv6 address, which we’re not going to talk any more about. It has an IPv4 address, which is 192.168.0.100 and it’s been given a subnet mask as well, 255.255.255.0, and a default gateway, 192.168.0.1. Now, the default gateway is the gateway to the internet – in this case it is the router that we’ve just connected to. So I can just check to see that that is working by doing a ping to the router, 192.168.0.1, and just check that we do get an exchange. And there we have some pings going backwards and received so that has a good connection. So that’s looking very good.

Let’s go wild and have a second laptop in the network. I’m going to do the same configuration again, just turning DHCP on and that’s all. I’m going to get another cable and I’m going to connect from that laptop Ethernet port to another free Ethernet port on the router. And again, I’ll need to be patient while that configuration takes place. Hopefully, I’m going to get an IP address; hopefully, I’m going to get a different IP address from the first laptop. So two different devices are going to need two different IP addresses to work on the same network, otherwise confusion will reign. Lights are still amber … there we are, gone green now. So I’m now going to open the command prompt on this laptop, do `ipconfig` on the second laptop, and we can see that we have an IP address. The IP address is different: it’s 192.168.0.101, so it’s different from the first one. The same subnet mask, because it is on the same subnet; the same default gateway because it is going to use the same router as a gateway to the internet, if the internet was connected. And I can check now that I can ping from the second laptop, which is where I’m sitting at the moment, to the first laptop: I can do ping 192.168.0.100 was the address of the first one. And there we are, we’ve got a reply from 0.100, some successful pings so I have got a path between the two laptops through the router acting as a switch.

So that’s all looking very good. And I could go on adding new devices, mobile devices using Wi-Fi – it would work in exactly the same way.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/27_dhcp_in_action.jpg)

         ##-- ENDMEDIACONTENT
    


Now watch the video below, which is about 3 minutes long. It shows how one device receives a new configuration when it moves from one network to another.


### DHCP continued

         ##-- MEDIACONTENT
        
What would be interesting now is to see what happens if I disconnect my laptop from my home and take it to work – bring it up here and take it to work. Look for another connection, so let’s get another cable and go from the Ethernet port to a spare port on the router. And then again I’m going to need to sit back and be quite patient while the DHCP on that router kicks in and gives me a configuration. While it’s doing that, I think I might just point out you might think there’s a bit of a problem here because the IP address is at the moment either not set or set incorrectly because it was on the wrong network. So how is communication happening at all? Well, the answer to that is that it’s working at the Ethernet level because it’s able to do that just within the local network because each device has got a unique MAC address, so Ethernet communication can work without IP addresses being correctly set. And it can be done as a broadcast: the laptop can just broadcast and say ‘is there a DHCP server out there?’ and then the DHCP server will reply and start the conversation that leads to configuration.

So let’s check to see that I have got configuration on the laptop now. I’m going to do ipconfig again, which was set at 192.168.0.100 at home. Let’s see what it is now. Ah, it’s changed. So we now have an IP address which is 172.16.0.100, so that fits with a different network; has a different subnet mask, and a different default gateway because I’m now talking to a different router, 172.16.0.1. And so that’s all looking good. So you can see that DHCP is able to take a dynamic host – take a host from one place to another – and sort out the configuration all automatically: there was nothing that I needed to do to type that in.

So there we are, DHCP (Dynamic Host Configuration Protocol).


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/28_dhcp_continued.jpg)

         ##-- ENDMEDIACONTENT
    


In the video you saw that instead of manually setting up the IP address for every device on a LAN, you can use DHCP (Dynamic Host Configuration Protocol) to do it automatically. A new device joining the network – for example a PC plugged in to an Ethernet socket or a tablet connecting to Wi-Fi – will receive an IP address.

A DHCP server has a pool of IP addresses which it can issue to devices as they join the network. On a home network the router will act as the DHCP server, but a dedicated DHCP server may be used in a business network.

Besides the IP address, DHCP will configure other important network parameters such as the subnet mask and default gateway.

The IP address is granted only for a limited period of time (a lease) such as 24 hours. If the device stays connected or reconnects before this lease expires, it keeps the same IP address. If the lease expires, the server can reallocate the IP address to any new device that connects. If the original device reconnects, it will be given a different IP address.

Some host devices in a network may need a permanent static address rather than obtain an address from the DHCP pool which might change. For example, a home gateway is usually given a static address that never changes.


### Activity 1 Think about


#### Question

*10 minutes*

Could you set up a coffee shop Wi-Fi network?

Customers expect to have wireless access so they can use their tablets and laptops. What would you have to consider when you set up a Wi-Fi network?


#### Discussion

You will certainly want to set up DHCP on your network so customers don’t need to reconfigure their devices manually. Some specific issues to consider are:

* 
The pool of addresses should be large enough for the number of customers you expect at any one time.


* 
The lease time should be short, or you may run out of available addresses.


* 
You may want to reserve some static addresses for the security cameras, tills or credit card terminals.


There are other considerations – for example making sure that your network is secure – which won’t be considered here.




### Activity 2 Try it out


#### Question

*15 minutes*

1. 
Open [PT Anywhere](https://forge.kmi.open.ac.uk/onl1-pt5.1a) in a new tab or window so you can read these instructions.

In this scenario, there is a home gateway router and one PC already connected.


2. 
Add the laptop to the network.


3. 
Check the laptop configuration – is DHCP turned on?


4. 
Connect the laptop to the home gateway.


5. 
What IP address is it assigned?


6. 
What other configuration does it receive?


7. 
Can you ping the laptop from the PC?


8. 
Can you ping the PC from the laptop?


9. 
Disconnect the laptop from the home gateway.


10. 
Connect the second PC to the home gateway.


11. 
What IP address is the new device assigned?


12. 
Now reconnect the laptop to the home gateway.


13. 
What IP address is it assigned now?



#### Discussion

When you add a new device to a network running DHCP, it will receive an IP address and subnet mask. The IP address will be different from other devices already on the network. (The new device will normally also receive the address of the home gateway but this is not simulated here.)

If you disconnect a device, its IP address won’t immediately be allocated to a different device. As long as the lease has not yet expired, you can reconnect the device and it will retain the same IP address.




### Activity 3 Sort it out


#### Question

*15 minutes*

1. 
Open [PT Anywhere](http://forge.kmi.open.ac.uk/onl1-pt5.1b) in a new tab or window so you can read these instructions.

In this scenario, there is a home gateway router and one PC already connected.


2. 
Add the laptop to the network by connecting it to the gateway.


3. 
Can you ping the laptop from the PC?


4. 
Check the laptop and PC configuration – is DHCP turned on?


5. 
Check the gateway configuration – is DHCP turned on and configured sensibly?


6. 
If not, fix it and try again.



#### Discussion

In this network, DHCP wasn’t turned on and so a new device would not be configured correctly. Once DHCP is turned on at the gateway router, new devices will be granted a new IP address automatically.




## 5.2 Private addresses


In this part you will look at the problem raised by the use of private IPv4 addresses that are commonly set up for home networks.

Now watch the video below, which is about 4 minutes long.


### Private addresses

         ##-- MEDIACONTENT
        
Welcome to a session about NAT, network address translation.

Here I am at home, with a typical setup: I’ve got a desktop and a laptop connected to a home gateway which connects to the internet.

Let’s just check that everything is set up correctly. I’ll open a terminal on my desktop, type in `ipconfig`. My desktop has got an IP address of 192.168.0.100, and is connected through my home gateway which has an IP address 192.168.0.1. That looks good.

I can check that I can ping that gateway. And there we are, I’ve got some pings coming back from that.

I can also check to see if I can ping my laptop, which has got the IP address 192.168.0.101. Again, I’ve got some pings in return.

So that’s all good – the gateway is working as a switch, it’s dealing with traffic on the local area network, the LAN, which is my home network.

MSo my colleague Helen is also at home, with her desktop and her laptop. Her LAN is working fine too. She has the same gateway from the same ISP. So in fact the configuration is identical.

If Helen opens a terminal on her machine and does `ipconfig`, she should see exactly the same configuration as I did: 192.168.0.100 for her own IP address, the default gateway 192.168.0.1 for her home gateway.

Now on the face of it, this can’t be right. On the internet, every connected device has to have a unique IP address or the traffic can’t be routed correctly, but here we clearly have two PCs with the same IP address.

If I tried pinging from my machine to Helen’s machine, that’s clearly not going to work because they have the same IP address.

But in fact there is another reason why it wouldn’t work. The addresses used here, starting 192.168, are in a private address range. These are intended for use in private networks, like a home network, and routers will never pass those addresses through to the rest of the internet. They can be used to network within each LAN happily enough, but they can’t be reached over the internet.

You might have spotted another potential issue: we also have two identical home gateway routers on the internet, and both are set up as a gateway at private address 192.168.1.1, so is that a problem?

Well, no, it’s not a problem, because a router is always a two-faced device. It has one network interface that sits on the local area network, the inside. And it has another interface that sits on the outside, on the internet. Each interface will have a different IP address.

So if I just reveal the setup of this gateway, you can see both IP addresses: 192.168.0.1 on the LAN side and 88.0.0.2 on the internet. And on the other home gateway: 192.168.0.1 on the LAN and 99.0.0.2 on the internet. So the outside IP addresses, the ones which are on the internet, are different, and there’s no clash between them.

The domestic gateways will have been supplied by an ISP, in this case the same ISP, and they will be configured to have different IP addresses – probably by DHCP running from a central server at the ISP.

So we’ve seen that in a typical home network, the devices on it use private addresses, and different networks might in fact use identical IP addresses, so they can’t be visible on the internet. But the IP address of the outward side of the gateway router will have a unique IP address, so the gateway itself can be part of the internet. We’ll see how this lets home devices communicate with the internet through the gateway.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/29_private_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


Home networks normally use addresses in an IPv4 private address range, most commonly starting 192.168.0.0. Addresses are obtained by DHCP from the home gateway provided by an internet service provider (ISP). (An ISP is the company who provides – and charges for –  access to the internet from your home over broadband, optical fibre or satellite.) The ISP has many thousands of customers, each of whom has a home network on which devices might end up with the same IP address.

Since private addresses are not forwarded by routers, using the same IP address in different home networks does not cause clashes. However, private addresses can’t communicate with the internet. The gateway does connect to the internet; it is a router and has two network interfaces: one on the internal LAN and one on the internet. The IP address for the router’s external interface is not private so the router is able to communicate with the internet.


### Activity 4 Test yourself


#### Question

*5 minutes*

Identify the __two__ correct statements in the list below.

IP addresses starting 192.168.0.0 are private addresses and are commonly used in home networks.

ISP stands for Internet Secret Protocol and is used to deliver packets to private addresses.

No. ISP is an abbreviation for internet service provider.

Devices can never have the same IP address, even on different home networks.

No. Devices on different networks can be given the same IP address as long as it is from a private range.

ISP is an abbreviation for internet service provider.




## 5.3 Changing addresses


In this part you will see how the gateway router’s external public IP address can be substituted for the private IP address of traffic leaving a private network. This translation of addresses is at the heart of network address translation (NAT).

Now watch the video below, which is about 3 minutes long.


### Changing addresses

         ##-- MEDIACONTENT
        
We’ve seen that I can ping from my computer to other devices on my own network. Let’s see if I can ping to somewhere on the internet such as the MegaCorp web server here. I’ll open a console and ping it: `ping` and then the address of the MegaCorp’s web server, which is 77.0.0.2. And there we are, we do have some replies. So from my desktop I can certainly ping out on to the internet and get an answer.

I can also open a web browser; I am going to type the address of the web server (77.0.0.2 – I’m using the IP address rather than the domain name), and then we can see that the server responds with its web page which I can browse around. So I can reach MegaCorp’s web server and Helen can do the same on her computer: type `http://77.0.0.2`and reach exactly the same website as before. So this is Helen’s desktop reaching MegaCorp’s website.

But that does raise another problem: the server has had two requests that seem to have come from the same IP address: my address is 192.168.0.100, and Helen’s is also 192.168.0.100. If the server were to just reply to that address, where will the packets end up? Myine machine or Helen’s machine? It just ain’t gonna work. So that is a problem, and we’ll have to see how that is sorted out.

We’ve seen that the gateways themselves have got unique IP addresses on the internet. So if those devices had actually asked the web server for a web page, there would be no problem: the replies could be directed back to the unique IP addresses that belong to those two different gateways.

So actually that’s the answer – the gateway is going to cheat. When it gets my request, it will take out the IP address of my desktop and replace it with its own IP address, and then forward that to the web server. Then the web server can reply and the packets will be routed back to the gateway.

Of course, the gateway has to remember what it has done and reverse the trick, that is take out its own IP address and put back my IP address as the destination. Then it passes the packets on for switching to the correct host on the LAN, my desktop.

So this is network address translation, NAT.

And that all works OK now – Helen and I can both request the same web page at the same time because by the time the requests reach the host server, the source IP addresses have been fiddled so that requests appear to come from two different gateways.

On the return journey, the page will be routed back to the correct gateway. Then each gateway has to reverse the swap it made so the page now has the destination address 192.168.1.100. That is in the private address range and will be switched only on the LAN, so it doesn’t matter that both gateways are sending to the same IP address.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/30_changing_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


The IP address on the external network interface of the gateway router is able to communicate with the internet. The gateway router will replace private source addresses with its own public address as it forwards traffic from the private LAN to the internet. The traffic now appears to come from the gateway itself and does not contain a private address; it can therefore be routed successfully over the internet. When traffic returns to the gateway router, the gateway will reverse the swap, replacing its own address with the private destination address, and then switch the packets on the LAN.

This is network address translation (NAT). NAT allows devices with addresses in the private range to communicate with the internet. It also means that all devices on the private LAN effectively share a single IP address to connect to the internet.


### Activity 5 Test yourself


#### Question

*5 minutes*

Identify the __one__ correct statement in the list below.

NAT is an acronym for network address transmission.

No. NAT is an acronym for network address translation.

A typical home gateway router can carry out network address translation (NAT).

If you want to use NAT on a typical home network, you will need to buy an additional computer to carry out network address translation.

No. A typical home gateway router will carry out network address translation (NAT).




## 5.4 NAT in detail


In this part you will examine the IP packets in detail to see network address translation happening at the router.

Now watch the video below, which is about 3 minutes long.


### NAT in detail

         ##-- MEDIACONTENT
        
I’m going to have a look at how NAT works in a little bit more detail. I’m using Cisco Packet Tracer to do that. I’ve recorded what happens when I send an HTTP page request to a web server, the MegaCorp web server here. We’ll look at the packets to see what’s happening to that request in detail.

So this shows my request as it’s about to start; if I step through, we’ll see that packet reach the gateway. Now we can look inside it: this is the packet as it reaches the gateway router. You can see the source address, my machine 192.168.0.100, and the destination, the IP address of the web server, 77.0.0.2.

Now is when the network address translation occurs – if I look at the outbound packet (when it leaves the gateway router) it has been changed. It appears now to be coming from the IP address 99.0.0.2 which is the gateway router itself. It still has the same destination IP address.

This packet will now be passed over the internet to the web server. Let’s look at it when it gets to the server. You can see it appears to come from the source 99.0.0.2 which is the home gateway router, not my desktop at all.

The web server will now send a reply back. Again, let’s have a look in detail at the reply. The source of the reply will be the web server, 77.0.0.2, and the destination will be the gateway –according to the web server, that’s where it came from – so the destination is 99.0.0.2, my gateway.

At the gateway, that’s going to be changed again. This is the inbound packet; the outbound will be changed. It still appears to come from the web server, 77.0.0.2, but now the destination’s been translated to 192.168.0.100, which is my desktop. So the router can now pass it on to the LAN, through the switch, to the correct device, my desktop.

So you can see the packets moving through the network, and network address translation at the gateway. It takes my original desktop address and replaces it systematically with the gateway’s own address and then forwards it out to the internet, receives any replies that come in addressed to the gateway, and says ‘actually that really wasn’t for me’ and replaces the original source address – my desktop in this particular case – and then forwards it on the LAN side, on the internal network.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/31_nat_in_detail.jpg)

         ##-- ENDMEDIACONTENT
    


Network address translation happens in the router. The router inspects each outgoing IP packet: if the source address is a private address, the router will replace this with its own public IP address. It will also record which translations it has made. Returning traffic will arrive with the router’s own IP address as the apparent destination, but the router will inspect each packet and replace the destination address, using the information it stored earlier to reverse the translation back to a private address. The packet can then be switched over the LAN in the normal way.


### Activity 6 Test yourself


#### Question

*5 minutes*

Identify the __one__ correct statement in the list below.

A router will not look at a packet containing a private address; it will just pass it on unchanged.

No. A router performing NAT changes private addresses in IP packets to the router’s own public address.

NAT changes private addresses in IP packets to a random IP address.

No. A router performing NAT changes private addresses in IP packets to the router’s own public address.

NAT changes private addresses in IP packets to the router’s own public address.

Computers and other devices in a private network always substitute the router’s address for their own before they send IP packets over the LAN.

No. Devices always send using their own IP address (private or public) so that switching works correctly, but the gateway router carrying out NAT will translate private addresses to its own address when routing traffic to the internet.




## 5.5 NAT and ports


In this part you will see how the IP port address allows the router to separate traffic intended for different devices in its private LAN.

Now watch the video below, which is about 5 minutes long.

Note that at 02:41 the speaker says ‘would then be 192.168.1.100, port 4321’ but meant to say ‘would then be 192.168.0.100, port 4321’; and at 03:12 says ‘in my case, 192.168.100, port 4321’ but meant to say ‘in my case, 192.168.0.100, port 4321’.


### NAT and ports

         ##-- MEDIACONTENT
        
You’ve seen how network address translation at the gateway router allows devices with private addresses to access the internet by systematic swapping of the original private address with the router’s internet address.

But that’s not quite the full story. What happens now if I ask for the same web page, once from my desktop and once from my laptop? The gateway is going to do its network address translation and change the source IP address in both requests to be its own. The web server will get two requests so it will send two replies. That’s fine, but when the replies come back to the gateway, one of these should be sent to my desktop and one to my laptop. Well, how is it going to sort them out?

There is a way to deal with this. I have been taking a liberty by only talking about IP addresses as the source and destination of traffic. But strictly I should also include the IP port number. IP port numbers are used to keep different streams of traffic separate on one computer. So for example, my PC may have one stream open to a website, another open to my email account. Traffic will come back to my IP address and be delivered to my PC, but it still needs to be delivered to the correct application. And it’s the port number that’s used to do that.

By the way, there’s possible confusion here with the network port as meaning the hole in which a cable’s going to be plugged – so here we’re talking about a software thing, not hardware. But the port is similar in the sense that both types of port are ways to keep connections separate.

Now, there are well-known port numbers for some traffic, for example port 80 is used for HTTP, that is web page traffic. So a request for a web page at MegaCorp will be to 77.0.0.2 port :80, while a mail request at MegaCorp might be to 77.0.0.2:23. The two port numbers, 80 and 23, will keep the traffic separate.

So my source address will also have a port number as well as an IP number. What will that be? Even if I’m asking for a web page, it won’t be port 80: the well-known numbers are reserved for server hosts, but there are many others available. My browser is acting as a client, so it will simply ask for a new unused port number from the operating system when it opens a connection to the website – it might get 4321 as the port number, so the full source address would then be 192.168.0.100:port `4321.*Audio mistakenly says 192.168.1.100*`

Now, the gateway, when it replaces my IP address in outgoing packets, can also replace the port number. It will of course keep a record of what translations it’s handling in a table, so when packets come back to the router, it can be used to look up the port number it used, and change the port number and IP address back to, in my case, 192.168.0.100:port 4321.*Audio mistakenly says 192.168.100*

That means the two requests, one from my laptop and one from my desktop, as they go out can be given different port numbers. When the replies come back with different port numbers, the router can look up the port number in its table to decide which device, desktop or laptop, the request originally came from.

I can have a look at the NAT table in the gateway router. For example, this originated on my desktop 192.168.0.100 with a port number of 4321, which has been translated to 99.0.0.2; in this case it didn’t change the port number. Another request, that was actually going to the same destination web server 77.0.0.2:80, but was coming from my laptop with address 192.168.0.101 and port number of 1027, that’s been translated to 99.0.0.2 with a port number of 1033. So we have two distinct port numbers, 4321 and 1033, both sending requests to the same web server, 77.0.0.2:80. When the replies come back in from 77.0.0.2:80, we can use the port number there, 4321 or 1033, to decide which was the required destination IP address.

So we’ve seen how network address translation with port numbers allows me to browse from my desktop and from my laptop, to the same website, at the same time, without the traffic getting messed up.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/32_nat_and_ports.jpg)

         ##-- ENDMEDIACONTENT
    


The gateway router may be performing network address translation for many devices within a private LAN. To distinguish between streams of traffic intended for different devices, the router may change the IP port number as well as the IP address.

IP port numbers are used in normal IP traffic because a single device may have many different network streams operating at the same time; the port number can be used to separate packets destined for different applications (e.g. email or web browsing) or components (e.g. tabs in a web browser). Some well-known port numbers exist that must be preserved; for example port 80 is always used by HTTP traffic to request a web page from a web server. But for many purposes the port number is obtained at random from a pool, so there is no problem caused by replacing the port number by a different value.
<div xmlns:str="http://exslt.org/strings" style="background:lightgreen">
<h1>IP port numbers and hardware ports</h1>
Note that the term __port__ is used in two different senses in networking. The IP port number referred to here is a software device; it has no connection to a hardware port which is a socket into which a cable is plugged. But there is some similarity: different hardware ports are used for traffic from different devices, and different IP port numbers are used for traffic from different programs running on a single network device.
</div>
The router maintains a table of network address translations it has carried out. This records the original IP address and port, and the replacement IP address and port. A different port number is used for every network stream. When incoming packets arrive, the router will look up the port number in the table to find the appropriate reverse translation and then replace the IP address and port number before the packet is switched over the LAN.


### Activity 7 Test yourself

*5 minutes*

Here is a NAT table which has entries for several current streams of network traffic. It shows the addresses of both ends of the stream, one of which is inside the LAN while the other is outside on the internet. For the inside, both the original private and translated public address for the device are shown.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Inside: private address</th>
<th>Inside: translated address</th>
<th>Outside address</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.3.10:51562</td>
<td class="highlight_" rowspan="" colspan="">203.0.113.56:55628</td>
<td class="highlight_" rowspan="" colspan="">137.108.200.90:80</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.3.23:53245</td>
<td class="highlight_" rowspan="" colspan="">203.0.113.56:54602</td>
<td class="highlight_" rowspan="" colspan="">137.108.200.90:80</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.3.45:63156</td>
<td class="highlight_" rowspan="" colspan="">203.0.113.56:53899</td>
<td class="highlight_" rowspan="" colspan="">151.101.64.81:80</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.3.36:51874</td>
<td class="highlight_" rowspan="" colspan="">203.0.113.56:57978</td>
<td class="highlight_" rowspan="" colspan="">151.101.64.81:80</td>
</tr>
</tbody>
</table>
<h1 xmlns:str="http://exslt.org/strings">Traffic leaving the LAN</h1>

#### Question

Some IP packets arrive at the router from the LAN for destinations on the internet. Translate the original private addresses to the appropriate source address so that the IP packet can be routed onto the internet.

IP packet source: 203.0.113.56:55628

Inside private address: 192.168.3.10:51562

IP packet source: 203.0.113.56:54602

Inside private address: 192.168.3.23:53245

IP packet source: 203.0.113.56:53899

Inside private address: 192.168.3.45:63156

IP packet source: 203.0.113.56:57978

Inside private address: 192.168.3.36:51874


#### Discussion

In this activity you are carrying out network address translation by hand for packets leaving the LAN.

Packets from the LAN arrive at the router with the source address of the sending device; this is a private address and needs to be replaced by the address of the router itself. The port address may also change to ensure that streams of traffic are kept separate. By looking up the private IP address and port number in the table, you can identify the translation needed to give the new source IP address and port number. For example, packets sent originally by 192.168.3.10:51562 should have their source address translated to 203.0.113.56:55628 before being routed on to the internet. The address 203.0.113.56 is the external IP address of the router; 55628 has been (randomly) allocated to identify this stream of network traffic.
<h1 xmlns:str="http://exslt.org/strings">Traffic arriving at the LAN</h1>

#### Question

IP packets are also returning to the router from the internet. Replace the destination addresses in the IP packet with that of the intended device on the LAN.

Inside private address: 192.168.3.10:51562

IP packet destination: 203.0.113.56:55628

Inside private address: 192.168.3.23:53245

IP packet destination: 203.0.113.56:54602

Inside private address: 192.168.3.45:63156

IP packet destination: 203.0.113.56:53899

Inside private address: 192.168.3.36:51874

IP packet destination: 203.0.113.56:57978


#### Discussion

In this activity you are carrying out the reverse step of network address translation by hand.

Packets from the internet arrive at the router with a destination address of the router itself but need to be delivered to devices on the LAN. By looking up the port number in the table, you can identify which private address needs to be placed in the packet to deliver it to the intended destination. For example, packets arriving at the router with the destination address 203.0.113.56:55628 need to have this address changed to 192.168.3.23:51562 to be delivered to the correct device on the LAN.




## 5.6 Implications of NAT


In this part you will consider the implications of NAT, in particular how the combination of NAT and private addresses has enabled home networking to become so common.

Now watch the video below, which is about 2 minutes long.


### Implications of NAT

         ##-- MEDIACONTENT
        
So just to take stock. We’ve been talking about NAT, network address translation. This is done systematically so that devices with private IP addresses in a local network can communicate with the internet.

Private addresses are changed at the gateway router for the router’s own address, and then passed on to the internet; replies come back to the router, which changes the address back again so it can be delivered to the correct destination inside the private network. Port numbers are used to keep traffic from different hosts separate.

So NAT allows you set up a private network and still allow devices in that private network to have access to the internet through the gateway router.

On domestic gateways, NAT is all automated and requires no configuration. (On a larger managed network in a commercial or corporate setting, some configuration may be needed).

This combination of NAT and private addresses has allowed the problem of a lack of global IPv4 addresses to be sidestepped. Private addresses can be reused in LANs, millions of times across the globe; each device doesn’t need a unique IP address. But with private addresses alone, we wouldn’t be able to communicate with the internet; and it’s NAT that makes this possible.

The combination of DHCP, private addresses and NAT also allows home networks to be largely self-configuring. Without them, every device on the internet would require manual setup – that was fine in the very early days of the internet, but completely impossible at the scale of the internet nowadays. So without NAT, internet use from home could never have happened.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/33_implications_of_nat.jpg)

         ##-- ENDMEDIACONTENT
    


Network address translation (NAT) is the systematic replacement of IP addresses and port numbers by the router. This can be done to allow devices with IP addresses in a private address range to communicate with the internet. A translation is made as traffic leaves the router and reversed when replies reach the router.

Private addresses are ideal for home networks because devices can be added to the network without needing to obtain new public IP addresses from a registration authority. However, private addresses were intended for use within local networks only. NAT in the gateway router makes it possible for devices with private addresses to communicate with the internet. All devices in the private network effectively share a single address on the internet which reduces the demand for IPv4 addresses.

The combination of private addresses, DHCP and NAT makes it possible for small home networks to be set up easily, without having to allocate public IP addresses. This combination also  underpins the rapid rise of home networks and the very large scale of the internet.


### Activity 8 Test yourself


#### Question

*5 minutes*

Identify the __one__ correct statement in the list below.

NAT never changes private addresses.

No. NAT changes all private addresses in a LAN to the public address of the gateway router so that devices on the LAN can reach the internet.

NAT and private address ranges mean that not all devices need to have unique IP addresses to use the internet.

You need permission from a registration authority to set up NAT.

No. NAT is typically set up for all home networks. Using private addresses means you don’t need to be allocated IP addresses by a registration authority.

NAT is only applied to packets as they leave a LAN for the internet.

No. If addresses are translated as they leave a LAN on their way to the internet, the reverse translation must be applied for packets arriving at the LAN from the internet.




## 5.7 Summary of Session 5


In this session you looked at the Dynamic Host Configuration Protocol (DHCP) and network address translation (NAT).

You have seen that DHCP allows a device to join a network and have important information assigned automatically so that no manual configuration is necessary. A host will automatically receive an IPv4 address, subnet mask, and the address of the default gateway to the internet. This information will be provided by a DHCP server; on a home network the gateway will act as a DHCP server. The DHCP server itself is configured to set aside a certain range of addresses to issue to other devices on the LAN for a given period. This configuration might be different for a home network compared with a network in  a café with public Wi-Fi, for example.

Home networks, like many LAN networks, are set up with IP addresses from an IPv4 private address range. These addresses can’t be used on the internet, but network address translation  allows devices with private addresses to access the internet. When the gateway routes traffic from the LAN to the internet, it systematically replaces the device source address (which is private) in IP packet headers with its own address (which is public). Traffic that returns to the gateway router will have the destination IP address switched back to the appropriate device’s local private address. By also replacing the port number, the gateway router can handle traffic for more than one device on the LAN at a time.

The combination of DHCP, NAT and private address ranges makes it easy to set up local networks with minimal configuration. Devices on the LAN share the router’s public IP address, helping to avoid the problem of a shortage of IPv4 addresses. This has made it possible to create networks at home very easily.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
Dynamic Host Configuration Protocol (DHCP)
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol used to dynamically assign TCP/IP configuration information to hosts on a network. DHCP can assign an IP address, subnet mask, default gateway and other details to a host when it joins the network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
lease
</td>
<td class="highlight_" rowspan="" colspan="">
The period for which an IP address assigned by DHCP remains valid (unless it is renewed).
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
network address translation (NAT)
</td>
<td class="highlight_" rowspan="" colspan="">
A system used to systematically change IP address information in network packets as they leave or enter a network. It is often used to give hosts in a private network access to the internet.
</td>
</tr>
</tbody>
</table>

---

