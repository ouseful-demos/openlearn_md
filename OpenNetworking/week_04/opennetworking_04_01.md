# Session 7: Representation of network addresses



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/07_communication_and_network.tif)

In previous sessions you have learned how to recognise IP addresses and MAC addresses. In this session you are going to take a closer look at how these addresses are represented. You will be looking at two different number bases – binary and hexadecimal – and how they can represent the addresses used in network communications. Then you’ll move on to have a closer look at subnet masks.

By the end of this session, you will be able to:

* use the binary and hexadecimal number base systems and convert between different number bases using a calculatoruse the binary and hexadecimal number base systems and convert between different number bases using a calculator

* express a subnet mask in Classless Inter-Domain Routing (CIDR) notationexpress a subnet mask in Classless Inter-Domain Routing (CIDR) notation

* recognise the role of CIDR in the scalability of communication networks.recognise the role of CIDR in the scalability of communication networks.


## 7.1 Base arithmetic


In this part there is a slight side track from the focus on communications networks: instead you’ll take a short time to look at some arithmetic that will help you to understand the representation of network addresses. This is very fundamental arithmetic about how we count and how we represent numbers, and you may already be familiar with this. If this is the case, then you can treat this part as revision.

There are three videos in this part – each video is followed by an activity.

Watch the video below, which is about 3 minutes long.


### Base arithmetic

         ##-- MEDIACONTENT
        
Hello. In this video I’m going to introduce the idea of number systems and then go on to explain the base 10 number system.

These are examples of an IP address and a MAC address. You know from earlier sessions thtype="video" width="512"at they are just identification numbers but they’re represented in a way that you might not be familiar with. They use a different number base from the system we commonly use. By ‘number base’ I am referring to the number of unique symbols used to express numbers.

Most humans work with a base 10 number system – that’s a system that uses ten unique symbols: 0, 1, 2, 3, 4, 5, ,6 7, 8 and 9.The base 10 system is also known as the decimal or denary system. Through the use of just these ten symbols, we’re able to express infinitely large numbers. This is done by applying different weightings to the symbols depending on their position.

I’ll use the number three thousand six hundred and ninety two to illustrate this. The number in the rightmost position has the weighting of one. That is, any number in this position is multiplied by one. Here it is the number 2. 2 times 1 equals 2. So in our example, the symbol in this position (the 2) contributes 2 to the overall value of the group.

Moving leftwards, the number in the next position has the weighting of ten, so any number in this position is multiplied by 10. Here the number in this position is 9. (9 times 10 equals 90).So in our example, the symbol in this position contributes 90 to the overall value of the group.

The number in the next position to the left has a weighting of one hundred. So any number in this position is multiplied by one hundred. Here it’s 6. (6 times 100 equals 600) and therefore it contributes 600 to the overall total.

Finally, in this example, the number in the remaining position has a weighting of one thousand. Here the number is 3. So the number in this position is multiplied by one thousand (3 by 1000 equals 3000), thus contributing 3000 to the overall total.

Now we add together all the numbers derived from the successive weightings: 3000 + 600 + 90 + 2. This gives us three thousand six hundred and ninety two (3692).

Of course, we’re so used to expressing numbers in this way that we no longer need to go through this procedure in order to determine what the number is, but you may well have done this when you were first learning about arithmetic.

We call this form of arithmetic the base 10 number system, also commonly known as the ‘decimal’ or ‘denary’ number system.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/41_base_arithmetic.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 1 Test yourself</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

In the base 10 (decimal) number 242, the symbol 2 represents different values depending on its position. What are these values?

The symbol ‘2’ on the left is in third place so a weighting of 100 is applied to it, giving it a value of 200. The symbol ‘2’ on the right is in first place so a weighting of 1 is applied to it giving it a value of 2.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

Working in the base 10 (decimal) number system, in a six-symbol number such as 495,362, what weighting is applied to the leftmost symbol? What does the symbol ‘4’ represent in the number 495,362?

The leftmost symbol in our example is in sixth place so a weighting of 100,000 is applied to this symbol. So in the decimal number 495,362, the ‘4’ represents 400,000.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 2 minutes long.


