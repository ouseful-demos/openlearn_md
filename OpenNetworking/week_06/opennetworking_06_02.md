# Session 12: More routing and switching



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/12_abstract_connections_lines_and_spheres.tif)

In previous sessions you looked at how devices are connected together, and what some of the devices used in commercial networks actually look like. In this session you will revisit routers and switches in more detail to see how they operate. Routers and switches are the most common interconnecting devices found on local area networks (LANs). They are used to link end devices together and to link networks together.

You will look at what these devices do – in other words, how they actually deal with the data they are moving from source device to end device.

By the end of this session, you will be able to:

* understand how ARP works to link Network Access layer addresses with Internet layer addressesunderstand how ARP works to link Network Access layer addresses with Internet layer addresses

* understand how routers make their routing decisionsunderstand how routers make their routing decisions

* understand how switches make their switching decisions.understand how switches make their switching decisions.


## 12.1 IP addresses, MAC addresses and the ARP process


In this section you will briefly recap MAC and IP addresses, look at where they fit into the TCP/IP network model, and how the addresses interact with each other. You will use a small network set up in Packet Tracer running in simulation mode, which will show you what the packets and frames of data are doing at each stage of the process.

Watch the video below, which is about 6 minutes long.


### The principles of routing and switching

         ##-- MEDIACONTENT
        
In this session we are going to take a look at how a router makes its routing decisions, and then how a network switch makes its switching decisions. This will expand upon your knowledge gained in Sessions 3 and 4 where these devices were covered in the context of a home network.

Before we do this we need to think about the addressing systems that are in use with each of these types of devices.

Switches operate using MAC addresses which are also referred to as Ethernet addresses or hardware addresses. These addresses are assigned to the hardware by its manufacturer and cannot be changed. These addresses sit at the Network Access layer of the TCP/IP network model.

Routers operate using IP addresses. These are logically assigned and are allocated to each device by the network programmer. These addresses operate at the Internet layer of the TCP/IP network model.

When a source device wishes to send a piece of information to a destination device, this information must be broken down into smaller pieces to be sent out. At each layer of the TCP/IP model the information is broken down into a different data unit which we call protocol data units (or PDUs), and it is encapsulated with some information which identifies it to that layer of the network model. This encapsulation normally adds headers at the beginning of the unit and a trailer at the end to mark the end of the unit.

We have built a small network in Packet Tracer to help us demonstrate this session. We will use this network for each of the following demonstrations. We will use a simple ping from one PC to another and look at how the router makes its routing decision, and how the switch makes its switching decision. While we are doing this, we are going to come across a problem in the process.

OK, so we are going to make PC2 ping Router0, which is its default gateway. When we type ping 172.16.0.1 into the command prompt of PC2, an ICMP echo packet will arrive at the Internet layer of the TCP/IP process running in the machine, which is also called the TCP/IP stack. The Internet layer then adds the source and destination IP addresses to the header of the packet. The source IP address is the address of PC2 where the packet comes from, and the destination address has been typed into the ping command by the user – so it is known too. The block of data is now called an IP packet and is passed down the stack to the Network layer below. This layer now needs to add in the MAC addresses to make up the header for the network frame – which is the protocol data unit of the Networklayer of the TCP/IP network model.

Again, we know the source MAC address (it is the MAC address of the network adapter in the PC, which was set by the manufacturer of the network card when it was made). The destination MAC address is the MAC address of Router0 – the destination of the ping. Now we have discovered our problem: how do we get the MAC address for Router0, which is elsewhere on the network?

This is where a process called Address Resolution Protocol comes to our aid. Also called ARP, this process is crucial to the operation of all networks and is the way of finding a network address or hardware address from a known IP address.

Whilste we run through the rest of the demonstration, keep an eye open for the simulation panel on the right-hand side. This is a useful feature of Packet Tracer and allows you to see the order and content of the packets and frames, whilst at the same time watching them move around the network. The packets are represented with little envelopes as they travel down the wires and through the devices.

OK, back to PC2. Because the destination MAC address in unknown, the PC will send out an ARP request on the network. This request is sent out to the broadcast MAC address, asking for the device with the IP address of 172.16.0.1 to identify itself. The switch will receive this frame of data and, because it is a broadcast, it will forward the frame out of all ports except the one it came in from. Both Router0 and PC3 will receive this ARP broadcast request. PC3 will ignore or drop the frame because its IP address does not match the request. The router *does* have this IP address, so it will generate an ARP reply frame which will contain its own MAC address as the source MAC address, and the destination MAC address of PC2 (which the router knows from the incoming ARP request).

