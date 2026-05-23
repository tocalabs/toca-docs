# Centralized Customer Data Application
## Scenario

A company interacts with customers across multiple channels—sales, support, marketing, and billing. Each department relies on separate systems, leading to fragmented customer data, duplicated records, and inconsistent information.

### The Scenario

To address these challenges, the company introduces a **centralized customer data application** that acts as a single source of truth for all customer information.

### How It Works

1. Customer data from CRM, support ticketing, billing, and marketing platforms is integrated into the centralized application.
2. Each customer has a unified profile containing:
   * Contact and account details
   * Purchase and subscription history
   * Billing and payment status
   * Communication and marketing preferences

Lets configure Workflow connectors to keep customer data synchronized across systems.

### Background configuration 
Create the Account Details Table (Parent)
Before you can add individual customers, you must define the organizations they belong to. This table acts as the foundational "anchor."

| Field | Description |
| :--- | :--- |
| **Account ID** | Unique identifier for the customer account |
| **Account Name** | Registered name of the customer or organization |
| **Account Type** | Customer classification (e.g., individual, business, enterprise) |
| **Status** | Current account status (active, suspended, closed) |
| **Primary Contact** | Main point of contact for the account |
| **Email Address** | Primary contact email |
| **Phone Number** | Primary contact phone number |
| **Billing Address** | Address used for invoicing and payments |
| **Created Date** | Date the account was created |
| **Last Updated** | Most recent account update timestamp |

---

## 3. Purchase and Subscription History ( optional )
Tracks all financial events and service entitlements associated with the customer and account.

| Field | Description |
| :--- | :--- |
| **Transaction ID** | Unique identifier for the purchase or subscription event |
| **Product / Plan Name** | Name of the product or subscription plan |
| **Product Type** | One-time purchase or recurring subscription |

## 2. Create the Customer Table (The Bridge)
The primary entity for individual contacts. This table bridges the gap between organizational data and individual activity.

| Field Name | Type | Description | Reference / Link |
| :--- | :--- | :--- | :--- |
| **Customer ID** | PK | Unique identifier for the individual person | Internal Unique ID |
| **First Name** | String | Given name of the customer | N/A |
| **Last Name** | String | Surname of the customer | N/A |
| **Job Title** | String | The individual’s role (e.g., CTO, Procurement Mgr) | N/A |
| **Account ID** | FK | Links this person to a specific organization | **Account Details Table** |
| **Latest Transaction ID** | FK | Links to the most recent purchase or subscription | **Purchase History Table** |
| **Loyalty Tier** | Enum | Calculated status based on total spend or tenure | Derived Data |
| **Last Interaction** | Date | The last time this person contacted support | Support / Ticketing System |

---
Add a few examples rows in the Account Details Table and the Purchase and Subscription History table:
![alt text](/src/assets/cookbook/workflows_as_resful_apis/image1.png) 

and link them to the original customers table:
![alt text](/src/assets/cookbook/workflows_as_resful_apis/image2.gif) 