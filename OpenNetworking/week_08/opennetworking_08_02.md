# Session 16: Building a more complex network



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/16_cokada.tif)

This session focuses on using the skills you have learnt in this course to make a more complex network from scratch. The network scenario is a company with several offices which need to be connected. You will look at configuring IPv4 and IPv6 addresses, adding routing protocols, and testing connectivity. You will have opportunities to try out some aspects of these activities yourself using PT Anywhere. The video demonstrations in this session all use Packet Tracer rather than Packet Tracer Anywhere; this is because some of the commands needed for this more complex network are not available in the simpler interface of Packet Tracer Anywhere.

By the end of this session, you will be able to:

* 
configure IPv4 and IPv6 addresses


* 
configure the RIP routing protocol for IPv4 and IPv6


* 
use show commands to interrogate the configuration of a device.



## 16.1 Device connections


A local company has tasked you with configuring their routers to provide two branch offices with connectivity to their DNS server, which is connected to their central router located in the head office. Branch office A is using IPv4 and Branch office B is using IPv6. The routers will need to be configured so that both offices can access the server.

You will see how the network below is configured, tested and saved.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/onl_s16_f01.png)

Watch the video below, which is about 2.5 minutes long. It shows this network being built in Packet Tracer.


### Device connections

         ##-- MEDIACONTENT
        
This network will consist of PCs, switches, routers and a server.

Here is the topology we will be working towards. You can see we have four PCs, four switches, three routers and a DNS server to configure. The topology uses IPv4 in the top half and IPv6 in the bottom half. The Central router will need to be configured as a dual-stack router, allowing it to route for both versions. Along the way we will be using `show` commands to check our configuration. Once the configuration is complete we can use `ping` and `traceroute` to check connectivity.

Let’s start by adding the devices to the workspace in Packet Tracer and then connecting them up. I will have the reference topology in the top-right corner to make it easier. Here we are in the latest version of Packet Tracer. Let’s start making this topology.

I will add four PCs, four 2960 switches and three 2911 routers. I will also add a generic server. I have specifically chosen 2911 routers because they have three gigabit interfaces that will be needed to make this topology.

The generic server will be configured to act as an IPv4 DNS server, allowing the resolution of domain names to IP addresses. Unfortunately, at this time Packet Tracer does not support IPv6 DNS.

I am connecting the devices together by selecting a straight-through cable, then clicking the device and selecting the port that the cable needs to attach to. This is repeated at the other end. I am using straight-through cables on all devices. This is because, for gigabit interfaces, crossover cables become irrelevant as the device can auto-sense the connection type.

I will skip the video ahead to where all the devices are connected.

Now I am going to label the devices to avoid confusion later. I will edit the device name labels and then add labels for the IP addresses. Labels can be added by selecting the text tool at the top of the screen and clicking anywhere in the workspace. You may wish to add coloured shapes to your workspace to make a visual representation of the network boundaries.

I will fast forward and neaten the topology to save time.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/83_device_connections.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Test yourself


#### Question

*5 minutes*

In this scenario, PC-A1 is shown as being in network 172.20.16.0/23 and PC-A2 is shown as being in network 172.20.18.0/24. For both of these networks, write out the subnet mask in dotted decimal.

In CIDR notation a /23 subnet mask indicates that there are 23 bits in the network part of the address and 9 bits in the host part. In binary this would be shown as 11111111.11111111.11111110.00000000 which converts to 255.255.254.0 in dotted decimal.

A /24 mask indicates that there are 24 bits in the network part and 8 bits in the host part. In binary this would be shown as 11111111.11111111.11111111.00000000 or 255.255.255.0 in dotted decimal.




## 16.2 Adding hostnames and IP addresses


In this part we will configure hostnames and IP addresses on the routers to allow devices on the same LAN to communicate with each other. It is good practice to assign an identifiable hostname to a router to make it easier to check you are connected to the correct one when you are using the CLI.

Watch the video below, which is about 6 minutes long. In this video, the interfaces of router Branch-A and router Branch-B are configured and each router is assigned a hostname. The video shows some useful shortcuts when working in Packet Tracer, but unfortunately these do not work in PT Anywhere.


### Configuring hostnames and addresses

         ##-- MEDIACONTENT
        
