# Session 3: An introduction to switching



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/03_network_hub_and_cable.tif)

In the last session you looked at the IP addresses used by devices on a small home network. You have also briefly met MAC addresses – introduced in Session 1. In this and the next session you will look at how these two types of address are used and why both are necessary. You will do this by exploring two very important networking terms: __switching__ and __routing__. Both of these terms are about getting data across networks from source to destination. You will look at the similarities and differences between them to understand why both are necessary.

By the end of this session, you will be able to:

* 
understand what is meant by a port


* 
understand why data is segmented into data units for delivery over a network


* 
understand that switches are used to deliver data on a local area network and that they use MAC addresses to do this.



## 3.1 Switches, routers and ports


In this part you will look at what switches and routers look like and how other network devices are physically connected to them via ports.

Watch the video below, which is about 4 minutes long.


### Switches, routers and ports

         ##-- MEDIACONTENT
        
Previously we looked at IP addresses used by devices on a small domestic network, how each device needs an address, and that the format of these addresses is important so that they are allowed on the network.

The small domestic network that we’re looking at here is a very simple one. The chances are when you are using a network you will want to do something that requires connecting to devices on the other side of the gateway – somewhere in the cloud – a web server, for example. IP addresses are what enable us to do this, as all devices on the internet have an IP address.

There is another type of address: a MAC address. These also play an important role in delivering data, but across a local network rather than the internet.

In this session we’ll briefly look at how these two types of address are used and why both are necessary by exploring two very important networking terms: switching and routing. Both these terms are about getting data across networks from source to destination and have several points in common, so they are easy to confuse. We will then focus on switching here in more detail.

The home gateway device explored in earlier sessions – and like the one shown here – has several roles to play, including that of a switch and a router. A device like this one is designed to handle data traffic travelling to and from a number of devices that are typically found in the home.

The number of devices is likely to be higher than in the PT Anywhere domestic network we have been looking at. Many domestic networks will have dozens of connected devices, although most will be connected wirelessly. Even so, the number of devices is small when compared to an organisation that has their own network where there may be many computers connected to the network by cables or wireless connections. There may be different offices or buildings within the network to support.

For large-scale networks, routers and switches are separate devices, like these, and much bigger than domestic devices.

Routers and switches have several ports. In this context ports are sockets into which cables are plugged. The term ‘port’ is also used at other layers in the TCP/IP protocol suite, where they refer to specific applications that the data is associated with – so this can get confusing. But here we are talking about the physical sockets. Switches like these can have 24, 48 or more ports. Routers usually don’t have so many.

There are obviously a lot fewer ports on our domestic broadband device than on the larger switches and routers. These are designed to handle fewer devices and support more wireless, than wired, connections. This a typical example with four ports (in yellow) for connecting devices via cables. For example, you might want to connect a docking station for your computer, or a games console, as cable can provide faster connections.

I’ll now go back to our domestic network in Packet Tracer and take a quick look at the ports that are being used by the gateway. I’ll find out how many it has and which are connected. In Packet Tracer I can view the ports on the gateway device by clicking on it and going to the ‘Physical’ tab: this gives an impression of what the device would look like. The view here shows there are four ports in yellow for connecting devices. The blue port is for connecting to the internet. So a close representation of the home gateway device that we looked at previously that had four ports.

I can go to the ‘Options’ tab and ‘Preferences’ and then click the ‘Always Show Port Labels in Logical Workspace’ checkbox. When I do this, it starts to showing the ports that are connected at the gateway. We can see that PC0 is connected to port 2 on the router. Port 0 on the router is connected to the internet. According to our physical view that we looked at previously, this means we still have three spare ports on the gateway.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/16_switches_routers_and_ports.jpg)

         ##-- ENDMEDIACONTENT
    


Now you will have a chance to explore a simulated network for yourself.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 1 Try it out</h1>
*10 minutes*

         ##-- ITQ
        

#### Question

1. Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt/app/default.html) in a new tab or window so you can read these instructions.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Click on the connections between the various devices.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. Can you find out the type of connections (e.g. FastEthernet) between devices and the ports they are connected to?

