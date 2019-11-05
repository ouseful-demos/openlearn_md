# Session 10: The command-line interface



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/10_server_configuration.tif)

In previous sessions you have looked at connecting commercial routers and switches together to make a network. This session describes and demonstrates how you can connect to a commercial device in order to view its status and configure it. This session will also introduce the command-line interface (CLI). Through the CLI, a network engineer can monitor, maintain, and configure a commercial networking device.

By the end of this session, you will be able to:

* understand how a network engineer would connect to a commercial networking device using a console portunderstand how a network engineer would connect to a commercial networking device using a console port

* understand how a network engineer would connect to a commercial networking device using a remote connection via Telnet or SSHunderstand how a network engineer would connect to a commercial networking device using a remote connection via Telnet or SSH

* identify the different modes within the Cisco CLIidentify the different modes within the Cisco CLI

* configure a hostname and IP address on a Cisco router via the CLI.configure a hostname and IP address on a Cisco router via the CLI.


## 10.1 Connecting to a Cisco device


It is important to understand how to connect to a Cisco device, both in a real-world situation and within the simulation tools available in this course. In the real world, Cisco devices do not have web interfaces or easy configuration screens. The configuration changes are made via a command-line interface (CLI) that is accessed via a terminal emulation client. Watch the video below (which is about 4 minutes long) to see how to connect to Cisco devices using a console connection or remote access methods.


### Connecting to a CLI

         ##-- MEDIACONTENT
        
In this part we will look at how to access the Cisco command-line interface. In Session 1 we looked at connecting to a home gateway; this was done with a GUI interface via a web page. By default, a Cisco device will not have a web page for configuration. With Cisco commercial networking equipment, the configuration is done via a CLI instead. The majority of manufacturers use the same principles in their own CLIs with slight variations on commands.

This is what the Cisco CLI looks like. It is part of the Cisco Internetwork Operating System or IOS for short. To connect to a device through the CLI you will need to use one of the following methods depending on the current status of the device. During the initial configuration of a device, or if the device is not accessible over the network, you will need to use a console connection. Whilst connected to the device a remote connection method should be set up, more likely Telnet or SSH. The serial connection, therefore, will no longer be needed as the router will now be accessed via its IP address. A username and password, however, will be required to gain access to the configuration options. The configuration of these protocols is shown in Session 15.

To connect to a device via the console port – normally indicated on Cisco devices with a pale blue colour – you will need a console cable also known as a Cisco rollover cable. This is a special cable with a different pin-out to Ethernet cables. On most routers this will need a serial console connection to a PC. If your computer doesn’t have a serial connector, you will need a USB converter as well. In my setup shown in the diagram, I have a USB-to-serial converter – that’s the grey cable – this is then connected to a Cisco rollover cable, the pale blue cable. These cables connect the PC’s USB port to the console port of the Cisco router. On newer routers the console connection can be a direct USB connection as well; you can see this in the picture here.

In a commercial environment where you are using physical equipment, this is where you would use a terminal emulation program such as Tera Term, PuTTY or SecureCRT. This software is normally free, with the exception of SecureCRT – more on these later. But in Packet Tracer you can just click the device and select the CLI tab. This is the equivalent of using a console connection in the simulation program.

If the device has been configured previously and you have network connectivity to the device, you would be able to use a remote connection method such as Telnet or SSH. The router could be in another country but as long as you and the device have an internet connection you can make configuration changes still.

The same terminal emulation programs used for console connections can be used to connect to a device via Telnet or SSH. If you have a choice between these two protocols you should always use SSH, this is because it uses encryption. Telnet is considered insecure because the packets can be captured, and everything can be read, including passwords. This will be demonstrated in Session 15.

I will SSH to my router using PuTTYY. To do this I select SSH on the radio buttons and then type the IP address of the device. When I click Open, we will be prompted for a username and password.

