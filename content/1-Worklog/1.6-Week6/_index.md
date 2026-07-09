---
title: "Week 6 Worklog"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives (Focus: Database):
Study Module 06 on databases (RDS, DynamoDB) in depth, a personal strength area, spent the most time and practiced most thoroughly here.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 22/05/2026 | Watched the Module 06 lecture and read detailed documentation on Amazon RDS and Aurora; took comparison notes on the engines (MySQL, PostgreSQL, Aurora) and concepts like Multi-AZ and Read Replica | |
| Saturday | 23/05/2026 | Practiced Lab 05 (Amazon RDS): created a MySQL RDS instance, configured a Security Group for EC2 to connect to RDS, installed Node.js and a MySQL client, deployed a Node.js application; fixed an empty .env file issue and an incompatible mysql package by switching to mysql2, and finally got the app running and connected to RDS successfully | [awsstudygroup.com](https://000005.awsstudygroup.com/)  |
| Sunday | 24/05/2026 | Reviewed SQL queries from basic to advanced (JOIN, GROUP BY, subquery, index) to support data manipulation and optimization | |
| Monday | 25/05/2026 | Studied Amazon DynamoDB in depth: the NoSQL model, the Partition Key and Sort Key concepts, and how to design tables for efficient querying while avoiding hot partitions | |
| Tuesday | 26/05/2026 | Practiced Lab 60 (DynamoDB): created a table using the AWS CLI, performed full CRUD operations (add/read/update/delete items), queried data using Query and Scan, and distinguished between the two query methods | [awsstudygroup.com](https://000005.awsstudygroup.com/1-introduce/)  |
| Wednesday | 27/05/2026 | Continued Lab 60: created and queried a Global Secondary Index (GSI) to query by a non-primary-key attribute; then redid all the operations using the Python Boto3 SDK | [awsstudygroup.com](https://000005.awsstudygroup.com/1-introduce/)  |
| Thursday | 28/05/2026 | Practiced more with Boto3: wrote my own scripts to create a table, load sample data, query, and delete items; this was direct groundwork for the DynamoDB part I'd be responsible for in the group project | |

### Week 6 Achievements:
* Gained a strong grasp of AWS databases: distinguished relational databases (RDS/Aurora) from NoSQL (DynamoDB) and their use cases.
* Completed Lab 05: successfully deployed a Node.js application connected to a MySQL RDS instance, and independently resolved a .env issue and a package compatibility issue (switching to mysql2).
* Completed Lab 60: became proficient in table design, CRUD operations, Query/Scan queries, and creating a Global Secondary Index on DynamoDB.
* Became proficient operating DynamoDB using both the AWS CLI and the Python Boto3 SDK.
* Reinforced SQL skills from basic to advanced.
* Built a solid, direct foundation for my role handling DynamoDB in the group project.