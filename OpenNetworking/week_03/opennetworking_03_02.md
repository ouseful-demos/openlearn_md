# Session 6: Configuring a home gateway



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/06_internet_connection_router.tif)

This session revisits the home gateway to show how it can be configured from another device on the same network. You will also see how the home gateway carries out several different roles on the network.

By the end of this session, you will be able to:

* 
state the roles carried out by a home gateway


* 
configure a home gateway from another device


* 
set up services on a home gateway, including Wi-Fi and DHCP.



## 6.1 Switching


In this part you will see how a home gateway acts as a switch to connect devices on a home network.

Now watch the video below, which is about 2 minutes long.


### Switching

         ##-- MEDIACONTENT
        
Welcome to a session about home gateways. In this session you will see that a home gateway carries out several different tasks. On a managed network in a business context, these might be carried out on several different devices; a home gateway won’t be as fast or powerful as these, but it is quite a sophisticated device.

I’ll start with something simple – a new network with a gateway router, a desktop, laptop and tablet, and I’m going to use wired connections first.

Initially I’m going to set up static IP addresses manually. What addresses should I use? It’s best to stick to the private address range because you won’t be popular if your IP address conflicts with Google or Facebook – or maybe you’ll be very popular.

So I’m going to set my desktop to IP 192.168.0.10 and my laptop to 192.168.0.20.

Now I can connect them to the router with Ethernet cables. So from the Ethernet port to the first free Ethernet port on the gateway, and then from this Ethernet port to the next free Ethernet port on the gateway.

So let’s see if I can ping between machines. I’ll type ipconfig to check my own IP address, and then ping 192.168.0.20, the address I set for my laptop. And there are some return pings, so I do have a network connection.

The gateway here is operating as a switch, nothing else. It learns which machines are connected and will pass packets to the correct destination.

The gateway router itself is a device on the network and it has its own IP address. But what is it?

With luck, the gateway will have set itself up with a default IP address that is well known and documented in the manual. Here I know it is 192.168.0.1 and I should be able to ping from my desktop to confirm that the router is responding. And there we are.

So we have a local network set up, and the gateway is acting as a switch transferring data between devices within the LAN.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/34_switching.jpg)

         ##-- ENDMEDIACONTENT
    


The home gateway incorporates a switch that connects devices within the LAN, using either wired or wireless connections. The gateway itself has an IP address on the LAN, usually set up to a known default value.


### Activity 1 Test yourself


#### Question

An ISP may send out thousands of similar home gateways to its customers. Can they all be given the same LAN IP address?

Yes.

No.

Home networks are set up with addresses in a private range (often IP addresses starting 192.168.0.0) so it doesn’t matter if gateways in different networks have the same address. Each home network will only have a single gateway.




## 6.2 Remote configuration


In this part you will see how a home gateway can be configured remotely from another device by using the web interface built into the gateway.

Now watch the video below, which is about 2 minutes long.


### Remote configuration

         ##-- MEDIACONTENT
        
Routers don’t have a screen or keyboard, so it isn’t obvious how you configure them. ‘Professional’ networking equipment often has a console connection so a network engineer can plug their laptop in and configure it directly. A home gateway won’t – but we do now have a network connection from the desktop to the gateway, so I can configure the gateway from my desktop.

Home gateways offer a web page interface to configure them. I can open a browser on my desktop and type in the IP address of the gateway. This gateway is challenging me for a password, which I fortunately know. It’s often written on a label on the gateway itself.

So here’s the configuration interface – remember I am looking at this on my desktop’s web browser, but I am now interacting with the gateway itself. (And by the way this means that the gateway is actually working as a small web server, serving up web pages.)

There are a number of tabs to choose; I’ll look at ‘Basic setup’, and scroll down a bit to see the local network setup – IP address 192.168.0.1 and subnet mask 255.255.255.0.

Remember that the gateway is a router and so it has two network interfaces – this is the LAN side, but there is also an interface to the rest of the internet. So this will need to be configured to work for your ISP, and so is not something you would normally change – I’ll assume this is setup correctly.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/35_remote_configuration.jpg)

         ##-- ENDMEDIACONTENT
    


