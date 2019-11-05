# Session 4: An introduction to routing



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/04_server_hardward.tif)

In the last session you looked at how data is segmented and delivered across a local area network. You also were introduced to switches and routers. In this session you will focus on the role of routers.

By the end of this session, you will be able to:

* 
understand that routers are needed to get data from network to network and that they use IP addresses to do this.



## 4.1 Revision of IP addresses


In the last session you looked at how switches deliver data across a local area network. In this session you will look at routing. Routers operate at the Internet layer of the TCP/IP model and use IP addresses to deliver data across networks. Whereas switches worked with data frames, at the Internet layer data units become packets.

Now watch the following video, which is about 2 minutes long.


### Revision of IP addresses

         ##-- MEDIACONTENT
        
In this session we’ll be looking at routing. But firstly, a quick reminder of some of the work you did with IP addresses in earlier sessions – as we will be working with IP addresses in this part. You examined the PT Anywhere gateway’s IP address, which you found to be 192.168.0.1. You also saw how all devices on this network started with 192.168.0 with the final part used to identify a specific device on that network. The network itself would be allocated the IP address 192.168.0.0, which means all the devices could have a final digit between 2 and 254.

This type of address is one commonly used for private networks, specifically small home networks. Most of the networks we are concerned with at the moment will use addresses similar to this. They will also usually use the subnet mask 255.255.255.0. Remember the subnet mask shows the portion of the IP address that identifies the network.

Later, when we look at larger networks you will be using other types of IP address and subnet mask, such as those used in the next activity. Sometimes the network part is smaller and the host part bigger, so subnet masks such as 255.255.0.0 are used.

In this part we will be looking at how data is sent across different networks – looking at the IP addresses of source and destination devices is useful to determine whether two devices are on the same local network or whether they are on different networks.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/21_revision_of_ip_addresses.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Think about


#### Question

*5 minutes*

Identify the network and host portions of the following IP addresses. The first has been done for you.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>IP address</th>
<th>Subnet mask</th>
<th>Network address</th>
<th>Host ID</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.1.105</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.0</td>
<td class="highlight_" rowspan="" colspan="">105</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.10.6</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">172.16.32.25</td>
<td class="highlight_" rowspan="" colspan="">255.255.0.0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">10.80.1.10</td>
<td class="highlight_" rowspan="" colspan="">255.0.0.0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
</tbody>
</table>
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>IP address</th>
<th>Subnet mask</th>
<th>Network address</th>
<th>Host ID</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.1.105</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.0</td>
<td class="highlight_" rowspan="" colspan="">105</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">192.168.10.6</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.10.0</td>
<td class="highlight_" rowspan="" colspan="">6</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">172.16.32.25</td>
<td class="highlight_" rowspan="" colspan="">255.255.0.0</td>
<td class="highlight_" rowspan="" colspan="">172.16.0.0</td>
<td class="highlight_" rowspan="" colspan="">32.25</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">10.80.1.10</td>
<td class="highlight_" rowspan="" colspan="">255.0.0.0</td>
<td class="highlight_" rowspan="" colspan="">10.0.0.0</td>
<td class="highlight_" rowspan="" colspan="">80.1.10</td>
</tr>
</tbody>
</table>



It can also be useful to determine whether two devices are on the same local network or on different networks. Two devices on the same local network will have the same network address.


### Activity 2 Test yourself


#### Question

*5 minutes*

In which of the following are the source and destination devices on the same local network, and which are on different networks? The first has been done for you.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Source: IP address and subnet mask</th>
<th>Destination: IP address and subnet mask</th>
<th>Same local network or different networks?</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
192.168.1.105

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">
192.168.1.250

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">Same: both have network address 192.168.1.0 </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
192.168.10.6

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">
192.168.10.252

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
192.16.32.25

255.255.0.0
</td>
<td class="highlight_" rowspan="" colspan="">
192.168.31.32

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
10.80.1.10

255.255.0.0
</td>
<td class="highlight_" rowspan="" colspan="">
10.80.2.26

