# Session 2: IP addressing



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/02_abstract_spheres.tif)

So far you have seen the components of a home network, and seen how all devices on the network have IP addresses. In this session you are going to delve further into the home gateway and into the nature of IP addresses. You will see that all IP addresses have two parts. One part identifies the network and the other part identifies the device itself. As a result of this division, there are rules covering network addresses.

By the end of this session, you will be able to:

* understand that an IP address has a network part (common to all devices on the network) and a unique part for device (or host)understand that an IP address has a network part (common to all devices on the network) and a unique part for device (or host)

* recognise that a subnet mask of 255.255.255.0 indicates that the final number of an IP address represents the devicerecognise that a subnet mask of 255.255.255.0 indicates that the final number of an IP address represents the device

* diagnose local network problems caused by incorrect IP addresses and non-allocation of IP addresses.diagnose local network problems caused by incorrect IP addresses and non-allocation of IP addresses.


## 2.1 Internet Protocol (IP) addressing


In this first part of Session 2 you will look in more detail at IP addresses for devices that are connected to a network. You’ll see that the IP address tells us about the device itself, and the network it is connected to.

These ideas will be demonstrated using a simulation of a home network. The simulation has different devices connected to the network. Data can be sent between devices in the network using a command called `ping`.

Later you will be able to try the ideas out for yourself.

To begin with, watch the video below which is about 7 minutes long. Feel free to make some notes as you watch it, if you like.


### Introduction to IP addressing

         ##-- MEDIACONTENT
        
S2 Video 1 Introduction to IP addressing

In Session 1 you looked around a home network. You saw that it had a gateway device (sometimes called a router), and you saw that devices could be connected to the gateway via a wire or via Wi-Fi. You also saw how, at the command prompt of a computer, typing `ipconfig` revealed some of the network data of that computer. And you saw that typing `ping`and an IP number at the command prompt was a way to test whether there was an IP connection between two devices.

In this session I’m going to look further at the addressing system used in this kind of network. It’s called IP addressing, and the IP here stands for Internet Protocol. It’s the addressing system that’s used throughout the internet. You’ve already seen that a key part of this addressing system is the IP number, or the IP address as it’s often called.

I’m going to look at IP addresses by showing you some of the settings from a domestic gateway or router. The domestic gateway I’m going to use is part of this simulated network. This is the gateway here.

This simulates an actual product made by Linksys. The network also has a personal computer up here, which has a wired connection to the gateway, and it also has a tablet here with a Wi-Fi connection to the gateway. There’s also an internet connection here, just as with most other gateways. I’m using this simulation here because it makes it easier for me to show some of the things I want to talk about.

Domestic gateways like this usually have many settings that the user can change if they need to. Here’s a settings page of this gateway. There are quite a lot of settings there. I’ll just concentrate on these here. I’m going to pick out just a few because the rest are rather complicated.

To begin with, this number here 192.168.0.1 is the IP address of this gateway, or to be more exact it’s the IP address of the side of the gateway that’s connected to the local network. That’s because the gateway also has a connection to the internet. There’s a side that faces the internet, and that has a different IP address, and that’s up here: 99.0.0.2.

For the time being I want to concentrate on this network IP address here, 192.168.0.1. You might be wondering why the address consists of four numbers separated by decimal points. Why these particular numbers? Would other numbers work just as well? Other sessions will look at these questions in detail, but for the moment just accept that this is what an IP address looks like, or rather, it’s what the widely used version 4 of the internet protocol addressing system uses. There’s a version 6 of IP addressing that hasn’t been widely adopted for home networks and addresses look very different in IP version 6.

You’ll have spotted this number, this subnet mask, 255.255.255.0, which looks like an IP address, but actually it isn’t. I’ll explain what it’s for in a moment.

Now all the other devices on this network must have IP addresses, or they won’t be able to handle IP traffic. A network that can’t handle IP traffic, though, might be able to handlecarry other forms of traffic, such as Ethernet data. But to be able to cope with IP traffic, devices on a network must have IP addresses; and they must not only have IP addresses, they’ve got to have the right sort of IP address.

So what do I mean by ‘the right sort of IP address’? One thing I mean is that the address has to be right for the particular network. An IP address that works properly on one network probably won’t work on another. That’s because the IP address doesn’t just identify a device: it also identifies the network itself. 

