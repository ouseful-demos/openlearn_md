# Session 9: Real-world networking



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/09_modern_city_communication.tif)

This session is a little different from the others you have worked through so far. Before you move on to look at some more complex networks you’re going to take a look at ‘real world’ networking in this session.

You’ll start by looking at some of the physical equipment that network engineers work with – that is the actual devices that network engineers typically spend their time connecting and configuring. You’ll also hear from people working as networking professionals. They will be talking about what initially interested them in getting into networking, what their jobs involve, and how they got into their role. Hopefully this will inspire you to take your study of networking further and consider the potential career opportunities this may open up to you.

By the end of this session, you will be able to:

* recognise physical devices that are used in local area networks and know how to connect themrecognise physical devices that are used in local area networks and know how to connect them

* understand the roles of networking professionalsunderstand the roles of networking professionals

* identify some of the entry routes for a career as a network professional.identify some of the entry routes for a career as a network professional.


## 9.1 Connecting devices


So far, you have been using network simulators to learn how to connect and configure network devices. Computer simulations are really useful tools for learning about computer networks, but it is also helpful to see the physical devices that these simulated components represent.

Knowing what these devices look like and, for example, where to plug the cables in, should help you associate the computer representations with the real thing.

In this first video, you will see what a server room is like. You will see network devices, such as switches, routers and servers, in action. A server is simply a computer, but as it usually serves a single function, or a limited set of functions. It doesn’t have a user driving it, so it doesn’t need a monitor, keyboard or mouse.

Watch the video now, which is about 2 minutes long.


### A server room

         ##-- MEDIACONTENT
        
Hi. I’m Andrew Smith from the Open University.

As you can tell, it’s really noisy in here because of all the networking equipment in this server room. In a little while I’m going to be introducing you to all the equipment in this room and its purpose and why we use it in networks and running the internet.

So it should be a little quieter now. We are actually looking at what’s called a patch panel. This is all the cable connections between the server room and the computers in the network, whether it’s your school computer, a teacher’s computer or an employee’s computer. Each of the flashing lights show data that’s travelling on the network now whilst I was taking this video. Some of these lights are very, very busy and some of them are not so busy.

This cable run here shows the run from the patch panel across the building to all the other computers.

We use this server room to teach Cisco networking. In this cabinet are switches that are used to run large buildings. You may discover that banks, other corporations use these switches to make sure that all their employees are connected and they can run their daily business.

We’re also looking at a series of routers. These connect networks. These connect buildings together or organisations together or different nodes on the internet. These are some very powerful routers. At the back we can see they are cabled differently. These blue cables are serial cables for wide area network links.

Finally, we get to look at some servers. These could be web servers, file servers. They could be telephony servers. They could be streaming your videos to you now. We run a number of servers in our labs offering a considerable amount of storage as well as many other services. Hopefully, you’ll find it’s very useful. You’ll discover in Open Networking Lab all the equipment that I’ve described. The cables, the routers, the switches and the servers exist as part of the PT Anywhere simulator.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/55_a_server_room.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 1 Think about</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. In the video you saw many switches and routers. What is the difference between a switch and a router?

A switch connects devices in a single network; a router connects networks to other networks.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. The video also showed lots of flashing lights on the devices. What were these indicating?

The flashing lights indicate that data is being transferred.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. At the end of the video you saw some servers. What kind of servers were mentioned? Do you know what these different kinds of servers do?

Web servers host websites; file servers store files, telephony servers offer digital phone services.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Now watch the video below, which is about 3 minutes long. It starts by showing a lab environment where two laptop computers are being connected to a switch using Ethernet cables, and the switch is connected to a router.


### Connecting devices together

         ##-- MEDIACONTENT
        
In this demonstration we’re going to look at how devices are connected together. We will use Packet Tracer to set up a small network. Before we do this, we’re going to show you the same network connected up with real devices in the lab. so that you can equate them to the equivalent in Packet Tracer.

To save time we have already positioned the devices on the desk and obtained all the cabling required. The diagram of the network topology we are using is here.

Firstly I’m going to take a network cable and connect it to the data socket on the wall. This is the internet feed. The other end of his cable connects to gigabit 0/1 of the router.