255.255.0.0
</td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
</tbody>
</table>
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Source: IP address and subnet mask</th>
<th>Destination: IP address and subnet mask</th>
<th>Same local network or different networks?</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
192.168.1.10

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">
192.168.1.250

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">Same: both have network address 192.168.1.0</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
192.168.10.6

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">
192.168.10.252

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">Same: both have network address 192.168.10.0</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
192.16.32.25

255.255.0.0
</td>
<td class="highlight_" rowspan="" colspan="">
192.168.31.32

255.255.255.0
</td>
<td class="highlight_" rowspan="" colspan="">Different: source has network address 192.16.0.0 but destination has 192.168.31.0</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
10.80.1.10

255.255.0.0
</td>
<td class="highlight_" rowspan="" colspan="">
10.80.2.26

255.255.0.0
</td>
<td class="highlight_" rowspan="" colspan="">Same: both have network address 10.80.0.0</td>
</tr>
</tbody>
</table>




## 4.2 Key routing terms


Now watch the following video, which is about 5 minutes long.


### Key routing terms

         ##-- MEDIACONTENT
        
Routers operate at the Internet layer of the TCP/IP protocol stack and use IP addresses to make routing, or forwarding, decisions.

As we have seen, unlike MAC addresses, IP addresses are hierarchical, and contain location information – in this case within a hierarchy of networks, not geographical places as would be the case in an address or postcode.

IP address can apply to networks themselves, as well as to individual devices, and that address locates a network within the hierarchy of networks.

The home gateway device we have focused on previously provides some routing capabilities – but these generally route local data traffic to the next level of router usually at the ISP (internet service provider) which will aggregate data traffic from several home routers (shown here as Tier 3). Then there are routers that will aggregate data from these and so on – core routers (or Tier 1, shown here) provide the backbone to the internet and are designed to carry huge amounts of data.

When a user sends a packet that has a destination on a different network – not the one that the user is connected to – the packet is sent to a router. In the case of our domestic network, a device is configured to know its ‘default gateway’ which will be the home gateway device.

The router then has to work out which network the packet should be forwarded to. The router might only be connected to a small number of devices and the ISP, or it may be connected to other networks, but the processes used are the same.

Routers make their decisions on how to direct packets from network to network using routing tables. Routing tables store destination IP addresses that can be reached via a particular port. This sounds similar to the way in which forwarding tables store MAC addresses and associated port numbers. However, with routing this can be a much more complex process and the ways in which routing tables are constructed also differ.

Normal PCs connected to a network also have a routing table so that they know where to direct a packet, although these are much simpler compared to the ones used by a router, as they have very little to route: they simply have to get data to the default gateway.

Using the command `route print` at the command line will show you your computer’s routing table. Another command that will also show the routing table is `netstat` (short for network statistics) with the parameter `-r`.

I’ll use `route print` here. So if I start at the command line by typing `route print`, my results look like this with several tables.

I’ll start by locating the IPv4 routing table. Let’s have a quick look at some of the information that’s shown. The top line is of most significance to us at the moment. Under ‘Interface’, the IP address given – 192.168.1.191 – is the IP address that my computer’s currently using. And under ‘Gateway’, you can see the IP address of my home gateway is 192.168.1.1. You should recognise this by now as a commonly used private network address.

The 0.0.0.0 under ‘Destination’ means that this is the default route. All packets sent from my PC will be sent to the gateway router which then has the more difficult job of deciding what to do next. The value in the ‘Metric’ column refers to how efficient the route is – in more complex networks there may be several routes a packet could take and therefore the router has to decide which is the best one. So the lower this value here – the lower the metric – the better.

Routers have more complex routing tables as it then has to decide where to send the packet next, sometimes via several ‘hops’ – where one hop is one section of the path taken. The number of hops a packet takes between source and destination is basically the number of network devices that the packet has to pass through on its journey. This is one of the pieces of information, amongst other things, that is used to determine the metric of a route. The more hops, the less efficient the route.

When a router is first connected to a network, it doesn’t know about other networks – so its routing table is empty. The router has to be configured with a routing protocol that will enable it to learn routes and populate the routing table.

