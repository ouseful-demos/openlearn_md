# Session 13: Configuring network interfaces



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/13_abstract_connections.tif)

In this session you will be revisiting several of the ideas and tasks related to routing and switching that were introduced in earlier sessions. Here, though, some are developed in more depth. You’ll have an opportunity to revise and practise your network set-up skills using PT Anywhere and you’ll meet some concepts that are probably new to you – for example the Cisco operating system and virtual LANs.

By the end of this session, you will be able to:

* understand the role of the Cisco IOSunderstand the role of the Cisco IOS

* interpret all the information displayed following ainterpret all the information displayed following a `show ip interface brief` command

* explain the terms ‘up’, ‘down’ and ‘administratively down’explain the terms ‘up’, ‘down’ and ‘administratively down’

* briefly explain what a VLAN isbriefly explain what a VLAN is

* build, configure and test a simple network using PT Anywhere.build, configure and test a simple network using PT Anywhere.


## 13.1 The command line and operating system


You were introduced to the Cisco CLI (command-line interface) in an earlier session, but you may have met some things there that you found a little baffling. In this part you’ll look at the CLI in greater detail and unravel some of its mysteries.

Watch the video below, which is a little over 3 minutes long. This video introduces you to the Cisco operating system and explains what happens when it is booted up.


### The command line and the operating system

         ##-- MEDIACONTENT
        
In this part of this session I want to say a bit more about the command-line interface. This interface is used for setting up routers and switches on large-scale commercial networks, or enterprise networks. You’ve already seen the command-line interface in an earlier session. Now I want to explore it further using Packet Tracer Anywhere, so that you can get more experience of using it for yourself. Also, I want to explore things you’re likely to see when using the command line. For example, why does the prompt sometimes change depending on the command you’re using? There’s an arrow head here showing you how it changes to a hash sign. And this GigabitEthernet0/0. What’s this about? Depending on the router or the switch you’re using, you might get ‘FastEthernet’ or ‘GigabitEthernet. And sometimes you’ll even see ‘Serial’. I want to look at theose as well. And what’s this ‘VLAN’? I think we can guess what the ‘unassigned’ means when we see the column headed ‘IP addresses’. But ‘administratively down’, or just ‘down’ in the next column, is a bit puzzling.

Before we delve into that level of detail, though, I want to say something about what’s happening when you use the command line of a router or a switch.

A router or a switch has one feature that is similar to what you find on your computer or your mobile phone. It has an operating system, just like a computer might have Windows or a phone might have Android. As with a computer or a phone, the operating does various jobs. One of the most important is providing services to programs running on your device. When you use the command-line interface of a router or a switch, you are in the operating system. 

With Cisco devices, the operating system is usually referred to as ‘IOS’ which stands for ‘Internetwork Operating System’, not to be confused with Apple iOS. In the past, when you switched on a computer or mobile phone, the operating system was loaded into the memory from storage on a hard drive. These days when you switch on a computer or phone you’re usually waking it up from standby rather than loading an operating system, but a clean boot reloads the operating systems [which] have to be taken from storage somewhere. That can take a little while and it’s usually from the memory.

In Packet Tracer Anywhere we can see what is displayed when a Cisco router or switch boots up. The operating system is loaded from storage into active memory and various checks have to be done on the hardware. Booting up ends with this question ‘Continue with configuration dialog?’ to which the sensible answer is nearly always ‘no’. Answering ‘yes’ takes you through a series of questions that are supposed to help you set up the router but in practice are not very helpful.

Along with other things, the operating system allows you to create and save a configuration file. A configuration file contains settings such as the name that has been given to the router, the IP addresses of its interfaces, security settings and so on. These details aren’t stored in the IOS itself, but in the configuration file created by the IOS.

After IOS has booted up, it will load the configuration file if there is one. If there’s no configuration file, then things like the anIP addresses of the interfaces, security settings and so on are not set, or will be at default settings.

Thank you for watching.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/70_the_command_line_and_the_operating_system.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 1 Think about</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. The following output shows part of a response to the command `show ip interface brief`. Explain what is meant by the term ‘unassigned’ in the IP address column.