A home gateway, like other communication equipment, doesn’t have a screen or keyboard attached and must therefore be configured from another device on the network. You connect to the gateway’s configuration pages using a web browser. You need to know the IP address or name of the gateway to connect to it.

The gateway contains a simple web server in order to produce the configuration pages.


### Activity 2 Think about


#### Question

*5 minutes*

Can you configure your home gateway from the other side of the world?


#### Discussion

You’ve seen how to access the gateway’s configuration web pages by typing its IP address in a web browser. We used the inside address gateway on the LAN which is normally a private address; since private addresses cannot be routed across the internet, you wouldn’t be able to connect to it from outside your own home network.

However, it may be possible to access the configuration pages using the router’s outside IP address – which can be reached from anywhere on the internet. Since this is a security risk, this access is usually disabled; if it is enabled, then it is very important that the admin password is secure.




## 6.3 DHCP


In this part you will see how a home gateway functions as a DHCP server to provide configuration for other devices on a home network.

Now watch the video below, which is about 1 minute long.


### DHCP

         ##-- MEDIACONTENT
        
I started by setting up my desktop IP addresses manually as a static address. But you don’t want to do that all the time – it would be a pain, particularly for mobile devices.

So instead I can set up DHCP on the gateway to allow IP addresses to be assigned automatically.

I need to enable DHCP (it probably would be set up by default), but I can choose a start address and number of users. These look fine: scroll down and click ‘Save’.

I’ll check that works. Back at my desktop, I can switch from static to DHCP – and there is the configuration appearing automatically, an IP address from the range we specified, but also other useful things: the subnet mask and the address of the gateway itself.

So the gateway is now acting as a DHCP server. And new devices can now join the network without needing any manual configuration.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/36_dhcp.jpg)

         ##-- ENDMEDIACONTENT
    


An important role for a home gateway is to be a DHCP server for the home network, handing out IP addresses and other configuration information to devices that join the network.


### Activity 3 Try it out


#### Question

*15 minutes*

1. 
Open [PT Anywhere](https://forge.kmi.open.ac.uk/onl1-pt5.1a) in a new tab or window so you can read these instructions.

In this scenario, there is a home gateway router and one PC already connected.


2. 
From the PC, click `Edit device`, then open the `DHCP Server (remote)` tab. This gives you access remotely to the home gateway’s configuration.


3. 
From the PC, check that the DHCP server on the gateway is turned on.


4. 
Check that the number and range of addresses is appropriate.


5. 
Add the laptop to the network by connecting it to the home gateway.


6. 
What IP address is it assigned?


7. 
What other configuration does it receive?



#### Discussion

PT Anywhere provides remote access from a PC to the home gateway’s configuration. This would normally be done by using a web browser on the PC to connect to web pages hosted on the gateway. The DHCP server on the gateway can be configured to use a particular range of IP addresses.

You can explore further by connecting other devices.




## 6.4 Wi-Fi


In this part you will see how to set up a home gateway as a wireless access point.

Now watch the video below, which is about 1 minute long.


### Wi-Fi

         ##-- MEDIACONTENT
        
Let’s think about adding wireless devices to the network by setting up the gateway as a wireless access point.

I’m using my desktop again to reach the admin pages of the gateway. I’ll click on the ‘Wireless’ tab.

Access points broadcast their identity so Wi-Fi users can see them and choose to connect. I need to give an SSID that doesn’t clash with the neighbours. Click ‘Save’.

And I need some security to restrict access to the network. WPA2 Personal is secure and widely supported. I need a passphrase: you should pick something much more secure but this is only a simulation. Click ‘Save’.

OK, the gateway is now set up as a Wi-Fi access point. 

I’ll connect my tablet. On a real device you would pick JONS-WIFI from a list, but here I have to type it in myself. And I need to set the correct security and give the correct passphrase.

And there we are – it has connected OK. 

I can check with a ping from my desktop – I need to check the tablet’s IP address first, and then ping from my desktop. And there I have a reply from the tablet.

So the gateway is set up and working as a wireless access point.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/37_wi-fi.jpg)

         ##-- ENDMEDIACONTENT
    