A routing protocol is a set of rules that uses software and algorithms to specify how routers share information with each other. Some examples that you may come across are shown here. But we won’t go into the detail of these until later in the course. For now you should just be aware of why they are used and that there are different types.

The routing protocol enables the router to learn about nearby networks by exchanging information with other routers. In this way it learns about more distant networks. This enables it to determine the best path for sending packets from source to destination device, and via which routers it will travel.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/22_key_routing_terms.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 3 Try it out</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. Try using `route print` or `netstat –r` at the command prompt of your PC.

Click *Reveal answer* if you would like a hint.

Look for the IPv4 route table.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. What can you deduce from the results?

Click *Reveal answer* if you would like a hint.

Can you find the IP addresses of your PC and gateway?

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 4.3 More on routing


Now watch the following video, which is about 2 minutes long.


### More on routing

         ##-- MEDIACONTENT
        
Let’s now look at an example involving three routers. Here, routers A, B and C are interconnected. Each router has a local network, reached via a switch.

The end devices have individual IP addresses, and the network itself also has an IP address. For example, if we take a closer look at router C we can see it has devices with IP addresses: 192.10.8.16, 192.10.8.25 and 192.10.8.84. And the network also has its own IP address, which is 192.10.8.0. This address cannot be allocated to a device, only to a network.

Here’s a device on router B’s local network sending a packet addressed to a device on router C’s local network. The destination device has address 192.10.8.16, so the network it is on is 192.10.8.0.

The first router the packet meets is router B. This router knows that the network 192.10.8.0 can be reached on port 1. The packet goes via router B’s port 1 to router A, which then passes it to router C. From router C it goes to a switch, which the end device is connected to.

From here, the switch takes over and uses its forwarding table as we saw in the previous part. It not only associates MAC addresses with port numbers, it also associates IP addresses with MAC addresses. The switch forwards a frame containing the packet to the correct port. This final stage of delivery is actually a switching process which occurs at the Network Access layer of the TCP/IP protocol stack. At this stage, the IP packet is encapsulated in an Ethernet frame. The initial stage of the journey, wheren the packet leaves the sender, also involves switching prior to the packet reaching router B.

Of course, one important point here is that we have assumed that the three routers already have enough information in their routing tables to be able to deliver packets to the other networks.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/23_more_on_routing.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Think about


#### Question

*5 minutes*

In the previous session you were asked why it might not be a good idea to have too many devices connected by just switches. Can you think how routers might help?

All devices connected by a switch will be in the same broadcast domain, which you saw previously means all devices will receive and have to process any broadcast packets. Routers do not forward broadcasts by default and therefore break up broadcast domains.



Now watch the following video, which is about 3 minutes long.


### Routers in Packet Tracer

         ##-- MEDIACONTENT
        
Here we have the same example, but now in Packet Tracer, with three networks each connected to a router. So we have router C connected to network 192.10.8.0, router B connected to network 192.10.6.0 and router A connected to network 192.10.7.0.

You may recognise that each of these networks is very similar to the ones we were looking at in the last part on switching, with a small number of PCs connected by a wire to a switch. Now though, each switch is connected to a router and there are connections between some of these routers.

This overall network is identical to the network in the animation we’ve just seen, but now we’ll take a closer look at what information we need to give these routers and how we configure them to enable them to send data from a PC on one network to a PC on another network.

So at the moment, the connections between the PCs and the switches are all green, which means they are up and working. This is because I’ve already configured each of these PCs with their IP address.

I’ll go into one of these PCs to show you that information – so if we go into ‘IP Configuration’ we can see that we’ve got the IP address of the device, the subnet mask and I’ve also put in the IP address of the gateway for that network. So if the network address is 192.10.8.0, the default gateway entered here is 192.10.8.1.

That should look similar for each of these networks: I’ll just check another one – this network is 192.10.7 and the host ID 56. The default gateway is 192.10.7.1.

So remember the switch can build a forwarding table using the MAC addresses and port numbers. It will also associate the IP addresses with the MAC addresses. So PCs are able to send data via the switch to other devices on the same network.