### Exponential notation

         ##-- MEDIACONTENT
        
Hello. This video introduces you to a system called ‘exponential notation’ which provides us with a useful shorthand for representing large numbers. I’ll start by revisiting the last part of the previous video.

Did you notice that as we moved from right to left the weighting applied was 10 times the previous one? This is what happens in a base 10 number system. We can express higher numbers simply by adding another position to the left with a weighting that is 10 times more than the previous position. But, as the weightings get larger, it becomes more and more difficult to show all the zeros. Did you notice how they were starting to get a bit squashed up in our example? And we were only using four places. It also becomes more difficult for us to interpret numbers when they’re followed by multiple zeros. They’re not easy for humans to count. Instead we use a convenient shorthand which I’ll explain.

In the decimal system, where we have a weighting of 1 which is the equivalent of no weighting at all, we use the shorthand 10 to the zero (ten to the power of zero). 10 to the zero is equal to 1. In fact any number raised to the power of zero is equal to 1. So, for example, 7 to the zero is equal to 1 and 12 to the zero is also equal to 1.

For a weighting of 10 we use the shorthand 10 to the one (ten to the power of one). 10 to the one equals 10 and raising it to the power of one has left it unchanged. In fact, any number raised to the power of one remains unchanged. That is 10 to the one = 10; and also, for example 7 to the one = 7; 12 to the one = 12.

For a weighting of 100 we use the shorthand 10 to the two. Ten to the power of two. That’s 10 times 10 which equals 100.

10 to the three equals 10 times 10 times 10 equals 1000 and so on.

This representation is known as exponential notation.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/42_exponential_notation.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 2 Test yourself</h1>
*5 minutes*

Give your answers to the following:

         ##-- ITQ
        

#### Question

8 × 103 = 

8 × 103 = 8000

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

4 × 105 = 

4 × 105 = 400,000

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

7 × 107 = 

7 × 107 = 70,000,000

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 3 minutes long.


### Base 2 arithmetic

         ##-- MEDIACONTENT
        
In this last video for this part I’m going to build on what you already know from the previous activities on base 10 arithmetic and exponential notation to explain base 2 arithmetic.

As you know, computers ‘think’ in zeros and ones. This means they can only use two symbols – a 0 and a 1 – to represent numbers. Number systems with only two symbols are known as base 2 or binary number systems. So how are we going to represent very large numbers using a binary system of only two symbols? I expect you’ve guessed or already know that we use a similar weighting system as we used with our base 10 system.

For example, let’s use the binary number 1010.

This time, as we move from right to left, the weighting is twice the value of the previous weighting. Remember it was 10 times the value in the decimal number system. This time I’m going to express the weightings using the exponential notation that you’ve just seen. The rightmost number has a weighting of 2 to the zero (that’s two to the power of zero). Remember I said previously that any number raised to the power of zero is one? So 2 to the zero is 1. There’s a 0 in this position so the value here is 0 times 1 equals 0. And the symbol in this position contributes 0 – nothing – to the overall value of the group.

The next number to the left has the weighting of 2 to the one. Remember I said previously that any number raised to the power of one remains unchanged? Therefore 2 to the one is 2. In this example there’s a 1 in this position so the value here is 1 times 2 equals 2, thus contributing 2 to the overall value of the group.

The next number to the left has the weighting of 2 to the two. That’s 2 times 2 equals 4. There’s a 0 in this position giving us 0 times 4 equals 0. So the symbol in this position contributes nothing to the total.

And finally, the next number to the left has the weighting of 2 to the three. That’s 2 times 2 times 2 equals 8. And here we have a 1 in this position contributing 1 times 8 equals 8 to the overall value.

Just as before, we add all the numbers derived from the successive weightings. This gives us 8 + 0 + 2 + 0 = 10, so the decimal equivalent of the binary number 1010 is 10.

Once you understand how the weighting system works in base arithmetic you can work in any number base.