```python

Router>enable
Router#show ip interface brief
Interface            IP-Address    OK?  Method  Status                  Protocol
GigabitEthernet0/0   192.168.1.2   YES  manual  up                      up
GigabitEthernet0/1   unassigned    YES  unset   administratively down   down
GigabitEthernet0/2   unassigned    YES  unset   administratively down   down
Vlan1                unassigned    YES  unset   administratively down   down
Router#
```


From the output, you should have noticed that for the interface GigabitEthernet0/0 there was an IP address in the ‘IP-Address’ column. From this you should have been able to deduce that ‘unassigned’ simply means that an IP address hasn’t yet been configured on those interfaces that ‘unassigned’ appears alongside.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Which of the following are Cisco IOS functions?

Checking the router hardware

Loading the config file

Sending a ping to all connected devices

Loading any default settings if there is no config file

Enabling a config file to be created and saved

Warning the user of any security threat.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 13.2 IOS levels and Ethernet


You already know from earlier sessions that there are multiple modes within the Cisco IOS and that each mode allows the user to execute different tasks. This section explains these modes in terms of hierarchical levels. It serves as a brief reminder of how to identify the current mode (or level) and then goes on to explore information stored about the router interfaces and how to interpret it.

Watch the video below, which is almost 6 minutes long.


### IOS levels and Ethernet

         ##-- MEDIACONTENT
        
When a router has booted up, if we go to the command-line interface we see something like this. 

Where it says ‘Router’, that’s the name of the router. If we haven’t given it a name, the default name is ‘Router’. So this one hasn’t been named.

Packet Tracer Anywhere, unlike a real router, can’t save its configuration. Every time we begin a Packet Tracer Anywhere session we start from scratch, so everything that can be configured is unconfigured or at its default settings. 

When the prompt is an arrow head, like this one, we’re at the top level of IOS. This is called the ‘user executive level’, or ‘user exec level’. Whatever level you are currently logged in as you can issue the question mark as a command to list all the available commands. This is shown here for the euser executive level.

This name is a bit misleading. An executive is supposed to be able to make things happen; but at the user exec level of IOS you can’t do very much. You can send a ping though.

Typing `enable` at the executive level prompt takes you to the next level, called the ‘privilege exec level’, or sometimes ‘privileged executive level’. Notice that the prompt has changed from an arrow head to a hash sign. The prompt keeps changing as we go down through the levels of IOS, as you will see.

If you want to go back a level from here, you can do so by typing `exit`. Commands that work at one level usually don’t work at another. But you’ve already seen in another session a command that does work at this level. It’s the show ip interface briefcommand, and it’s very useful.

On the left there is a list of interfaces on this router. More specifically, these are ‘built-in’ interfaces. They are the interfaces [in] this router when you buy it.

Most routers have slots that you can slide additional modules into. This gives you more interfaces if you need them. But what are Gigabit interfaces, and what do these numbers mean 0/0, or 0/1 etc. mean?

Ethernet, in one form or another, is a common form of wired local area internet. It’s widely used in offices for networking computers and peripherals.

Ethernet was in use before the wide-scale adoption of the Internet Protocol. In its first commercial form it had a speed of 10 megabits a second.

Since then it has gone through various generations, and the term ‘Ethernet’ is now used as a general name covering all varieties of Ethernet. The first major upgrade of Ethernet was FastEthernet, with a top speed of 100 megabits a second. After FastEthernet came Gigabit [Ethernet] with a top speed of 1 gigabit a second. Routers are likely to have FastEthernet ports or GigabitEthernet ports, or a mixture of FastEthernet and GigabitEthernet. Later versions of Ethernet are backwards-compatible with earlier, so GigabitEthenet is compatible with earlier versions of FastEthernet, and FastEthernet is compatible with Ethernet.

All versions of Ethernet have the same type of connector. Here’s an Ethernet plug, with a coin to show you the scale. 

All versions of Ethernet use MAC addresses to identify the source and destination addresses. In fact, some authors refer to MAC addresses as Ethernet addresses.

Switches are often used to direct Ethernet traffic between one local network, and every device on the local network that has its own connection to the switch. This is why switches typically have 24 or 48  interfaces, unlike routers which usually have far fewer interfaces. In the early days of Ethernet, though, switches weren’t used and other methods were used to direct traffic between devices on a local networks. After the widespread adoption of Internet Protocol, switches have had to translate between IP addresses of devices on their local networks and MAC addresses, and routers are added to the network to provide a gateway into and out of the local network.