This reply will be sent to the switch, which in turn will forward it on directly to PC2. We will be looking at how switches work later on in this session, so don’t worry about what the switch is doing for now.

When the ARP reply reaches PC2, it will store the MAC address to IP address mapping in its ARP cache. By storing the MAC to IP mappings in an ARP cache, the device will not have to do this ARP process every time a packet needs to be sent to this destination. This will speed up the network process, but a time limit of a few minutes is applied to this mapping, so that changes in the network can still take place.

This means that we now have the source and destination IP addresses *and* the source and destination MAC addresses. So we have all of the information the PC needs to communicate with the router.

With this information the ping now completes the ICMP echo request which can now be sent to the destination device – in this case the router. The frame will now arrive at the switch where it will be forwarded to Router0. When Router0 receives this echo-request, it will respond with an ICMP echo-reply. This echo-reply will arrive back at the switch, and will be forwarded on to PC2. When the echo-reply is received back at PC2 it will display a message on the screen confirming the reply, with some other information such as the round-trip delay. This round-trip delay is usually measured in milliseconds and is an indication of how long the echo has taken to travel back to the PC.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/67_the_princuples_of_routing_and_switching.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Test yourself


#### Question

*5 minutes*

1. What is the Network Access layer protocol data unit (PDU) called?

(a) Packet

Incorrect. This is the Internet layer PDU.

(b) Frame

(c) Data

Incorrect. This is the PDU at the Application layer.

(d) Block

Incorrect. No TCP/IP model layer PDUs are referred to as ‘block’.


#### Question

2. What is the purpose of the ARP cache?

(a) The ARP cache records the number of ICMP packets sent.

(b) It is an address table.

Incorrect. Saying it’s an address table is not specific enough.

(c) The ARP cache stores the IP address to MAC address mappings temporarily to minimise ARP lookups.

(d) The ARP cache stores a history of destination IP addresses the machine has communicated with.




## 12.2 How are routing decisions made?


In this section you will have a look at how a router makes its routing decisions, using the same demonstration network made in Packet Tracer as you used in the previous section, and running in simulation mode to show you what the packets are doing at each stage.

Watch the video below, which is about 4 minutes long.


### How are routing decisions made?

         ##-- MEDIACONTENT
        
In order to demonstrate how the router makes its routing decision, we will use the same demonstration network we have used in the previous demonstrations.

This time we will use a ping from PC0 to PC1. We will ignore what happens in the internet router at first, and just look at the decisions made by Router0. As the ICMP packet comes in from the internet router it will have the destination IP address of 192.168.0.10 in its Internet layer header. The destination IP address in the packet is 192.168.0.10. The routing table contains entries for the connected networks of 172.16.0.0/24, 192.168.0.0/24 and also the 1.1.1.0/30 network in which the packet came in from. Note that each connected network shows up twice, one with the code of C which is the network it is on, and one with the code of L – which is the exact IP address of the router’s port. Note also that there is an entry marked S* at the end of the list. We will come back to this in a moment.

Now, back to the routing decision. The router will look at the destination address of the packet, in this case 192.168.0.10, and compare this address with the addresses in the routing table. The router will try and match the address with the entries in the routing table. If it finds multiple matches it will choose the best match – the one with the most bits matched will be selected. In this case there is a match with the network 192.168.0.0/24, which is on GigabitEthernet0/0. The packet will now be sent out of this interface and on to the switch, which will then send it on to PC1. PC1 will then respond with an echo-reply, which will have the source address of itself, and the destination of 10.0.0.10, which was the source of the echo request in the first place. When Router0 receives this packet it will look for 10.0.0.10 in its routing table. As you can see, there is no entry for any 10.0.0.0 network in this routing table. If the router does not find any match, it should drop the packet completely. This would cause the ping to fail and is not a very desirable outcome. We could either fix this by putting static routes into the routing table for all networks we wish to reach, or we can put a default route into it. This default route would then direct any traffic for networks not in the routing table to a valid destination. This default route has already been put into the routing table and is the entry with the code of S* we mentioned earlier in this presentation. This S* entry will also be listed above the routing table as the gateway of last resort when you do a `show ip route`.

