# Session 14: Routing protocols



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/14_network_connection.tif)

In an earlier session you looked at the job a router does, which is to route packets of data across networks so that the packet will get to the desired destination. You saw how routers make their routing decisions by looking up the destination address in their routing tables and sending the packet on its way via the appropriate port.

In this session you are going to look at how routers learn about distant networks they are not directly connected to.

By the end of this session, you will be able to:

* understand the differences between static routing and dynamic routingunderstand the differences between static routing and dynamic routing

* know how to configure default static routesknow how to configure default static routes

* know how to configure a simple dynamic routing protocol called RIP (Routing Information Protocol).know how to configure a simple dynamic routing protocol called RIP (Routing Information Protocol).


## 14.1 Troubleshooting the routing process


In this section you are going to troubleshoot the demonstration network shown in Figure 1. You’ll look at the routing tables of the routers to see why ping packets cannot reach their destinations.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/session14-figure1.png)


Figure 1


Watch the video, which is about 2 minutes long.


### Troubleshooting the routing process

         ##-- MEDIACONTENT
        
In an earlier session we looked at the job a router does – which is to route packets of data around our networks, so that the packet will get to the desired destination. We looked at how routers make their routing decisions by looking up the destination address in their routing tables and then sending the packet on its way via the appropriate port.

In this session we are going to look at how routers learn about distant networks that they are not directly connected to. We are going to start with the following network, which we have cabled up and configured all the IP addresses on.

We have setup a ping from PC1 to 192.168.2.2 – which is the address of PC2. We can see here that PC1 can ping PC2 successfully. You should be able to explain already why the first of the pings has timed out.

You would expect this ping to work as both networks are local to Router1 and these networks will be entered into the routing table of the local router automatically when the IP addresses are entered and the interfaces come up.

We are going to ping the gigabit 0/0 interface of Router1 from PC1. This again should be successful as it is local to the same router.

Next we are going to ping the IP address at the other end of the cable linking the routers. So we execute ping 10.10.10.2 from PC1. As we can see, this has failed – even after allowances for any ARP lookups.

Just for good measure we will now ping PC3 from PC1. We would expect this to fail as well, as we couldn’t even reach Router2 from the previous ping.

To try and work out what is wrong, we will now look at the routing tables of both routers. We can see that in Router1 we have entries for the directly connected networks and in Router 2 there are the directly connected networks here as well. We need to think about why PC1 cannot ping PC3.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/75_troubleshooting_the_routing_process.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Think about


#### Question

*10 minutes*

1. In the video, when we pinged PC2 from PC1, the first ping timed out, whereas the remaining three succeeded. Write one or two sentences to explain what you think the reason is for this.

This happened because the ARP table in PC1 did not have an entry from PC2, so an ARP request was issued to find it. This process takes some time, which caused the first ping packet to time out.


#### Question

2. An extract from the routing table of Router 1 from the demonstration network in the video is shown below.


```python

Gateway of last resort is not set
    10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.10.10.0/24 is directly connected, GigabitEthernet0/0
L       10.10.10.1/32 is directly connected, GigabitEthernet0/0
    192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.1.0/24 is directly connected, GigabitEthernet0/1
L       192.168.1.1/32 is directly connected, GigabitEthernet0/1
    192.168.2.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.2.0/24 is directly connected, GigabitEthernet0/2
L       192.168.2.1/32 is directly connected, GigabitEthernet0/2
```


Why can’t a ping from PC1 to PC3 get beyond Router 1? Choose the best answer from the options below.

(Hint: think about how we have set up our network so far.)

An interface has had its IP address wrongly configured.

No. In the demonstration, all of the addresses were correctly set.

One of the routers has an interface down.

No. In the demonstration, all the interfaces were correctly configured and the interfaces were switched on.

There is no route in Router 1’s routing table for the destination network.

Yes. In Router 1’s routing table, there is no known route from Router 1 to Router 2 for packets addressed to anything in the 172.16.1.0/24 network.

The destination PC is switched off.

No. In the demonstration, the PCs were powered on and then had their IP addresses correctly configured.




## 14.2 Routing with default static routes