In Part 3 of this session, you’ll meet the base 16 number system, known as hexadecimal.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/43_base_2_arithmetic.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 3 Test yourself</h1>
*5 minutes*

Give the denary equivalents of the following binary numbers:

         ##-- ITQ
        

#### Question

1110

1110 = (1 × 23) + (1 × 22) + (1 × 21) + (0 × 20) = 8 + 4 + 2 + 0 = 14

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

1001

1001 = (1 × 23) + (0 × 22) + (0 × 21) + (1 × 20) = 8 + 0 + 0 + 1 = 9

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

101101

This is more difficult as you need to apply some higher binary weightings of 25 (16) and 26 (32).

So 101101 = (1 × 25) + (0 × 24) + (1 × 23) + (1 × 22) + (0 × 21) + (1 × 20) = 32 + 0 + 8 + 4 + 0 + 1 = 45.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 7.2 Converting between number bases


This part demonstrates the use of the Windows calculator to convert between binary and decimal number systems and also identifies sources for online tools that will do the same job. There is just one video in this part, which is followed by some questions.

Watch the video below, which is about 4 minutes long.


### Using a calculator

         ##-- MEDIACONTENT
        
Hello. In the previous part we looked at two different number systems: base 10 (decimal) and base 2 (binary). In particular we looked at how large numbers can be represented using both of these number systems. But what do we do if we want to convert a number from one base to another? Fortunately there are tools to help us with this otherwise rather tedious task and I’m going to demonstrate them in this very short part.

The tool I’m going to use is the Windows calculator, but later I’ll identify some online tools you can use instead. You can find the Windows Calculator in Windows Apps.

By default it will open as a standard calculator unless you previously altered the settings, so first of all we need to change the calculator from standard to programmable. Click the Menu button and select Programmer from the list.

Here you select the number base you want to convert from. Mine has opened by default in decimal as you can see from the blue flash at the side. But I can also choose HEX to convert from hexadecimal which uses base 16, OCT to convert from octal which uses base 8, or BIN to convert from binary. I’ll stick with decimal for now.

Let’s say I want to convert the decimal number 10 into binary. I enter the number 10 using the calculator’s keypad, and I’m immediately presented with the hexadecimal, decimal, octal and binary equivalents.

So the binary equivalent of decimal 10 is 1010.

Let’s try a longer decimal number now: how about that number we were working with in the previous part – 3692?

First I’ll need to clear the previous conversion by clicking the C button.

Entering the decimal number 3692 immediately displays the equivalents in the other number bases. So the binary equivalent of decimal 3692 is 1110 0110 1100. Note how longer binary numbers are displayed in groups of four. This makes it easier for us to read them.

Now let’s go the other way from binary to denary. I’ll choose the 8-bit binary number 1010 1010.

First I need to clear the previous conversion by clicking on C and then I need to select the binary input option. Notice how the only symbols I’m offered now are 0 and 1. Now I'll enter the binary number 1010 1010 via the keypad. Immediately the equivalents in the other number bases are displayed.

So the decimal equivalent of binary 1010 1010 is 170. Easy, isn’t it!

There are numerous online converters that you can use to convert between binary, decimal and hex. Here are three that you could try. Or you can find your own by entering ‘number base converter’ into your search engine.

Use the activities that follow this video to experiment with one or more of these online tools and also the Windows Calculator if you have access to it.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/44_using_a_calculator.jpg)

         ##-- ENDMEDIACONTENT
    


You’ve seen how you can use the Windows calculator to convert numbers between binary, octal, decimal and hexadecimal number systems. You’ve also been given the links to some online converters.

         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 4 Test yourself</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. Use a calculator/converter to convert the binary number 10101010 into its decimal equivalent, then use the weighting method of converting from binary to decimal (explained in Section 8.1) to check that you arrive at the same result. (Here you will need to extend your weighting to 28 = 128.)

The calculator/converter should have given you the answer 170. Using the weighting method your calculations should have been: (1×128) + (0×64) + (1×32) + (0×16) + (1×8) + (0×4) + (1×2) + (0×1) = 128 + 32 + 8 + 2 = 170.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. What is the largest decimal number that could be represented by a 16-symbol binary number? Use a calculator/converter to find out.