Now we can start configuring the devices. We can see both networks connected to Branch A’s router will be configured with IPv4 addresses, and the two networks connected to Branch B’s router will be configured with IPv6 addresses.

Let’s start by configuring the IP addresses on Branch A’s router. To do this we need to click the router and select the CLI tab. Here if we are asked if we want to go through the first-time set-up wizard we will answer ‘no’.

If we press Return we will be in user exec mode. We can type `enable` to enter privilege exec mode indicated by the hash symbol. Now we can get into global configuration by typing `configure terminal`, or `conf t``for short.`

The first thing I will do is configure the hostname to reduce confusion later. We can do this by typing `hostname Branch-A`. We can see that the router prompt changes to ‘Branch-A’. Now we need to configure the interfaces of the router with IP addresses and then turn them on.

From global configuration, the command `interface gigabit 0/0` will take us into the sub-configuration mode for that interface. Within this mode, we can set an IP address for the interface by typing `ip address 172.20.16.1`. We also need to specify the subnet mask, in this case a /23 subnet mask, the decimal equivalent of which is 255.255.254.0. The interfaces on routers by default are turned off, because they need to be configured first, so we need to turn this interface on. The command is `no shutdown`. Generally the opposite of any command in Cisco is preceded with `no`. As we type `no shut`we will receive a notification message stating that the interface has come up. This means the interface is now functional.

As you become familiar with using the command-line interface you will learn a number of shortcuts to make your use of time more efficient. A number of shortcuts I use in this session include: tab to complete a command, up and down arrows to scroll through the history of commands, Ctrl+A to skip to the front of a command and Ctrl+E to skip to the end of a command. For example, instead of retyping all of those commands again to configure G0/1, we can use the up arrow and just edit the commands instead. Now we can configure gigabit Ethernet 0/1. If we use the up arrow we can get the IP address and just edit it to save some time and then move on to gigabit 0/2. Up arrow again; change the IP address and subnet mask. I forgot to turn gigabit Ethernet 0/1 on so we can just go back into 0/1 and issue `no shut`and then go back to 0/2 and do `no shut`again. Now all the interfaces are configured for Branch-A.

We can check Branch-A’s IP configuration by using the `show``command ``show ip interface brief`. This will show us the IP addresses and the state of the interface. We can see that all the interfaces that have been configured have the right IP addresses and the status is up, up, meaning the interface is configured correctly.

We can now move on to Branch-B. We answer `no``, type ``enable`, `configure terminal`. We can set the hostname to host Branch-B. Go into interface G0/0. This is where the configuration changes slightly. To configure an IPv6 address, you must use `ipv6 address` and then the address followed by the subnet mask in CIDR notation. Note there is no space between the IP address and the subnet mask.

Now we can continue the configuration as before. First `no shut` to turn that interface on. Interface G0/1. IPv6 address 2001:DB8:FADE:100::1/64 `no shut`. Interface gigabit Ethernet 0/2. Set the IPv6 address. Oh, I made a typo. Not to worry: we can just remove the IP address and add the correct one. To do this use the up arrow, then to get to the start of the line you can use Ctrl+A. Then we can insert `no` and hit Return. This will remove the incorrect IP address. And now we can add the correct IP address 2001:DB8:FFFF:FFFF::2/64 `no shut`.

That completes Branch-B’s IP addressing.

We can check Branch-B’s IP configuration with `show ip interface brief`. You can see that there are no IPv4 addresses listed and they are all unassigned. That is because Branch-B is only using IPv6. The `show`command to see the IPv6 address configuration is `show ipv6 show interface brief`where we can see the address is configured and the status of the interface. We can see that all three interfaces have the correct IPs and are up, up meaning they are working.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/84_configuring_hostnames_and_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


When watching this video you may have wondered why a pair of IPv6 addresses were shown for each of the Branch-B router interfaces after the command `show ip interface brief` was issued. You probably recognised the second addresses in the pair as the ones configured for each router interface. The first address is an automatically assigned link-local address for the network segment. Link-local addresses were mentioned in Session 2. Such addresses are not intended for normal networking.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 2 Test yourself</h1>
*2 minutes*

         ##-- ITQ
        

#### Question

Why do you need to issue the `no shutdown` command on a router interface ?