With any Cisco device, once you have a session open – either by console, Telnet or SSH – you will be presented with a prompt similar to this one. You will see the hostname, in this case Jason_Router. This is normally an identifiable name for the device, followed by the mode indicator. More on these modes in the next part of Session 10.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/59_connecting_to_a_cli.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Test yourself


#### Question

*5 minutes*

1. How do you connect to the CLI in Packet Tracer?

(a) Double-click the device.

(b) Single-click the device.

(c) Right-click the device.

(d) Click the device and select the CLI tab.


#### Question

2. Select the correct answer statements from the following list. Which programs can be used to connect to the CLI of a Cisco router?

(a) PuTTY

(b) Google Chrome

Incorrect. Google Chrome is a web browser.

(c) SecureCRT

(d) VLC Media Player

Incorrect. This is a media player.

(e) Atom

Incorrect. Atom is a text editor.

(f) Remote Desktop

Incorrect. This is an application for allowing remote access to computers.

(g) Tera Term


#### Question

3. From the options below, select two protocols that enable a network device to be remotely accessed and managed.

(a) CRT

(b) PuTTY

(c) SSH

(d) Telnet



You now know what the Cisco CLI looks like and have seen how to connect to it, either directly via a console cable or remotely using network protocols, particularly SSH.


## 10.2 Modes within the Cisco CLI


Now you know how to connect to the routers, it is important to understand how to navigate around the command-line interface of a Cisco router.

You will now have the opportunity to use the command-line interface. Be aware that there are multiple modes within the Cisco internetwork operating system (IOS). Each mode allows the user to achieve different tasks; for example, each mode can be password-protected so specific people can only use specific modes. Watch the video below (which is about 2 minutes long) to see how to identify different modes and how to navigate between them.


### CLI modes

         ##-- MEDIACONTENT
        
There are three main modes within the Cisco CLI: user exec, represented by a greater-than symbol, privileged exec, represented bywith a hash symbol, and global configuration, which is represented with the word config in brackets followed by a hash symbol. These three modes allow you to use different commands. User exec is a restricted view where only a few basic commands work, for example ping, traceroute and some basic show commands. Privileged exec mode is less restricted. This allows you to execute all of the show commands and save the configuration. Global configuration is the mode to make configuration changes. From here you can configure the hostname or enter a sub-mode to configure an IP addresses on an interface.

OK, now we are connected to a Cisco 2911 router being simulated in Packet Tracer. When you turn the router on for the first time it will ask you if you want to go through the configuration wizard. If you answer yes, the device will ask a series of questions and make a configuration depending on the answers. We don’t want this, so we always answer no. Now we can see the default hostname ‘router’ and that we are in user exec mode indicated by the greater-than symbol to the right of the hostname. How do I know what commands I can use in this mode? We can use the question mark to list all the commands available. We want to move to privileged exec, so the command we are interested in is `enable`. If we type `enable` and hit Return, the prompt will change to a hash symbol indicating that we are now in privileged exec mode. If we use the question mark now, we can see that there are a lot more commands available. If I want to see how theis router is configured, I can do this by typing `show` and then use the question mark again, it will list all the show commands we can use. To see the configuration of the router we can use the `show running-config`command. We can see the complete configuration of the router from here. If I press Return multiple times, we will scroll one line at a time or if I press Space, we will scroll a page at a time. The prompt will keep scrolling to the end of the configuration and then return us to the previous prompt, so we can continue the configuration. Use the PT Anywhere activity below to open a CLI and practise moving between modes. In the next part we will look at changing the hostname of the device.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/60_cli_modes.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 2 Try it out


#### Question

*10 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt10.23) in a new tab or window so you can read these instructions.

1. Select the router and open its CLI by selecting ‘Open console’ from the menu bar. Remember to answer ‘no’ to the question ‘Continue with configuration dialogue?’Select the router and open its CLI by selecting ‘Open console’ from the menu bar. Remember to answer ‘no’ to the question ‘Continue with configuration dialogue?’