The basic data unit of Ethernet is a frame. The Ethernet data stream is split into frames, and frames travel [separately] across the network. So when internet packets are carried across Ethernet networks, the packets are encapsulated inside Ethernet frames.

As we have seen, routers typically have Ethernet interfaces, usually for connecting to a switch, but sometimes for connecting to another router. Clearly each interface on a router needs a unique identifier, so that can be configured independently of other interfaces. Numbers are used to identify the interfaces, but the numbering system varies from one manufacturer to manufacturer, and from one model to another.

Here’s one example of a numbering system for interfaces. To understand this numbering system, remember that routers and switches have built-in interfaces and empty slots which additional network cards can be slid into if more interfaces are needed. The built-in interfaces have 0 in their number, like this. Interfaces on additional cards would have the 0 replaced by a number, depending on the slot occupied by the card. So you get 1/1 or 1/2 for a 1 card, and if there was a second card added it might get a 2/1 or a 2/2 on it.

Ethernet ports are usually configured to serve the local network, like this. Whether we use FastEthernet or GigabitEthernet is determined mainly by what’s available on the devices. Of course, Wi-Fi is also widely used for serving the local network, but with enterprise equipment, as opposed to domestic equipment, it’s unusual for wireless devices to be incorporated into a router or switch. Usually there would be a separate Wi-Fi access point, connected to a switch by Ethernet.

On the internet-facing side of the router, the network connected to is called the wide area network, or WAN. A suitable interface needs to be chosen for this connection and a ‘serial’ port is often used for this; and you will see at least one serial port among those listed when you do the `show ip interface brief`command. Increasingly, though, Ethernet is used for the WAN as well as the LAN connections.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/71_iso_levels_and_the_ethernet.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 2 Test yourself


#### Question

*5 minutes*

1. If a router interface has the identity GigabitEthernet3/2 what does this tell you? Select one or more correct answers from the list below.

This is not a Cisco router.

No. The Cisco routers you have seen used in Packet Tracer use this interface identity format, so this could be a Cisco router.

The router has a total of two interfaces.

No. There must also be interfaces with IDs of GigabitEthernet3/0 and GigabitEthernet3/1.

This is a wireless interface.

No. It’s unusual for wireless to be incorporated into a router. Usually there would be a separate Wi-Fi access point, connected to a switch by Ethernet.

The router probably has at least three network cards added.

Correct. The first number of the ID identifies the network card; the second number gives the identity of the interface on that card.

Fast Ethernet is not being used on this router.

No. GigabitEthernet is backwards compatible with FastEthernet, so this interface could be used for FastEthernet.


#### Question

2. What would be the result of the command `Router&gt;show ip interface brief`? Select one or more correct answers from the list below.

The IP addresses and subnet masks of all the router interfaces will be displayed.

No. The subnet masks are not displayed following a `show ip interface brief` command.

A summary of the status of the router’s interfaces will be displayed.

Correct. The status is shown as ‘up’ or ‘administratively down’.

A ‘% incomplete command’ message will be displayed.

No. `show ip interface brief` is a valid command in User exec mode.

A ‘% invalid input detected at ‘^’ marker’ will be displayed.

No. `show ip interface brief` is a valid command in User exec mode.

The router’s interface IDs and configured IP addresses are shown.

Correct. Not all the network IP addresses are shown.

All the network IP addresses are shown.

No. Only the IP addresses of the router interfaces are shown.




## 13.3 Interfaces, up and down


This section revisits the process of configuring a router terminal and serves as a reminder of the commands to use. It then delves more deeply into the information returned after a `show ip interface brief` command. Watch the video below (which is just over a minute and a half long) and then test your understanding by answering the questions that follow.


### Interfaces, up and down

         ##-- MEDIACONTENT
        
Although privilege exec mode lets you see all the interfaces by using the `show ip interface brief`command, it doesn’t let you change any configurations. To do that you have to go down a level to ‘global configuration’ mode by typing `configure terminal`or `conf t`. Notice the prompt changes again. And then we have to choose the interface we’re configuring. You don’t have to type the whole name: this abbreviation `g0/0`is enough. Once again the prompt changes.

