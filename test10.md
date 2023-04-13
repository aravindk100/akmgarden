---
type: meeting
aliases: 
subtype: adhoc
status:
notestatus: 
tags: meeting
share: true
---
goal:: [[]]
project:: [[]]

# Running agenda
- [ ] testing project:: [[test10]]

# Open Actions




# Expected Outcome

# Attendees

# Summary

![[Semi Managed Mode and Impact to ADP meeting notes]]

### Raw

#### Mem SS
Top level parameters will drastically change. 
Port changes 
It will be a new IP in IP catalogue
will need to be regenerated.. 
Parameters at the top level should change . Functionally they will equivalent. 

If a customer had done customization, can they get back to the same config? Yes but it is not automated. 

Parameters name may change but if shell is touching the parameter then it will get impacted. 
Shell will have to redo the IP. 

Port change -- 

Will this affect One API? Port that comes in to AFU region will change. Port names are provided by FIM so no impact to One API. 

Presets will be done manually. Even today we provide presets, presets are configured and after that customers can change. 

Ports will change - AXI naming not connected to semi managed mode. There are some redundant ports in SS and we would like to remove it.  Shell will have to rename the ports.. 
- [x] @Ayush will have this list end of week port changes. W3 for internal version and before that if possible. Respond on port change within a week. 
- [x] @Ayush will update the HAS (will provide timeline)

We can keep the old subsystem if needed.. 

Functional version by W3; functional version by code complete for 23.1. 

There are performance issues ( from Quartus side) that are under considered.  

we may not have production ready by 23.1

Will need to poll customers to understand if there are changes in mem configs needed. 

No conversation yet on PVE validation , functionality is not changing.  No LZs for GUI generation time etc. 

#### HSSI SS


same flow 

diff flow -- non PD flow to PD flow.. user 
E To F is not supported
downgrade is not supported

IP with new flow should bre ady by W3 but not enough testing. 
DV expected to close by w8.. 
23.1 production version from there they will not support both the flows. 
- [x] @Anil will provide ppt for flow changes/GUI changes by end of week. 

sub IP parameters will have name changes, but they are writing extra processor to do the conversion. 

No HAS changes are planned for HSSI SS. 

#### PCIe SS

available in 23.1 and non PD flow 23.1 
port name will remain same , parameters will remain same but sub paramaers will exposed.
Hidden in 23.1 but 23.2 it will be public

In IP catalog it will not be used, command line 

It is not a new IP core.. GUI will be different..  customers cannot upgrade IP but they will have to regenerate.. There are no presets today in SS even for non PD flow.  
	
Hierarchy will change but it will be transparent to uses. 

MIF file generation -- no solid plan yet.. 
- [x] @Kay Keat can prepare a screen shot difference between old and new [completion:: 2023-01-05]

PCIe SS .. KK will provide a date. 
# References


# Table of Mentions
| File                                                                                        | type    | status |
| ------------------------------------------------------------------------------------------- | ------- | ------ |
| [[_Projects/Project - AC ADP Sustaining strategy.md\|Project - AC ADP Sustaining strategy]] | project | \-     |





