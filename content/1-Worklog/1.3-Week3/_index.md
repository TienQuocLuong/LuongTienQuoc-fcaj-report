---
title: "Week 3 Worklog"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
Study the advanced labs of Module 02 (DNS Resolution, VPC Peering). Since networking is fairly hard, focused on just a couple of core labs and did them very thoroughly.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 01/05/2026 | Watched the walkthroughs for Lab 10 (DNS Resolution) and Lab 19 (VPC Peering); took notes on the steps and prerequisites before practicing | https://www.youtube.com/watch?v=HACor1gL3ww&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=50  https://www.youtube.com/watch?v=sllYqAECBoM&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=56|
| Saturday | 02/05/2026 | Rewatched both labs carefully, researched Route53 Resolver, Inbound Endpoint, and Private Hosted Zone beforehand to avoid confusion during practice | |
| Sunday | 03/05/2026 | Started practicing Lab 10; the sample CloudFormation template failed to deploy, so had to research how to manually create the Inbound Endpoint instead of using the ready-made script | https://www.youtube.com/watch?v=EQ-5P6U7Ph4&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=47 |
| Monday | 04/05/2026 | Continued Lab 10: configured a Private Hosted Zone and associated it with the VPC to complete the internal DNS resolution part | https://www.youtube.com/watch?v=HACor1gL3ww&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=50 |
| Tuesday | 05/05/2026 | Finished Lab 10; read more material to fully understand how internal domain name resolution works within a VPC | |
| Wednesday | 06/05/2026 | Practiced Lab 19 (VPC Peering): ran into an issue where two EC2 instances in two VPCs couldn't ping each other, used traceroute to trace and find the issue in the Route Table, then fixed it and connected successfully | https://www.youtube.com/watch?v=sllYqAECBoM&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=56 |
| Thursday | 07/05/2026 | Reviewed all the networking content learned; weighed the schedule and decided to set Lab 20 (Transit Gateway) aside to save time for later modules | |

### Week 3 Achievements:
* Completed Lab 10 (DNS Resolution) and Lab 19 (VPC Peering).
* Independently resolved an issue with a failed CloudFormation template by manually configuring the Inbound Endpoint and Private Hosted Zone.
* Understood the internal DNS resolution mechanism within a VPC.
* Learned to use traceroute to diagnose and fix routing errors in VPC Peering.
* Developed the skill of researching and troubleshooting when things don't go exactly as the guide describes.