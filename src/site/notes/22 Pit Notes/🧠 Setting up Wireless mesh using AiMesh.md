---
{"dg-publish":true,"permalink":"/22-pit-notes/setting-up-wireless-mesh-using-ai-mesh/","tags":["pit"]}
---

 
# Summary
- Establishing ASUS AiMesh with AC 89u as main node and AC 5300 (Tri band) and AC 68U as nodes
	- Using wireless backhaul, i.e. routers talk to each other wirelessly
	- When using 5 GHz wireless backhaul with the main router, node broadcasting speed on 5 GHz will be halved as the same signal space is shared between node and main router as well as node and client. 
	- Using AC 86U (dual-band 2.4 and 5) as the main router and AC 5300 (tri band 2.4, 5, 5) helps as AC 5300 can talk to 86U over 5 G as well as talk to its clients over 5G
	- Ended up removing AC 68U as the speeds coming out of it were bad; this could be useful if I am doing a wired node
- To add as an AiMesh node, router needs to be factory reset first (i.e., it cannot have the usual router configurations)
- AC 5300 had to be updated to newer firmware and then factory reset
	- To update new firmware,
		- Setup as a new router using ASUS app, login to internet and then update firmware
	- To factory reset 5300, 
		- press the reset button near ports for 10 seconds OR
		- Power off, Hold the WPS button pressed and turn power on again. Let go of the WPS button once the power led comes back on 
- After reset, search for new Ai node
	- Newly reset routers should show up, and you will be able to add 
- My AiMesh was set to Ethernet backhaul from earlier setup
	- In this mode, new node was always showing offline since they were not wired
- When I turned off Ethernet backhaul (from the computer) both the nodes went offline
	- Note: Use from computer as from the phone app some of these options did not show up
	- To bring them back online needed to re-pair with the main router once backhaul is setup,
		- placed the node near the main router and hooked it up directly to the main router via Ethernet cable
		- Ethernet cable may not be required if nodes are paired properly.
	- Once it is paired via Ethernet cable, removing the cable it stayed connected.
	- At that point I could relocate the router to other places and it stayed connected