On this network, and on most home networks, the fourth number of the IP address identifies the device. The three numbers before it identify the network. This zero in the subnet mask shows which part of the IP address labels the device. These 255s in the subnet mask show the network parts of the IP address. For example, this subnet mask on a network shows that the last two numbers of an IP address on the network are for the device, and the first two numbers are for the network itself. But this would be very unusual on a home network.

Returning to our home network, the gateway here has a 1 as the last of the four numbers in its IP address. Because the subnet mask is 255.255.255.0, that 1 in the gateway’s IP address identifies the device, the gateway.

Only one device on the network can have the number 1 here in the fourth place. And only one device could have the number 2, or the number 3 and so on. It’s similar to the way on a street only one house can be number 1, and only one can be number 2, and so on. You need unique numbers to be able to get things delivered to the right place. A gateway doesn’t have to have the number 1, but it often does.

So here’s a rule of IP addressing: The part of the IP address that identifies the device must be unique on the network. You can’t have more thant one device with that number.

On this network, the first three numbers of an address identify the network. So in the case of the gateway, the numbers 192.168.0 identify the network. Every device on this network must have these same numbers as the first three numbers of its IP address. These three numbers are a bit like the town and street of a postal address, in the sense that every house on a street must have the same street name and town in its address.

So here’s another rule for IP addressing. The network part of the address must be the same for all devices on the network.

And just to close this part, another rule. The subnet mask has to be the same for every device on the network.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/10_intro_to_ip_addressing.jpg)

         ##-- ENDMEDIACONTENT
    


Try the following quick quiz to see how much you have picked up from the video.


### Activity 1 Test yourself


#### Question

*5 minutes*

On the network in the video, which of these IP addresses will work?

(a) 192.168.0.14

(b) 191.168.0.150

(c) 192.150.0.200

(d) 192.168.1.1

(a) is the only one that will work on this network. (b) fails because in the first position it has 191 instead of 192. (c) fails because in the second position it has 150 instead of 168. (d) fails because in the third position it has 1 rather than 0.




## 2.2 Checking the local network


In this part you will use ideas from Section 2.1 to locate and fix problems in a small local network. In the following video, you will see the network in PT Anywhere and the preliminary stages of locating the problem. In the activity following the video, you are asked to complete the investigation and to fix the problem, or problems.

You might need to remind yourself about how to use PT Anywhere by looking again at the <a xmlns:str="http://exslt.org/strings" href="">Introduction to PT Anywhere video in Session 1</a>.

Now watch the video below, which is about 5 minutes long.


### Checking the local network

         ##-- MEDIACONTENT
        
You’ve seen that an IP address has four numbers separated by decimal points. On the home networks we’ve looked at, all devices on the network must have the same three numbers at the start of the address. Although our examples had the numbers 192.168.0, other networks might have different numbers.

These three numbers must be the same for all devices on the network. The last number, which I’ve shown as X here, must be different for each device on the network. On our gateway, X was 1; but it doesn’t have to be 1. The important point is that this number must be different for each device on the network.

We saw that the subnet mask shows which numbers of an IP address are for the network, and which for the device. The 255s show the parts of the address that are the network part, and the 0 shows the device part.

If there’s a problem with a network, a good starting point for fixing it is to check that all the devices have IP addresses that satisfy these rules. So we’ll try that with this network.

Let’s suppose someone has reported a problem here. A computer in this network can’t send or receive data, but we don’t know which computer; and we don’t even know what network addresses are being used on this network. A straightforward way to solve the problem would simply be to look at the settings for each device. But I don’t want to do that. I want to track down the problem computer just using ping commands. I’ll start my pinging with the router. Of course, the router itself might be incorrectly configured, but if it were incorrectly configured, more than one computer would be having problems.

To get to the router’s command prompt I just select the router and click on ‘Open console’. Alternatively I can just double-click the router.

Now, what IP number should I ping? I don’t know what addresses are being used on this network. We could try our old friend 192.168.0.255 and see what happens. I’ll do that. Nothing there. If I’m going to work my way through all possible network addresses, this could take a long time.