Because, by default, interfaces on routers are switched off, whereas on switches they are on by default

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

The IPv6 address of G0/0 Branch-B router is given as 2001:DB8:FADE:FF::1. Explain the meaning of the double colon in this address.

An IPv6 address is usually written as eight blocks of four hexadecimal numbers, separated by a colon. A double colon indicates that one or more blocks in this position is the hexadecimal number 0000. In the example given, only five number blocks are shown; therefore there must be three 0000 blocks at the double colon.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

### Activity 3 Try it out


#### Question

*10 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt16.3) in a new tab or window so you can read these instructions. In this network only Branch-A’s router has been configured.

1. Check whether the configuration of Branch-A router’s interfaces agrees with the IP addresses given in the table below and make any corrections necessary.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IP address</th>
<th>Subnet mask</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router Branch-A</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">*172.20.16.1*</td>
<td class="highlight_" rowspan="" colspan="">*255.255.2554.0*</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">*172.20.18.1*</td>
<td class="highlight_" rowspan="" colspan="">*255.255.255.0*</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">G0/2</td>
<td class="highlight_" rowspan="" colspan="">172.20.31.254</td>
<td class="highlight_" rowspan="" colspan="">255.255.255.252</td>
</tr>
</tbody>
</table>

2. Configure Router Branch-B with the IPv6 addresses given below. Don’t forget to configure the router’s hostname as well.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IPv6 address</th>
<th>Subnet mask</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router Branch-B</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">*2001:DB8:FADE:FF::1*</td>
<td class="highlight_" rowspan="" colspan="">*/64*</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">*2001:DB8:FADE:100::1*</td>
<td class="highlight_" rowspan="" colspan="">*/64*</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">G0/2</td>
<td class="highlight_" rowspan="" colspan="">2001:DB8:FFFF:FFFF::2</td>
<td class="highlight_" rowspan="" colspan="">/64</td>
</tr>
</tbody>
</table>

3. Check to confirm that Branch-B’s router has been correctly configured.

1. 
To check Branch-A router’s interface configuration, you could use the `show ip interface brief` command, which can be used either in user exec mode or privilege exec mode. This would reveal an incorrect IP address for G0/0. You should have removed the incorrect IP address and then configured the interface with the correct IP address. Of course, you would also need to add the `no shut` command. Checking that the subnet masks are correct would require the use of the `show ip interface` command, which can also be used either in user exec mode or privilege exec mode. The `show ip interface` command gives the subnet mask in slash notation (or CIDR notation).


2. 
Because the Branch-B router uses IPv6 addresses, you need the command `ipv6 address` at the config-if prompt, followed by the appropriate IPv6 address and the subnet mask in CIDR notation. To configure the host name you would use

`Router(config)# host Branch-B`


3. 
This time, because the Branch-B router uses IPv6, the appropriate command to check the configuration of the interfaces is `show ipv6 interface brief`, or `show ipv6 interface`.




Now watch the video below, which is about 2.5 minutes long. It shows the Central router being configured with both IPv4 and IPv6 addresses.


### Configuring the Central router

         ##-- MEDIACONTENT
        
Now we can quickly configure the Central router. Open the command line. Answer `no` to the auto-configuration wizard. Type `enable`. Type `configure terminal``. Set the hostname to ‘Central’. Enter ``interface gigabit ethernet 0/0`. Set an IPv4 address of 172.20.31.253 with a subnet mask of 255.255.255.252. Turn the interface on with `no shut`. Go to interface G0/1. Add its IPv6 address 2001:DB8:FFFF:FFFF::1/64. Turn the interface on with `no shut`.

Go to gigabit Ethernet 0/2 and this is where the configuration changes. On the Central router we have to configure both IPv4 and IPv6 addresses on the same interface to allow connection to the DNS server. So first we can set the IPv4 address, IP address 172.20.32.1 255.255.255.0 and then we can set the IPv6 address 2001:DB8:FADE:1000::1/64. And then turn the interface on. That completes the IP addressing of the Central router.

We can check the IP configuration of the Central router with `show ip interface brief`. As you can see, G0/0 and 0/2 both have IP addresses and they are up. We also need to check the IPv6 configuration `show ipv6 interface brief`. You can see that G0/1 and 2 are both configured and up.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/85_configuring_the_central_router.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Think about