Next I’m going to put a cable between the left-hand laptop’s fast ethernet port and the port fast ethernet 0/1 of the switch. Then I’m going to put the cable in between port fast ethernet 0/2 of the switch and the right-hand side laptop. Finally, I’m going to take a network cable and connect the router’s port gigabit 0/0 to port fast ethernet 0/24 of the switch. Now we have our finished network. OK. So not everybody has a nice pile of equipment available to set up a real network. In order to help people learn networking without having access to real equipment, Cisco have developed the Packet Tracer network simulator. This allows students to learn about networking without the need for real kit.

Now we’re going to create exactly the same network in Packet Tracer. When we open up Packet Tracer, we start off with an empty page. The beauty of Packet Tracer is that we can pretty much do whatever we like, and make networks with many devices and combinations. We are going to construct the same network as we set up in the lab. Firstly we will go to the WAN emulation section and select the PT Cloud. This will represent the Internet. Next we will go to the routers section; select a 2900 series router, as this is what we had available in the lab. at the time.

Next we will go to the switches section and select a suitable switch.

Finally we go into the end-user devices and select a laptop. We can simply drag and drop two of the laptops onto the page: one for the left, and one for the right.

We now have all of our devices positioned on the diagram. Now we need to connect them all up. Using standard ethernet cables we now connect the devices up. When you take the relevant cable, and click it over the device, a list of port numbers will be displayed. All you need to do is click the right port number, and the Packet Tracer will connect one end of the cable to that port. Go to the second device with the same cable, click the device, ands select the correct port for the end of the cable. We now have the internet connection connected to gigabit 0/1 of the router. Next, take the same type of cable and connect up port gigabit 0/0 of the router to port fast ethernet 0/24 of the switch. Finally, we take a cable and connect fast ethernet 0/1 of the switch to the left-hand laptop, and another from fast ethernet 0/2 to the right-hand laptop. Now we have our network connected up. This is all of our hardware sorted out, but it’s not going to work until we program it all. We will be doing that in a later session.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/56_connecting_devices_together.jpg)

         ##-- ENDMEDIACONTENT
    


The video also shows an equivalent network being created in the Packet Tracer network simulator. Later in this session you will have a go at building the same network using PT Anywhere.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 2 Think about</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. Could you make out how many ports the Packet Tracer switch had? How did this compare to the physical switch in the lab? What about the router – did it have many ports?

In Packet Tracer you may have been able to see that there were 24 Fast Ethernet ports on the switch, whereas the switch in the lab had 48. The router (both simulated and physical) had just a few ports (which is typical), but these provide Gigabit Ethernet connections. In fact the router used in the Packet Tracer network is actually a representation of the same model of router (2900 series Cisco router) used in the first video.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. In the video, which devices were connected to the switch?

The laptops and the router were connected to the switch.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. What was the router connected to and why?

The router was connected to the switch and also connected to a socket on the wall which provided access to the internet. Routers are needed to connect a network to the internet.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

### Activity 3 Try it out


#### Question

*10 minutes*

As a revision exercise, use [PT Anywhere](https://forge.kmi.open.ac.uk/blank) to create the same network that you saw in the video. You will need to drag into the main screen the devices that will make up the network, and also the cloud symbol that represents the internet. Just build the network for now making the necessary connections between the devices. You don’t need to configure any devices (unless you want to do this to practise what you have learned earlier in the course).

Hint: when making the connection between the cloud and the router, choose the Cloud’s Ethernet interface.

Here is an image of the finished version of the network.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/session9-activity3-solution512.png)




## 9.2 The role of a network professional


Finally in this session you will find out more about the roles of networking professionals. In the following videos you’ll hear from three networking professionals currently working in the industry for large or small companies:

* Jason, who works for a computer networking company, designing and installing networksJason, who works for a computer networking company, designing and installing networks

* Laura, who works for an e-discovery house, identifying and collecting data for legal proceedingsLaura, who works for an e-discovery house, identifying and collecting data for legal proceedings

* Toby, who is Head of Applications at a large accountancy and business advisory firm.Toby, who is Head of Applications at a large accountancy and business advisory firm.

They each talk about their role, what it involves and how they got into networking and IT.

Watch the video below, which is about 2.5 minutes long.


### Early career interests

         ##-- MEDIACONTENT
        
[Laura:] I wasn’t really interested in IT at all at school. It was more kind of after-school tinkering around with computers and just kind of figuring out how to get around the restrictions my parents put on the computers that was kind of my motivation.

[Jason:] When I was in school, I was interested in sciences and I did a lot of diving and I was heading towards marine biology. But I also had an interest in computers and