Instead I’m going to ping this IP number:255.255.255.255. This broadcasts the ping to everything on the network, whatever its IP address; but I’ll only get replies from devices that are correctly configured. So here are the replies to my ping. It’s pretty clear that this network uses addresses that begin with 192.168.100. Three devices have responded, and they’ve got the numbers 10, 20 and 30 in the fourth place. There are five devices on this network: the router and the four computers. (The switch doesn’t count, because it doesn’t operate at the IP level.) So two addresses are missing. The router hasn’t responded, because that’s the device the ping was sent from, and the sending device doesn’t respond to pings. The other device not represented here is the rogue computer.

So now I’ll go to the command prompt of Mary’s computer and ping 192.168.100.255. A new address has appeared: 192.168.100.254. That must be the router. And the address 192.168.100.10 has disappeared. That must be the address of Mary’s computer, because, as I said just now, a ping isn’t responded to by the computer that sent it.

So we can start to draw up a list of IP addresses and devices on this network. So now on to Advait’s computer. Here I’ll ping 192.168.100.255 again. Mary’s computer, 192.168.100.10, has reappeared, but the address 192.168.100.20 has disappeared. That must be Advait’s computer.

So your task in the activity below is to fix the network. But you’ll see I’ve added a slight complication.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/11_checking_the_local_network.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 2 Try it out


#### Question

*15 minutes*

Your task in this activity is to make the [PT Anywhere network used in the video](https://forge.kmi.open.ac.uk/onl2-pt2.2) work properly. You will see that the network has an additional computer, Winston’s computer, which does not appear in the video, but otherwise the network is identical to the one in the video.

A sensible way to proceed is in four stages:

1. 
Find the IP addresses of all working devices.


2. 
Identify the non-working device(s). (This should emerge from stage 1.)


3. 
Give non-working devices suitable settings.


4. 
Check that the network works properly. This is not simply a matter of checking that any devices you have fixed are working properly: it’s also necessary to check that the rest of the network has not been messed up.


My answer can be viewed in the video below, which is about 4 minutes long. In places where I have assigned IP numbers to devices, other IP numbers are possible and would work just as well.

         ##-- MEDIACONTENT
        
Well, here we are with the network and we now have a new computer here, Winston’s computer. But we’re told that all the rest of the network is as it was before. So I will carry on as I was doing before.

I’ll try Harshi’s computer, and I’m going to ping 192.168.100.255. So the address 192.168.100.30 has disappeared. So that must be Harshi’s computer, and it must be correctly configured. And no new computer has appeared, so Winston’s computer is obviously also incorrectly configured.

So the finger of suspicion points both at Dorothy’s computer as not working and also at Winston’s. If Dorothy’s computer is not correctly configured, then when we ping from there nothing should happen – so we’ll try that. As expected, Dorothy’s computer isn’t communicating with the network.

If we have a look at the settings of Dorothy’s computer, ‘Interfaces’, and we see there that it has a 99 in the third place where it should be 100. But simply changing that to 100 wouldn’t fix the problem, because that would make the IP address identical to Harshi’s. So we’ll make this 40 and ‘Submit’. And we’ll see what happens now: ping 192.168.100.255. So this computer is able to communicate with the other computers and with the router, so that appears to have sorted that problem out.

So let’s have a look at Winston’s. We know that that’s not communicating with the network because it hasn’t appeared in any of the pings we’ve just done. We’ll just check that by pinging from there. No, nothing doing there. So have a look at the settings on that device. And we see it’s got no IP address at all, or subnet mask. So we can give that 192.168.100.50 and subnet mask the usual one255.255.255.0 and ‘Submit’. So what I’m going to do now is go back to the router and try to ping everything from there to check that everything is working. We’re getting replies from 10, 20, 30, 40 and 50, so the network is working as it should.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/12_answer_to_activity.jpg)

         ##-- ENDMEDIACONTENT
    





## 2.3 Networks of networks


In this part you will look at the internet-facing side of the home gateway. In particular, you’ll look at its IP address and subnet mask, which are very different from those on the home gateway side. This leads to an exploration of what is on the ‘other side’ of the gateway. For shorthand, this is usually referred to simply as ‘the internet’, but the internet is actually a vast network of networks. Networks are linked to other networks by routers. The router’s job is to transfer data packets from one network to another, according to the packet’s destination IP address. The important concepts of latency and hopping are introduced.

Now watch the video below, which is about 6 minutes long.


### Networks of networks

         ##-- MEDIACONTENT
        