#### Question

*3 minutes*

The result of issuing the command `show ip interface brief` for a router that uses both IPv4 and IPv6 addresses is shown below.


```python

Router#sh ip in br
Interface           IP-Address   OK?  Method  Status                    Protocol
GigabitEthernet0/0  168.30.10.1  Yes  manual  up                        up
GigabitEthernet0/1  unassigned   YES  unset   up                        up
GigabitEthernet0/2  168.30.20.1  Yes  manual  up                        up
Vlan1               unassigned   Yes  unset   administratively down     down
```


Select the correct statement(s) from the list below.

No IP address has been assigned to interface G0/1.

Incorrect. Interface G0/1 might have an IPv6 address. The command `show ip interface brief` (or the shortened form `sh ip in br` used here) applies only to IPv4. It reveals nothing about the use of IPv6 addresses.

Interfaces G0/0 and G0/2 only use IPv4 addresses.

Incorrect. Interfaces G0/0 and G0/1 might have IPv6 addresses in addition to their IPv4 addresses. The command `show ip interface brief` (or the shortened form `sh ip in br` used here) applies only to IPv4. It reveals nothing about the use of IPv6 addresses.

Interface G0/1 is the only interface that could use an IPv6 address.

Incorrect. Any interface could have both an IPv4 and an IPv6 address assigned to it.

It is possible that all three interfaces have an IPv6 address assigned to them.

Correct. An interface can have both an IPv4 and an IPv6 address assigned to it.




### Activity 5 Try it out


#### Question

*5 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt16.5) in a new tab or window so you can read these instructions. In this network both Router Branch-A and Router Branch-B have been configured.

1. Configure the Central router with the IPv4 and IPv6 addresses given below. Don’t forget to configure the router’s hostname as well.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IPv4 address</th>
<th>Subnet mask</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router Central</td>
<td class="highlight_" rowspan="" colspan="">G0/0</td>
<td class="highlight_" rowspan="" colspan="">*172.20.31.253*</td>
<td class="highlight_" rowspan="" colspan="">*255.255.255.252*</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">*172.20.32.1*</td>
<td class="highlight_" rowspan="" colspan="">*255.255/255/0*</td>
</tr>
</tbody>
</table>
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Interface</th>
<th>IPv6 address</th>
<th>Subnet mask</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router Central</td>
<td class="highlight_" rowspan="" colspan="">G0/1</td>
<td class="highlight_" rowspan="" colspan="">*2001:DB8:FADE:1000::1*</td>
<td class="highlight_" rowspan="" colspan="">*/64*</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan=""></td>
<td class="highlight_" rowspan="" colspan="">G0/2</td>
<td class="highlight_" rowspan="" colspan="">*2001:DB8:FFFF:FFFF::1*</td>
<td class="highlight_" rowspan="" colspan="">*/64*</td>
</tr>
</tbody>
</table>

2. Use the correct commands to check that the router’s interfaces have been correctly configured.

1. At theAt the `(config-if)#` command the correct command to configure IPv4 addresses is `ip address` followed by the appropriate IPv4 address and subnet mask. At the `(config-if)#` command the correct command to configure IPv6 addresses is `ipv6 address` followed by the appropriate IPv6 address and subnet mask in CIDR notation.

2. The commands to check the correct interface configuration areThe commands to check the correct interface configuration are `show ip interface brief` and `show ipv6 interface brief`. You need to be in either user exec or privilege exec mode to enter these commands. The results should look something like the following (although your link-local addresses, which are the ones beginning with FE80, might be different):


```python

Central#show ip int br
Interface           IP-Address     OK?  Method  Status                  Protocol
GigabitEthernet0/0  172.20.31.253  YES  manual  up                      up
GigabitEthernet0/1  unassigned     YES  unset   down                    down
GigabitEthernet0/2  172.20.32.1    YES  manual  up                      up
Vlanl               unassigned     YES  unset   administratively down   down
 
Central#show ipv6 int br
GigabitEthernet0/0        [up/up]
GigabitEthernet0/1        [up/up]
     FE80::2D0:58FF:FEE6:DD02
     2001:DB8:FFFF:FFFF::1
GigabitEthernet0/2        [up/up]
     FE80::2D0:58FF:FEE6:DD03
     2001:DB8:FADE:1000::1
Vlanl                      [administratively down/down]
Central#
```