When configuring the gateway as a Wi-Fi access point, an SSID (service set identifier) is given which will be broadcast so that users can pick the right network if several are in range. Security should also be set up to prevent unauthorised use: an appropriate setting is *WPA2 Personal* which requires the user to know a passphrase. The passphrase (also called a pre-shared key) should be picked so it is impossible to guess!


### Activity 4 Think about


#### Question

*5 minutes*

Some years ago, home gateways were often delivered with the same default SSID and passphrase/key, accompanied by instructions on how to change these. Nowadays, there is usually a label displaying a complicated passphrase/key attached to the gateway. Which is better?


#### Discussion

Using the same SSID caused problems if neighbours received the same gateway. Sending a gateway pre-configured with well-known default passwords is insecure. There is a high risk that many people (not network engineers!) would not change the default values, because they didn’t know how to, didn’t see the need, or just never got around to it. Configuring each device with a unique, strong password at the factory is clearly preferable.

Are there any downsides? The passphrase/key is clearly printed on a label on the gateway and known by everyone who has used the network; it isn’t secret in the way we normally understand a password to be (hence it is strictly known as a ‘pre-shared key’). But to read the label, someone must be in your house: if you trust someone enough to let them through the door, then you probably trust them enough to use your Wi-Fi. The passphrase/key is complicated but no one needs to remember it: you enter it once on a new device which then stores it. All users of the network can share the same passphrase/key: they don’t all need different passwords.




## 6.5 Routing


In this part you will see how the home gateway is a router, passing traffic between the LAN and the internet.

Now watch the video below, which is about 4 minutes long.


### Routing

         ##-- MEDIACONTENT
        
The one job the gateway router hasn’t done yet is act as a router!

We need to connect it to the rest of the internet. At home, that typically means either a broadband connection through copper phone line or an optical fibre connection, maybe in some rural areas 4G radio or even satellite. 

Whatever, it won’t be an Ethernet connection, so a device, a modem, is required to convert signals from one system to another. Home gateways often include a broadband ADSL modem that connects to the phone system – it’s another role for the gateway. In this simulation, I’m skipping that detail.

But where are we connecting when we do connect to the internet? It isn’t really a cloud – we will really connect to another router, one that belongs to our ISP. That will take our traffic and be responsible for forwarding it out to the rest of the internet, from router to router until it is delivered to the destination host. Reply packets will hop back over the internet, eventually coming back to the ISP router, which then delivers back to our router which will deliver back to our device.

So I have made a connection from the gateway router to the ISP’s router. Now, at this point our own gateway router itself will be configured by DHCP; it will receive an external IP address from the ISP’s DHCP server. (So this is it working in another role – the gateway router itself is working as a DHCP client, getting its external IP from the ISP’s DHCP server, while also acting as a local DHCP server itself for the devices in the LAN.)

Note that the gateway is a router. A router always has two network interfaces each with its own IP address. One faces the LAN and is used for traffic on LAN only. The other faces the internet and is used for traffic between the LAN and the internet. The router’s job is to decide which packets to forward from one interface to the other.

I’m going to go back to desktop and check its configuration. We need to make sure that it knows where to find the gateway router. I can check with ipconfig and see that the gateway is correctly set.

And I can now ping outside my home network to a server on the internet. I happen to know that the IP address of the Megacorp web server is 77.0.0.2 – and there after some delay we finally have some return packets. So it’s taken a little while for the routing to sort itself out.

I can open a web browser on my desktop to show that we can do something more useful than simply ping – I can reach the Megacorp server by giving its IP address. And there we can see its web pages.

The reason that we are calling this gadget a gateway is because it does act as the gateway from the LAN to the rest of the internet – all internet traffic is routed through it. And finally the gateway router is doing the job of a router – it’s forwarding traffic from one network to another, from the LAN to the internet.

