# Introduction

Time Spent : 3 hours

I started this lab by using AI to generate a simple set of needed devices to create a network topology
for a VLAN lab. I set up three switches in order to practice understanding how VLANs communicate between one another.
I have a router connected to the central switch (S1), and PC1 and PC2 are connected independently to each seperate switch connected 
to the central switch.

# Diagram

<img width="1120" height="784" alt="Screenshot 2026-05-26 at 12 17 45 PM" src="https://github.com/user-attachments/assets/8e5447fc-e071-4ee9-af35-3ac69f855f57" />


This diagram was changed in the actually topology slightly. It was my first one. 

# Issues and Troubleshooting

1. The first issue I ran into was understanding the intial commands needed to set up the router. I learned this, but it had been a while since
I did it from scratch. I was able to figure it out once I looked up a couple of the commands to refresh my memory. I set the IP to 192.168.10.1.
I made sure to use no shutdown to ensure the interface's protocol was up.

2. The second major issue I had was that when I set up my switches, I used both access ports and trunk ports. So this caused a confliction in my configuration. I had to disable access ports for all of my internal switch connections. Without realizing though, I set my PC connections to trunk as well. So I had to change those back to access ports.

3. The third issue I had was a mismatch in my VLANs. I did not have consistent VLAN naming scemes in all of my switches. So I went through each switch and checked the VLAN briefs to ensure that each switch had access to both of my VLANs.

4. The fourth issue I had was figuring out how to set up sub channels on my router to ensure my VLANs were recognized by the router. So through researching the proper commands I created two seperate sub channels for my two VLANs on the router.

5. The fifth issue I had was a router IP issue. I had my router set to a regular IP even though I had VLANs as well. I did not understand why this caused issues until later on in the troublshooting process. My PCs had their gateways set to the default router IP, "192.168.10.1". So when I was pinging I did not realize this was a part of my issue. So I went through and took out the default router IP and left the sub channels only. This allowed the network to connect using both VLANs without IP mismatch.

6. The last major issue I came across is what led me to a working network. I didn't have a native channel for untagged traffic. I had to research to understand what this meant and why I needed it. I had already assigned sub channels for my VLANs, but those channels, when met with untagged traffic, did not understand what to do with it. So I had to create another sub channel, but using the native sub-interface command. This was needed in order for my network topology to work because otherwise, my router wouldn't know what to do with untagged traffic. I assigned it to VLAN1, which is the default Cisco VLAN that takes care of untagged traffic.

# What I learned

I learned a lot in this simple VLAN lab. I learned the difference in Trunk and Access ports and why both cannot work at the same time and why both are important. I learned many new commands in CLI that I will continue to learn about and use frequently. I learned and now understand the importance of ensuring that names for VLANs are the same across all devices. I learned how to create sub-interfaces on a router and why the router needs them. I learned how to set up a router properly without dealing with IP mismatches. I learned the concept of why routers need subchannels, and especially those that can divert untagged traffic in the right direction. 

# Commands learned

- show vlan brief
- show trunk interfaces brief
- show ip interface brief
- encapsulation dot1Q 1 native
- encapsulation dot1Q #
- switchport mode access
- switchport access vlan #
- switchport mode trunk