Now watch the video below, which is about 2 minutes long. It shows the PCs being configured with their IP addresses


### Configuring the PCs

         ##-- MEDIACONTENT
        
Now we can configure the IP addresses on the PCs.

Click the PC, select the ‘Desktop’ tab, and then select the ‘IP Configuration’ option. Within this window we can configure both IPv4 and 6 addresses. We are configuring PC-A1 so the IP address is 172.20.16.10 and the subnet mask is 255.255.254.0. The default gateway is the IP address of the local router, 172.20.16.1 and for testing later I will set a DNS server address of 172.20.32.10.

I will now move to PC-B1 to demonstrate configuring a IPv6 address on a PC. It is very similar. Go to the ‘IP Configuration’ of the PC, but in the lower section of the window you add the IPv6 details instead. So for PC-B1 the IPv6 address is 2001:DB8:FADE:FF::10 with a mask of /64. The IPv6 gateway will be 2001:DB8:FADE:FF::1 and the DNS server will be 2001:DB8:FADE:1000:10.

These two configurations will need to be repeated on PC-A2 and PC-B2 with the appropriate addresses to complete the IP configuration of all the devices. In the background, the DNS server has been configured with its IPv4 and IPv6 address and an A record has been created for contoso.com for testing purposes in a later section.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/86_configuring_the_pcs.jpg)

         ##-- ENDMEDIACONTENT
    