In this section you will to take a more detailed look at static routes.

Watch the video below, which is just under 2 minutes long.


### Routing with default routes 1

         ##-- MEDIACONTENT
        
The reason why the pings previously failed was because there was no route in the routing table for the destination network.

One solution to the problem would be to put in a default static route – which we briefly saw in a previous session

To do this we are going to add the command `ip route 0.0.0.0 0.0.0.0 10.10.10.2` to Router1. This is called the quad zero route (as it matches all destination networks to the specified IP address). In this case, all traffic for unknown networks will be forwarded to the IP address of gigabit 0/0 on Router2 – this will result in all traffic to unknown networks being sent to Router2.

We will now ping 10.10.10.2 from PC1 again.

This ping still fails.

We will now introduce another useful diagnostic command called traceroute, which is used in network fault-finding to see where the path to a destination network fails.

On a Windows PC this command is entered at a command prompt by typing `tracert`. We can see from the results that there is still no completed path from R1 to R2 – yet we have already entered a default static route out of R1 to R2, which can be demonstrated by using the `show ip route`command on Router1. It shows up as ‘Gateway of last resort is 10.10.10.2 to network 0.0.0.0’. The default static route also shows up at the end of the routing table with an S* next to it.

We need to think about why this might be happening.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/76_routing_with_default_routes.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 2 Think about


#### Question

*5 minutes*

An extract from the routing table of Router 2 from the demonstration network in the first video is shown below.


```python

Gateway of last resort is not set
    10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
C       10.10.10.0/24 is directly connected, GigabitEthernet0/0
L       10.10.10.2/32 is directly connected, GigabitEthernet0/0
    172.16.0.0/16 is variably subnetted, 2 subnets, 2 masks
C       172.16.1.0/24 is directly connected, GigabitEthernet0/1
L       172.16.1.1/32 is directly connected, GigabitEthernet0/1
```


Following the additional configuration to Router 1 shown in the second video, PC1 still cannot ping PC3. Can you think of any reason why this might be happening? Choose the best answer from the options below.

The default route from Router 1 to Router 2 is incorrectly configured.

No. This was correctly set up in the second video.

There is no reverse path in Router 2’s routing table to direct the returning traffic back to Router 1.

Yes. In Router 2’s routing table, there is no known route from Router 2 to Router 1 for packets addressed to anything in the 192.168.1.0/24 network.

PC3 has been configured with an incorrect IP address.

No. PC3 was correctly configured in the first video.

The ping typed on PC1 had the wrong IP address.

No. The correct destination address was entered.




## 14.3 Routing with static routes


In this section you will look at why the network path still isn’t complete, and think about why the ping packet still doesn’t get to its destination and back. You’ll look at how to put static routes into the routers so that they know where to send their packets.

Watch the video below, which is about 4 minutes long.


### Routing with default routes 2

         ##-- MEDIACONTENT
        
The reason why the ping from PC1 to PC3 still does not work is because we don’t have a return path created in the reverse direction for the traffic to come back.

To solve this we need to put the default static route command into Router2 as well, to direct unknown traffic from Router2 to be sent to Router1. We will put the command `ip route 0.0.0.0 0.0.0.0 10.10.10.1`into Router2, which will direct traffic for unknown networks in Router2 back to FRouter1’s address.

OK, so let’s try the ping again. Now when we ping 172.16.1.2 from PC1 we should expect a reply.

From this we have learned that you need to set up both the outward path and a return path between the two routers. Default static routes are really only useful where there is only one router connected to another – such as in the network topology we have used here, or with your home or business broadband connection. Default static routes are useful where there is only one choice of destination to send the traffic to.

With bigger networks we need a different approach to setting up the routing tables. One solution could be to use static routes – where we set up the path to each destination network manually.

First we are going to remove the default static routes we created on both Router1 and Router2. To do this we need to execute the same command we used to put the default route in, but enter the word ‘no’ at the beginning of the command.

OK, let’s look at the following command on Router1: `ip route 172.16.1.0 255.255.255.0 10.10.10.2`.