You will need to enter 1111 1111 1111 1111 as the binary number. Your calculator/converter should show you the decimal equivalent 65,535.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. What is the hexadecimal equivalent of the binary number 1111 1111 1111 1111? Use a calculator/converter to find out.

Your calculator/converter should show you the hexadecimal number FFFF.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 7.3 Representation of IP and MAC addresses


This part explains how the binary numbers of an IP address and a MAC address are represented to be more readable for humans. There are two videos in this part – each video is followed by an activity.

Watch the video below, which is about 4 minutes long.

Note that at 00:45 the speaker says ‘provides nearly 4 million 3 hundred different addresses’, but meant to say ‘provides nearly 4.3 billion addresses’.


### IP addresses

         ##-- MEDIACONTENT
        
Hello. Now you’re familiar with the idea of representing numbers with different number bases, we’ll have a closer look at how network addresses are represented. In this video I’ll look at IP addresses, specifically IP version 4 addresses and in the next video I’ll look at MAC addresses.

Remember we started off this session in Part 1 with a reminder of what an IP address and a MAC address look like.

Computers can only recognise these addresses as a series of zeros and ones, but humans find long strings of zeros and ones difficult to read and interpret so this is why we represent them in this way. 

An IPv4 address is in fact a 32-bit binary number which, as you know from Part 1, provides nearly 4 million 3 hundred different addresses.

But let’s just focus on the IP address. To a computer, this would look like this.

You can see how difficult it is to read this number, so for convenience I’ll show the 32 binary numbers in groups of four bits.

When representing an IP address as a decimal number, we actually deal with these groups in pairs. This gives us four groups of eight bits. A group of 8 bits is often referred to as an octet. So here we have four octets. What’s the highest decimal number we can represent using 8 bits? Well, the highest 8-bit number has a 1 in every place. What would this be in decimal? We could go for the easy way of answering this question which would be to use a binary-to-decimal converter – maybe one of those I showed you in Part 2 of this session. 

Or we could calculate it ourselves using the weighting system I discussed in Part 1 of this session. Because there’s a 1 in each position this would result in adding together 2 to the seven, 2 to the six, 2 to the five, 2 to the four, 2 to the three, 2 to the two, 2 to the one and 2 to the zero giving 255.

But there’s a quicker way than this. 8 binary bits enables us to represent 2 to the eight different decimal numbers. That equals 256 in total. One of these numbers will, of course be a zero, making it 255 as the highest decimal number we can represent with a group of 8 bits.

So that’s 2 to the eight minus 1 equals 255. So 255 is the highest decimal number we can represent using 8 binary bits.

This provides us with a neat and easy way of working out the highest decimal number we can represent with any given number of binary bits. It will be 2 to the *n*, minus 1, where *n* is the number of binary bits.

But I’ve digressed – a little bit! Let’s go back to that IP address.

The final step in translating the 32 binary bits into the dotted decimal equivalent is to convert each of these four octets into a decimal number. These are then shown together separated by dots as you can see in this example IP address here.

This representation is known as dotted decimal.

In the next video we’ll look at the representation of a MAC address.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/45_ip_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 5 Test yourself</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

What is the highest decimal number that could be represented by 10 binary symbols? (Hint: use the formula introduced in the video.)

The formula is 2*n* − 1. You need to substitute a 10 for the n in the exponent. This gives 210 − 1 = 1024 − 1 = 1023.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 3 minutes long.


### MAC addresses

         ##-- MEDIACONTENT
        
Now we’ll turn our attention to the MAC address.

A MAC address (sometimes called the hardware address or physical address) is also a string of binary numbers. A MAC address is a 48-bit binary number– 16 bits longer than an IPv4 address – giving it 6 octets rather than the 4 octets in an IPv4 address.

Though these could also be represented in dotted decimal, it’s more efficient to use a different number base: base 16 (hexadecimal). Using hexadecimal it’s possible to represent an octet as a group of two symbols rather than the group of three symbols required by decimal.