In passing we should note that my desktop has a private IP address, like everything else on the LAN, but it is successfully communicating with the internet. That means there must be NAT (network address translation) going on in the gateway – so that’s another role that the gateway is carrying out.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/38_routing.jpg)

         ##-- ENDMEDIACONTENT
    


The home gateway is the router which connects the LAN to the internet; all traffic from the LAN to the internet therefore passes through this gateway. The gateway itself will connect to a router at an ISP, and through that to the rest of the internet. Since home gateways often connect to the internet via a broadband phone line, they often include a modem to convert signals to the form required for transmission over phone lines.

The gateway will use network address translation (NAT) so that private addresses can be used on the home network.


## 6.6 Domain Name System (DNS)


In this part you will see how devices on a home network look up the IP address for domain names using the Domain Name System (DNS) servers.

Now watch the video below, which is about 3 minutes long.


### DNS

         ##-- MEDIACONTENT
        
So far I have only used IP addresses as destinations. Computers use IP addresses; humans prefer to use human-readable domain names, such as google.com, open.ac.uk or even megacorp.com.

So something needs to convert those names into the appropriate IP address so that packets can be directed to the right destination – IP packets can only contain IP addresses, not names.

The system responsible for that is the Domain Name System (DNS). Devices on the LAN need to know the address of a DNS server to which requests for translations from name to IP address can be sent. And obviously we do need an IP address for that server.

Typically your ISP settings will include the IP address of their DNS server, and that will be set up in the gateway and then passed by DHCP to each device on the LAN. Let’s check using ipconfig /all. And there you can see the DNS server has been set.

Let’s perform a lookup for megacorp.com. The command to use is nslookup www.megacorp.com, and there is the reply – first it confirms which DNS server responded, and then gives the IP address 77.0.0.2.

So now we can use a server name instead of an IP address, for example in a ping – so replies there from the Megacorp web server. And I can use a URL in a browser also.

So does the gateway have a role to play here? In this example, no, but sometimes a home network will be set up so that the gateway itself is a DNS server. Of course your home gateway won’t know about every domain on the internet, so when it receives a request it can’t handle it will pass the request on to another DNS server – that’s the way the Domain Name System works. But when it gets an answer, it can save it and then reply immediately if asked again. You may have noticed that the lookup I did previously gave a ‘non-authoritative’ result; that’s because it picked up a cached value and there is a chance that it might be out of date. Saving values, or caching them, is very common in networking because networks are still very slow compared to processing speeds, so avoiding a network transfer by using a saved value is always a good idea.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/39_dns.jpg)

         ##-- ENDMEDIACONTENT
    


The Domain Name System exists to convert between human-readable domain names, such as `www.google.com` or `www.open.ac.uk`, and the numeric IP addresses used in IP networking such as `172.217.18.196` or `137.108.200.90`.

There are DNS servers in the internet to carry out these translations, and each device on a home network should be configured with the address of a DNS server. The gateway will relay the IP address of a DNS server from the ISP to devices on the network as part of DHCP configuration.

If a DNS server doesn’t know how to translate a particular domain name, then it will forward it to other DNS servers until an answer is returned; it will then save the answer in a cache in case it receives the same request again. A home gateway can act as a simple caching DNS server, passing new requests to the ISP’s more capable DNS server and caching the result.


### Activity 5 Try it out


#### Question

*10 minutes*

1. 
Open a command-line prompt on your computer.


2. 
Check using `ipconfig /all` that a DNS server is set up.


3. 
Enter the following command to run a sample DNS look up:

`nslookup www.open.ac.uk`


4. 
What is the IP address returned?


5. 
Use this address to perform a reverse lookup, for example enter:

`nslookup 137.108.200.90`

Does this always work?


6. 
Repeat the above with some other domain names and websites.


7. 
Are there any surprises?


8. 
Can you confirm which server is responding to your queries?



#### Discussion

Your computer should be set up with the address of at least one DNS server; it may have a list of several alternatives. `ipconfig /all` should show these and each `nslookup` will state which server responded. Most replies will be flagged as ‘non-authoritative’ meaning that the server has replied with a cached value.