You have already seen how to apply an IP address and a subnet mask to the terminal, so I won’t go over that again. You can’t actually change the configuration of an interface while it is ‘up’, or operating. So by default interfaces are initially down, both ‘administratively’ and in terms of the protocol, as shown here. ‘Administratively down’ means that the interface is switched off. Under the ‘Protocol’ heading, ‘down’ means that the interface is not able to communicate with an interface it is connected to. We switch on an interface that is administratively down by using the `no shut` command at the same prompt that we use for assigning an IP address and a subnet mask to an interface. If the interface is connected to another interface that is administratively up, the `no shut`command usually causes the status under the ‘Protocol’ heading to change to ‘up’ too. That’s because interconnected interfaces that are administratively ‘up’ can negotiate the details of the protocol between themselves, so you don’t have to configure that yourself.

Thank you for watching.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/72_interfaces_up_and_down.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 3 Test yourself


#### Question

*5 minutes*

1. After the command `Router#configure terminal`, which one of the following options shows what the prompt will change to?

`Router&gt;`

`Router(config)#`

`Terminal(config)`

`Router(config-if)#`


#### Question

2. The `Router(config)#` prompt shows that the CLI is at the level where configuration changes can be made. What is the name of this level?

User executive

Privilege executive

Interface executive

Global configuration


#### Question

3. At the `Router(config-if)#` prompt, which of the following could be entered to have a useful effect?

Name of the router

‘Save’

IP address and subnet mask

Interface ID


#### Question

4. The following output shows part of a response to the command `show ip interface brief`. From the options below, choose the best explanation of the term ‘administratively down’ in the status column.


```python

Router>enable
Router#show ip interface brief
Interface            IP-Address    OK?  Method  Status                  Protocol
GigabitEthernet0/0   192.168.1.2   YES  manual  up                      up
GigabitEthernet0/1   unassigned    YES  unset   administratively down   down
GigabitEthernet0/2   unassigned    YES  unset   administratively down   down
Vlan1                unassigned    YES  unset   administratively down   down
Router#
```


The interface is faulty

The interface is switched off

The interface is not yet configured with an IP address

The interface is not connected to any devices




## 13.4 Configuring devices


In this section all your learning in the first three sections of this session is consolidated by going through the process of building and configuring a fairly simple network. The more often you engage in these practical activities the more confident you will become and the more proficient in using the commands. Your work here starts with a practical video demonstration and then an activity where you become the network manager.

First watch the video below, which is about 6 minutes long. This video demonstrates how to build and configure the network shown in Figure 1. For convenience, the configuration settings are also shown in Table 1.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/session13-figure1_512.png)


Figure 1

<table xmlns:str="http://exslt.org/strings">
<caption>Table 1</caption>
<tbody>
<tr>
<th>Device</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.20</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
</tbody>
</table>


### Configuring devices

         ##-- MEDIACONTENT
        
In this part I’m going to set up a Packet Tracer Anywhere network, starting from a blank screen, using some of what you’ve already seen in the other sessions.

For the router, which is the most complex device to set up, I will use the command-line interface. Actually, in Packet Tracer Anywhere it is possible to apply the IP addresses and subnet masks using the graphical interface under ‘Edit device’, but it is not possible to issue a `no shutdown`command via the graphical interface. So, as we should have to use the command-line interface for the `no shutdown` command, I will configure the router’s settings this way. In any case, this is a more realistic way in which we would configure enterprise equipment.

For the PCs, there is no command-line interface, so we will use the graphical interface for those. The switches do not actually require any configuration, as you will see. The router is now booted up and in the command line mode ready for us to start configuring everything. First of all we need to type `enable`to get into the privilege exec mode. Then we can type `show ip interface brief`so we can see the state of our current interfaces. As you can see here they are all down, administratively down and the protocol is down.

Now we will have a go at configuring everything so just typing `configuration terminal` or `conf t`to get into the configuration mode. Then we type the interface we want to configure. First of all it’s g0. I’m now adding an IP address of 192.168.0.1 with a subnet mask of 255.255.255.0. Then of course the all-important thing we have to add is the `no shut` command to make sure our interface is now activated.