Hexadecimal follows the same rules as the previous number bases we’ve discussed, but this time the weightings are made in multiples of 16.

Of course, we don’t have 16 different number symbols, so we borrow some from the alphabet to make up the difference. Here are the symbols and their decimal equivalents.

So you can see that when we get to the hexadecimal equivalent of 10 we’ve borrowed an A from the alphabet and so on. Looking at the example MAC address given earlier, you’ll see some of these letter symbols.

So what is the highest decimal number we could represent with a group of two hexadecimal symbols? Well, here’s where that formula comes in again: the one I gave you to work out the highest decimal number that can be represented using a group of binary bits. 

But here we’re using hexadecimal symbols not binary, so we substitute 16 for 2.

And the question I asked was ‘What’s the highest decimal number we could represent with a group of *two* hexadecimal symbols?’ so we substitute 2 for *n* in the exponent, giving us 16 squared minus 1. Result: 256 minus 1 equals 255.

So whereas we needed to use 8 binary bits to represent a decimal number of up to 255, we only need two hexadecimal symbols to do the same job. Or, to put it another way, a binary octet (8 bits) can be represented either by three decimal symbols or two hexadecimal symbols. Hexadecimal is therefore more efficient, especially when representing large numbers such as MAC addresses. 

So a MAC address consists of six pairs of hexadecimal numbers, usually separated by a hyphen but sometimes you will see them separated by a colon. Each pair represents one binary octet.

You may be wondering why, if it’s more efficient, we don’t express IP addresses in hexadecimal too. I’ve wondered that myself. I think the answer is that it just comes down to convention.

So, you’ve seen that an IP address is a 32-bit binary number that we represent as four 3-digit decimal numbers, separated by dots, and a MAC address is a 48-bit binary number that we represent as six 2-digit hexadecimal numbers, usually separated by hyphens.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/46_mac_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 6 Test yourself</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. What is the decimal equivalent of hexadecimal D?

D is the hexadecimal equivalent of decimal 13.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Use the Windows calculator or an online converter to ascertain the highest possible MAC address. (Hint: it’s easier to enter this in hexadecimal rather than 48 binary bits.)

You know that 48 binary bits of a MAC address are represented by 6 pairs of hexadecimal numbers. The highest hexadecimal number is F so you will need to enter F twelve times: FF FF FF FF FF FF. This will produce the decimal equivalent 281,474,976,710,655.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. If instead the highest MAC address was represented in dotted decimal, what would it be? (Hint: the highest MAC address in binary has a 1 in every place.)

The highest binary number for any given number of bits would have a 1 in every place. 48 bits would be 6 octets and the highest decimal number that can be represented by a binary octet is 255. Therefore, if this were to be represented in dotted decimal it would be 255.255.255.255.255.255.

Note: in many other contexts 8 bits are referred to as a byte, but in the context of MAC addressing it is more normal to refer to 8 bits as an octet.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 7.4 Subnet masks and CIDR


In this part you’ll revisit subnet masks but in a little more depth than you’ve seen previously. This will reinforce and extend your understanding of how the subnet mask indicates ‘network’ parts of the IP address and ‘host’ parts. You’ll also learn how a process called Classless Inter-Domain Routing (abbreviated as CIDR) achieves more efficient use of available network addresses in the IPv4 addressing scheme.

There are four videos in this part – each video is followed by an activity.

Watch the video below, which is about 3 minutes long.


### Revision

         ##-- MEDIACONTENT
        
You’ve met subnet masks at various places in the preceding sessions and particularly in Session 1 and Session 2. This video is just a brief reminder of what you already know about them.

You know that an IPv4 address is represented as four decimal numbers separated by dots like the example here, but that this is just a representation that makes it easy for humans to understand. It’s really a group of 32 binary digits, or bits, made up of four octets with each octet translated into a decimal number.

This shows the 32 bits for our example IP address. You also know from your study of Sessions 1 and 2 that an IP address has two components. The part to the left identifies the network a device is attached to. This part is known as the network part.

