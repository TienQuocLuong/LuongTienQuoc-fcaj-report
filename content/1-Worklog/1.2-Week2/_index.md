---
title: "Week 2 Worklog"
date: 2026-04-24
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:
Start Module 02 on virtual networking (VPC), learning each component slowly and thoroughly to build a solid networking foundation.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 24/04/2026 | Watched the Module 02 lecture on Amazon VPC; took notes on the overall network architecture and the role of each component (VPC, Subnet, Gateway, Route Table) | awsstudygroup.com (Lab 3) |
| Saturday | 25/04/2026 | Practiced the VPC and Subnet creation part of Lab 3; looked things up along the way to understand CIDR addressing and distinguish Public/Private Subnets | awsstudygroup.com (Lab 3) |
| Sunday | 26/04/2026 | Continued Lab 3: created an Internet Gateway and Route Table, configured routing so the Public Subnet could reach the internet; read more about VPC security | awsstudygroup.com (Lab 3) |
| Monday | 27/04/2026 | Configured Security Groups for Public and Private; initially confused inbound and outbound direction, so redid it a few times and checked each rule carefully until it was clear | awsstudygroup.com (Lab 3) |
| Tuesday | 28/04/2026 | Spent an entire session reviewing all the VPC components learned, drew the network diagram out on paper to solidify how the components connect to each other | |
| Wednesday | 29/04/2026 | Practiced deploying EC2 inside the VPC and configuring an EC2 Instance Connect Endpoint to securely access an instance in the Private Subnet | awsstudygroup.com (Lab 3) |
| Thursday | 30/04/2026 | Verified network connectivity between EC2 instances in the VPC, confirmed Public/Private worked as designed; wrapped up the basic part of Module 02 | |

### Week 2 Achievements:
* Clearly understood and could independently configure the core VPC components: Subnet, Internet Gateway, Route Table, Security Group.
* Distinguished Public Subnet from Private Subnet and understood how traffic routes to the internet.
* Successfully deployed EC2 inside a VPC and used an Instance Connect Endpoint to securely access a Private instance.
* Overcame initial confusion about Security Group inbound/outbound direction.
* Built a solid networking foundation to move on to more advanced labs next week.