Note that at the end of the above video the speaker says ‘… and an A record has been created for contoso.com for testing purposes’. An A record on a domain name server (DNS) links a domain name such as [open.ac.uk](http://www.open.ac.uk) to an IP address. When you type the URL into a browser, an A record at the DNS enables your computer to be informed of the IP address of the web page you wish to consult.


### Activity 6 Think about


#### Question

*2 minutes*

The video showed that when an IPv6 address is configured, the subnet mask has to given in CIDR – for example as /64. Why is this more sensible than using dotted decimal form for the subnet mask?

The slash notation is much simpler than the dotted decimal, and therefore less likely to be a source of error when it is keyed into the settings or written down. With IPv4, the dotted decimal notation is not too complicated, but in IPv6 it is horrendous. This is because IPv6 address consists of 128 bits arranged in eight groups of four hexadecimal digits. Each group of four hexadecimal digits represents 128 bits ÷ 8 = 32 bits. That is as many bits as an entire IPv4 address has. So, if the first 32 bits of an IPv6 subnet mask were all 1s, to show that this part of the address was in the network part of the address, the dotted decimal number in the subnet mask would be 4,294,967,295; and that would just be one-eighth of the subnet mask!

It would be less complicated to represent the subnet mask as a series of hexadecimal numbers, like the address itself. In that case, if the first 32 bits of an IPv6 subnet mask were all 1s then they would be represented as FFFF, which is not so bad, but it is still only one-eighth of the complete mask. The slash notation is much simpler.




## 16.3 Adding a routing protocol


In this part you will learn how to configure the RIP routing protocol on the routers. The protocol has different versions for IPv4 and IPv6, and the IPv4 version itself has two versions. For IPv4, we will use RIPv2, which is the version that is almost always used for IPv4. The IPv6 version is RIPng. The Central router will need to be configured for both as it is using both IPv4 and IPv6. This is called a dual-stack router.

Watch the video below, which is about 5 minutes long. It shows RIP and RIPng being configured.


### Adding a routing protocol

         ##-- MEDIACONTENT
        
Now we have the IP addresses configured we will have LAN connectivity. We need to configure the routers with a routing protocol to allow access to the DNS server from the PCs. We could do this with static routes, but that would be time consuming and less efficient to manage later. The better solution is to use a dynamic routing protocol. RIP is the simplest routing protocol and uses hops as its metric.

We can start by configuring RIP version 2 on Branch-A’s router. Open the CLI and enter global configuration mode. From here type `router rip`. This will enter router configuration mode. Then type `version 2`, allowing us to use classless networks instead of the classful addresses used in version 1. Then we need tell RIP which networks to advertise on. This can be done using the `network`` command. Type ``network 172.20.16.0`and then `network 172.20.18.0`and also `network 172.20.31.252`.

To check the configuration of RIP we can use `show ip protocols`. This command shows us how often updates are sent and when the next update is expected. Also it shows us which interfaces are being used within RIP and some other useful information for troubleshooting if we need it.

Moving to Branch-B, we need to configure RIPng for IPv6 routing. This is done slightly differently compared to the IPv4 version. Start by entering global configuration mode. We need to enable IPv6 routing capabilities on this router. The command is `ipv6 unicast-routing`. Now we can enable RIPng on the router. The command is `ipv6 router rip`. Then you type an instance name; I will use RIPng1. This name is only locally significant, but it is easier to use the same name on all devices.

This is where the key difference between IPv4 and IPv6 configuration comes in. You have to add the interfaces to the RIP process and not the network. Therefore, enter the interface. Then add the interface to the RIP process with the command `ipv6 rip RIPng1 enable` where RIPng1 is the same as the process ID you set previously. Repeat this on all interfaces that need to be included in the RIP process.

Now, on the Central router we will need to configure RIP for both IP versions. First I will setup RIPng. From global configuration mode, use the command `ipv6 unicast-routing` to turn on IPv6 routing. Then we’re going to use `ipv6 router rip RIPng1` to enable RIP on the router. Then we need to go into the interfaces that are being used by RIP and enable RIP on the interface using the command `ipv6 rip RIPng1 enable`. Repeat this on G0/2: `ipv6 rip RIPng1 enable`. We can then type `exit` to get back to global configuration mode.

Now we can start configuring RIP version 2 for IPv4. First we use `router rip` then upgrade it to version 2 and then add the network statements to advertise RIP. So we need `network 172.20.31.252` and `network 172.20.32.0`.

To check that RIP is working properly and that routers are receiving updates, we can use show ip route to check the routing table to see if there are any RIP routing entries. From the Central router’s point of view, it should have two RIP entries for IPv4 and two RIP entries for IPv6. We can see the two specific routes at the top of the routing table and if we do `show ipv6 route`we can see the IPv6 routes at the top of this table as well.

Now we have routing configured on all the routers, all the IPv4 devices should be able to communicate and all IPv6 devices should have connectivity. We will test this later in the session.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/87_adding_a_routing_protocol.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 7 Test yourself</h1>
*2 minutes*

         ##-- ITQ
        

#### Question

Is the following statement true or false? ‘By default, a router will route both IPv4 and IPv6 packets.’

True

False

The statement is false: IPv4 routing is on by default, but IPv6 must be switched on with the `ipv6 unicast-routing` command.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

### Activity 8 Try it out


#### Question

*15 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt16.8) in a new tab or window so you can read these instructions.

You saw in the last video the `show ip protocols` command on the Branch-A router. The equivalent command for IPv6 is `show ipv6 protocols`. Use this command on the Branch-B router to work out which interface has not been configured with RIPng. Then configure the interface with RIPng, and use the `show ipv6 protocols` command again to check that it has been suitably configured.

This is what the `show ipv6 protocols` command produces on the incorrectly configured Branch-B router:


```python

Branch-B#show ip protocols
IPv6 Routing Protocol is "connected"
IPv6 Routing Protocol is "ND"
IPv6 Routing Protocol is "rip RIPng1"
Interfaces:
   GigabitEthernet0/0
   GigabitEthernet0/2
```


The GigabitEthernet0/1 interface is missing from the list of interfaces above. Its absence shows it has not been configured with the routing protocol `rip RIPng1`.

To configure the GigabitEthernet0/1 interface with this protocol requires these instructions:


```python

Branch-B(config)#int g0/1
Branch-B(config-if)#ipv6 rip RIPng1 enable
```


To check this has produced what we want, using the `show ipv6 protocols` command now gives the following:


```python

Branch-B#show ipv6 protocols
IPv6 Routing Protocol is "connected"
IPv6 Routing Protocol is "ND"
IPv6 Routing Protocol is "rip RIPng1"
Interfaces:
   GigabitEthernet0/0
   GigabitEthernet0/1
   GigabitEthernet0/2
```


The list of configured interfaces now includes the GigabitEthernet0/1 interface.