The part to the right uniquely identifies the device that is attached to the network. This part is known as the device part or, more commonly, the host part. I’ll stick to the term ‘host’ from now on. 

The subnet mask identifies where the boundary between the network part and the host part lies.

The subnet mask looks a bit like an IP address in that it is also four decimal numbers separated by dots, but these decimal numbers are either 255 or 0. This is an example subnet mask.

Where there’s a 255 in the mask it means that the corresponding decimal number in the IP address is a network part and that this number mustn’t be altered on this network. A zero in the mask means that the corresponding decimal number in the address is a host part and this can be varied.

So with a subnet mask of 255.255.255.0, 192.168.2 is the network part and 100 is the host part.

You also know from Session 2 that the number of octets used by each part is variable. For example, the network part could be two octets long with a two octet host. So with a subnet mask of 255.255.0.0 the network part in our example would be 192.168 and the host part would be 2.100.

Now try the activities that follow this video to complete your revision.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/47_revision.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 7 Test yourself</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

Identify the true statement from the options below for the IP address 192.168.2.10 with its subnet mask of 255.255.255.0.

The host portion of the IP address is 192.168.2.

Incorrect. 192.168.2 is the network part of the address, indicated by the presence of 255 in the equivalent portion of the subnet mask.

The IP address 192.168.2.254 is in the same network.

Correct. All IP addresses that start 192.168.2 are in the same network.

The maximum number of device addresses on this network is less than 10.

Incorrect. The available addresses start at 192.168.2.0 (which is the network address) and finish at 192.168.2.255 (which is the broadcast address) so the maximum number of device addresses is 254.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 3 minutes long.


### Classful and classless addresses

         ##-- MEDIACONTENT
        
In this video I’m going take a closer look at subnet masks and introduce you to a system called Classless Inter-Domain Routing. I’m going to start with a bit of history.

When the IP addressing scheme was first developed, subnet masks weren’t used. Instead the address space was divided into five classes: A, B, C, D and E.

Class A addresses were indicated by a zero in the leading bit of the address (that is, the left-most bit) and provided 128 separate networks, each with over 16 million different addresses.

Class B addresses were indicated by one-zero in the two leading bits of the address, giving 16,346 networks each with over 65,000 different addresses.

Class C networks had one-one-zero in their three leading bits and could provide over 2 million separate networks each with 256 different addresses.

Class D addresses were used for broadcasting, and Class E addresses were reserved for future use. 

By the way, for this this course you won’t need to remember any of the details shown here but they do help to provide a foundation for what I’m going to explain next.

One of the problems with this early addressing scheme (now known as ‘classful addressing’) is that the smallest allocation (a Class C address) provided only 256 host addresses whereas the next size up had 65,536. For some small organisations 256 address were more than enough but for others they weren’t. However, the 65,000 or so provided in the next size allocation (Class B addresses) were far, far too many so network addresses were being wasted and Class B addresses were starting to run out.

The answer to both these problems is Classless Inter-Domain Routing, abbreviated as CIDR (but pronounced ‘cider’). CIDRider eliminates the previous octet boundaries (8, 16 and 24) of classful addressing by allowing fluidity between the network portion and the host portion of the address. I’ll explain how this works.

Look again at the IP address 192.168.2.0 and its subnet mask 255.255.255.0.

By writing them out in binary and putting one below the other, you can see that the only portion of relevance to the subnet mask is where all the bits have a one in them. These are always contiguous and start from the left. So a subnet mask can just be expressed by counting up these bits. By convention this is shown with a forward slash followed by the number of bits with a one in them.

In this example there are 24 is in the subnet mask. This would be forward-slash-twenty-four and the complete network address / subnet mask pair could be expressed as 192.168.2.0/24.

This provides a convenient shorthand which is known as CIDR notation.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/48_classful_and_classless_addresses.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 8 Test yourself</h1>
*5 minutes*

         ##-- ITQ
        

#### Question

1. In the old classful addressing system, if an organisation needed 1500 network addresses, roughly how many network addresses from their allocation block would have been wasted?