2. Practise moving between modes by using the commandsPractise moving between modes by using the commands `enable` and `configure terminal`. Can you use the `configure terminal` command in user exec mode? How does the prompt change when you move from one mode to another?

3. Later in the course you will be using the commandsLater in the course you will be using the commands `interface g0/0` and `show running-configuration`. Try to discover what modes you must be in to use these commands. (Hint: remember you can use the `?` command to show what commands are available in each mode.)

4. When you’re in privileged exec mode what happens when you enter the commandWhen you’re in privileged exec mode what happens when you enter the command `exit`?

You should have found you were unable to use the command `configure terminal` in the user exec mode (where the prompt is a ‘greater than’ symbol). To use this command you need to be in the privileged exec mode (where the prompt is a hash symbol).

You should have found that the commands `show running-config` and `configure terminal` are available in the privileged exec mode but not in the user exec mode. When you enter `configure terminal` the prompt changes to `(config)#` which indicates you have entered global configuration mode.

When in privileged exec mode, the command `exit` takes you back to user exec mode. In fact, in any mode, the command `exit` will take you to the next higher mode (for example from global configuration mode to privileged exec mode and from privileged exec to user exec mode).



You’ve now tried using some commands in the Cisco CLI. You should become confident with moving around it and knowing where the majority of commands should be used, but this comes with practice. The next section of this session moves on to start configuring the router.


## 10.3 Configure a hostname


You will now have an opportunity to configure a hostname on the router. The main reason for configuring a hostname on a device is to easily identify the device when accessing it remotely. For example, if you are working from an office in Milton Keynes but you are configuring a router physically located in London, the only reference you have via the command line is the hostname. It is possible that you could be connected to multiple routers at the same time, so it is important to establish the correct and identifiable hostname before you change the configuration of the device.

Watch the video below (which is about 2 minutes long) to see how to configure a hostname on a router.


### Add a hostname

         ##-- MEDIACONTENT
        
The task for this part is to configure the router with the hostname ‘Piccadilly’. We are connected to an unconfigured router. If we are asked about the configuration wizard, remember to answer no. Then we need to get into global configuration mode. First we need to enter privileged exec mode by typing `enable`. Then we can type `configure terminal`. The prompt will change, and then we are in the configuration mode. We could use the question mark to find out the command, but there are a lot of options in this mode. The command that we need to use is `hostname`. If you get stuck half way through a command you can use the question mark to get help: it will tell you what options can be used with that command. If I use the question mark, we can see that the command needs a word as stated in the CLI. This word is what you want the router to be named. We want this router to be called ‘Piccadilly’, so the full command will be `hostname Piccadilly`. As you hit Return you will see the prompt change to ‘Piccadilly’. This configuration change will take immediate effect, as this is now part of the running configuration. This is the configuration the router is using to make any decisions currently.

If we want the changes to still be effective after a reboot, we will need to save the configuration to the startup configuration. When the router turns on it copies the startup configuration to the running configuration and then continues to make decisions based on this running configuration. We can save the config by going back to privileged exec mode with the command `exit`, then use the command `copy running-config startup-config`. Now the configuration is saved. If the router was to restart now, the configuration of the device would come back to the same state. In the next part we will look at configuring an IP address via the command-line interface.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/61_add_a_hostname.jpg)

         ##-- ENDMEDIACONTENT
    


It is highly recommended to set a hostname on every router or switch. You need to be aware that there are rules for hostnames. For example, a hostname must not exceed 63 characters. It must start and end with a letter or digit, and contain only letters, digits, or hyphens.


### Activity 3 Try it out


#### Question

*5 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt10.23) in a new tab or window so you can read these instructions.

1. Select the router, open the CLI tab, then go to the appropriate configuration mode to configure a hostname.Select the router, open the CLI tab, then go to the appropriate configuration mode to configure a hostname.

2. Configure the hostname ‘Coventry’ on the device and save the configuration.Configure the hostname ‘Coventry’ on the device and save the configuration.