You might expect that if `nslookup` converts a server name into an IP address and you then ask for the reverse lookup, you would get back the original name. There are two possible surprises. First, you may get a message ‘Non-existent domain’. This is because the reverse lookups rely on network administrators creating special reverse records and these may not exist. Second, some DNS records involve aliases; for example `www.megacorp.com` may be an alias for `the-real-server.megacorp.com`.




## 6.7 Review


In this part you will briefly review the different roles the home gateway plays in a home network.

Now watch the video below, which is about 2 minutes long.


### Review

         ##-- MEDIACONTENT
        
We’ve seen that a home gateway carries out a number of different roles.

The crucial role – the reason we call it a gateway – is that it is the gateway from the LAN to the rest of the internet. This is because it is a router, able to pass packets from its inside interface to the outside interface, from the LAN to the internet.

In fact, the same box is also acting as a switch, dealing with local traffic on the LAN, for example computer to printer, computer to tablet, and so on. It does this both for wired and wireless traffic.

It’s also a wireless access point, so that devices can connect to the LAN using Wi-Fi as well as wired Ethernet.

To connect to the internet, it may include a modem able to convert from Ethernet to broadband phone line for example.

It will also be working as a DHCP server, responsible for configuring devices that connect to the LAN.

The local configuration is very likely to use private addresses, so the gateway will have to carry out network address translation, NAT, so that devices can communicate with the internet.

The gateway may also act as a firewall, protecting the network against malicious attack. We haven’t discussed the details of firewalls, but techniques include inspecting IP packets, which the gateway is doing for NAT in any case.

Besides being set up as a DHCP server, some gateways will be set up as DNS servers.

And they also include a web server, because that is needed to display the configuration pages so you can manage the gateway from another device on the LAN.

And for some purposes, the gateway will act as a client – it may get its own configuration by connecting to an ISP’s central DHCP server, for example.

So taken as a whole, overall the typical home gateway is really quite a capable device.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/40_review.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 6 Think about


#### Question

*10 minutes*

Your ISP has given you a new, updated gateway. Could you use your old gateway device as a second wireless access point? What would you need to consider?


#### Discussion

Yes, it should be possible to use your old gateway device as an additional wireless access point. Once set up, the old box will no longer be a ‘gateway’ but it will use the Wi-Fi and switching functions. Routing, NAT, DHCP and DNS will all be carried out by the new gateway.

Some gateways have a configuration option to set this up automatically; otherwise, you can do it manually. This is easier if you plan to connect the old box to the new gateway with an Ethernet cable connection; trying to connect between old and new boxes by Wi-Fi is challenging or impossible.

Since both old and new gateways may by default have the same IP address, do the initial setup of the old box using a cable connection from a laptop. Change the inside IP address of the old box to be a static address on the same network as the new gateway but which doesn’t clash. Disable DHCP on the old box.

Connect the old box (use a LAN port, not the port labelled ‘internet’ or ‘WAN’ since you are not using the routing functions) by cable to the new gateway. You should now be able to connect to your home network and the internet through either Wi-Fi point; your mobile device should pick the better connection, or you can pick manually if you have kept different SSIDs.




## 6.8 Summary of Session 6


In this session you looked at how to configure a home gateway and considered the roles that it plays in a home network. A home gateway can be configured from a web browser on another device on the network. (The gateway contains a simple web server in order to produce these pages.)

The home gateway acts as a switch that connects wired and wireless devices within the LAN, provides a wireless access point, and is a router that connects the home network to the internet. It uses network address translation (NAT) to allow private addresses to be used on the home network, and may also function as a firewall. It provides DHCP to automatically configure devices that join the home network. Configuration includes access to a DNS server to convert domain names to IP addresses; some gateways are capable of acting as a simple DNS server.

You can see that the home gateway carries out many roles in a home network, all conveniently packaged into a small but sophisticated device.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody><tr>
<td class="highlight_" rowspan="" colspan="">
firewall
</td>
<td class="highlight_" rowspan="" colspan="">

</td>
</tr></tbody>
</table>

---