Now I type `interface g0/1`to do the second interface. Type in the IP address of 192.168.1.1 and subnet mask of 255.255.255.0 and again `no shut`to activate our interface. That is all our interfaces changed and you can see the changed state is now up and if we do another `show ip interface brief`we can now see what the current state of our interfaces is. And as we can see the status is now up and no longer administratively down but the protocol is still down because the device is not connected to anything. If we now add in our devices; first of all we will add in our two switches, Switch0 and Switch 1. Now we’ll add in our two PCs, PC0 and PC1. Next we need to connect these together. I’ve clicked ‘Connect devices’ and now I’m attaching the cables to each device, selecting in turn the interfaces I need to connect to. So it’s F0 on the switch. Then I take the next …. Now the switch needs to be connected to the router so we select the fast Ethernet and the gigabit ports to these devices. And now we can connect the second switch to the router, again selecting the fast Ethernet and the gigabit ports for these devices. And finally we need to connect PC1 to the switch. We’ll just do that now by selecting the fast Ethernet ports … and now we’re ready to start configuring the devices.

So for the PC I’ll just demonstrate that there’s nothing configured at the moment. You can see that it’s all zero there. I go into ‘Global Settings’ and set the default gateway to be 192.168.0.1 and now I need to configure the interfaces so that’s 192.168.0.10 for the first device, PC0, with a subnet mask of 255.255.255.0. Now we click ‘Submit’ to ensure that’s all connected properly. Now we’ll do the second device PC1. Again I’ll show `ipconfig`just to demonstrate that there’s nothing configured at the moment and you can see all the settings are at zero. Now we’ll edit the device and set default gateway to be 192.168.1.1. And now select the ‘Interfaces’ and the IP address for this device is 192.168.1.20 with a subnet mask of 255.255.255.0. Then we ‘Submit’ that.

Now all the devices are configured and we can see whether everything is now working or not. Here’s my configuration for my PC0 and as you can see that’s all now correctly configured with the default gateway. If I now ping the default gateway, this is successful. I’ll now ping PC1, this is also successful. And now looking at PC1 I’ll just show the configuration for that. As you can see that’s all correctly configured with its default gateway set. I will now ping the default gateway; that’s successful. And now I’ll ping PC0; this is also successful.

Thank you for watching.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/73_configuring_devices.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Try it out


#### Question

*10 minutes*

In this activity you will enlarge the network demonstrated in the video above by adding two more PCs and a switch connected as shown in Figure 2.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/session13-figure2_512.png)


Figure 2


1. Complete Table 2, choosing suitable values.
<table xmlns:str="http://exslt.org/strings">
<caption>Table 2</caption>
<tbody>
<tr>
<th>Device</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.20</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC2</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC3</td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
<td class="highlight_" rowspan="" colspan=""> </td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/2</td>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
</tbody>
</table>

2. Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt13.4) in a new tab or window so you can read these instructions. In this scenario, the completed network from the video above is provided.

3. Add Switch2, PC2 and PC3, and connect them to the network as shown in Figure 2.

4. Configure PC2, PC3 and the router interface G0/2 with the settings you chose in Table 2.

5. Can you ping PC0 from PC3?

6. Can you Ping PC2 from PC3?

Here are the things to check if your pings were unsuccessful:

* Did you choose suitable values for PC2, PC3 and router interface G0/2?Did you choose suitable values for PC2, PC3 and router interface G0/2?

* Did you correctly set the default gateways for PC2 and PC3?Did you correctly set the default gateways for PC2 and PC3?

* Did you remember to include theDid you remember to include the `no shut` command when configuring the router interface G0/2?