So, back to our ping packet. There is no match for 10.0.0.0 in the routing table so the router will use the default route, which will send the packet out of GigabitEthernet0/2, which points towards the internet router. The ping will now continue on its journey to PC0. Now let’s have a quick look at the command prompt output which has happened while we were watching our ping packets going from the source to the destination and back. The first three ping packets have in fact failed, and the fourth one has succeeded. You should be able to guess why this happened. Think further back in this session to the ARP problem. The reason for the first failures is because the ARP process needed time to obtain all the MAC addresses for each section of the network – so PC0 needs to find the internet router’s MAC address, the internet router needs to find R0’s mac address, R0 needs to find PC1’s MAC address. This all takes time and means that some pings may be dropped. Remember we told you that these MAC addresses are cached for a period of time. This can be proved when you execute the ping again soon after. This time all four pings pass.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/68_how_are_routing_descisions_made.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 2 Test yourself


#### Question

*5 minutes*

1. What component of the router’s system does the router use to decide which port to send the data packet out from?

(a) ARP table

Incorrect. The ARP table maps IP addresses to MAC addresses and is not used in the routing decision.

(b) MAC address table

Incorrect. Routers do not make routing decisions based on Network Access layer addresses.

(c) Routing table

(d) Default gateway

Incorrect. The default gateway might be stored in the routing table as a default static route, but the default gateway is not consulted to make the decision.


#### Question

2. What does a router do with any packet it cannot find a destination network for in its routing table?

(a) Sends it out of all ports.

Incorrect. This is not an appropriate thing for a router to do.

(b) Creates a new route.

Incorrect. Routers do not create routes on demand.

(c) Returns the packet to the sender.

Incorrect. Routers never return the packet – though they may reply with ICMP error messages.

(d) Drops the packet.

Correct. Routers should drop a packet if there is no matching destination network – unless there is a default static route set up.


#### Question

3. Why do the first few ping packets fail when you ping an IP address you haven’t pinged recently?

(a) The layer 2 address (MAC address) is not present in the ARP table and must be looked up by the ARP process; this takes time, so the first few packets will fail.

(b) The router doesn’t know where to send the packet and takes too long to decide.

Incorrect. The router will make its decision very rapidly.

(c) The destination device is busy at the time.

Incorrect. This might be true on an odd occasion, but the results will not be perfectly repeatable.

(d) The router was switched off at the time.

Incorrect. Routers take a long time to boot up, so it is likely that all the ping packets would fail.




### Activity 3 Try it out


#### Question

*10 minutes*

1. Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt12.2) in a new tab or window so you can read these instructions. A ‘spare’ PC is provided at the bottom for use in step 4 of this activity.

Investigate the network and enter the configuration settings into a copy of the table.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router1</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router1</td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
</tbody>
</table>

2. Check to see if there is a gateway of last resort set on each router. If there is, make a note of each one. (Hint: use the command `show ip route`.)

3. Ping PC1 from PC0. What happened?

4. Connect an additional PC (PC2) to the switch on the network 192.168.8.1 and configure it with an appropriate IP address, subnet mask and default gateway. (Use the spare PC provided at the bottom for this.)

5. Ping PC0 from PC2. What happened?

1. On both routers the command `show ip interface brief` should have given you the IP address of each configured interface. (It will also have given you the status of the configured interfaces which should have been ‘up’). To check the IP addresses and default gateway for each of the PCs you can use the command `ipconfig`. This is what your table should have looked like.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.50.8.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router1</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.2</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router1</td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.50.8.2</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.50.8.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.2</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.1</td>
</tr>
</tbody>
</table>

2. To show the gateway of last resort of each router, you need to use the command `show ip route`. You should have discovered that for both routers, the gateway of last resort was g0/0.

3. When pinging PC1 from PC0 you may have found that the first two or three pings timed out. As you learned in this session, this is because the ARP process needs time to ascertain all MAC addresses for each section of the network.

4. A suitable IP address for PC2 would have been anything in the range 192.168.8.3 to 192.168.8.254, but a logical choice would be 192.168.8.3.

5. When pinging PC0 from PC2 you may again have found that the first two or three pings timed out for the reason given above.




### Activity 4 Think about


#### Question

*2 minutes*

As you learned in the video ‘How are routing decisions made?’, configuring a static route by setting a router’s gateway of last resort is one way of ensuring that a packet doesn’t get dropped when its destination address isn’t in a router’s routing table. This is how the network in Activity 3 was configured, with each router using the other one as its gateway of last resort. This isn’t an ideal solution though. Can you see why?

It is possible that a packet could arrive at the router with an IP address that neither router knew anything about. In this event, the packet could end up going backwards and forwards between the routers until it is eventually discarded as it reaches its maximum number of hops specified in its ‘time to live’.




## 12.3 How are switching decisions made?


