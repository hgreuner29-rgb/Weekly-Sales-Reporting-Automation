# Weekly Sales Reporting Automation

This project demonstrates a practical n8n automation workflow for recurring weekly sales reporting. The goal is to reduce manual effort, improve accuracy, and create a repeatable process that can support reporting and operational follow-up in a business environment.

The workflow retrieves sales data from an API, evaluates the returned records, routes them based on conditions, and then either stores structured data in Airtable or sends a message to Discord depending on the result of the logic branch. The design reflects a realistic reporting setup where data needs to be processed, validated, and shared with different stakeholders in a consistent way.

## Business Context

Weekly reporting is one of the most common operational tasks in many organizations. It often requires the same series of manual actions every week:

- retrieving data from an internal system,
- checking whether the data is complete and valid,
- separating records based on business rules,
- preparing outputs for different audiences,
- and sharing the final result in the right channel.

In many companies, this kind of work is still done manually. That makes it time-consuming, repetitive, and vulnerable to errors. A missed number, a wrong filter condition, or a delayed report can create avoidable friction for the team.

This workflow automates that process in a structured way so the reporting logic becomes more reliable, more transparent, and easier to maintain.

## Project Goal

The purpose of this automation is to show how a standard business process can be automated end to end with n8n.

The workflow is designed to:

- run on a schedule,
- retrieve data from an API,
- evaluate the records with a conditional decision step,
- transform the data where needed,
- create a structured record in Airtable,
- and send a Discord notification for the relevant reporting outcome.

This makes the workflow suitable as a portfolio project for process automation, business operations, analytics support, and workflow design.

## Workflow Overview



The workflow starts with a **Schedule Trigger**, which initiates the automation at a defined interval. This makes the process recurring and removes the need for manual execution.

Next, an **HTTP Request** node fetches the required data from the API. This simulates a legacy or internal system that exposes data through an endpoint rather than a CSV export or direct file download.

After that, an **IF** node evaluates the incoming records and splits the workflow into two branches based on the condition logic.

- The **true** branch uses an **Edit Fields** node and then creates a structured record in **Airtable**.
- The **false** branch uses a **Code in JavaScript** node to transform or prepare the output and then sends a message to **Discord**.

This structure shows how a workflow can combine scheduling, API integration, conditional logic, transformation, and delivery to external systems in one automated process.

## Workflow Logic

### 1. Scheduled Start
The workflow runs automatically on a schedule.  
This is important because reporting tasks usually need to happen at a fixed time every week.

### 2. API Data Retrieval
The workflow calls an API endpoint using an **HTTP Request** node.  
This represents the upstream system from which the sales data is obtained.

### 3. Conditional Evaluation
An **IF** node checks the data against the business logic defined in the workflow.

This can be used to decide, for example, whether a record should be stored, whether a record should be escalated, or whether a reporting message should be sent.

### 4. Structured Data Handling
If the condition is met, the workflow enters the **true** branch.  
Here, the data is cleaned and structured using **Edit Fields**, then written into **Airtable** as a record.

This is useful for auditability, tracking, and future follow-up.

### 5. Output and Notification
If the condition is not met, the workflow enters the **false** branch.  
Here, a **Code in JavaScript** node prepares the data for output and then the workflow sends a message to **Discord**.

This creates a fast communication layer for reporting or escalation.

## Why This Workflow Is Valuable

This project is valuable because it reflects a real enterprise pattern: one system retrieves data, another system evaluates it, and a third system stores or communicates the result.

That means the workflow demonstrates more than just tool usage. It shows:

- process thinking,
- business logic handling,
- data transformation,
- integration with external services,
- and automation design with practical business relevance.

These are the kinds of skills that are useful in process automation, analytics operations, and digital transformation roles.

## Technical Stack

This project was built with the following tools and concepts:

- **n8n**
- **Schedule Trigger**
- **HTTP Request**
- **IF node**
- **Edit Fields**
- **Code in JavaScript**
- **Airtable**
- **Discord**
- **Workflow logic and branching**

## Error Handling and Reliability

A production-ready automation should not only work when everything is perfect. It should also handle common problems gracefully.

This workflow can be extended to handle cases such as:

- missing or incomplete API responses,
- malformed data,
- unexpected values in the condition logic,
- failures when creating records in Airtable,
- delivery issues when posting to Discord,
- and general execution errors.

Adding these controls makes the workflow more realistic and more useful as a portfolio project because it shows that the automation was designed with reliability in mind.

## Example Use Case

A weekly reporting process could use this workflow to process sales data as follows:

- retrieve the weekly dataset,
- evaluate the records,
- store relevant output in Airtable for tracking,
- and send a reporting update to Discord.

This is a common pattern in operational teams where data needs to be organized, reviewed, and communicated quickly.

## What This Project Demonstrates

This project demonstrates that I can:

- design a real workflow from a business requirement,
- integrate external data sources through APIs,
- build conditional logic into an automation,
- transform and structure data before output,
- connect workflow results to business tools,
- and document the process clearly.

## Repository Structure

```text
weekly-sales-reporting-automation/
├── README.md
├── workflow/
│   └── n8n-workflow.json
├── screenshots/
│   └── workflow-overview.png
├── sample-data/
│   └── api-response.json
├── docs/
│   ├── process-description.md
│   └── error-handling.md
└── output/
    └── sample-output.png