The term ‘ND’ refers to a legacy technology used when routing isn’t available between direct connections. Sometimes you will see ‘static’ here instead.




## 16.4 Testing the configuration


In this part you will use `show` commands to interrogate the configuration of the routers. Also you will use `ping` and `traceroute` commands to test connectivity between devices.

Watch the video below, which is about 2 minutes long. It demonstrates using the commands above to test connectivity, and then saving the configuration.


### Testing the configuration

         ##-- MEDIACONTENT
        
To test this we can use `ping`. From PC-A1 we will ping contoso.com. The A record for contoso.com points to the IP address of the DNS server. If the ping is successful, we know everything is configured and working correctly. The first time you do this ping you may drop one to three pings. This depends on the ARP caches of each device on the network and whether an ARP request needs to be sent. So from PC-A1 if we ping contoso.com we should get a successful ping – like that.

If we move to PC-B1 and try to ping contoso.com the pings fail. This is because PC-B1 is only configured to use IPv6 and the DNS server does not have an IPv6 A record or quad A record configured. To test connectivity we can just ping the IPv6 address of the DNS server. So if we do `ping 2001:DB8:FADE:1000::10` we should get a response – like that.

Another useful command to help troubleshoot when you have issues would be `traceroute`. Traceroute shows the hops taken to get to a destination. So if we type `tracert contoso.com` into PC-A1, we can see that we get a response from 172.20.16.1 and then 172.20.31.253 and then 172.20.32.10. This is what is expected. As you can see, it’s responding with Branch-A’s gigabit 0/0 interface and then the Central router’s gigabit 0/0 interface and then the DNS server’s IP address.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/88_saving_the_configuration.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 9 Test yourself</h1>
*2 minutes*

         ##-- ITQ
        

#### Question

Match the description to the correct command:

`ping`

A command that can be used to test whether there is end-to-end connectivity

`tracert`

A command that tracks the path of the traffic between routers and which can show you where in the device sequence a fault is.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

### Activity 10 Try it out


#### Question

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt16.10) in a new tab or window so you can read these instructions. This is the fully configured network.

1. In the last video you saw `traceroute` being used with an IPv4 address, but not with an IPv6 address. From PC-B2, use `traceroute` to check the route to the DNS server, which has an IPv6 address of 2001:DB8:FADE:1000::10. Is the result what you would expect?

2. The DNS server also has an IPv4 address, which is 172.20.32.10. Try pinging this from PC-B2. Explain your result.

1. When I did this I got:


```python

1 1 ms 0 ms 0 ms 2001:DB8:FADE:100::1
2 0 ms 0 ms 0 ms 2001:DB8:FFFF:FFFF::1
3 0 ms 1 ms 0 ms 2001:DB8:FADE:1000::10
```


The first line is the response from Branch-B router’s G0/1 interface. The second line is from Central router’s G0/1 interface. The third line is from the DNS server. This is what we would expect if the network is working properly.

2. The ping fails because the Branch-B router is configured for only IPv6 addresses (and also the Central router’s G0/1 interface is configured only for IPv6 addresses). Even if these were dual stack, and able to handle both IPv4 and IPv6, the ping would fail because PC-B2 has no IPv4 address, so there is no address to send the response to the ping to.




## 16.5 Saving the configuration


Watch the video below, which is about 1 minute long. It demonstrates how the configuration is saved.


### Saving the configuration

         ##-- MEDIACONTENT
        
In the network’s current state, if there was a power cut, all the configuration changes we have made would be lost. This is because all the changes that we have made are in the running config. When a router turns on, it copies the config from the startup config to the running config. But currently our startup cofig is empty. You can see the running configuration by typing `show running-config`. Likewise if you want to see the startup config you can use `show startup-config`.

To save the config we need to use the command `copy running-config startup-config`. This will copy all the information from the running config to the startup config. The shortest form of this command is actually `wr`. This does exactly the same as `copy run start`.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/89_testing_the_configuration.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 11 Think about


#### Question

*2 minutes*

Packet Tracer Anywhere does not allow a configuration to be saved (unlike Packet Tracer itself). What are the implications of this if you are building a complicated network of if your computer suddenly fails?