Click *Reveal answer* if you would like a hint.

This information should show underneath the device names once you have clicked on the connection. They should all be either FastEthernet connections (typically between the switch and PCs) or GigabitEthernet connections (even faster connections between network devices).

The /1 or /2 indicates the port used for that connection.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

4. Can you find out how many FastEthernet ports the switch has?

Click *Reveal answer* if you would like a hint.

Click on the switch and `Edit device`. Select `Interfaces` and click on the drop-down arrow next to `name`. You should find there are 24 FastEthernet ports.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

5. Add another PC and connect to the switch with a FastEthernet connection. What port has this used?

Click *Reveal answer* if you would like a hint.

Drag and drop a PC to the workspace. Click on `connect devices` and follow the instructions on screen. Select FastEthernet and the first available port (/4).

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 3.2 Segmentation of data


In this part you will look how and why data is broken up into smaller chunks for delivery across a network. You will be using the TCP/IP layered model that was introduced in Session 1. This will help you understand the differences between switching and routing that you will be looking at in subsequent parts.

Watch the video below, which is about 4 minutes long.


### Segmentation of data

         ##-- MEDIACONTENT
        
Data that is sent across a network is broken down into small chunks – or data units – first. This is important as switches and routers follow rules that require them to work with data units of a certain size and format.

The layered approach to the delivery of data across a network was introduced in Session 1. An analogy with shipping containers was used to explain this, where goods were packed into containers of the same size and then systems put in place to deal with containers of this size.

The four layers used to define the protocols (that is, the rules) that are used in networking are shown here.

At the top layer, data is created by users interacting with software. As this data is sent down the stack to the next layer – the Transport layer – it is broken down into units of the same size. This is called segmentation. Once the data has been segmented into data units, information is added to each one that is needed for this layer to be able to do its job. This information includes a unique identifier or address of the data unit’s destination.

By splitting data into smaller units, data from many different devices can share the network resources rather than them being dominated by a single data transmission. It also means if a data unit is corrupted, or lost, only that unit would be affected rather than the whole data stream.

Data units are called different things at different layers, as we will see shortly.

Once data units reach the Internet layer, this is where IP addresses come in. The Internet layer is responsible for getting data units across networks – sometimes via many different networks. The information that is added here includes the IP addresses of the source and destination networks. Routers work at this level and use IP addresses to get information from network to network. We will look at this in more detail in a later session.

You may have noticed that the information that was added at the layer above has now been included within the new data unit at the Internet layer. The Internet layer doesn’t need to know what information the layer above added: it is only concerned with its own information. This process of each layer adding its own information and creating its own data unit is called encapsulation.

At the Internet layer, data units become known as packets.

Finally, just before the data unit is launched onto the transmission medium – whether that be cables or a wireless link – it is passed to the Network Access layer. The Network Access layer is responsible for delivering data within the local area network, which could be another PC on the network itself or – if data is destined for outside the local network – it means getting it as a far as the networking device that will pass it onto other networks. As with the other layers, the data unit from the previous layer is encapsulated within a new data unit. The information that is added here includes the MAC addresses of the source and destination devices. Switches work at this level and use MAC addresses to get information across the local network – we will look at this in more detail next.

At the Network Access layer, data units become known as frames.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/17_segmentation_of_data.jpg)

         ##-- ENDMEDIACONTENT
    


The TCP/IP protocol suite and the concept of layers can be difficult to understand. Try this drag-and-drop activity that highlights some of the main points to take away.

Drag the darker blue answers into the white blank areas.


### Activity 2 Test yourself

*5 minutes*


#### Question



__Which networking device would you use …__

Switch

… for delivery of data across a local network?

Router

… for delivery of data across other networks (the internet)?


#### Question



__Which TCP/IP layer is responsible …__

Network Access

… for delivery of data across a local network?

Internet

… for delivery of data across other networks (the internet)?


#### Question



__What name is used for a data unit …__

Frame

… for delivery of data across a local network?

Packet

… for delivery of data across other networks (the internet)?


#### Question