So if we open a command window and ping from one device on this network to another to test that out; we should see that packets are reaching their destination successfully.

However, you may have also noticed that the ports connecting the switches and the routers, and *between* the routers, are all still red. This is because we haven’t configured the routers yet. So each of these routers doesn’t know what networks are available on each of its ports yet. We’ll look at this in more detail in the next video.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/24_routers_in_packet_tracer.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 5 Try it out</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt3.4/) in a new tab or window so you can read these instructions. There are two networks connected by two routers.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Can PC0 on the first network send messages to PC1 on the same network?

Click *Reveal answer* if you would like a hint.

You will need to find the IP addresses of both PCs and ping from PC0 to PC1. You should find this is working OK.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Now watch the following video about configuring routers, which is about 4 minutes long. In the video the speaker refers to a serial connection. This is a type of connection sometimes used to join routers.


### Configuring routers

         ##-- MEDIACONTENT
        
In this video we will look at how to configure the routers.

We know that this port, or interface, on router C (which is actually FastEthernet Port 0/0), is connected to network 192.10.8.0.

If I click on Router C, and then ‘Config’, then FastEthernet 0/0 (as this is the port we’re currently working with) – I need to set the IP address to 192.10.8.1 because this provides the default gateway for this network. The subnet mask fills in automatically. I also then need to switch this port ‘on’, and then when I close this down we can see that this is starting to configure, so these ports should now turn green.

This router now knows that on port 0 it can access network 192.10.8.0.

If we then do the same for Router B, so configure, and then FastEthernet port 0, the network on this port is 192.10.6 and then .1 as it is the default gateway for this network. Then remember to switch it on and close it down.

Finally, we would need to do the same for Router A.

As well as configuring the routers this way, we could use the command-line interface. The window at the bottom here, when we were in the ‘Config’ tab, shows the commands that are used: for example, `interface` and `ip address`. We won’t look at this in any more detail at the moment, but we will be using those commands later in this course.

So as well as the three networks that we’ve already configured on each of those ports, the connections between routers also need to be considered networks. So the link between Router C and Router A is one network. There is also a network between Router A and Router B. So the next job is to provide network addresses for these router interfaces.

So to save a little time – as you’ll be looking as this in more detail later in the course – I’ve created a preconfigured version. I’ve given these network segments addresses. So you can see here between Router A and Router C we have a network address 172.16.0.0. And the between Router A and Router B we have a network address 10.0.0.0.

If we now have a look at Router C, remember before we had configured the FastEthernet 0 port to show this network address. If we look at the connection between the two routers here, which is actually serial connection 2/0, we can see that this now knows that this network is available on this interface – as we’ve given it the address 172.16.1.1.

Router A has two connections – one to Router B and one to Router C – so we should see that in the configuration here. Again, we’ll just check the FastEthernet connection to the local network, which is 192.10.7.1. And then we’ll take a look at the two serial connections. The first one here is 172.16.1.2. And to the other router we have 10.10.10.1.

We’ll take a final look at Router B – which has also been done.

So now we can see that all ports are up and everything is green.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/25_configuring_routers.jpg)

         ##-- ENDMEDIACONTENT
    


Now watch the following video about using the configured routers as a network, which is about 5 minutes long.


### Using the configured routers

         ##-- MEDIACONTENT
        
Next I’m going to try to send some packets between different devices. There’s a facility in Packet Tracer that enables us to send a simple packet by clicking on this icon and then clicking on a source and destination device, and it sends a simple packet. We could of course do this by pinging at the command line from one PC to another, but this will be quicker.

A report is received – down at the bottom here – on each packet that’s sent.

So we’ll start off by doing a simple test between two PCs on the same network. We can see here that the packet was sent successfully.

We’ll now try between two PCs on a different network. And again, we have a successful packet sent.

What we’ll do now is try sending a packet from a device from network B to network C. As you can see, when we’ve done that, that’s failed. This is because we haven’t yet configured each of these routers with a routing protocol which would in turn discover which networks are available and via which ports and which routers. So this is what we’re going to do next.