#### Discussion

You should have used the command `enable` to enter the privileged exec mode, and then the command `configure terminal` to enter global configuration mode. The next step was to enter the command `hostname Coventry`. Following this you should have noticed the prompt change from `Router (config)#` to `Coventry (config)#`. To save the change you should have entered the command `exit` to return to privileged exec mode and then used the command `copy running-config startup-config`.

You’ve now used the commands in the CLI to configure a hostname on a router. Now you know which router you are connected to, you can start making configuration changes. The next section will explain how to set an IP address on a router.




## 10.4 Configure an IP address


The video below explains how to configure an IP address on a router. As you will see, you can use Packet Tracer or PT Anywhere to emulate this task. However, not all routers have the same interfaces, so first it’s necessary to determine what interfaces your router has. The common interface types are:

* FastEthernetFastEthernet

* GigabitEthernetGigabitEthernet

* Serial.Serial.

Watch the video below (which is about 3 minutes long) to see how to discover a router’s interfaces and configure their IP addresses.

Note that the presenter uses the Tab key to complete certain commands; in PT Anywhere the Tab key cannot be used in this way.


### Add an IP address

         ##-- MEDIACONTENT
        
In this part the task is to set the IP address 192.168.0.1 on the interface GigabitEthernet0/0 and then save the configuration. We are connected to a blank router, remember to answer no to the configuration wizard, then enter privileged exec with the command `enable`. First let’s check to see what interfaces we have available to configure. We can do this by typing `show ip interface brief`. The output of this command lists the types of interfaces available on the router. It will show the IP address of the interface if one has been configured as well as the current status of the interface. We can see GigabitEthernet0/0 is an available interface but is not configured.

Therefore, we need to make a configuration change, so we will need to enter global configuration mode. This is a good time to point out you do not need to type out the full command for Cisco’s IOS to understand the command. For example, I can type `conf t`instead of `configure terminal` and the router will accept this command as long as it is not ambiguous. Another shortcut is to use the Tab key to complete the command for you. The next command we need to type is `interface GigabitEthernet0/0`. We only have to type `int`, then we can press the Tab key. `interface`will be auto- completed for us. Then instead of typing `GigabitEthernet0/0`, I can save time by only typing `g0/0` – the router will also accept this. You will notice the prompt has changed again from ‘config’ to ‘config-if’ – this indicates that we are now configuring an interface. Now we can add the IP address to the router. Use the command `ip address 192.168.0.1 255.255.255.0`. This is the IP address followed by the subnet mask, more on this later. The IP address is now configured. But the interface will not function – this is because by default router ports are turned off. To turn the interface on, you will need to use the command `no shutdown`. The interface is now functional.

We can check this with the `show ip interface brief` command, but we are currently in the wrong mode. We can get back to privileged exec mode by either typing `exit`twice, or `end` to go straight back to privileged exec mode. From here we can use the shortest version of the command `sh ip int br`to see the configuration change. We can now see GigabitEthernet0/0 has an IP address and the status is ‘up, up’ meaning the interface is working correctly. Don’t forget to save the configuration. We can do this by typing `copy run start`.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/62_add_an_ip_address.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Test yourself


#### Question

*5 minutes*

1. By default, are router interfaces turned on?

(a) No.

(b) Yes.

By default, interfaces are turned off: you must use the `no shutdown` command to turn them on.


#### Question

2. Which IOS modes allow you to issue the `show IP interface brief` command?

(a) Privileged exec

(b) User exec

(c) Global configuration

Incorrect. You cannot issue `show` commands in the global configuration mode.

(d) Interface configuration

Incorrect. You cannot issue `show` commands in the interface configuration mode.


#### Question

3. Which of these are a valid IPv4 host on the network 192.168.0.0/24?

(a) 192.168.0.254

(b) 192.168.0.255

Incorrect. This is the broadcast address.

(c) 192.168.0.0

Incorrect. This is the network address.

