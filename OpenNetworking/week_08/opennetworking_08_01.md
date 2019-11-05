# Session 15: Security



![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/15_authentication.tif)

In this session you will learn how to make a router secure. Routers, because they are networked devices, can easily be configured remotely. However, this makes them vulnerable to cyber-attack unless they are properly secured.

Because all network traffic passes through a router, an attack on the router could allow traffic to be read or to be blocked, denying service to many users. They are therefore tempting targets for a malicious hacker. As a network engineer, you should understand the need for cybersecurity, and know the commands required to configure a router so that it is secure against threats.

This session concentrates on routers but other enterprise network equipment, such as advanced switches, can be accessed remotely and so the same security considerations also apply to them.

By the end of this session, you will be able to:

* configure passwords for authorised usersconfigure passwords for authorised users

* configure secure remote access to a router.configure secure remote access to a router.


## 15.1 Securing the console


The console port means that anyone who has physical access to the router could connect to it. In the early days of the internet, routers were found only in machine rooms behind locked doors, and this was sufficient security. Nowadays they are more likely to be found in the corner of an office, or in server rooms and datacentres where engineers from different companies may have access. So a first step in securing a router is to make sure that access to the console is always protected with a password.

Watch the video below, which is about 3 minutes long. You will see how commands can be used to set a log-in password for the router console and also to protect the console port itself.


### Securing the console

         ##-- MEDIACONTENT
        
So what can we do to secure our router? Well, whether we connect directly through the console port or over the internet, we will end up at the console so let’s make sure the user needs to log in by giving a password.

For a Cisco router, the first level of access isn’t secure – but you can’t do much except check the status of the router. To do anything useful – or dangerous – we need to enter privilege exec mode using the `enable`command, and this is the step that we can protect with a password.

There are actually two ways of doing this. I’ll show you the better way, which is to enter the command `enable secret`` and then the new password ``opennetlab`. I’ll exit from privilege exec mode, and then re-enter it. You can see I am being asked for a password, which I can give, and now I’m successfully in.

I mentioned that there was another way of doing this, but that has a fairly basic flaw because the password is simply stored in the running configuration and could be easily read over my shoulder! But if I display the running configuration, you can see that the `enable secret` command stored the password in an encrypted form, which can’t easily be used.

We can go a bit further and prevent access to the console port itself, so anyone trying to plug in directly will have to give another password. To do this we enter line configuration mode, type `line console 0`, and now we set a password using `password onlcon`. We also need to tell the router to check for a password using the command `login`.

I’m going to test this by exiting and then reopening the console. Remember that this simulates me plugging in my laptop through a cable to the console port of the router. You can see now that the router is prompting me for a password, which I need to give, and then I am back into the router.

Let’s show the running configuration again – you can see that the console port password has been stored in plain text! I’ll need to do something to prevent someone seeing the password over my shoulder. This time I have to go back to global configuration mode, enter `service password-encryption`, and this will encrypt the password. Now if we look at the running configuration, we can see it’s unreadable.

A word of warning: don’t believe your passwords are safe now! It is very simple to reverse this type of encryption using online tools such as this website. You can see all I need to do is paste the cipher text in and it immediately tells me the password. You can use much stronger encryption methods, but this is beyond the scope of this course.

Also, anyone with this password can log in: there is only one password for the device and everyone who needs access will have the same password. And given that an engineer may need to access many routers, they will either need a very good memory, or they will need to write down the passwords – hopefully in some secure manner and not in a list on their wall!


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/80_securing_the_console.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 1 Think about


#### Question

*5 minutes*

Assume you bought a new home gateway and a new enterprise router. Out of the box, which is more secure?

A home gateway is preconfigured with a strong, unique administrator password. An enterprise router typically has no preconfigured security, and a network engineer is responsible for configuring it correctly to be secure.




### Activity 2 Try it out


#### Question

*10 minutes*

1. 
Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt15.1a) in a new tab or window so you can read these instructions.

In this activity you will configure the router in the network.


2. 
Open the router’s console


3. 
Enter global configuration mode.


4. 
Set a secret password, for example ‘mysecret’, for the `enable` command


5. 
Exit from the console and re-enter it to confirm that your security measures are in place.


Initially the router is not secure and you can enter global configuration mode by simply typing `enable`.

To set a secret password such as ‘mysecret’ on the `enable` command, enter `enable secret mysecret`.

Now exit from the console connection (by entering `exit` until you return to the initial console ‘&gt;’ prompt). When you now enter global configuration mode with the `enable` command, you will be prompted for the password you gave earlier.