The organisation would have been given a Class B address block with just over 65,500 addresses as a Class C address block (256 addresses) would have been too small. Therefore about 64,000 addresses would have been wasted.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. Express the following in CIDR notation:

* IP address: 192.168.100.0IP address: 192.168.100.0

* Subnet mast: 255.255.0.0Subnet mast: 255.255.0.0

The subnet mask indicates that there are 16 bits in the network address, therefore in CIDR notation the IP address would be expressed as 192.168.100.0/16.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 2 minutes long.


### CIDR

         ##-- MEDIACONTENT
        
In the last video you saw how CIDR notation enables fluidity between the rigid octet boundaries of the old classful addressing system. This has provided a way to make networks more scalable, so the old Class B addresses could be broken down into smaller allocations. Let me show you how this works.

I’ll demonstrate it with a simple example. I’ll use the network address 192.168.0.0 with a subnet mask of 255.255.255.0 and show both in binary. You can see that this provides 8 bits for the host portion (all those bits shown grey here).

Now, if we were to take two bits from the network portion and add it to the host portion, this would result in a network portion of 22 bits and a host portion of 10 bits giving 1024 addresses –four times as many as the old Class C addresses.

Now look at the third octet of bits in the subnet mask. This is 1111 1100. Your studies in the previous parts of this session should have enabled you to translate this into the decimal equivalent of 252, so in dotted decimal the subnet mask would be expressed as 255.255.252.0 or in CIDR notation as /22.

By the way, although 192.168.0.0 is a perfectly legitimate network address, it’s seldom used for reasons that I won’t go into here. I just used this address because it provided a convenient demonstration.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/49_cidr.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 9 Test yourself</h1>
*1 minute*

         ##-- ITQ
        

#### Question

What is the size of the host portion of the following IP address (expressed in CIDR notation): 192.168.10.0/24?

/24 indicates that there are 24 bits in the network portion of the address. Therefore there must be 8 bits in the host portion.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    
Watch the video below, which is about 4 minutes long.


### Subnetting with CIDR

         ##-- MEDIACONTENT
        
In the previous video, you saw how CIDR provided a way to subdivide the network allocation boundaries of the old classful system into smaller chunks, resulting in more scaleable networks and less waste of network addresses. But other benefits arise from being able to subdivide networks into smaller portions. Remember that subnetting with CIDR is simply a method of dividing a block of IP addresses into smaller portions which can be operated as independent networks. This means that network managers can subdivide their networks to provide separation between different departments and functions.

In fact there are many advantages to separating out a network into smaller subnetworks. It can lead to an increase in reliability as technical problems in one subnet won’t affect other subnets. It helps with security as sensitive data can be restricted. Administration also becomes simpler and network traffic is reduced as broadcasts can be contained in smaller domains.

So I’ll briefly demonstrate how CIDR can be used to divide a network with 256 network addresses into smaller subnetworks. Let’s go back to that network address of 192.168.2.0. Here it is with the binary version, shown in red, and here’s the binary version, shown in blue, of the original subnet mask 255.255.255.0.

This subnet mask tells us that the first 24 bits give the network part of the address, and the last 8 bits give the host part. This network can provide 256 host addresses starting with the address 192.168.2.0 and ending with the address 192.168.2.255. You already know that 192.168.2.0 is, of course, the network address and 192.168.2.255 is the broadcast address for this network, so this leaves 254 available device addresses.

Now, here’s a new subnet mask of 255.255.255.192 where we have taken two bits from the host address portion. This subnet mask tells us that there are now 26 bits in the network part and 6 bits in the host part.

Here are the addresses of the four newly created subnetworks. Each of these has a host portion of 6 bits providing 64 network addresses.

So, taking the top network, it has a network address of 192.168.2.0. It can provide 62 device addresses starting 192.168.2.1 and ending 192.168.2.62. Its broadcast address will be 192.168.2.63.

The next network has a network of address of 192.168.2.64 and it also has a host portion of 6 bits and can provide 62 devices addresses, and so on.

So effectively, the previous 8-bit host address space which provided 256 different addresses has now been divided into four separate subnetworks each with a 6-bit host address (shown in black) and each providing 64 different network addresses.