Near the start of this session, I showed you that the gateway has a side that faces the internet. You can see that the IP address of the internet-facing side of the gateway is very different from the one on the side that faces the local network. The internet-facing side doesn’t have the usual three numbers, 192.168.0, at the start, but instead has an address starting with 99. This means that the internet-facing side of the gateway is on a different network from the side that faces the local network.

One of the jobs of a router is to transfer data from one network to another, and a gateway is, among other things, a router. Notice also that the subnet mask on the internet-facing side of the gateway is different from the ones we’ve already seen. This one is 255.0.0.0, which is very different from 255.255.255.0.

Now the gateway address shown here, 99.0.0.1, doesn’t refer to this gateway, the one that we’ve been looking at on the home network It refers to the gateway at the internet service provider. The internet service provider is the company that provides a domestic customer, or a business customer, with access to the internet.

The internet service provider has a router, or possibly several, serving customers and their own home networks. So, the gateway on our home network is also part of the internet service provider’s network. In our example, the internet-facing side of the home gateway has the address 99.0.0.2, and we could guess that other home networks served by this internet service provider would have addresses such as 99.0.0.3, 99.0.0.4, and so on.

But the internet service provider’s router is also part of another network, usually a network of core routers, which might serve other internet service providers, or other large-scale users. Core routers are high-speed routers carrying traffic on the internet backbone.

So you can see the internet is a network of networks. Because it’s a network of networks, there’s often more than one route from A to B. This gives the internet some of its robustness, because if part of the internet stops working properly, there’s usually an alternative route that can be used.

The internet addressing system is really a system for getting data from one network to another. It doesn’t specify a route, just a destination, and there’s no guarantee that all the data packets of a data transfer will go by the same route.

We’ve already seen that a network address consists of a part that represents the network and a part that represents the device. As a packet of data travels from network to network, only the network part of the address is used, because routers transfer data from network to network not from device to device. That’s why there always has to be a subnet mask, that travels with the data packet, so that routers along the way know which part of the destination address is the network part. Only when the packet gets to its final network does the device part of the address get consulted, and on the final network it’s actually a switch that makes the delivery, although on home gateways the switch is built in to the gateway.

This picture is complicated a bit by the fact that some IP addresses can only be used on private networks. The 192.168 class of addresses belongs to those that can only be used on private networks. We’ll see more about private networks later.

But there has to be a certain amount of trickery to get data with private addresses across the internet. And we’ll look at that later.

When you think of a packet of data travelling from network to network, you have to think of it as travelling from router to router in a series of hops, as they are called. Usually a packets has a maximum number of hops specified, so if the maximum is reached before the packet gets to its destination, the packet is discarded. This prevents the internet getting clogged up with data that has never been delivered, for example if the destination network no longer exists. But it also means that delivery of a packet is not guaranteed.

Each router in the internet has to do a certain amount of processing work to transfer a packet from one network to another. The router has to look at the destination address, and it has and decide which router, of the ones it’s connected to, to forward the packet to. Sometimes a queue of data packets can build up at a router. So routers can introduce delay, and therefore contribute to the latency of the data transfer. Roughly speaking, the latency is a measure of the delay between sending some data and its arrival at the destination. On the internet, data can travel quite slowly compared with, say, radio, where transmissions travel at the speed of light.

The multitude of networks that make up the internet use many underlying communication technologies. Some use optical fibres, others use copper wires or coaxial cables. Sand some use wireless. In many cases the networks that make up the internet already existed before the internet came into widespread use. For example, in many countries there was already an extensive network of optical fibres carrying data traffic and telephone calls between major cities, before the internet arrived. So the introduction of the internet was not so much the introduction of a new set of networks, but the introduction of a new addressing system that could be used across existing networks.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/13_network_of_networks.jpg)

         ##-- ENDMEDIACONTENT
    


Now try to answer the questions below.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 3 Test yourself</h1>
*10 minutes*

         ##-- ITQ
        

#### Question

1. What aspect of data transmission using the Internet Protocol is likely to cause problems for ‘real-time’ exchange such as a web conference or video call?

The latency of the exchange can cause awkward gaps when neither side knows whether the other side is speaking. Also, the lack of guaranteed delivery could be a problem (although the loss of the odd packet is not disastrous for a conversation).

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. The packets of a data transmission do not necessarily arrive at the destination in the right order. Why?