__What addressing scheme is used …__

MAC address

… for delivery of data across a local network?

IP addresses

… for delivery of data across other networks (the internet)?




## 3.3 Switching


In this part you will look at switching. Switches operate at the Network Access layer of the TCP/IP model. You will see how switches use MAC addresses to deliver data frames within a local area network.

Watch the video below, which is about 3 minutes long.


### Switching

         ##-- MEDIACONTENT
        
Let’s start this part on switching by looking at how data units get between devices more generally.

Data units are sent by devices and arrive on the cables plugged into the ports of routers or switches. Each data unit is inspected by the router or the switch to see what the destination is. Then the data unit is sent out via another port, which leads either directly to the destination, or to the next step towards the destination.

All destination devices must have an identifier or address that is unique on that network. This is true for both routing and switching although, as we have seen, they use different kinds of addresses.

Shifting our focus now to switching, this is a local area networking technology. Local area networks have their own standards that define how they work, but the one most commonly used one is Ethernet. You may have also come across the term gigabit Ethernet, which is basically a very fast version of Ethernet. You will find that the term Ethernet is commonly used when talking about local networking technologies – for example you may hear cables connecting devices referred to as Ethernet cables, or frames as Ethernet frames. This means they comply to specific rules defined by the Ethernet family of standards, but these form the basis of pretty much all wired local area networks.

Wi-Fi is the equivalent term for wireless connections and technologies.

The addressing used for devices on Ethernet or local area networks are MAC addresses or a media access control address, sometimes also called a physical or hardware address. You can often find it attached to a label on a piece of equipment, like this.

MAC addresses are unique. There ought to be only one item in the world with a given address.

You will see more about what the numbers and digits of a MAC address represent in a later session. But for the purpose of this session you should just be able to recognise a MAC address as 12 numbers and letters grouped into either six groups of two digits or sometimes three groups of four digits.

In Packet Tracer I can find the MAC address of a device simply using the `ipconfig``command. `

This is just a very simple network comprising a switch and two PCs. If I click on one of the devices and open a command prompt, and then at the prompt type `ipconfig /all` (the ‘all’ parameter gives me more detailed information than using `ipconfig` on its own), then we can see that the MAC address (here it’s listed as the physical address) is three groups of four digits.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/18_switching.jpg)

         ##-- ENDMEDIACONTENT
    


