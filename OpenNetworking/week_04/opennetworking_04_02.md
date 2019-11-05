# Session 8: Route tracing, collision avoidance and scene setting



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/08_chaotic_background.tif)

In this session you will be looking at a way of tracing the route used by an IP packet. You will also look at the method used in Wi-Fi for distributing access to the radio channel among users. Finally, as scene-setting for the next eight sessions, you’ll briefly look at some of the ways networking in large enterprises differs from networking in homes and small businesses.

By the end of this session, you will be able to:

* use traceroute and interpret traceroute responsesuse traceroute and interpret traceroute responses

* understand the principles of multiple access and collision avoidance in Wi-Fiunderstand the principles of multiple access and collision avoidance in Wi-Fi

* understand how enterprise-scale networking differs from home networking.understand how enterprise-scale networking differs from home networking.


## 8.1 Tracing the route


Traceroute is a diagnostic tool for locating blockages on the route of an IP packet. This section shows you how to use it. Traceroute is also useful for giving an idea of the number of routers, and sometimes their locations, that a packet has to pass though to reach its destination.

Now watch the video below, which is about 6 minutes long.


### Tracing the route

         ##-- MEDIACONTENT
        
You’ve used ping commands for checking networks, but there are other commands that can be used for diagnostics. A common one is traceroute, and I’ll talk about that now.

First of all, though, I want to say something about the limitations of ping. Some routers on the internet block incoming ping messages. This is particularly true with the gateways to some organisations and businesses.

Pings have been used maliciously by hackers, so this is probably why they are sometimes blocked. Blockages can lead to false conclusions.

For example, where there’s a blockage on pings, you might conclude that because pings fail on that IP address, no IP traffic can get through. But this might not be true. So that’s one possible problem with the ping test.

But leaving aside deliberate blocking, a problem with pinging occurs if you ping a host that is several routers away from you, or several hops away. If the ping times out, you can’t tell where the problem is. The ping might be failing at the destination, or at any of the routers on the way to the destination.

Traceroute is designed to help locate the problem in cases like this. Traceroute works by probing each router along the journey from your computer to the destination device. Each router should respond to the traceroute probe, so you can work out how far towards the destination your probes are getting.

For each hop of the journey, traceroute gives you get a round-trip time, or RTT. Ideally you should get a response from here, then here, and here, and so on. If there’s a router that’s not processing your probes, the responses should stop at the preceding router.

Let’s have a look at this in practice. I’m doing this traceroute test from a Windows machine. The traceroute command takes different forms depending on the device you’re sending it from. On Windows machines the traceroute command is this, which looks like ‘tracert’, but I think you’re supposed to read it as ‘trace rt’, and the ‘rt’ is an abbreviation for route.

On Cisco routing devices, at the command prompt you would enter the command traceroute .

I’m going to direct the traceroute command towards an online timeserver. A timeserver is an online clock that other online devices consult to find the current date and time. Home gateways generally use a timeserver to get the date and time, and computers do too.

So here I am at the command prompt of my Windows computer. I enter tracert and the IP address, which in this case is 128.138.140.44. And we can see that the host with this IP address is in the USA, so we can expect there to be lots of routers between my computer and the destination. I’m doing this at home, so this first line of the responses is from my home gateway. The traceroute command sends three packets to each router, and these are the three round-trip times corresponding to the three packets: 7 milliseconds, 6 milliseconds, and then 3 milliseconds. The second response is from a router with this IP address on one of its interfaces. I assume this router belongs to my internet service provider.

The third response is no response at all. It looks as though this router here is not replying to the command, but the fourth line shows that traffic is nevertheless getting beyond the third router.

The fourth and fifth responses look as though they’re from the same neck of the woods as the second.

You might be wondering why these round-trip times from routers further away are shorter than the round-trip times from the second router. The point here is that the round trip time doesn’t just include the time for the outward trip and the return trip. It also includes the time it takes for the router to get round to sending a response back to me. Response times vary a lot from router to router.

You can get situations like this where a more distant router has received a data packet, forwarded it, and sent a response, while an earlier router still hasn’t got round to responding.

Towards the end here you can see that several routers are located in the University of Colorado, which is where the destination host lives. The final response is from the IP address I typed at the start, so we know the destination was reached via 19 routers.