In this section you will have a look at how switches make their switching decisions, using the same demonstration network you used in the previous section. You will again be able to see what the frames of data are doing at each stage, with Packet Tracer running in simulation mode.

Watch the video below, which is about 3 minutes long.


### How are switching decisions made?

         ##-- MEDIACONTENT
        
In this part we are going to look at how a switch works. Switches work at the Network Access layer of the TCP/IP network model, which means that they use MAC addresses to forward frames of data. Although there are more powerful and advanced switches which use IP addresses and operate at the Internet layer as well, most switches know nothing about the Internet layer and only use MAC addresses to make their switching decisions. This means that normal switches do not generate ARP requests or have anything to do with IP addresses.

When a switch is first powered on, its MAC address table will be empty and will contain no addresses. This can also be simulated by issuing the command `clear mac-address-table`, which we have done in the Packet Tracer network. The MAC address table is currently empty. To populate the MAC table we must generate some traffic between the PCs. In this case we are going to start with a ping from PC2 to Router0. We have set up a table to the left of the diagram which will show you the current entries in the MAC table of Switch1 at the relevant time. PC2 pings Router0. The packet leaves the PC in an Ethernet frame and enters Switch1 on port FastEthernet0/1. When the switch receives the frame, it looks in the Ethernet frame at the source address in that frame. The address is then added to the MAC table and referenced to the port number the frame came in on. The switch looks in its table to see if the destination MAC address is there. Currently it is not, so the switch forwards the frame out of all ports except the one it came in on. This means that both Router0 and PC3 will receive the frame. Only Router0 will get a match to the destination MAC address; PC3 will ignore it completely. When Router0 replies back, the reply frame will contain its own MAC address as the source address and the destination MAC address of PC2. At this point the switch will look at the incoming frame on Gigabit0/2 and read the source MAC address and add it into the MAC table. It will then look at the destination MAC address and see if there is a match. There will now be a match as the MAC address of PC2 was already added to the table previously. The frame will now be sent out only on the port Fa0/1 and on to PC2.

This is the content of Switch1’s MAC address table, just to show you that the table we created to the left of the screen is genuine. In order to complete the network, we need to generate some traffic from PC3 so that its MAC address can be added to the table of the switch too. PC3 pings the router on 172.16.0.1. The frame arrives at the switch and its source address is added to the MAC table. The destination MAC address is checked against the entries in the table. There is a match for port Gigabit0/2, so the switch will send the frame back out on that port to the router. The ping reply frame will leave the router and enter the switch on Gigabit0/2. The switch will record the source MAC address in the table. Because it’s already there, the table will simply be updated with the time-out counter reset; in other words, the entry is refreshed. The switch will then look up the destination MAC address and find that it matches that of PC3 on port Fa0/2. The frame is then sent out of that port where it will be received by PC3, competing the ping. Here we can see the fully populated MAC address table of the switch.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/69_how_are_switching_descisions_made.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 5 Test yourself


#### Question

*5 minutes*

1. Do switches generate ARP requests?

(a) Yes

(b) No


#### Question

2. What type of addresses do switches store in their switching tables?

(a) IP addresses

Incorrect. It is routers that use IP addresses, not switches.

(b) Postal addresses

Incorrect. Completely irrelevant to the operation of switches.

(c) MAC addresses

(d) Gateway addresses


#### Question

3. Will switches forward frames out of all ports (except the one the frame came in on) if the destination MAC address is not in the MAC address table?

(a) Yes

(b) No



Next you are going to revisit an earlier activity that involved a simple network comprising a switch and four PCs.


### Activity 6 Try it out


#### Question

*10 minutes*

1. Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt12.3) in a new tab or window so you can read these instructions. The ‘spare’ switch and the two PCs at the bottom are for use in step 4 of this activity.

Investigate the network and enter the configuration settings into a copy of the table.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC2</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC3</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
</tbody>
</table>

2. From the CLI of the switch have a look at the MAC address table. You should find the table is currently empty. (Hint: to view the MAC address table you will need to use the command `show mac-address-table` from the privileged executive mode.)

3. Generate some network traffic by sending a broadcast ping from one of the PCs and then have another look at the table. You should now find that the table has been populated.

4. Add a second switch to the work area, with a couple of PCs connected to it, to create a second isolated network. (Use the spare switch and PCs provided at the bottom for this.) Configure these new PCs with suitable IP addresses and add the configuration details to the table you created in step 1.

5. Generate some network traffic on the new network and then have a look at the MAC address table of the new switch.