This has put in a path to network 172.16.1.0 (with a subnet mask of 255.255.255.0) sending the traffic to the IP address of 10.10.10.2 – which is Router2’s address. We must not forget to put in the return path so that Router2 knows how to send the ping back to PC1. For this we will use the command `ip route 192.168.1.0 255.255.255.0 10.10.10.1`.

We now have a path out from PC1 to PC3, and a return back to the starting point. If we now try pinging PC1 from PC3, we can see that this works nicely. It should also work the other way round, so next we will ping PC1 from PC3. This works properly too.

OK, let’s try something else. Let’s see if PC3 can ping PC2. If we ping 192.168.2.2 from PC3, we get this result. We can see that it has failed. The reply was from 172.16.1.1 (which is Router2) and it says that the destination host is unreachable. Let’s look at Router2’s routing table to see what is going on: `show ip route` shows that the new network we manually entered to 192.168.1.0 and with a mask of 255.255.255.0 (which is represented as /24) is in the routing table.

We need to think about why PC3 and PC1 can ping each other, but not PCs 3 and 2.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/77_title_tbc.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 3 Think about


#### Question

*5 minutes*

At the end of the demonstration in the second video, PC3 could ping PC1 and vice versa, but PC3 couldn’t ping PC2. Can you work out why this is happening? Choose the best answer from the options below.

PC3 is incorrectly set up.

No. We know that it is working correctly because PC1 can ping it successfully.

PC2 is incorrectly set up.

No. PC1 can ping PC2 too, so it must be working.

There is no route in Router 2’s routing table pointing to PC2’s network.

PC2 has the wrong IP address configured on it.

No. PC2’s address is correct.




## 14.4 Putting in the final static routes to make it all work


In this next section you are going to fix the network by putting in the final missing routes manually.

Watch the video below, which is about a minute long.


### Routing with static routes

         ##-- MEDIACONTENT
        
Let’s think about what the router is doing when the ping is being sent to 192.168.2.2. The router will look in its routing table for a match to the 192.168.2.0 network. No matching route exists, and there is no default route, so the packet will be dropped.

We can easily fix this by adding the command `ip route 192.168.2.0 255.255.255.0 10.10.10.1` into Router2.

This will put a route in the routing table for the 192.168.2.0 network, again pointing it towards Router1

If we now look at the routing table of Router2, we can see that there is an entry for the 192.168.2.0 network in there now.

Let’s try the ping again and see if it works. This time we can see that it is successful and our network is complete.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/78_title_tbc.jpg)

         ##-- ENDMEDIACONTENT
    


We have now configured the two routers in our small network so that traffic can pass among all the host devices connected to them. To do this we have added static routing information to the routing table on each router, using the `ip route` command. This tells the router which interface to use to forward packets addressed to a particular network address. This information has to be entered manually by the network administrator, so this method is only useful for simple networks that rarely change.


### Activity 4 Try it out


#### Question

*20 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt14.1) in a new tab or window so you can read these instructions.

In this activity you are going to configure static routes on each of the routers to enable the PCs connected to one router to access the PCs connected to the other router.

1. Configure PC1 with IP address 192.168.1.2, subnet mask 255.255.255.0 and gateway 192.168.1.1.Configure PC1 with IP address 192.168.1.2, subnet mask 255.255.255.0 and gateway 192.168.1.1.

2. Configure PC2 with IP address 192.168.2.2, subnet mask 255.255.255.0 and gateway 192.168.2.1.Configure PC2 with IP address 192.168.2.2, subnet mask 255.255.255.0 and gateway 192.168.2.1.

3. Configure PC4 with IP address 172.16.2.2, subnet mask 255.255.255.0 and gateway 172.16.2.1.Configure PC4 with IP address 172.16.2.2, subnet mask 255.255.255.0 and gateway 172.16.2.1.

4. Configure PC3 with IP address 172.16.1.2, subnet mask 255.255.255.0 and gateway 172.16.1.1.Configure PC3 with IP address 172.16.1.2, subnet mask 255.255.255.0 and gateway 172.16.1.1.

5. On the routers (Router 1 and Router 2) enter the commands in the table below.On the routers (Router 1 and Router 2) enter the commands in the table below.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Commands to enter</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router 1</td>
<td class="highlight_" rowspan="" colspan="">
`enable`