(d) 172.16.0.12

Incorrect. This has the wrong subnet.

(e) 192.168.1.1

Incorrect. This has the wrong subnet due to the /24 subnet mask.




### Activity 5 Try it out


#### Question

*10 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/blank) in a new tab or window so you can read these instructions.

1. Drag two routers and a switch onto the work area.Drag two routers and a switch onto the work area.

2. Connect each router to the switch using a GigabitEthernet port. (Using a switch between the routers avoids complications that can arise when connecting routers directly in PT Anywhere.)Connect each router to the switch using a GigabitEthernet port. (Using a switch between the routers avoids complications that can arise when connecting routers directly in PT Anywhere.)

3. Configure an IP address on the connected interface on each router.Configure an IP address on the connected interface on each router.

4. Attempt to ping between the routers.Attempt to ping between the routers.


#### Discussion

By now you should be familiar with the commands for entering global configuration mode. If in doubt, look back to <a xmlns:str="http://exslt.org/strings" href="">Activity 3 in Section 10.3</a>. Once in global configuration mode, you should have entered the command `interface g0/?`, replacing the question mark with the number of the interface that you chose. The next command should be `no shutdown` to turn the interface on. You could have used the command `show ip interface brief` to check your settings.

Was your ping successful? If not, check that you were pinging the correct IP address for the other router and that this was correctly configured.




## 10.5 Summary of Session 10


In this session you have learnt how to connect to a Cisco router via a console connection, how to use the different modes within the Cisco IOS and how to configure a hostname and IP address on the router. Using this information, you can continue to build up your knowledge of more commands that enable you to configure more complex networks.

Check that you are familiar with the commands listed below before moving on, as they will be used repeatedly throughout the remainder of the course.

---


### Commands

In this session you have met the following commands.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Command</th>
<th>Mode</th>
<th>Result</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`configure terminal`</td>
<td class="highlight_" rowspan="" colspan="">Privileged exec</td>
<td class="highlight_" rowspan="" colspan="">Enter global configuration mode</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`copy running-config startup-config`</td>
<td class="highlight_" rowspan="" colspan="">Privileged exec</td>
<td class="highlight_" rowspan="" colspan="">Save the configuration to the `startup-config` file</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`enable`</td>
<td class="highlight_" rowspan="" colspan="">User exec</td>
<td class="highlight_" rowspan="" colspan="">Enter privileged exec</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`end`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration mode</td>
<td class="highlight_" rowspan="" colspan="">Reverts to privileged exec mode</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`exit`</td>
<td class="highlight_" rowspan="" colspan="">Any mode</td>
<td class="highlight_" rowspan="" colspan="">Revert to next highest mode in the mode hierarchy</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`hostname *&lt;hostname&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">Configure a hostname on the device</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`interface *&lt;interface ID&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">Enters into interface configuration mode indicated by `router(config-if)#`</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`ip address*&lt;IP address&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Interface configuration</td>
<td class="highlight_" rowspan="" colspan="">(from interface config mode) Configure an IP address on an interface</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`no shutdown`</td>
<td class="highlight_" rowspan="" colspan="">Interface configuration</td>
<td class="highlight_" rowspan="" colspan="">(from interface config mode) Restarts the interface</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show ip interface brief`</td>
<td class="highlight_" rowspan="" colspan="">Privileged exec</td>
<td class="highlight_" rowspan="" colspan="">Display information about the interfaces of the devices, such as IP address and status</td>
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
command-line interface (CLI)
</td>
<td class="highlight_" rowspan="" colspan="">
The interface used by network engineers to configure a commercial networking device.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Telnet (teletype network)
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol that enables a network device to be remotely accessed and managed.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
terminal emulation client
</td>
<td class="highlight_" rowspan="" colspan="">
The software used by network engineers to access the CLI.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
SSH (Secure Shell)
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol that enables a network device to be remotely accessed and managed.
</td>
</tr>
</tbody>
</table>

---