With a really complicated network you probably wouldn’t want to construct it and configure it in one long session. You would probably want to do it in stages with a break between, and save your work at the end of each session. That is not possible with PT Anywhere. Also, if your computer suddenly failed you would lose any work you had done setting up or configuring the network.




## 16.6 Summary of Session 16


In this session you have put all your knowledge of routers, switches and connecting cables together to make a network. You have then added the relevant IPv4 and IPv6 addresses and the RIP routing protocols to enable communication between all of the end devices. Finally you have saved all of your configuration work so that the devices will return to their working state after they are powered off and back on again.

---


### Commands

In this session you have used the following commands.
<table xmlns:str="http://exslt.org/strings">
<caption>General commands</caption>
<tbody>
<tr>
<th>Command</th>
<th>Mode</th>
<th>Command prompt</th>
<th>Purpose</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`host *&lt;name&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)#`</td>
<td class="highlight_" rowspan="" colspan="">To configure the hostname</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`copy running-config startup-config`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To copy the running configuration to the startup configuration file</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`ipv6 address *&lt;IPv6 address and subnet mask in CIDR notation&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">interface configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-if)#`</td>
<td class="highlight_" rowspan="" colspan="">To configure an IPv6 address</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show ipv6 interface brief`</td>
<td class="highlight_" rowspan="" colspan="">user exec</td>
<td class="highlight_" rowspan="" colspan="">`Router&gt;`</td>
<td class="highlight_" rowspan="" colspan="">To show brief IPv6 status of router interfaces</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show ip route`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To show RIP (or other protocol) information</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show ip protocols`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To check RIP function</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show ipv6 route`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To show RIPng (or other protocol) information</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show ipv6 protocols`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To check RIPng function</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show running-config`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To show the running configuration</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`show startup-config`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router#`</td>
<td class="highlight_" rowspan="" colspan="">To show the startup configuration</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`tracert *&lt;destination&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">user exec</td>
<td class="highlight_" rowspan="" colspan="">`Router&gt;`</td>
<td class="highlight_" rowspan="" colspan="">To show the hops taken to reach the specified destination</td>
</tr>
</tbody>
</table>
<table xmlns:str="http://exslt.org/strings">
<caption>Commands to configure RIP for IPv4 networks</caption>
<tbody>
<tr>
<th>Command</th>
<th>Mode</th>
<th>Command prompt</th>
<th>Purpose</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`router rip`</td>
<td class="highlight_" rowspan="" colspan="">global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)#`</td>
<td class="highlight_" rowspan="" colspan="">To turn on RIP IPv4 routing</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`version 2`</td>
<td class="highlight_" rowspan="" colspan="">global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-router)#`</td>
<td class="highlight_" rowspan="" colspan="">To instruct router to use RIP version 2 for IPv4 classless network addressing</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`net *&lt;IP address&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-router)#`</td>
<td class="highlight_" rowspan="" colspan="">To instruct RIP which networks to advertise on</td>
</tr>
</tbody>
</table>
<table xmlns:str="http://exslt.org/strings">
<caption>Commands to configure RIPng for IPv6 networks</caption>
<tbody>
<tr>
<th>Command</th>
<th>Mode</th>
<th>Command prompt</th>
<th>Purpose</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`ipv6 unicast routing`</td>
<td class="highlight_" rowspan="" colspan="">global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)#`</td>
<td class="highlight_" rowspan="" colspan="">To turn on RIPng IPv6 routing</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`ipv6 router rip *&lt;instance name&gt;* enable`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)#`</td>
<td class="highlight_" rowspan="" colspan="">To enable RIPng on router</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`int *&lt;interface name&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-rtr)#`</td>
<td class="highlight_" rowspan="" colspan="">To nominate the router interface using RIPng</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`ipv6 rip *&lt;instance name&gt;* enable`</td>
<td class="highlight_" rowspan="" colspan="">privilege exec</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-if)#`</td>
<td class="highlight_" rowspan="" colspan="">To add nominated interface to RIPng process</td>
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
A record
</td>
<td class="highlight_" rowspan="" colspan="">
A DNS record used to point to an IP address.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
dual-stack router
</td>
<td class="highlight_" rowspan="" colspan="">
A router that can route both IPv4 and IPv6 traffic.
</td>
</tr>
</tbody>
</table>

---

