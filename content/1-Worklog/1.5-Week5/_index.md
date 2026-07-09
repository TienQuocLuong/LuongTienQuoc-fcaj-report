---
title: "Week 5 Worklog"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:
Study Module 05 on security; focus on the core IAM and encryption labs, skip the advanced IAM labs.

### Tasks carried out this week:
| Day | Date | Task | Reference Material |
|---|---|---|---|
| Friday | 15/05/2026 | Watched the Module 05 lecture on security services (advanced IAM, KMS); took notes on permission and encryption concepts | [youtube (playlist FCJ)](https://www.youtube.com/watch?v=tsobAlSg19g&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=150) |
| Saturday | 16/05/2026 | Practiced Lab 48 (configuring an IAM Role for EC2 to access S3): tried both approaches, using an Access/Secret Key and using an IAM Role attached directly to the EC2 instance, to compare their security levels | [awsstudygroup.com](https://000048.awsstudygroup.com/)  |
| Sunday | 17/05/2026 | Reviewed IAM knowledge and redid Lab 48 to make it solid; understood clearly why Access Keys shouldn't be hardcoded in applications | |
| Monday | 18/05/2026 | Practiced Lab 33 (encrypting S3 data with AWS KMS): created a KMS key, configured object encryption on S3, and checked access permissions | [awsstudygroup.com](https://000057.awsstudygroup.com/vi/1-introduce/) |
| Tuesday | 19/05/2026 | Continued studying KMS: verified that a user without permission on the KMS key can't read an object even with S3 access, understood KMS as an additional layer of access control | [awsstudygroup.com](https://000057.awsstudygroup.com/vi/1-introduce/) |
| Wednesday | 20/05/2026 | Practiced Lab 08 (Amazon CloudWatch): observed Metrics and Logs, set up basic Alarms and a Dashboard to monitor resources | [awsstudygroup.com](https://000008.awsstudygroup.com/)  |
| Thursday | 21/05/2026 | Previewed the Module 06 lecture on databases (RDS, Aurora); decided to skip the advanced IAM labs (Labs 22, 28, 30, 44) to devote more time to the Database section, a personal strength | [youtube (playlist FCJ)](https://www.youtube.com/watch?v=OOD2RwWuLRw&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=217) |

### Week 5 Achievements:
* Understood and practiced the IAM Role permission mechanism, clearly grasped the security risks of using Access Keys directly.
* Completed Lab 48, learned how to attach an IAM Role to EC2 for secure S3 access.
* Completed Lab 33, configured S3 data encryption with AWS KMS and managed permissions on the KMS key.
* Completed Lab 08, learned basic system monitoring with CloudWatch (Metrics, Logs, Alarm, Dashboard).
* Proactively trimmed advanced IAM labs to devote more time to the Database section, a direct foundation for my project role.