The overarching network address of the organisation remains the same: 192.168.2.0. You can see that all the numbers in the first 24 bits of the IP address remain unchanged. But within the organisation, CIDR has enabled the original 256 network addresses to be split into four separate and independent subnetworks.

So, just to summarise. The old classful method of indicating the network and host portions of an IP address was very rigid allowing boundaries to be placed only between octets. Classless Inter-Domain Routing (CIDR) removed the previous octet boundaries and enables scalability of networks. This helps to conserve network addresses and enables subdivision within networks.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/50_subnetting_with_cidr.jpg)

         ##-- ENDMEDIACONTENT
    


         ##-- EXAMPLE
        <h1 xmlns:str="http://exslt.org/strings">Activity 10 Test yourself</h1>
*5 minutes*

Imagine you are a network manager who has been allocated an IP address block of 512 addresses.

         ##-- ITQ
        

#### Question

1. What would be the CIDR notation for your network?

A block of 512 addresses would have 9 bits in the host portion (29 = 512). This would mean that the network portion would be 32 − 9 = 23 bits. Therefore the CIDR notation would be /23.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

2. How many subnetworks with 128 addresses would you be able to create?

512/128 = 4, therefore four subnets would be possible.

         ##-- ENDITQ
    
         ##-- ITQ
        

#### Question

3. What would be the CIDR notation for each of these four new subnets?

128 addresses in the host portion would require 7 bits (27 = 128), leaving 25 bits in the network portion. Therefore the CIDR notation would be /25.

         ##-- ENDITQ
    
         ##-- ENDEXAMPLE
    

## 7.5 Summary of Session 7


In this part you’ve explored two number systems: decimal and binary. Through this exploration you’ve seen how counting can be done using a set quantity of symbols: 10 for the decimal system and 2 for the binary system. You’ve been introduced to the idea that other symbol sets can be used such as base 16 (hexadecimal) which you will meet later in the course. You’ve also seen how exponential notation can be used to signify the weighting applied to each symbol in a series of symbols representing large numbers. This can be used as mathematical shorthand to express large numbers.

You’ve been reminded that an IP address consists of a network portion and a host portion and that a subnet mask is used to indicate where the boundary between the two lies. You’ve seen how the use of Classless Inter-Domain Routing (CIDR) eliminates the previous octet boundaries of the subnet mask and by doing so makes more efficient use of network addresses. Finally, you’ve also seen how CIDR enables networks to be split into subnetworks for more efficient network management.

---


### New terms

In this session you have met the following terms.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<td class="highlight_" rowspan="" colspan="">
binary number system
</td>
<td class="highlight_" rowspan="" colspan="">
A number system based on two symbols: 0 and 1.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
CIDR notation
</td>
<td class="highlight_" rowspan="" colspan="">
A notation used to indicate the size of the network portion in an IP address.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
classful addressing
</td>
<td class="highlight_" rowspan="" colspan="">
An early IP addressing scheme in which the available network addresses were divided into five classes – A, B, C, D and E – based on octet boundaries.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
classless addressing
</td>
<td class="highlight_" rowspan="" colspan="">
The generic term used to describe the later IP addressing scheme in which the number of bits in the network portion became variable rather than fixed.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Classless Inter-Domain Routing (CIDR)
</td>
<td class="highlight_" rowspan="" colspan="">
The name by which the classless addressing scheme is known.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
decimal number system
</td>
<td class="highlight_" rowspan="" colspan="">
A number system based on ten symbols: 0, 1, 2, 3, 4, 5, 6, 7, 8 and 9.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
exponential notation
</td>
<td class="highlight_" rowspan="" colspan="">
A mathematical shorthand for representing large numbers, also known as ‘scientific notation’.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
hexadecimal
</td>
<td class="highlight_" rowspan="" colspan="">
A number system based on sixteen symbols: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
octet
</td>
<td class="highlight_" rowspan="" colspan="">
A group of eight bits.
</td>
</tr>
</tbody>
</table>

---