`configure terminal` (abbreviate this to `conf t`)

`interface gi0/0`

`ip address 192.168.1.1 255.255.255.0`

`no shutdown`

 

`interface gi0/1`

`ip address 192.168.2.1 255.255.255.0`

`no shutdown`

 

`interface gi0/2`

`ip address 10.10.10.1 255.255.255.0`

`no shutdown`
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router 2</td>
<td class="highlight_" rowspan="" colspan="">
`enable`

`configure terminal` (abbreviate this to `conf t`)

`interface gi0/0`

`ip address 172.16.1.1 255.255.255.0`

`no shutdown`

 

`interface gi0/1`

`ip address 172.16.2.1 255.255.255.0`

`no shutdown`

 

`interface gi0/2`

`ip address 10.10.10.2 255.255.255.0`

`no shutdown`
</td>
</tr>
</tbody>
</table>

1. Verify that PC1 can ping PC2 (ping 192.168.2.2) and PC3 can ping PC4 (ping 172.16.2.2).Verify that PC1 can ping PC2 (ping 192.168.2.2) and PC3 can ping PC4 (ping 172.16.2.2).

2. Check to see if PC1 can ping PC3 (ping 172.16.1.2) – this should fail.Check to see if PC1 can ping PC3 (ping 172.16.1.2) – this should fail.

3. On the routers (Router 1 and Router 2) enter the commands from the table below.On the routers (Router 1 and Router 2) enter the commands from the table below.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Commands to enter</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router 1</td>
<td class="highlight_" rowspan="" colspan="">
`ip route 172.16.1.0 255.255.255.0 10.10.10.2`

`ip route 172.16.2.0 255.255.255.0 10.10.10.2`
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router 2</td>
<td class="highlight_" rowspan="" colspan="">
`ip route 192.168.1.0 255.255.255.0 10.10.10.1`

`ip route 192.168.2.0 255.255.255.0 10.10.10.1`
</td>
</tr>
</tbody>
</table>

1. Check to see whether PC1 can now ping PC3 (ping 172.16.1.2) and PC4 (ping 172.16.2.2).Check to see whether PC1 can now ping PC3 (ping 172.16.1.2) and PC4 (ping 172.16.2.2).

You have now configured static routes so that Router 1 can get to the two networks on Router 2 and vice versa. (Note: if you were to build this network from scratch in PT Anywhere then you would need to place a switch in the link between Router 1 and Router 2. You would also need to have switches in the links between each PC and router. This is because PT Anywhere does not provide the crossover cables for direct links.)




## 14.5 Routing with dynamic routes


In this section you will look at how dynamic routing protocols can be used to automate the process so that static routes don’t have to be put in place for all of our networks.

Watch the video below, which is about 4 minutes long.


### Dynamic routing

         ##-- MEDIACONTENT
        
The idea of static routes works nicely for very small numbers of routers, but what happens if the network is very large? There needs to be a way of making routers learn about each other automatically rather than the network administrator having to keep entering the details manually each time the network changes in some way.

This type of routing is called dynamic routing as opposed to static routing.

There are several routing protocols which have been developed to allow routers to learn about each other’s networks. Examples of these protocols include open-source protocols such OSPF and BGP, but we are going to look at a simple routing protocol called RIP (Routing Information Protocol) as it is about the simplest one to setup and demonstrate in the lab.

First we need to remove all the static routing we entered previously. Again we will do this by re-entering the `ip route` commands with a ‘no’ in front of them.

To configure RIP on each router we need to start the RIP protocol going with the command `router rip`. There are two versions of the RIP protocol for IPv4 – we need to use version 2 as version 1 is now obsolete. This is why we normally type the command `version 2` whenever we type the `router rip`command.

To finish the configuration of RIP, we need to enter a network statement for each network that is local to our routers.

On Router1 enter the following statements: `network 192.168.1.0`, `network 192.168.2.0`and `network 10.10.10.0`on Router1. We now need to go to the command-line interface of Router2 and enter `network 172.16.1.0`and `network 10.10.10.0`.

