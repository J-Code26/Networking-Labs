## Introduction

This notes page is for my first real hands-on networking experience

## Network Gear

1. Cisco Catalyst 2960-C PoE
2. Console Cable (Usb-A to Ethernet)
3. Raspberry Pi Zero

## June 2nd 2026

# Introduction

Today, all of my needed components came in. I bought a Cisco Catalyst 2960-C for 40 dollars on ebay. I got a 5-pack of Cat 6e 3ft cables to test with along with a compact extension cable and a nice console cable to get into the switch.

# Notes

To start off, I started up the switch and then realized I did not know how to actually look at the switch CLI. I researched a little and came to using my Mac terminal with the screen function to get directly into my USB port. The screen came up and went through the loading process. Once it got to the point where I needed to press enter, it came up with a username (Great!). It was not reset prior to the seller giving it to me. 

I looked up multiple methods on how to get the switch to reset. I ended up using the mode button to do a full reset and get the swtich to go into the mode I needed it to. It came up with "switch:". With some help, I used the command _flash_init_ to flash the switch. I then used the del command to delete the previous vlan and config files from the previous owner. Once this was done I used the _boot_ command to reboot the switch. 

After waiting for a few minutes, I got into the initial set up prompt. I said no to the initial setup and proceeded to do a routine switch setup like in CPT. 

Using these commands:
 - enable
 - configure terminal
 - hostname Home-Switch
 - enable secret #$%@#$%^%#$%^&
 - interface vlan 1
 - ip 192.168.*.*** ***.***.***.0
 - no shutdown
 - exit
 - end
 - write memory

After all of that, leaving out a couple of commands, I ended up plugging in an ethernet cable to my linux computer to the first port (FasteEthernet0/1). I first configured it and used the command _switchport mode access_ and then proceeded to create a manuel IPv4 setting on my linux computer. Once that was set up (After a few troubleshooting issues), I was able to successfully ping my switches IP from my linux computer, making my first physical ping test with a managed switch. Awesome!
