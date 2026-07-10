---
title : "Storage & Database"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Create DynamoDB tables to store test history and error logs

The system uses 2 DynamoDB tables: one storing the history of each test run, and one storing system errors when a message lands in the Dead Letter Queue.

**Step 1:** Go to the **DynamoDB Console**.

![Access DynamoDB Console](/images/5-Workshop/5.3-Data-Storage/1-access-dynamodb-console.png)

**Step 2:** Click **Create table**.

![Click Create table](/images/5-Workshop/5.3-Data-Storage/2-create-table-button.png?featherlight=false&width=90pc)

**Step 3:** Enter **Table name** = `playwright-test-history`.

**Step 4:** Enter **Partition key** = `task_id`, type **String**.

![Create the playwright-test-history table](/images/5-Workshop/5.3-Data-Storage/3-create-test-history-table.png)

**Step 5:** Leave the other settings as default, click **Create table**.

![Create table playwright-test-history](/images/5-Workshop/5.3-Data-Storage/4-create-test-history-table.png)

**Step 6:** Click **Create table** again to create the second table.

**Step 7:** Enter **Table name** = `playwright-error-log`.

**Step 8:** Enter **Partition key** = `error_id`, type **String**.

![Create the playwright-error-log table](/images/5-Workshop/5.3-Data-Storage/5-create-error-log-table.png?featherlight=false&width=90pc)

**Step 9:** Click **Create table**.

![Create table playwright-error-log](/images/5-Workshop/5.3-Data-Storage/6-create-error-log-table.png?featherlight=false&width=90pc)

**Step 10:** Wait for both tables to switch to **Active** status.

![Both tables in Active status](/images/5-Workshop/5.3-Data-Storage/7-tables-active.png?featherlight=false&width=90pc)

*(Note: No need to create any other fields such as `target_url`, `status`, `report_url`, etc. — DynamoDB is NoSQL and automatically picks up fields when the application writes data, with no need to declare a rigid schema upfront.)*

#### Detailed schema

**Table `playwright-test-history`**

| Field | Type | Description |
|---|---|---|
| task_id | String | Partition Key |
| target_url | String | URL to be tested |
| test_script | String | Name of the test script |
| status | String | running / success / failed |
| triggered_by | String | manual / schedule |
| started_at | String | ISO datetime |
| finished_at | String | ISO datetime |
| report_url | String | S3 Presigned URL to the report |
| ai_summary | String | AI-generated error summary |

**Table `playwright-error-log`**

| Field | Type | Description |
|---|---|---|
| error_id | String | Partition Key |
| original_message_id | String | Original MessageId from SQS |
| message_body | String | Original message content |
| error_message | String | Error content, if any |
| timestamp | String | ISO datetime |

#### Grant permissions for the Fargate container to write directly to DynamoDB

Since the Fargate container writes the `running/success/failed` status directly to the `playwright-test-history` table (bypassing Lambda), the Task Role needs additional permissions.

**Step 11:** Open the **IAM Console**, find the role `playwright-ecs-task-role`.

![Find the role `playwright-ecs-task-role`](/images/5-Workshop/5.3-Data-Storage/8-search-playwright-ecs-task-role.png?featherlight=false&width=90pc)

**Step 12:** Click **Add permissions → Create inline policy**.

![Create an inline policy](/images/5-Workshop/5.3-Data-Storage/9-create-inline-policy.png?featherlight=false&width=90pc)

**Step 13:** Select the **JSON** tab, paste the following content:
```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": ["dynamodb:PutItem", "dynamodb:UpdateItem"],
    "Resource": "arn:aws:dynamodb:ap-southeast-1:<account-id>:table/playwright-test-history"
  }]
}
```

**Step 14:** Replace `<account-id>` with the real Account ID (12 digits, shown in the top-right corner of the Console).

**Step 15:** Name the policy, e.g. `SecretsManagerReadWrite`, click **Create policy**.

![Policy attached to the role](/images/5-Workshop/5.3-Data-Storage/10-inline-policy-attached.png?featherlight=false&width=90pc)

#### Verification

- Both tables show **Active** status in the Console.
- `playwright-ecs-task-role` shows the inline policy `SecretsManagerReadWrite` in the Permissions tab.
- After running a test: go to the `playwright-test-history` table → **Explore table items** tab → see a record with `status`, `report_url`, `ai_summary` all populated.