Packets can arrive out of sequence because they do not necessarily all take the same route. Some routes might involve more hops than others. More hops mean more routers visited, and routers introduce delay. An early packet could take a longer route than a later packet, and therefore arrive after it.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. If packets arrive out of sequence, they are assembled into the correct sequence by a protocol known as Transmission Control Protocol (TCP) at the destination computer. Why would it not be a good idea to use TCP for a ‘real-time’ exchange?

Using TCP would increase the delay (or latency). It would take time to assemble packets in the right order, and TCP might wait too long a time for a packet that never arrives.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

4. The video shows an IP address of 99.0.0.1 being used for the gateway of the internet service provider (ISP). A subnet mask of 255.0.0.0 is used with this address. Comment on the number of devices this network could support, and whether there would be a problem using the kind of fault-finding approach used in Section 2.2.

Potentially there could be very many devices. With a 255.255.255.0 subnet mask, only the last number of the IP address is available for devices. With 255.0.0.0, the last three numbers of the IP address are available for devices. This would make fault-finding very difficult if every device had to be individually investigated.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 2.4 Public and private addresses


There are two major types of IP address: private addresses and public addresses. This part looks at the differences between these two types of address, and the different ways they are used.

Now watch the video below, which is about 6 minutes long.


### Public and private IP addresses

         ##-- MEDIACONTENT
        
IP addresses are either public or private, and in this part I want to look at the distinction between them.

Nearly all small local networks for homes and small businesses use private addresses. Here are some screenshots from the settings pages of some domestic gateways. These are all the default settings: I haven’t changed anything. What’s striking is how the same network addresses keep cropping up. These are very common numbers in home addresses. It’s very likely that your home network uses these numbers, and that your neighbour’s does too.

And yet data from your network doesn’t get mixed up with your neighbour’s, even though theoretically there’s a route from your network to theirs via the internet.

That’s because virtually all home network addresses belong to a class of IP addresses called ‘private addresses’. These addresses can only be used on private networks, which are self-contained networks found in homes, offices, businesses, schools, colleges, and so on. Private network addresses can’t be used on the public internet. And by ‘public internet’ I mean what’s usually just referred to as ‘the internet’. Trying to use a private address on the public internet would be like dropping into the post a letter addressed to ‘Jane Smith, Office 207, Administration Building’. But in the right context, such as a business or a campus, this address could well work.

It’s common for private networks to have a gateway to the public internet. The gateway allows data traffic from the private network to travel over the public internet to its destination. And it’s quite likely that its destination is itself on another private network. Within the gateway, a process called network address translation is used to replace a private address with a public one for traffic passing through the gateway on to the public internet.

These are the official private IP address ranges. It’s not worth remembering these, but it’s useful to know that addresses beginning 192.168 are always private addresses.

So, to summarise, private addresses are only unique on the network they are used on. Exactly the same addresses can be used on another private network, and often are.

It’s a different story on the public internet, or the global internet, where IP addresses must be unique. Addresses on the public internet, incidentally, consist of four numbers separated by dots, just as on private networks.

Looking again at the IP address ranges, you can see the number 255 cropping up a lot as the highest number in each range. 255 is the biggest number you can have as a number in an IP address. That’s true whether it’s a private IP address or a public IP address. The smallest number you can have in an IP address is 0. So on a typical home network, the range of possible IP addresses is 192.168.1.0 to 192.168.1.255.

In any IP network, neither the lowest nor the highest address can be allocated to a device. So on a home network no device could have the address 192.168.1.0. In fact, this is referred to as the network address. So, although the network part of the address is the three numbers 192.168.1, it’s usual to say that the address of the network (as opposed to a device) is 192.168.1.0. And no device could have the address 192.168.1.255. This highest address is used for broadcasting data to all devices on the network, and you’ve seen examples of this in earlier parts of this session.

The lowest address that can be given to a device on a typical home network is 192.168.1.1. It makes sense to use this address for the gateway, but the gateway doesn’t have to have this address. The highest usable address is 192.168.1.254, and this is quite often used for the gateway address.

So all that’s consistent with this router’s settings that we saw earlier. The gateway has an address of 192.168.1.1, and allocated IP addresses are in the range from 192.168.1.2 to 192.168.1.254.