6. Now connect your new network to the router by adding a link between the router interface G0/1 and the switch.

7. Configure the router interface G0/1 with an appropriate IP address and add this address as a default gateway on both of the new PCs. Once again, add the configuration details to the table you created in step 1.

8. Try to ping between networks.

9. Examine the routing table from the CLI of the router. Can you see the connected networks (C)? And the IP addresses of the router interfaces (L)? (Hint: use the command `show ip route` from the privileged executive mode.)

1. Your table should look like this.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">-</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.11</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC2</td>
<td class="highlight_" rowspan="" colspan="">-</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.12</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC3</td>
<td class="highlight_" rowspan="" colspan="">-</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.13</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
</tbody>
</table>

2. If there were any entries in the MAC address table, you may have accidentally generated some network traffic. You can clear the MAC address table with the command `clear mac-address-table`.

3. The broadcast address for this network is 192.168.2.255 . You should have seen replies come in from each of the other three PCs and that the MAC address table now has five entries – one for each of its connected interfaces.

4. You could have chosen any private IP addresses for the two new PCs but, of course, they should both belong to the same network. For example, 192.168.8.10 and 192.168.8.11.

5. Again, you need to use the broadcast address for this network. For the example IP addresses given above, this would be 192.168.8.255. Once again, your ping should have populated the switch’s MAC address table.

6. Router interface 0/1 needs to be configured with a suitable IP address which will be the same for the PCs’ default gateways. For the example IP addresses given above, this would be 192.168.8.1. Using these example IP addresses, the complete configuration table would be:
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.11</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC2</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.12</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC3</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.13</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.2.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC4</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC5</td>
<td class="highlight_" rowspan="" colspan="">–</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.11</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router0</td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.168.8.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
</tbody>
</table>

7. If your ping between the two networks was unsuccessful, it may have been because the default gateways on the PCs were not correctly set.




## 12.4 Summary of Session 12


In this session you have looked at how both routers and switches make their forwarding decisions based on their relevant addresses, and how MAC addresses are learned from an IP address via the ARP process.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
ARP (address resolution protocol) 
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol used to find the MAC address of an unknown device on the local network, if you know its IP address.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
ARP broadcast
</td>
<td class="highlight_" rowspan="" colspan="">
The broadcast MAC address of FF:FF:FF:FF:FF:FF which will be received by *all* devices on the local network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
ARP reply
</td>
<td class="highlight_" rowspan="" colspan="">
The reply data which the device sends back to the source giving its MAC address.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
ARP cache
</td>
<td class="highlight_" rowspan="" colspan="">
A data table used to temporarily store the IP address to MAC address pairings.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
broadcast
</td>
<td class="highlight_" rowspan="" colspan="">
In this context, a type of traffic which is designed to be seen by *all* devices on the local network, not just a single device.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
destination IP address
</td>
<td class="highlight_" rowspan="" colspan="">
The IP address of the destination device (where the traffic is heading to).
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
destination MAC address
</td>
<td class="highlight_" rowspan="" colspan="">
The MAC address of the destination device (where the traffic is heading to).
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
frame header
</td>
<td class="highlight_" rowspan="" colspan="">
A block of information put at the start of a frame containing information such as the source and destination MAC addresses and other fields.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
ICMP (Internet Control Message Protocol)
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol used to report network problems that prevent the delivery of IP packets. Both ping and traceroute use ICMP.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
IP packet
</td>
<td class="highlight_" rowspan="" colspan="">
The basic unit of data at the Internet layer of the TCP/IP protocol suite.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
MAC address table
</td>
<td class="highlight_" rowspan="" colspan="">
Also known as ‘forwarding table’. Table used by a switch to associate MAC addresses of devices with port numbers to enable frames to be forwarded to their destination.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
PDU (protocol data unit)
</td>
<td class="highlight_" rowspan="" colspan="">
The term used to describe the data at each layer of the network model.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
source IP address
</td>
<td class="highlight_" rowspan="" colspan="">
The IP address the traffic originated from.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
source MAC address
</td>
<td class="highlight_" rowspan="" colspan="">
The MAC address the traffic originated from.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
TCP/IP Internet layer
</td>
<td class="highlight_" rowspan="" colspan="">
The layer of the TCP/IP model containing the IP address information.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
TCP/IP Network Access layer
</td>
<td class="highlight_" rowspan="" colspan="">
The bottom layer of the TCP/IP network model. This is where the hardware sits, along with MAC addresses.
</td>
</tr>

</tbody>
</table>

---