If we now do a `show ip route` command on each router, we will see that there are some new routes in the routing table with a capital R next to them. This shows that they have been learned by the RIP protocol.

Just to prove everything is working, we will now do some pings from PC to PC to see the response. We can see that PC3 can ping PC1, and PC3 can also ping PC2.

Just to prove that routing protocols make our lives simpler than doing all the work manually, we are now going to add in a new network. We will create PC4 and join it to the gigabit 0/2 interface of Router2. We will then add the IP address of PC4 as 172.16.2.2.

We then give the gigabit 0/2 interface the IP address of 172.16.2.1, and then not forget to switch the interface on.

All we need to do to make this new network show up round the whole system, is to finally enter the new network statement of `network 172.16.2.0` on Router2. To do this, type `router rip`to enter the RIP configuration mode. We do not need to type `version 2`again as it has already been entered previously. We then enter the command `network 172.16.2.0`.

If we now go to Router1 and look at its routing table again, we will now see that the new network has appeared in the routing table and there are now two networks which have been learned by RIP.

You should now have some understanding about the roles of static routing and dynamic routing, and have some idea of the situations in which you would use each type of routing.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/79_title_tbc.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 5 Try it out


#### Question

*10 minutes*

Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt14.2) in a new tab or window so you can read these instructions.

This activity starts off with the same layout as in the previous activity in this session, except this time the IP addresses on all of the devices have already been configured for you.

Your task is to enable dynamic routing (using RIP) on both of the routers.

1. Verify that PC1 cannot ping PC3 (ping 172.16.1.2).Verify that PC1 cannot ping PC3 (ping 172.16.1.2).

2. On the routers (Router 1 and Router 2) enter the commands in the table below.On the routers (Router 1 and Router 2) enter the commands in the table below.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Device</th>
<th>Commands to enter</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router 1</td>
<td class="highlight_" rowspan="" colspan="">
`enable`

`configure terminal` (abbreviate this to `conf t`)

`router rip`

`version 2`

`network 192.168.1.0`

`network 192.168.2.0`

`network 10.10.10.0`
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">Router 2</td>
<td class="highlight_" rowspan="" colspan="">
`enable`

`configure terminal` (abbreviate this to `conf t`)

`router rip`

`version 2`

`network 172.16.1.0`

`network 172.16.2.0`

`network 10.10.10.0`
</td>
</tr>
</tbody>
</table>

1. Verify that PC1 can ping PC3 (ping 172.16.1.2) and PC4 (ping 172.16.2.2).Verify that PC1 can ping PC3 (ping 172.16.1.2) and PC4 (ping 172.16.2.2).

2. Check to see if PC3 can ping PC1 (ping 192.168.1.2) and PC2 (ping 192.168.2.2).Check to see if PC3 can ping PC1 (ping 192.168.1.2) and PC2 (ping 192.168.2.2).

You have now configured RIP on the two routers and verified that each PC can see (ping) all of the other PCs successfully. (Note: as above, if you were to build this network from scratch in PT Anywhere then you would need to place a switch in the link between Router 1 and Router 2, and in the links between each PC and router. This is because PT Anywhere does not provide crossover cables.)




## 14.6 Summary of Session 14


In this session you have looked in detail at routing. A router uses its routing table to determine where to forward IP packets that arrive at its interface. Each entry in the routing table links a network address or a device address to an interface. Incoming IP packets are checked against each line of the table: when an incoming IP address matches an address, the router will forward the packet to the corresponding interface.

Creating the routing table can be done manually by using the `ip route` command. Static routing like this is only appropriate for small networks that rarely change. Dynamic routing protocols such as RIP allow the router to build the routing table by learning which networks are connected to each interface. Dynamic routing can deal with more complex and dynamic networks.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
Routing Information Protocol (RIP)
</td>
<td class="highlight_" rowspan="" colspan="">
A simple dynamic routing protocol used on small networks to enable a router to learn about networks from other routers it is connected to.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Quad zero route
</td>
<td class="highlight_" rowspan="" colspan="">
The default route in IPv4.
</td>
</tr>
</tbody>
</table>

---

