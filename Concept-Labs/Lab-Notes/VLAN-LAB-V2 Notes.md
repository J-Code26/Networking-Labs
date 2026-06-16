# Introduction

In the past lab I configured two vlans on three switches with a router and two PCs. For this lab I decided to go back into the same lab and
create an additional VLAN on the switches. I figured this will test both my command memorization and the ability to ensure a configuration is
working properly and is properly set up. 

# Diagram

<img width="1160" height="820" alt="Screenshot 2026-06-16 at 1 10 41 PM" src="https://github.com/user-attachments/assets/2e170e8e-f7b5-4ae3-b600-f41148dc0f45" />

# Issues and Troubleshooting

1. The first issue I ran into is the fact that I do not have these commands memorized yet. I went and research the correct set up CLI commands
   for the switches and wrote them down in my computers notes. I wrote down the commands for setting up a VLAN name, assigning its ports, and
   allowing access to the proper ports on the switch.
2. The second issue I had was working with the router. I forgot how to set up the sub channel so I had to look up those commands again. I
   remembered as soon as I saw it. I created a new sub channel for my VLAN 60.
3. The third issue I had was figuring out why in the world my PCs were not pinging anywhere. I checked the router and all the switches and
   realized that I forgot to set up a VLAN 60 on each of the swtiches and router instead of just one of the switchs(wow). So once I did that it
   still was not working.
4. The fourth and final issue I figured out was that I was using a trunk port on my PC cables. When I did interface range commands, I forgot
   that my PC lines need to be access ports, but have allowed trunk channels for all the VLANs. So I went through and set up access ports for all
   the PC lines and we had connectivity accross the board.

## CLI Screenshots

<img width="670" height="713" alt="Screenshot 2026-06-16 at 12 35 14 PM" src="https://github.com/user-attachments/assets/603d1936-283e-43e1-ab08-8813b194b5b6" />
<img width="674" height="725" alt="Screenshot 2026-06-16 at 12 23 38 PM" src="https://github.com/user-attachments/assets/b13d919c-c5c6-4cee-b26c-c4900aa00346" />
<img width="671" height="722" alt="Screenshot 2026-06-16 at 12 16 55 PM" src="https://github.com/user-attachments/assets/e15e2918-d812-449d-a664-62728f2ba64e" />
<img width="650" height="715" alt="Screenshot 2026-06-16 at 12 15 35 PM" src="https://github.com/user-attachments/assets/d789531b-376a-4392-b324-248111b31b30" />
<img width="670" height="714" alt="Screenshot 2026-06-16 at 12 08 08 PM" src="https://github.com/user-attachments/assets/8a8f6523-405f-4774-bfe9-2f822e00efc5" />
<img width="666" height="714" alt="Screenshot 2026-06-16 at 11 58 22 AM" src="https://github.com/user-attachments/assets/d5323cdd-e5f3-4e18-b690-2f38dd4da9b8" />

# What I learned

In this lab, I learned some more valuable things. Although these lessons were similiar to the lessons in the last lab, I reinforced my knowledge in
commands, setting up switches, routers, ports, and sub channels. I ran into some minor, avoidable issues, but it will help me not make as many of
those mistakes going forward. 

## Commands used -

Setting up a VLAN - 

Switch> enable 
Switch# configure terminal 
Switch(config)# vlan 10 
Switch(config-vlan)# name Sales_Dept 
Switch(config-vlan)# exit

Assiging VLAN ports - 

Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport mode access (Or trunk)
Switch(config-if)# switchport access vlan 10
Switch(config-if)# end

Access to VLAN - 

Switch(config)# interface fastEthernet0/1
Switch(config-if)# switchport trunk allowed van 20,40,60
Switch(config-if)# switchport mode trunk

Setting up router sub channels - 

Router(config)# interface gigabitethernet 0/0.10
Router(config-subif)# encapsulation dot1q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config-subif)# exit

Interface Range - 

Switch(config)# interface range GigabitEthernet 1/0/1 - 24

Remove Access ports - 

Switch(config-if)# no switchport access vlan
Switch(config-if)# no switchport mode access