Sometimes, though, the range of allocated IP addresses is restricted, as with this one we saw earlier. Here the gateway has an address of 192.168.1.1, but other devices are allocated addresses in this range, where the last number goes from 100 to 200.

This restricted range of IP addresses is connected with this thing here, DHCP or Dynamic Host Configuration Protocol, which you’ll be looking at in a later session. This restriction on IP addresses doesn’t mean that a network address such as 192.168.1.5 won’t work on this gateway: it’s just that this address won’t be allocated by the gateway to a device


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/14_public_and_private_ip_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


Now try to answer the questions below.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 4 Test yourself</h1>
*15 minutes*

These questions are about network addresses.

         ##-- ITQ
        

#### Question

1. On a private network, two devices have these IP addresses: 192.168.3.2 and 192.168.3.1. Could these be expected to work?

Yes, both these IP addresses would work.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. A data packet with a destination address of 172.16.25.16 is launched on to the public internet. Could it be expected to reach its destination?

No. This is a private network address.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. If someone setting up their home network were advised to give the gateway an address of 192.168.4.255, would this be good advice? If it is bad advice, suggest some good advice.

No. This is a broadcast address and cannot be allocated to a device. 192.168.4.254 would be suitable.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

4. If someone setting up their home network were advised to give the gateway an address of 192.168.1.284, would this be good advice? If it is bad advice, suggest some good advice.

No. 284 exceeds the largest possible number as part of an IP address. The largest possible number is 255, but that can’t be used as it’s a broadcast address. Better advice would be to use 192.168.1.254 or 192.168.1.1.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 2.5 Fixing a host address, and two special addresses


In this part you will look at some nuts-and-bolts ideas that can be useful when setting up networks or diagnosing problems.

The ‘fixing a host address’ part of the title refers to the assigning of a fixed IP address to a networked device (or host, as it is often called). As you will see in a later session, IP addresses are generally assigned to networked devices automatically through a process called Dynamic Host Configuration Protocol (DHCP), and can change. Sometimes, though, you need a host’s IP address to be fixed. The first section of the video looks at how this can be done to a Microsoft Windows computer.

The remainder of the video looks at two classes of ‘special’ IP address. These addresses have diagnostic use, and are not used as normal IP addresses.

Now watch the video below, which is about 5 minutes long.


### Fixing a host address, and two special addresses

         ##-- MEDIACONTENT
        
In this part I want to look at some settings on my personal computer; and I’ll start by going to the Control Panel, Network and Sharing Centre, and then, up here, Change Adapter Settings, and Ethernet – so that’s the port for the wired connection.

Let’s have a look at this: Internet Protocol Version 4 and look at Properties. And this is what I want to bring to your attention: ‘Obtain an IP address automatically’. So that’s what this computer does. It gets its IP address automatically, from the gateway as it happens, and a later session will look at that in more detail.

There is this alternative possibility, here, and sometimes this is handy for diagnostic work where you actually want to give the wired interface an IP number. So I could give it this one [192. 168.2.66], and it knows what the subnet mask is without me typing it in. And I could give it a gateway address [192.168.2.254]. And if I were to hit ‘OK’ those would be implemented. But I don’t recommend hitting ‘OK’ unless you’re engaged on serious diagnostic work. So I’ll put it back to that [‘Obtain an IP address automatically’], and close that down.

Now, an interesting question that arises is ‘What happens if you boot your computer up so that it can’t get an IP address from anywhere?’ And that’s what I’m going to do now.

I’ve booted up my computer again, and this is what we get. `ipconfig`, and we get this very characteristic number here: 169.254.34.148. These numbers, beginning 169.254, are what Windows gives you when this automatic IP allocation doesn’t work. It’s called a link-local address, and it’s supposed to have some usefulness, but its main use is for telling you that the IP allocation system isn’t working.

I’m going to demonstrate the loopback address with this PT Anywhere network. There are two computers and this router, but the details of the network aren’t important.

The most important thing for my purposes is that none of the devices has been configured. So none of the devices or interfaces has an IP address or a subnet mask. We could imagine that perhaps we’re about to start configuring this network device by device.

I’m going to start with this computer here. Edit device, Interfaces. I’m giving it an IP address of 192.168.1.10 and the usual subnet mask. And then we do ‘Submit’ and then go to the command prompt. Now I’ll ping this IP address: 127.0.0.1.