It would be possible to input the information manually, typing in each network and path that packets need to take. This wouldn’t take much to do here because we only have three routers. But in large networks this becomes a very complex task. So instead we’re going to use a routing protocol to do it. Again, this is something that could be done via the command-line interface, and you’ll see how to do this in a later session. But for now it’s easier to see what I’m doing if I use the configure option. So starting with Router C, I’m going into ‘Configure’ and I need to click on RIP (which stands for Routing Information Protocol) – the routing protocol I’m going to use here. Then I need tell the router which networks are available on its ports.

So we know Router C is connected to the network 192.10.8.0, so we’re going to add that one. We also know it’s connected to this network here, so we’re going to add that one, too. Then I need to make sure I save those.

Now going to Router A. ‘Configure’, ‘RIP’, and then we’re going to add the network addresses that Router A is connected to. So we have 192.10.7.0, and we also have 172.16.0.0. We also have a third one, which is 10.0.0.0. And again, I make sure I save those. Finally, we do the same for Router B.

We may need to allow a little time for this to update. I’m going to start by sending a few packets to see if they’re reaching their destination yet. We might need to send a few packets before the route’s found. Finally, we can see that packets are starting to be sent from network to network successfully.

So just one final word on broadcast domains. We saw in the part on switching how a broadcast domain comprises all the devices that will receive each other’s broadcast frames – so all the devices a switch will forward a broadcast message on to. Routers do not forward broadcast messages. So in our example, a broadcast message sent on network C will not be sent on via Router C so will not reach A or B. Let’s just try this. If I send a broadcast ping on network C, let’s see where it reaches. So we can see we’re getting replies from hosts 16, 84 and 1, but packets are not going any further than devices on the network 192.10.8.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/26_using_the_configured_routers.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 6 Sort it out</h1>
*10 minutes*

         ##-- ITQ
        

#### Question

1. Go back to [this network in PT Anywhere](https://forge.kmi.open.ac.uk/pt3.4/) that you were just exploring.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Can PC0 on the first network send messages to PC2 on the other network?

Click *Reveal answer* if you would like a hint.

You will need to find the IP addresses of both PCs and ping from PC0 to PC2. You should find it doesn’t work.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. Can you identify what the problems might be in sending messages from one network to the other?

Click *Reveal answer* if you would like a hint.

Router0 is OK, but Router1 should have the FastEthernet0/0 and Serial2/0 interfaces configured. We also haven’t checked the RIP settings on the routers.

You haven’t yet covered how to do this at the command line (which is the only option in PT Anywhere) but you will be looking at how this is done later in the course.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 4.4 Summary of Session 4


In this session you’ve looked at routing. You have practised configuring different devices with IP addresses and seen how routers use these to get data across networks.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
default route
</td>
<td class="highlight_" rowspan="" colspan="">
The route a packet takes when no specific route is defined in the routing table. In a home network all packets from a device on the network will be sent to the default gateway via the default route.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
hop
</td>
<td class="highlight_" rowspan="" colspan="">
One section of the path (from one network device to the next) taken by a packet between the source and destination.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
metric
</td>
<td class="highlight_" rowspan="" colspan="">
A value that refers to how efficient a route that a packet can take is. It can be used by routers to determine the most efficient routes and make routing decisions.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
`netstat –r`
</td>
<td class="highlight_" rowspan="" colspan="">
A command (short for network statistics) that can be used to view the routing table for a system.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
RIP
</td>
<td class="highlight_" rowspan="" colspan="">
Stands for Routing Information Protocol and is one type of routing protocol that is used by routers to exchange information about other networks.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
`route print`
</td>
<td class="highlight_" rowspan="" colspan="">
A command that can be used to view the routing table for a system.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
routing table
</td>
<td class="highlight_" rowspan="" colspan="">
Contains data about various routes to other networks that a router uses to determine how to direct or route packets.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
routing protocol
</td>
<td class="highlight_" rowspan="" colspan="">
A set of rules that uses software and algorithms to specify how routers share information with each other.
</td>
</tr>
</tbody>
</table>

---