To confirm the password isn’t stored in plain text, use the `show running-config` command; in the output you should spot a line such as `enable secret 5 $1$mERr$QtCDSpd2k7BLWRTGnR35X1` where the string of characters is an encrypted version of the password you entered.




### Activity 3 Sort it out


#### Question

*10 minutes*

A network engineer has started to configure a router with an `enable` password of ‘opennetlab’. Check the configuration and improve it if necessary.

1. 
Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt15.1b) in a new tab or window so you can read these instructions.


2. 
Open the router’s console.


3. 
Enter global configuration mode; you may need the password ‘opennetlab’.


4. 
Check to see if the password is encrypted in the running configuration.


5. 
If necessary, improve the security settings.


6. 
Exit from the console and reopen it to confirm that your security measures are in place.


The router has had a password ‘opennetlab’ set for the `enable` command, but  the `show running-config` command shows the password in plain text.

To remove the plain-text password, enter `no enable password`. To set a secret password that is stored only in encrypted form, enter `enable secret opennetlab`. 

It is also possible to use the `enter service password-encryption` command to encrypt all passwords in the running configuration. However, the encryption used is weaker: sufficient to make it unreadable to a human, but easily cracked by computer.




## 15.2 Remote access with Telnet


Telnet is a protocol that was very widely used to connect remotely to computers and other devices including routers. Because it is not secure, it should no longer be used over the internet, but it is easy to configure and still used internally within companies and for legacy equipment.

Watch the video below, which is about 3 minutes long. You will see how Telnet can be used to connect to a router, how to protect the router with a password and warning message.


### Remote access with Telnet

         ##-- MEDIACONTENT
        
We’ve now seen how we can connect to the router’s console directly through the console port; now we’ll see how I can connect over the network.

At this stage I am going to use Telnet – it is simple, still used internally and for legacy devices, but isn’t secure.

I’m going to connect from a PC on the same LAN: traffic won’t be going over the internet so the lack of security isn’t too great a problem. I’ve opened a command prompt and now use the command `telnet`and then the IP address of the router `192.168.1.1`.

And it doesn’t let me in! This is because Cisco routers are set up by default to require a login for Telnet – but since I haven’t yet set a password, the login is going to fail.

So back to the router console window where I can setup the password. In global configuration mode, enter the command `line vty` – vty stands for virtual teletypes which is how it refers to terminal connections. Routers can support a number of simultaneous connections. I want to configure them all, so I’ll type `0` then a question mark ?so that the router will tell me the maximum it supports, which turns out to be 0 through 15, that is 16 in total. Now we are configuring all 16 vty lines. And I add a password with `password onlvty`.

I can do one more thing. I can get the router to display a message whenever someone tries to connect. I’m back in global configuration mode and now I’ll use the command `banner motd` (motd means message of the day). To enter my message, I need to type some character at the start – the same one will be used to end the message – I’ll use an exclamation mark. So I’ve entered `! Authorised users only, please !` Now a hacker can’t claim ‘Well, the door was open so I just wandered in …’.

Let me test by Telnetting from my PC again. I’ll enter `telnet 192.168.1.1`and this time I can see a banner message telling me I must be authorised. I am and I know the password, which was `onlvty`, so now I’m back in to the router’s console.

I said earlier that Telnet is insecure because the characters are sent over the wire in plain text form. This means that packet capture software like Wireshark for example, which is a really useful tool for diagnosing network problems, can easily show all the text in a Telnet session. You can see from this screenshot. Everything we did in the Telnet session was captured – including the password we logged in with!


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/81_remote_access_with_telnet.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 4 Try it out


#### Question

*10 minutes*

1. 
Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt15.2) in a new tab or window so you can read these instructions.

In this activity you will configure the router in the network to accept a Telnet connection from the PC.


2. 
Open the router console and enter global configuration mode using the password ‘opennetlab’.


3. 
Configure the virtual teletypes (vty) with the password ‘onlvty’.


4. 
Set a message of the day.


5. 
Now open the PC command line and check that you can ping from the PC (192.168.0.100) to the router (192.168.0.1).


6. 
Open a Telnet session by entering the command `telnet 192.168.0.1`, giving the appropriate password.


7. 
Confirm that you are connected to the router by entering global configuration mode and entering the command `show running-configuration`.


8. 
Finish the Telnet session by entering `exit`.


The router will accept Telnet connections from a PC or other remote device; the router considers these to be ‘virtual teletypes’. For security, a password must be given before a connection is allowed.

To configure the virtual teletypes, enter the command `line vty 0 15` (the range depends on the particular model of router). Then enter `password onlvty` to set the password to ‘onlvty’.