Now, you’ll notice that this IP address is very different from the network address that I’ve put on the computer. And as the router hasn’t been configured, and isn’t connected to any other networks anyway, we can be fairly confident that this ping should go nowhere and time itself out. Let’s see. In fact we get successful responses.

When you ping a loopback address, the ping isn’t launched on to the network. It gets as far as being launched, and then gets looped back to the device as though it were a reply from the network. That’s why it’s called loopback.

It does give you a sort of check that the PC has been set up for sending and receiving packets, but of course, it would work even if you’d set up a computer with an IP address that wasn’t compatible with the network. So its value as a check is a bit limited.

Actually, there’s a huge range of loopback addresses. The one I used just now, 127.0.0.1, is the lowest loopback address.

This one is the highest: 127.255.255.254. And there are the responses.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/15_fixing_a_host_address.jpg)

         ##-- ENDMEDIACONTENT
    


Now try to answer the questions below.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 5 Test yourself</h1>
*15 minutes*

         ##-- ITQ
        

#### Question

1. One of the main reasons to give a computer a fixed IP address is to enable it to communicate directly with another device that has a fixed IP address (for example, a printer). Via a direct connection, you can change the device’s IP address or other settings. The direct connection would typically be a length of Ethernet cable between the two devices.

Suppose you are given a printer that has a fixed IP address of 192.168.2.25 and a subnet mask of 255.255.255.0. Your network uses addresses that begin with 192.168.1 and has the same subnet mask. How do you enable the printer to work on your own network, given that you cannot find a way of doing a factory reset on the printer?

Give the Ethernet port of your own computer a fixed IP address that is compatible with the printer’s current address, for example 192.168.2.30. Join the computer to the printer with an Ethernet cable. Use the computer to change the settings of the printer to something compatible with your own network (or to receive IP addresses automatically), and connect the printer to your network. Restore your computer’s Ethernet port to receive IP addresses automatically.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. A friend rings you to say that their computer is not receiving emails and cannot browse the web. You ask your friend to enter `ipconfig` at the computer’s command prompt to see whether it has an IP address. Your friend reports that the computer has an IP address, and says, ‘So that cannot be the problem’. Why should you ask what the IP address is?

If the automatic allocation of IP addresses has failed, then the computer might have allocated itself a link-local address, which begins with 169.254. This is not a usable address.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. As a result of 2 above, your friend says, ‘The problem must either be the computer or the network’. What test do you suggest?

Ask your friend to ping 127.0.0.1 (or any other loopback address) at the command prompt and see whether there is a reply. If there is a response, then it suggests – but doesn’t prove – that the computer is all right.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 2.6 Summary of Session 2


In this session you have learned about IP addresses. The main learning points from the session are summarised below.

An IP address consists of four dotted-denary numbers. Part of the address identifies the network, and part identifies the device on the network. The subnet mask identifies the network part of the address and the device part. The network part of the address must be the same for all devices on the network, but the device part must be unique.

Neither the lowest nor the highest IP address on a network can be allocated to a device. The highest address is used for broadcasting to all devices on a network.

Private local area networks use private IP addresses. These cannot be used on the public internet, but can be reused across multiple networks.

Link-local and loopback addresses can help with the diagnosis of problems in network connectivity.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
core router
</td>
<td class="highlight_" rowspan="" colspan="">
A high-speed router carrying traffic on the internet backbone.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
host
</td>
<td class="highlight_" rowspan="" colspan="">
An end device on a network such as a smartphone, tablet, laptop.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
internet service provider (ISP)
</td>
<td class="highlight_" rowspan="" colspan="">
A company that provides a domestic customer, or a business customer, with access to the internet.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
link-local address
</td>
<td class="highlight_" rowspan="" colspan="">
An IP address allocated to a device when automatic IP allocation fails.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
loopback address
</td>
<td class="highlight_" rowspan="" colspan="">
An IP address, such as 127.0.0.1, that simply loops back to the host device.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
private address
</td>
<td class="highlight_" rowspan="" colspan="">
An IP address that can be used only on private networks such as LANs and home networks, not on the internet. Private addresses are only unique on their own networks.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
public address
</td>
<td class="highlight_" rowspan="" colspan="">
An IP address that can be used on the public network – the internet. Public addresses must therefore be unique.
</td>
</tr>
</tbody>
</table>

---

