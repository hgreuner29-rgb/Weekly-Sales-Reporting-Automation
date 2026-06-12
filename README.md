# Weekly Sales Reporting Automation

An n8n-based automation workflow that streamlines weekly sales reporting from a legacy data warehouse.

The workflow retrieves sales order data via API, calculates the total value of all **Booked** orders, posts the result to a Discord channel, and generates a spreadsheet of all **Processing** orders for review by Sales Managers.

## Problem

Weekly sales reporting is repetitive, time-sensitive, and prone to manual errors.  
The original process required:

- retrieving data manually from a legacy warehouse,
- calculating sales totals by hand,
- posting the weekly summary in Discord,
- and preparing a spreadsheet for follow-up on open sales orders.

This created unnecessary effort, increased the risk of mistakes, and made the process dependent on manual execution every week.

## Solution

This workflow automates the reporting process end to end.

It uses n8n to:

1. fetch sales order data from an API,
2. normalize and validate the response,
3. filter all orders with status **Booked**,
4. calculate the total booked amount,
5. publish the result to Discord,
6. extract all orders with status **Processing**,
7. generate a spreadsheet for Sales Managers,
8. and log the execution for traceability.

## Workflow Overview

### 1. Scheduled Trigger
The workflow starts automatically every Monday using a schedule trigger.

### 2. Data Retrieval
An **HTTP Request** node calls the legacy warehouse API and retrieves sales order data.

### 3. Data Normalization
A **Set** node or **Code** node structures the incoming response into a clean internal format, for example:

- `order_id`
- `customer_name`
- `status`
- `amount`
- `created_at`

### 4. Booked Orders Aggregation
Orders with status **Booked** are filtered and their amounts are summed.

### 5. Discord Notification
The total booked sales amount is posted automatically to the company Discord channel.

### 6. Processing Orders Export
All orders with status **Processing** are extracted and written into a spreadsheet.

### 7. Error Handling
The workflow includes handling for:

- API failures,
- missing or malformed data,
- unexpected status values,
- Discord delivery errors,
- and spreadsheet creation issues.

### 8. Logging
Each run is logged to support traceability and operational visibility.

## Tech Stack

- **n8n**
- **HTTP Request**
- **Code / Set nodes**
- **Discord integration**
- **Spreadsheet output**
- **Error handling and logging**

## Why This Project Matters

This project demonstrates practical process automation skills in a realistic business scenario. It shows that the workflow is not just technically functional, but also designed with operational reliability, business value, and maintainability in mind.

Key benefits:

- reduces manual effort,
- prevents calculation errors,
- ensures consistent weekly delivery,
- and creates a repeatable reporting process.

## Repository Structure

```text
weekly-sales-reporting-automation/
├── README.md
├── workflow/
│   └── n8n-workflow.json
├── sample-data/
│   └── api-response.json
├── output/
│   └── processing-orders-sample.xlsx
├── screenshots/
│   ├── workflow-overview.png
│   ├── api-node.png
│   ├── filter-node.png
│   └── output-example.png
└── docs/
    ├── process-description.md
    └── error-handling.md