[Laura:] It was more kind of after-school tinkering around with computers and just kind of figuring out how to get around the restrictions my parents put on the computers that was kind of my motivation.

I did GCSEs then went to college and studied computers in general and then specialised in computer networking as I went further down the route.

[Toby:] At school, all I really wanted to do was make money and survive, really. Post that, my father was in IT already, so it was just kind of a natural progression into an IT-related learning, really. And so finishing or going through GCSEs and everything like that I then choose IT and then went to college and got to actually be a bit more hands-on and technical.

[Laura:] So we did some IT, like basics, how to use Word, things like that. And it was just boring; it was so boring. It was just like how to type, how to use Excel, and it wasn’t interesting at all until you got to sort of college and then it was kind of like ‘right, take this apart, put it back together again; if you’ve got screws left over,well you’ve got to find out where they go!’. And it was that kind of hands-on, take it apart, put it back together and it worked, that was actually more interesting. And you’re actually seeing like how this would apply to everyday life and into the workplace as well.

[Toby:] I then choose IT and then went to college and got to actually be a bit more hands-on and technical.

[Jason:] I did GCSEs and then went to college and studied computers in genera and then specialised in computer networking as I went further down the route. 

Whilst at college, there was a few good tutors that were pushing me towards networking more than software development and I found it personally easier to get along with networking over software development. And that was the route that I took in the end.

[Laura:] From college I was adamant that I wasn’t going to go to university, that I was going to get an apprenticeship or placement and go from there. But then when I met with some lecturers at an open day at the university, they had such passion which led me ultimately into a degree in security and forensics. And from there, there was guest lecturers and I got a placement year for my third year at university with a digital forensics company who threw me in right at the deep.end and I was performing network collections, digital collections. And then from there t

[Jason:] Whilst I was at college, there was a few good tutors that were pushing me towards networking more than software development and I found it personally easier to get along with networking over software development. And that was the route that I took in the end.

[Laura:] They offered me a job when I finished my degree.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/57_boc_onl_1_video_week5_9_2_earlycareer_1.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 4 Think about</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. What contribution did the interviewees’ study at school make to their choice of career as a network or IT professional?

The interviewees’ school studies did not inspire them to get involved with networking. Two of the speakers had other career plans, and one said that IT lessons were boring.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. What/who encouraged the interviewees to embark on a career in networking?

Generally, their interest was captured by their college studies. In particular, the ‘hands-on’ element of networking and IT appealed to them, as did the links to everyday life and work. They were also inspired and encouraged by their college and university lecturers.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Now watch the video below, which is a little under 3 minutes long.


### Your role

         ##-- MEDIACONTENT
        
[Laura:] So now I work in an e-discovery house.

[Toby:] Head of Applications at BDO, so that covers five distinct areas.

[Laura:] Collecting lots of different types of data from lots of different data systems. Some of those are networked and can be more tricky to get the data from as you have to sort of traverse the networks in order to get those. But collecting the data and preserving that along with the metadata for use in legal proceedings.

[Toby:] What I really do is problem solve. So I will have people come up with issues or wanting to try and get something done. And it’s trying to find the right parts around our environment or the company to then make things work. And normally from an IT side but half the time it’s also people related as well. So it’s really about finding the right people and tools and bringing them together.

[Jason:] Recently we went to Spain to do a large network install. And walking away from that and seeing it working was quite a good day to have. And just knowing that the network is now going to work and improve their day-to-day work lives is good to know..

[Laura:] No two days are the same, which is brilliant. You can go from spending 14 hours collecting different types of data in one country to being in London investigating a network breech the next to doing all the paperwork the next day. Yes, it’s very varied.

[Jason:] Recently we went to Spain to do a large network install. And walking away from that and seeing it working was quite a good day to have. And just knowing that the network is now going to work and improve their day-to-day work lives is good to know.

[Toby:] A meaty problem which I’m dealing with at the moment is really a merger between ourselves and another organisation and having to just look and see what they’ve got in terms of their environment and their technology and then working out what’s the best to bring together and deliver to people as a single solution. That’s actually a really – it’s a lot of work – but it’s a really fun problem to have to deal with.

[Jason:] On a day-to-day basis, I’m looking at networks all over Luton, mostly. We go to smaller companies and if they have issues we resolve them, we install new networks – networks being anything from computers to CCTV because that’s all network based now, door-access controls and so on.