In global configuration mode, set a message of the day with a command such as `banner motd !Authorised users only, please!`.

This completes the setup for the router. To test the connection, you will need to turn to the command line on the PC. You can first confirm that the PC is connected to the router with a ping.

Then to open a Telnet session, you should enter the command `telnet 192.168.0.1`, giving the password ‘onlvty’ which you previously set on the router. You will see the message of the day and the prompt will change to ‘Router&gt;’ showing that you are now giving commands to the router.

You can now work with the router’s command line, for example entering global configuration mode (you will need the password ‘opennetlab’) and show the running configuration.

You should exit from the Telnet session using `exit`.

Confirm that you are back on the PC command line by checking the prompt and using commands such as `ipconfig`.




## 15.3 Secure shell access


Secure Shell (SSH) is a protocol, similar to Telnet, for remote access to computers and other devices. Unlike Telnet, SSH is secure because all traffic is encrypted, and it is essential to use it for remote access over the internet. SSH uses the same type of encryption as secure websites.

Watch the video below, which is about 3 minutes long. You will see how to generate SSH keys and to configure the router only to accept connections from particular users.


### Secure shell access

         ##-- MEDIACONTENT
        
Telnet is an insecure protocol for connecting to terminals – SSH, or Secure Shell, should be used instead wherever you need to make a connection over the internet because all the data that travels over the network is encrypted. It is a bit more trouble to configure, but an essential stage in making your router properly secure.

I am going to get the router to generate some cryptographic keys that will be used to set up encrypted connections. Before I do that, I need to make sure that the router has been given a host name. To do this, we go to global configuration and use the command `hostname ONLRouter1`. I also need to add a domain name – this would be the domain name offor whatever organisation owns the router but I am going to use `example.com`. From global configuration, I will use the command `ip domain-name example.com`.

Now I can go ahead and create the keys that SSH will use. I will use the command `crypto key generate rsa`, then I will choose a key size – the bigger the number the more complex and secure the key becomes – I will use 2048, although it will take a while to be generated by the router. The key generation uses the host and domain name, which is why I had to set that up first. The new key is unique to that router, so the bad guys can’t setup another router and pretend to be me.

I need to do several more things to make the security as tight as a I can.

First I am going to set up an individual user for the router with their own password, rather than have a shared password for all users. From global configuration mode, type `user`then the username, so `jason`, followed by `secret`and the user’s password, `onlssh`.

Secondly, I’m going to set the vty line to use the new configuration, so use `line vty 0 15`. To make this use the username I created, I will enter `login local`.

Finally, to force SSH to be used, I’ll use the command `transport input ssh` – this will disable Telnet and force the users to use SSH.

Let’s test our configuration. I’ll try first to Telnet from the PC to the router – as you can see I get ‘denied access’ with the network error ‘connection refused’.

Now I’ll try SSH. The command for that is `ssh -l` followed by the username, so `jason`, and then followed by the IP address of the router, which is `192.168.1.1`. I’m now prompted for my password, which if I remember correctly was `onlssh`. You can see the banner I made earlier.

If you’re using PuTTY to connect to a real router, you’ll get a key caching message like this one. If you’re sure you have the correct IP for the router then you can answer ‘Yes’ and you won’t receive this message again.

Now I’ve made my router as secure as possible. Only specified individuals can log in, they must know their password, and they must use SSH. If we look at a packet capture of the SSH session, you will see the data is encrypted and we can no longer see the passwords; SSH encryption is very strong and effectively unbreakable.