Suitable values are shown in Table 3. but others could have worked just as well.
<table xmlns:str="http://exslt.org/strings">
<caption>Table 2</caption>
<tbody>
<tr>
<th>Device</th>
<th>IP address</th>
<th>Subnet mask</th>
<th>Default gateway</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.10</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC1</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.20</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.1</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC2</td>
<td class="highlight_" rowspan="" colspan="">__192.168.2.30__</td>
<td class="highlight_" rowspan="" colspan="">__255.255.255.0__</td>
<td class="highlight_" rowspan="" colspan="">__192.168.2.1__</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">PC3</td>
<td class="highlight_" rowspan="" colspan="">__192.168.1.10__</td>
<td class="highlight_" rowspan="" colspan="">__255.255.255.0__</td>
<td class="highlight_" rowspan="" colspan="">__192.168.1.1__</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/0</td>
<td class="highlight_" rowspan="" colspan="">192.168.0.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/1</td>
<td class="highlight_" rowspan="" colspan="">192.168.1.1</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.0</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router G0/2</td>
<td class="highlight_" rowspan="" colspan="">__192.168.2.1__</td>
<td class="highlight_" rowspan="" colspan="">__255.255.255.0__</td>
<td class="highlight_" rowspan="" colspan="">–</td>
</tr>
</tbody>
</table>




## 13.5 The virtual local area network (VLAN)


While you’ve been working your way through this session you probably noticed an interface labelled ‘VLAN’ and wondered what it is and what it’s for. This section provides you with a very brief explanation of VLANs and their function. Watch the video below, which is about 2 minutes long.


### The virtual local area network (VLAN)

         ##-- MEDIACONTENT
        
You’ll have noticed the VLAN in the interfaces list. This is a bit beyond the scope of this course, but as we will see [it] while we’re working with Packet Tracer Anywhere I should say something about it.

VLAN stands for ‘virtual local area network’. To understand what a VLAN is, imagine that an organisation has several local area networks, or LANs. Each LAN serves a different set of offices. You can see here that PC0 and PC1 belong to a LAN for the Finance Department. Suppose we want PC3 to be part of the Finance Department LAN, but it’s a long way from the Finance Department, maybe in another building.

We can’t easily run a cable from PC3 to Switch0, which is the obvious way to make it part of the Finance Department’s LAN. But PC3 is near to Switch1. Using a virtual local area network, or VLAN, it’s possible for PC3 to be connected to Switch1 and yet be part of the Finance Department’s LAN. PC2, though, can remain part of a different local network from the Finance Department’s. Similarly, with VLANs, Switch0 doesn’t have to be used solely by the Finance Department. It can be used by other LANs too. VLANs allow you to create LANs that are not defined by the networking infrastructure of switches and their attached networks. Sometimes this is expressed by saying that ‘the VLANs are based on logical connections rather than physical connections’. This makes it sound as though not using VLANs is illogical. What people mean when they use the word ‘logical’ like this is that VLANs allow you to create LANs based on their purpose, rather than on their physical location or connections. A VLAN needs an IP network address, which is why it appears in the `show ip interface brief`` command.`


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/74_the_virtual_local_area_network.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 5 Test yourself


#### Question

*5 minutes*

Write two or three sentences to briefly explain a VLAN.

Here’s a possible answer.

VLAN is short for virtual local area network. It provides network managers with a way of organising network devices into isolated groups that are independent of their geographical position. This can be done without having to run new cables or make major infrastructure changes.




## 13.6 Summary of Session 13


This session has largely been revision for setting up a simple network and you’ve revisited commands and procedures you’ve covered earlier in the course. It’s given you an opportunity to consolidate your learning and practise your network set-up skills. It’s also explained some terms and concepts that may have been puzzling you.

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
<tr>
<td class="highlight_" rowspan="" colspan="">`show ip interface brief`</td>
<td class="highlight_" rowspan="" colspan="">Displays the current state of the network interfaces</td>
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
configuration file
</td>
<td class="highlight_" rowspan="" colspan="">
A file created by the Cisco IOS to store device settings.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Fast Ethernet
</td>
<td class="highlight_" rowspan="" colspan="">
A type of Ethernet with a top speed of 100 megabits per second.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Gigabit Ethernet
</td>
<td class="highlight_" rowspan="" colspan="">
A type of Ethernet with a top speed of 1 gigabit per second.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Internetwork Operating System (IOS)
</td>
<td class="highlight_" rowspan="" colspan="">
The operating system used on Cisco devices.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
virtual local area network (VLAN)
</td>
<td class="highlight_" rowspan="" colspan="">
LANs that are based on logical connections rather than physical connections.
</td>
</tr>
</tbody>
</table>

---