Something else you might be wondering is how these probes can be directed at particular routers, when the path isn’t known at the start. The answer is that the probes aren’t directed at particular routers. The IP packets used in these probes, like all IP packets, have a ‘time to live (TTL)’. The time to live is specified as the maximum number of hops a packet can do before it is discarded. As each router forwards a packet, it decreases the packet’s time to live by 1, or typically by 1. If the time to live hits zero before the packet arrives at its destination, the packet is discarded.

The first traceroute probe is launched with a time to live of 1. This packet gets only as far as the first router. The second is launched with a time to live of 2, and gets as far as the second router. The third has a time to live of 3, and so on.

As you saw, the traceroute command, by default, has a maximum of 30 hops, so the 19 hops in my example falls comfortably within the limit.

In principle, the traceroute’s round-trip time could be used to show the major causes of latency in a route, on the assumption that the round-trip time indicates the latency of each router. But, as I mentioned earlier, the round-trip time isn’t a reliable indicator of how quickly a router forwards packets, so you have to be very cautious about drawing conclusions about latency from traceroute.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/51_tracing_the_route.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Try it out


#### Question

*20 minutes*

1. 
Configure the computers on this [PT Anywhere](https://forge.kmi.open.ac.uk/onl2-pt8.1) network.


2. 
Send a traceroute probe to one of the computers from the other.


3. 
Send a traceroute probe from the router to one of the computers. Bear in mind that the router is a Cisco device.


4. 
Send a traceroute probe from any device to 127.0.0.1. (This is an example of a loopback address. Loopback addresses were explained in [Session 2, Section 2.5](https://www.open.edu/openlearn/ocw/mod/oucontent/view.php?id=92820&amp;section=2.5).)




The next video compares traceroute responses when a computer uses a wired connection and Wi-Fi.

Now watch the video below, which is about 2 minutes long.


### Traceroute using wired and wireless connections

         ##-- MEDIACONTENT
        
In this video, I’m saying a little more about traceroute, but mainly setting the scene for Part 2 of this session, which looks at the way access to the radio channel is managed in Wi-Fi.

I said at the end of the last video that you had to be cautious about using round-trip times as an indication of latency. All the same, the round-trip times in traceroute can throw up some illuminating surprises, and I want to show you one here.

In this video I’m sending a traceroute command from one computer in my home to another, via the home gateway. I’ll do it twice. The first time, the sending and receiving computers are both wired to the Ethernet ports at the back of the gateway. The second time the computer at the receiving end uses Wi-Fi to communicate with the gateway. The sending computer remains connected by wire to the gateway.

So here’s the result of the first traceroute command, with both computers wired to the gateway. Notice that the traceroute command went to an IP address with this number at the end: 110. Round-trip times are short and consistent. One millisecond each time.

Now let’s look at what happened when the receiving computer used Wi-Fi. It’s the same computer at the receiving end, but its wireless interface and wired interface have different IP addresses – as is usual. This time I sent the traceroute command to this IP address, with a final number of 101. And this is what I got. The huge variation of round trip times is striking.

There could be more than one reason this. For example, on many laptops the wireless interface can go into a low-power mode during idle periods, and coming out of that mode could take some time. But what’s probably also significant is the way Wi-Fi devices regulate access to the radio channel, which can involve relatively long delays. And that’s what I’ll be looking at in Part 2.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/52_traceroute_using_wired.jpg)

         ##-- ENDMEDIACONTENT
    



## 8.2 Collision avoidance and multiple access in Wi-Fi


In all networks, ‘access’ is a major consideration. ‘Access’ in this context means ‘access to the underlying communication medium in order to send and receive data’; and by ‘underlying communication medium’ we mean things like cables, radio channels and optical fibres.

If many people use the same medium, the term ‘multiple access’ is used. Designers of multiple access systems have to deal with questions like ‘How do we ensure that one person’s data doesn’t interfere with someone else’s?’ and ‘How do we ensure that all users get fair access to the medium?’

The procedure used for multiple access in Wi-Fi is effective, in the sense that it can cope with many users in a small area, but at the cost of increased latency, or delay. As you will see in the following video, delays are part of the system used for multiple access in Wi-Fi. This connects with the video you saw at the end of Section 2.1.

Now watch the video below, which is about 6 minutes long. It is narrated by a colleague.


### Collision avoidance and multiple access in Wi-Fi

         ##-- MEDIACONTENT
        
This animation looks at how Wi-Fi allocates the use of the radio channel among its various users. The way it’s done in Wi-Fi is very different from the way it’s done in cellular mobile communications (such as 3G and 4G).

In cellular mobile communications, the base station controls how the communication resource is shared out among users’ devices. Wi-Fi networks can work in a similar way, with the access point controlling the individual devices, but this type of Wi-Fi network is rare. It’s much more common to use the so-called distributed coordination function, or DCF, where the responsibility for sharing access is distributed among all the devices in the network.

In the DCF, the access point is not privileged – it gets access to the radio channel in the same way that other devices in the network do. I will refer to all devices in the network as nodes. A node can be an access point, a Wi-Fi-enabled computer, a smartphone, a wireless printer, or any other Wi-Fi-enabled device.

The access point does have a special role in allowing other devices onto the network (through the use of passwords and so on), but the way it determines when to transmit is the same as the way other nodes on the network do it.

Before we look at the distributed coordination function, it’s useful to establish some terms. An access point and the nodes associated with it, under the control of a common coordination function, is called a basic service set (or BSS).

This set of nodes could be a BSS if all the devices were communicating with the access point.

A BSS is identified to Wi-Fi users by a service set identifier (SSID). This in effect is the network name, such as Sarah’s Network. Among other things, the SSID enables the user of a device to see which networks are available, and to choose one to connect to.

Coordination of network nodes is needed to prevent collisions like these. Collisions cause signal corruption and loss of data. The distributed coordination function ensures that only one device at a time transmits. It does this through a ‘listen before transmit’ protocol. The official name for this protocol is carrier-sense multiple access with collision avoidance, or CSMA/CA.

Before transmitting data, all nodes monitor the radio channel that is being used by the SSID that the nodes are intending to connect to. The same radio channel might also be in use by another nearby SSID. I’ll come back to that point later.

When the channel is clear, nodes with data to transmit wait a fixed length of time. I’ll call this the check period. At the completion of the check period, provided the channel has remained clear, a period called the ‘contention window’ begins. At the start of the contention window, each waiting node starts counting down from a random value chosen by itself. This is called ‘backing off’.

It’s extremely unlikely that more than one device will back off from the same number, so whichever node reaches zero first gains control of the channel. Provided the channel has remained clear during the contention window, the successful node starts to transmit all its frames in sequence.

A frame consists of a data payload, with headers indicating the destination MAC address, and other control data. It usually also incorporates error detection or correction data. A typical payload for a frame would be an Internet Protocol packet, which would have the IP address of the destination.

Other nodes with data to transmit that were also backing off must start the whole process again, beginning by monitoring the channel for the check period. But during the next contention period, they count down only the remainder of their back-off period from the previous attempt. This increases their likelihood of success.

You might wonder what the point of the check period is. Why doesn’t the contention period begin immediately the channel is clear?

The point of the check period is to enable certain types of traffic to be given priority over others. Priority is enabled by specifying a short check period for certain types of traffic.

For example, if a node has just completed a transmission, it will expect to receive an acknowledgement very soon afterwards. Acknowledgements therefore should have priority over new transmissions.

Priority is achieved by allocating a short check period to acknowledgements. This guarantees they will be transmitted before new data, which has a longer check period.

The collision avoidance protocol means that Wi-Fi networks behave quite well together, even when there’s a high density of networks, as you often get in urban areas.

These are Wi-Fi signals in the 2.4 GHz band detected in a shopping centre. This density of signals is not unusual for a busy location.

The waiting periods involved in CSMA/CA mean that the radio channel is not used as efficiently as it could be if there were centralised control. This has led to the use of frame aggregation in Wi-Fi versions 802.11n and 802.11ac. In these Wi-Fi versions, when a node is finally able to transmit, it can send several aggregated frames at once rather than a series of frames.

Nevertheless, delay-sensitive traffic such as voice or video is not well served by the process I have described.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/53_collision_avoidance.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 2 Test yourself</h1>
*15 minutes*

         ##-- ITQ
        

#### Question

1. After the first frame of someone’s data has been successfully transmitted, subsequent frames in the same data transfer are given a short check period. What is achieved by using a short check period in this case?

It should ensure that all frames are sent in unbroken succession, without the need to enter a contention period again. Going into a contention period would probably result in loss of control of the radio channel, and hence cause delay.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. An advice column in a magazine says: ‘If your neighbour is using the same Wi-Fi channel as you, change your Wi-Fi channel so that you don’t interfere with each other.’ The advice is good, but the reason is wrong. Explain.

The CSMA/CA system used in Wi-Fi ensures that two users on the same channel who are within range of each other do not use it simultaneously. So there will be no interference. However, there could be additional delays before each user gets access to the channel if both neighbours use the Wi-Fi intensively. To reduce the risk of delay, it would be sensible to switch to a channel that is not being used (although this is not always possible in very busy areas).

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 8.3 Looking ahead


The last eight sessions have been based on home networks, or the networks you would find in a small business. In large organisations or enterprises, however, the equipment used is more sophisticated, and networks are more complex because of the use of subnetworks. The next eight sessions focus on ‘enterprise’ networks and processes. For example, setting up a router in an enterprise network is very different from setting up a gateway in a home network. The following video looks briefly at some of the significant differences between home and enterprise networking.


### Looking ahead

         ##-- MEDIACONTENT
        
Throughout these eight sessions we been looking at networking, IP addressing and related ideas in the context of home networks. Actually, what we’ve been showing you wouldn’t just be found in homes. It would also be found in small businesses, such as shops, cafés and restaurants, solicitors’ offices, estate agents, and so on.

In large businesses and organisations, the same basic principles of IP addressing, subnet masks, DHCP, network address translation, and so on, apply. But the way they are implemented, for example the equipment used and the network structures, are more complicated. In fact, organisations like these to employ full-time network managers to keep things working.

Networks at this level areis often described as ‘enterprise’ networks, and the equipment used is described as enterprise routers, enterprise switches, and so on. Setting up enterprise equipment and networks is more involved than it is for home equipment and networks.

The next eight sessions relate mainly to the enterprise context. In this part I want to give a quick overview of the way enterprise networking differs from home networking.

As we’ve already mentioned, the home gateway, which is often informally called a router, combines the functions of a router, a switch, a DHCP server, and a Wi-Fi access point.

In the enterprise context, these are usually separate pieces of equipment, and often far from each other.

In a home gateway, the router has just two interfaces. Setting up these interfaces was mainly a matter of entering appropriate numbers in a graphical interface.

An enterprise router might have two or more interfaces. Giving an interface an IP number on one of these routers is usually done through a command-line interface, and involves several steps. It’s very different from the way you do it on a home gateway. Just to give you a flavour of what’s involved, I’ll set up an IP address on one of the router interfaces here, using the command-line interface.

I go to the command prompt of the router. I type `enable`. The prompt changes to a hash sign.

The next stage isn’t actually necessary, but it’s useful: `show ip interface brief`. It shows that there are two Ethernet interfaces, without IP addresses, and both are ‘down’, that is, not working.

So now I type a new instruction, `configure terminal`, and the prompt changes again.

Now I choose which interface to set up. This is the gigabit Ethernet 0 slash 0 interface.

The prompt changes again, and I key in the IP address and the subnet mask.

And then this curious instruction, `no shutdown`, to switch it on, or ‘up’.

Now it’s useful to go back to the `show ip interface brief`command, just to check everything looks right. And there we see that the 0 slash 0 interface has the right IP address and is ‘up’, that is working. So all that’s just for one interface.

Another distinctive feature of enterprise networks is the extensive use of subnetworking to create manageable groups of users.

For example, in a large organisation, you could have subnetworks for these groups of staff, and within each of these groups there might be further subnetworks. Typically there might be differing security policies for these subnetworks. For example, some subnetworks might only be accessible to certain categories of staff.

There might be further subnetworks for functions like printing, and subnetworks for servers providing public-facing services such as web pages, online purchasing, enrolment, and so on.

Enterprise networks also often span multiple sites, often widely separated, but interlinked so that, for the staff, there’s no difference between communicating with someone on the same site, or someone on a different site, possibly in another country.

So the world of enterprise networking is quite a step up from what we’ve been looking at so far.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/54_looking_ahead.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 3 Test yourself</h1>
*15 minutes*

         ##-- ITQ
        

#### Question

1. In the video, an enterprise router is described as having two or more interfaces. This refers to the number of network interfaces. Why might such a router have more than two network interfaces?

To transfer data between more than two networks. A router’s function is to act as a gateway between networks, so that data packets can be transferred between networks. A router with four network interfaces can receive a data packet on one interface and forward it to one of the three networks connected to its three other interfaces.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. The activity shows the interface of an enterprise router being set up manually via the command-line interface. Enterprise networks use DHCP, so why is manual configuring of some interfaces necessary?

On the public internet, network addresses need to remain constant so that packets can be directed to the right destination network. This means that router interfaces need to remain fixed.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. Towards the end of the video, it is pointed out that some enterprises have an international spread, and yet ideally users’ experience should not be noticeably different when communicating with remote colleagues compared with local colleagues. What particular difficulties could be expected with such long-range communication (compared with local communication)?

One problem is increased latency for long-range traffic, which almost certainly has to pass through more routers than local traffic. Another potential problem is security, as data could be expected to be vulnerable on the public internet. (In fact, so-called ‘tunnels’ are used in practice to mitigate both problems. Data tunnels are virtual private lines, which nevertheless operate over the public internet, and data traffic can traverse them with less latency than ordinary IP traffic. Traffic in data tunnels is also usually encrypted.)

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 8.4 Summary of Session 8


In this session you have seen how the traceroute command can be used diagnostically to locate routers that are not forwarding packets. You also saw that traceroute gives an indication of the latency of routers, although the latency indicated by traceroute can be misleading.

You also saw how the collision avoidance of Wi-Fi enables a Wi-Fi radio channel to be shared in an orderly way among multiple users (even among users who are on different Wi-Fi networks but whose networks use the same channel and are within range of each other). The access method was shown to be dependent on delays of varying lengths, and on busy radio channels users are likely to suffer longer delays than on little-used channels.

Finally you saw that enterprise networking, although sharing many of its basic networking principles with home networking, makes use of more complex equipment, which is configured using specialised techniques, and extensively uses subnetworking (or subnetting) for network management, security and robustness.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
backing off
</td>
<td class="highlight_" rowspan="" colspan="">
In Wi-Fi, backing off is a procedure for randomly allocating access to a radio channel to a single device out of all the ones waiting to transmit data. When a radio channel has been unused for a set length of time (the ‘check period’), devices with data to transmit count down from a random number. This is backing off. The first device to reach zero gains access to the radio channel.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
check period
</td>
<td class="highlight_" rowspan="" colspan="">
A fixed length of time for which a radio channel must be unused before backing off begins.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
contention window
</td>
<td class="highlight_" rowspan="" colspan="">
The period of time during which contending devices count down from a random number in order to determine which one will gain access to the radio channel. It’s the stage during which backing off occurs.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
enterprise network
</td>
<td class="highlight_" rowspan="" colspan="">
A network used in large-scale businesses and organisations. Enterprise networks use powerful, dedicated hardware, such as separate switches, routers, firewalls and DHCP servers, rather than a single device that does all this as would be found in a home network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
listen before transmit
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol (carrier-sense multiple access with collision avoidance, or CSMA/CA) to ensure that only one device at a time transmits data on a radio channel. The protocol governs all devices within range of each other that use the same radio channel, irrespective of whether the devices belong to the same network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
multiple access
</td>
<td class="highlight_" rowspan="" colspan="">
Allowing many users to use the same medium.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
round-trip time (RTT)
</td>
<td class="highlight_" rowspan="" colspan="">
The time it takes a packet of data to reach a destination and be returned.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
timeserver
</td>
<td class="highlight_" rowspan="" colspan="">
An online clock that other devices consult to find the current date and time.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
time to live (TTL)
</td>
<td class="highlight_" rowspan="" colspan="">
The maximum number of hops an IP packet can make before it is discarded.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
traceroute
</td>
<td class="highlight_" rowspan="" colspan="">
A diagnostic tool for locating blockages on the route of an IP packet.
</td>
</tr>
</tbody>
</table>

---