![](https://www.open.edu/openlearn/ocw/pluginfile.php/1625457/mod_oucontent/oucontent/92007/82_secure_shell_access.jpg)

         ##-- ENDMEDIACONTENT
    



### Activity 5 Try it out


#### Question

*10 minutes*

1. 
Open [PT Anywhere](https://forge.kmi.open.ac.uk/pt15.3) in a new tab or window so you can read these instructions.

In this activity you will configure the router in the network to only accept SSH connections from the PC.


2. 
Open the router console and enter global configuration mode using the password ‘opennetlab’.


3. 
Set the hostname and domain name as ‘ONLRouter1’ and ‘example.com’.

Generate the SSH keys with a size of 2048.


4. 
Create a username, either ‘jason’ or your own name, with a secret password such as ‘onlssh’.


5. 
Make sure that SSH is used rather than Telnet for connections.


6. 
Now open the PC command line and start an SSH session to the router, giving the appropriate password.


7. 
Confirm that you are connected to the router.


8. 
Finish the SSH session by entering `exit`.


9. 
Confirm that you can no longer connect to the router using Telnet.


Some configuration is required before SSH can be used. A set of keys must be generated on the router, and this will use information such as the router name and a domain name to generate unique keys.

Open the router console window and enter global configuration mode. Set the hostname with the command `hostname ONLRouter1` and the domain name with command `ip domain-name example.com`. (You would replace these by appropriate names in a real installation.)

Use the command `crypto key generate rsa`, giving an appropriate key size such as 2048, to create the keys.

To create a user account with a secret password, enter a command such as `username jason secret onlssh`.

To ensure that only SSH is accepted for connection, the vty lines must be configured with a sequence of commands. First, use `line vty 0 15` to enter line configuration mode. Then `login local` will require a username to be given, and `transport input ssh` will mean that only SSH connections are accepted.

This completes the setup for the router. To test the connection, you will need to turn to the command line on the PC.

To open an SSH session, you should enter the command `ssh -l jason 192.168.0.1`, giving the password ‘onlvty’ which you previously set on the router. You will see the message of the day and the prompt will change to ‘Router&gt;’ showing that you are now giving commands to the router.

You can now work with the router’s command line, for example entering global configuration mode (you will need the password ‘opennetlab’) and show the running configuration.

You should exit from the SSH session using `exit` and confirm that you are back on the PC command line.




## 15.4 Summary of Session 15


In this session you’ve seen a variety of ways in which security for a router can be improved.

You have seen that enterprise routers allow a network engineer to connect in two ways: with a direct connection to a special console port, or over the network. Passwords can be set to control access to both of these. When a remote connection is made over the internet, a secure communication protocol such as SSH should be used to prevent an eavesdropper from reading passwords.

A message can be configured to warn that only authorised users can connect. Separate passwords can be applied to protect access to the console port and to network access through virtual teletypes.

The command-line interface on Cisco routers can be password protected, requiring the user to enter the correct password to enter further configuration commands. This applies whichever method is used to connect to the router.

You have also seen that security is difficult to get right. Possible weaknesses are storing passwords as plain text in configuration files, or using unencrypted Telnet for remote access. A network engineer should be alert to problems such as these and know ways to avoid them – for example, by adding encryption to passwords and by requiring SSH instead of Telnet for remote access.

---


### Commands

In this session you have used the following commands.
<table xmlns:str="http://exslt.org/strings">
<caption></caption>
<tbody>
<tr>
<th>Command</th>
<th>Mode</th>
<th>Command prompt</th>
<th>Purpose</th>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`enable secret *&lt;password&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)`</td>
<td class="highlight_" rowspan="" colspan="">To set a password for privileged execution mode</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`banner motd *&lt;sep&gt;&lt;banner&gt;&lt;sep&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)`</td>
<td class="highlight_" rowspan="" colspan="">To set a message of the day</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`service password-encryption`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)`</td>
<td class="highlight_" rowspan="" colspan="">To encrypt passwords stored in the running configuration</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`username *&lt;name&gt;* secret *&lt;password&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)`</td>
<td class="highlight_" rowspan="" colspan="">To create a user account</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`line console 0`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)`</td>
<td class="highlight_" rowspan="" colspan="">To configure the console connection</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`password *&lt;password&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Line configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-line)`</td>
<td class="highlight_" rowspan="" colspan="">To set a password for the console connection</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`login`</td>
<td class="highlight_" rowspan="" colspan="">Line configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-line)`</td>
<td class="highlight_" rowspan="" colspan="">To require login with a password to the console connection</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`line vty 0 *&lt;max&gt;*`</td>
<td class="highlight_" rowspan="" colspan="">Global configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config)`</td>
<td class="highlight_" rowspan="" colspan="">To configure a set of virtual teletype lines</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`login local`</td>
<td class="highlight_" rowspan="" colspan="">Line configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-line)`</td>
<td class="highlight_" rowspan="" colspan="">To require login with a user account name and password</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">`transport input ssh`</td>
<td class="highlight_" rowspan="" colspan="">Line configuration</td>
<td class="highlight_" rowspan="" colspan="">`Router(config-line)`</td>
<td class="highlight_" rowspan="" colspan="">To only accept SSH connections</td>
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
Telnet
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol used for unencrypted remote terminal connections.
</td>
</tr>
<tr>
<td class="highlight_" rowspan="" colspan="">
Secure Shell (SSH)
</td>
<td class="highlight_" rowspan="" colspan="">
A protocol used for encrypted remote terminal connections.
</td>
</tr>
</tbody>
</table>

---