[Toby:] Probably just knowing that you’ve been able to get something working. So that idea of becoming a part of a unit and working for a company and believing in their values or their principles, and then being able to help them achieve or deliver something. When that pulls off and it’s after a long piece of work – and we’re talking like a good 6 or 9 month piece – that point where you just actually get to take a step back, relax and then kind of go OK, yeah, that’s a useful piece done, that makes me smile.

[Laura:] So if there’s something that’s kind of got into the category of you know, ‘above my pay grade’, ‘that’s too tricky’, ‘we need to outsource this’, and then through perseverance you’ve managed to get to the bottom of it, you’ve managed to get the job done. Yeah, that really sends me home with a smile on my face.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/58_boc_onl_1_video_week5_9_2_role_1.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 5 Think about</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. What surprised you most about what is involved in being a networking professional?

Perhaps you were surprised when Jason mentioned that he had recently travelled to Spain as part of his work? Or when Laura said that her work involved preparing for legal proceedings? Or when Toby said that much of his job was people-related?

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. All three interviewees identified aspects of their jobs that they particularly liked and that gave them a sense of achievement. What were some of these?

Variety (‘no two days are the same’); problem solving and sorting things out; achieving things ‘above their ‘pay grade’.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

### Activity 6 Think about


#### Question

*10 minutes*

Below are links to three websites that provide information about careers as a network professional. Pick any two of these links and spend no more than five minutes looking at each one. Jot down a few notes on the kind of work a network engineer does, and routes into a networking career.

* [https://nationalcareers.service.gov.uk/job-profiles/network-engineer](https://nationalcareers.service.gov.uk/job-profiles/network-engineer)

* [https://www.prospects.ac.uk/job-profiles/network-engineer](https://www.prospects.ac.uk/job-profiles/network-engineer)

* [https://www.newhorizons.com/article/how-to-become-a-network-engineer](https://www.newhorizons.com/article/how-to-become-a-network-engineer)

Depending on which of the websites you visited, you will have seen that a network engineer can be involved in the following aspects of computer and communications networks:

* Planning; design; analysis; installation; development; maintenance; repair, troubleshooting; administration; management.Planning; design; analysis; installation; development; maintenance; repair, troubleshooting; administration; management.

The sites identified the following entry routes:

* University (entry at A level): Foundation Degree, Higher National Diploma, Bachelor Degree or MastersUniversity (entry at A level): Foundation Degree, Higher National Diploma, Bachelor Degree or Masters

* College (entry at A level or Diploma): Professional Certificates and DiplomasCollege (entry at A level or Diploma): Professional Certificates and Diplomas

* Apprenticeship (entry at GCSE or A level): Professional Certificates and DiplomasApprenticeship (entry at GCSE or A level): Professional Certificates and Diplomas

* Work experience (for example, from IT helpdesk or entry level IT support): Professional Certificates and Diplomas.Work experience (for example, from IT helpdesk or entry level IT support): Professional Certificates and Diplomas.

All the sites identified recognised technical training courses, for example:

* Cisco Certification ProgramCisco Certification Program

* Comp TIA CertificationComp TIA Certification

* Jupiter Network Certification ProgramJupiter Network Certification Program

* Microsoft Certification.Microsoft Certification.




## 9.3 Summary of Session 9


In this session you have seen some networking equipment in a live server room. You have also seen how real devices can be connected together in a lab to form a simple network and how the same network can be ‘built’ in the Packet Tracer simulator. You had a go at building the network yourself using PT Anywhere.

Finally, you heard three networking professionals talking about their jobs and what brought them into their current careers and you briefly investigated possible career paths as a network professional.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
cabinet
</td>
<td class="highlight_" rowspan="" colspan="">
The housing for network equipment.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
cable run
</td>
<td class="highlight_" rowspan="" colspan="">
The length of cable that connects together two distance network devices.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
CCTV network
</td>
<td class="highlight_" rowspan="" colspan="">
Closed circuit television: a system that transmits television signals within a limited network.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
metadata
</td>
<td class="highlight_" rowspan="" colspan="">
Data about data.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
patch panel
</td>
<td class="highlight_" rowspan="" colspan="">
A board with sockets for connecting devices together using cables.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
serial cable
</td>
<td class="highlight_" rowspan="" colspan="">
A type of cable use to transfer data between two devices.
</td>
</tr>
</tbody>
</table>

---