Now you can have a go with another simulated network.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 3 Try it out</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. Open [this network](https://forge.kmi.open.ac.uk/scenario-2) that has a switch and 2 PCs.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Find the MAC addresses of the PCs.

Click *Reveal answer* if you would like a hint.

Click on `PC1`, open a command prompt (by clicking on `Open console`), type `ipconfig /all`, and look for the physical address.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 5 minutes long.


### More on switching

         ##-- MEDIACONTENT
        
Although a MAC address is called an address, it’s really just a unique label. Calling it an address is a little misleading, because the addresses we use in ordinary life do more than simply identify something uniquely.

For example, here’s a postal address. It indicates a building, and its location. It locates the house in relation to a hierarchy of locations. A hierarchical structure like this makes it easier to reach the destination. Postcodes use a similar structure where part of the postcode identifies the nearest town or city and the rest the local area or street.

You saw earlier that IP addresses identify both the host (or end device) and the network it is on. This means they *are* hierarchical – like postcodes or postal addresses.

MAC addresses don’t do this. They simply give a device a unique label. This means a separate piece of information needs to be linked to it in order to know where that device is located. For example, a person’s name tells you nothing about their location. An address book does this by associating the name with a location.

In a network, the relevant location information for a device with a MAC address is the switch port that the device is connected to. Together these two pieces of information – the MAC address and the port number – mean that switches can deliver data units (or frames as they are known here) to the correct destination.

Next we’ll take a look at how a switch learns to associate the MAC addresses of different devices on the network with the ports that they are connected to. Remember, this is one of the functions of our home gateway as well as the more complicated larger switches that are used in bigger networks.

This is a very simple network comprising four PCs connected to a switch. PC A1 (which is on the left) is connected to port 4 on the switch. And PC A2 (at the top) is connected to port 1. And so on.

When a switch is first connected to a network, it doesn’t know the MAC address of any device. But it starts to learn the addresses and port numbers as soon as it is powered up and starts receiving frames. It gradually builds a table that associates MAC addresses with port numbers. It then consults the table to forward incoming frames to their correct destinations. So a forwarding table or a MAC address table is like a directory of connected devices and their locations.

One way that a switch starts to construct a table is by looking at arriving frames. This is the layout of an Ethernet frame. The different parts of the frame – or fields as they are sometimes referred to – carry different types of information. The numbers above the names of the fields shown here indicate the size of the field. The data that is actually being transmitted is in the next-to-last field, which is why it is so much bigger than the others. This is also sometimes referred to as the payload.

You don’t need to be concerned with all these fields and what they mean. The ones we are concerned with are the third and fourth fields – these are the destination address and source address. Each of these addresses is a MAC address. The switch reads the source address in an arriving frame and associates it with the port the frame arrived on. These two pieces of information become an entry in the forwarding table.

In the early stages of table construction, a switch is likely to receive frames with a destination address that isn’t in the forwarding table yet. In this case, the switch sends the frame out via all ports except the one it arrived on. So in this example, a frame is sent by PC A1 which arrives at the switch. The switch looks at the frame but doesn’t yet know which port the destination MAC address is associated with – so it sends it to all the other PCs it is connected to. This is called broadcasting. Broadcasting is a key principle of switching, as it ensures that destination addresses are reached even if they are not listed in a switch’s forwarding table.

All the devices shown here are said to be in the same broadcast domain. All computers that are connected to the same switch are members of the same broadcast domain – this means they will receive any frames broadcast by the switch.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/19_more_on_switching.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Think about


#### Question

*5 minutes*

In the example you have just watched, the switch only has four ports but switches can have 48 ports or more. Can you think why it might not be a good idea to have too many devices connected by just switches?

All devices connected by a switch will be in the same broadcast domain which means every time a host or server sends a broadcast, all devices will receive and have to process that broadcast. If broadcast domains are too large, network response times can become slow. You’ll see later that using routers as well as switches enables broadcast domains to be broken up, as they do not forward broadcasts by default.



Watch the video below, which is about 4 minutes long.


### MAC address tables

         ##-- MEDIACONTENT
        
Let’s look at something similar in Packet Tracer. So this is very like the previous example – a network with a switch and four PCs connected to it.

I’m going to do my own investigation to figure out what the MAC addresses of each of these PCs are and which ports they are connected to. I’ll then compare this to how the switch discovers the same information for itself.

I’ll start by finding the MAC address of one of the PCs. So if we open a command prompt and type in `ipconfig /all`, this will give us the MAC address of the first PC, which we can see here. So I’m going to make a note of that address next to the PC itself.

If I repeat the same thing for all the other PCs, then these are the results I get.

So we’ve found the MAC addresses of each of the PCs that are connected to our switch. If I then enable the ports to be shown, I’ll be able to find out which of the ports each of these PCs are connected to.

So we have port 1 over here. And port 2. And so on.

So far, I’ve been showing you how to find out this information manually. But now we’ll see how the switch does this for itself.

So I’m going to use the command-line interface on the switch. This is how we can interact with the switch in the same way the command prompt lets us interact with the PCs.

So if I click on the switch, and go to ‘CLI’ (command-line interface), I’m going to start by typing `enable`. This command enables a higher-level privilege access to the switch, which is what we are going to need to be able to carry out the next task.

If I then type `show mac-address-table` it brings up the MAC address table, which you can see at the moment is empty.

So we need to go back to the network and send some packets so that the switch can build up a picture of which PCs are connected to which ports and start to populate the table.

I’ll send some packets from one of the PCs to all the others, and I’m going to do this using the `ping`command and the broadcast address of the network. So if I go to one of the PCs and open a command prompt and then type `ping 192.168.0.255` – the broadcast address of the network – we can watch the results of sending these packets.

So it looks like the switch is forwarding these messages on and they are being delivered successfully.

So having done that, I’m now going to go back to the switch and type `show mac-address-table`again. And this time, we can see that after doing this, the MAC address table has now been populated with the MAC addresses of the PCs and the ports of the switch they are connected to.

We can compare these results with the MAC addresses we found out previously and see that they are the same.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/20_mac_address_tables.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 5 Try it out</h1>
*15 minutes*

         ##-- ITQ
        

#### Question

1. Open this [PT Anywhere network](https://forge.kmi.open.ac.uk/scenario-1), which has a switch and four PCs.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Add another PC and make a note of the port number it is connected to.

Click *Reveal answer* if you would like a hint.

Drag and drop a PC onto the workspace or click on `Add device` and follow the instructions, selecting `PC` under ‘Device type’. Click on `Connect devices` and follow the instructions to connect the new PC to the switch, selecting the next available FastEthernet port on the switch. Make a note of the port number you select.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. Configure the new PC with a suitable IP address and subnet mask.

Click *Reveal answer* if you would like a hint.

To configure with a suitable IP address and subnet mask (which you will need to identify from the IP address of the network and those already in use), click on the new PC, then `Edit device` and then the `Interfaces` tab. Input the IP address and subnet mask and click `Submit`.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

4. Find the MAC address of the new PC.

Click *Reveal answer* if you would like a hint.

Open a command prompt, type `ipconfig /all` and find the physical address. Make a note of the MAC address of the PC.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

5. Log on to the switch and identify the new PC in the MAC address table. 

Click *Reveal answer* if you would like a hint.

Send a broadcast ping from one of the PCs (you will need to identify the broadcast address from the IP address of the network). Select the switch, open a command prompt and type `enable`. Then type `show mac-address-table`. Find the new PC using the MAC address and port you identified earlier.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 3.4 Summary of Session 3


In this session you’ve looked at how switches use MAC addresses to deliver data across a local area network.

You’ve also looked at the hierarchical layers used in communication networks and how different processes – in this case switching and routing – happen at different layers. You have also met the terms ‘segmentation’ and ‘encapsulation’, which describe how data is split up into data units, and control information added, so that the data units can be sent across a network and delivered to their destination device.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
broadcast
</td>
<td class="highlight_" rowspan="" colspan="">
To send a message to all devices on a network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
broadcast domain
</td>
<td class="highlight_" rowspan="" colspan="">
The set of devices on a network that will be sent the same broadcast messages.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
data unit
</td>
<td class="highlight_" rowspan="" colspan="">
A small chunk of data, of a certain size and format.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
encapsulation
</td>
<td class="highlight_" rowspan="" colspan="">
The process of each layer adding its own information and creating its own data unit.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
forwarding table
</td>
<td class="highlight_" rowspan="" colspan="">
Table used by a switch to associate MAC addresses of devices with port numbers to enable frames to be forwarded to their destination.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
frame
</td>
<td class="highlight_" rowspan="" colspan="">
A data unit at the Network Access layer.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Internet layer
</td>
<td class="highlight_" rowspan="" colspan="">
Layer of the TCP/IP protocol suite with responsibility for getting data across networks.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Network Access layer
</td>
<td class="highlight_" rowspan="" colspan="">
Bottom layer of the TCP/IP protocol suite with responsibility for delivering data within the local area network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
packet
</td>
<td class="highlight_" rowspan="" colspan="">
A data unit at the Network Access layer.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
payload
</td>
<td class="highlight_" rowspan="" colspan="">
The part of a data unit that is the actual user data.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
port
</td>
<td class="highlight_" rowspan="" colspan="">
In this context, the physical sockets into which network cables are plugged.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
router
</td>
<td class="highlight_" rowspan="" colspan="">
A network device responsible for getting data across networks.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
segmentation
</td>
<td class="highlight_" rowspan="" colspan="">
The process of breaking data down into smaller units of the same size.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
switch
</td>
<td class="highlight_" rowspan="" colspan="">
A network device responsible for delivering data within the local area network.
</td>
</tr>
</tbody>
</table>

---

