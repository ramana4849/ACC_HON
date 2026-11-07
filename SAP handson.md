# SAP TM with BN4L - Training Notes

## 1. Creation of Company Code

**Transaction code:** OBY6

**SPRO Path:**
Enterprise Structure → Definition → Financial Accounting → Edit, Copy, Delete and Check Company Code

### Steps
1. Open SPRO and select SAP Reference IMG.
2. Navigate to the path above.
3. Copy an existing company code.
4. Click Create Request and enter a description.
5. Change the company name and other required details.
6. Save the configuration.
7. Use OBY6 to check the company code.

**Example:**
- Reference company code: 4001 or 1404
- New company code: THSC

## 2. Creation of Profit Center and Cost Center

### 2.1 Profit Center

**Transaction code:** KE51

**Example:**
- Profit center: THSPRO
- Controlling area: 6000
- Reference profit center: 11100101
- Reference controlling area: 600

### Steps
1. Open KE51.
2. Enter the profit center details.
3. Use an existing profit center as a reference.
4. Maintain the required assignments.
5. Save.

### 2.2 Cost Center

**Transaction code:** KS01

**Example:**
- Controlling area: 6000
- Cost center: THSCOS
- Valid from: 01.01.2019
- Valid to: 31.12.9999
- Reference cost center: 40012001
- Reference controlling area: 6000

### Steps
1. Open KS01.
2. Enter the controlling area and cost center.
3. Maintain the validity period.
4. Enter the reference cost center, if required.
5. Review accounting and joint venture accounting details, if applicable.
6. Maintain the required company code and profit center.
7. Save.

## 3. Materials Management (MM) Configuration

### 3.1 Define Plant

**SPRO Path:**
Enterprise Structure → Definition → Logistics - General → Copy, Delete and Check Plant

**Example:**
- Reference plant: 4111
- New plant: THSC

Copy the reference plant and maintain the required plant name and details.

### 3.2 Define Storage Location

**SPRO Path:**
Enterprise Structure → Definition → Materials Management → Maintain Storage Location

Create the required storage location for the plant.

### 3.3 Define Purchasing Organization

**SPRO Path:**
Enterprise Structure → Definition → Materials Management → Maintain Purchasing Organization

Create the required purchasing organization.

### 3.4 Assign Plant to Company Code

**SPRO Path:**
Enterprise Structure → Assignment → Logistics - General → Assign Plant to Company Code

Assign the plant to the appropriate company code.

### 3.5 Assign Purchasing Organization to Plant

**SPRO Path:**
Enterprise Structure → Assignment → Materials Management → Assign Purchasing Organization to Plant

Maintain the required purchasing organization and plant assignment.

## 4. Sales and Distribution (SD) Configuration

### 4.1 Define Sales Organization

**SPRO Path:**
Enterprise Structure → Definition → Sales and Distribution → Define, Copy, Delete, Check Sales Organization

**Example:**
- Reference sales organization: 4100
- New sales organization: As required

Copy the reference sales organization and maintain the required details.

### 4.2 Define Distribution Channel

Create the required distribution channel in the SD enterprise structure configuration.

### 4.3 Define Division

Create the required division in the SD enterprise structure configuration.

### 4.4 Define Shipping Point

Configure the shipping point required for shipping execution and SAP TM integration. See Section 10.

### 4.5 Assign Sales Organization to Company Code

**SPRO Path:**
Enterprise Structure → Assignment → Sales and Distribution → Assign Sales Organization to Company Code

Assign the sales organization to the company code.

### 4.6 Complete the Remaining SD Assignments

- Assign the distribution channel to the sales organization.
- Assign the division to the sales organization.
- Set up the sales area.
- Assign the sales organization and distribution channel to the plant.

**Note:** A sales area consists of a sales organization, distribution channel, and division.

## 5. Creation of Purchasing Group

**SPRO Path:**
SAP Reference IMG → Materials Management → Purchasing → Create Purchasing Groups

### Steps
1. Open the purchasing group configuration.
2. Click New Entries.
3. Enter the purchasing group and description.
4. Save.

**Examples:**

| Purchasing Group | Description |
|---|---|
| THS | THSC Buyer Group |
| KNR | ASRC Buyer Group |

## 6. Creation of Organizational Model in SAP TM

**Status:** Pending

**SPRO Path:**
SAP Reference IMG → Transportation Management → Master Data → Organizational Management → Organizational Model

Create or maintain the organizational model required for SAP Transportation Management.

## 7. Ledger and Material Valuation Configuration

Transaction codes covered in training:

- OMX3
- OMX2
- OMX1
- CKMSTART

These relate to Material Ledger and material valuation configuration or processing. Follow the sequence provided by your trainer because the required steps depend on your SAP system setup.

## 8. Creation of Material Master

**Transaction code:** MM01

### Steps
1. Open MM01.
2. Enter the material number, if required.
3. Select the material type.
4. Select the necessary views.
5. Enter the organizational levels, such as plant and storage location, where applicable.
6. Maintain the required material details.
7. Save.

## 9. Creation of Business Partner (BP)

**Transaction code:** BP

Create or maintain Business Partners for customers and carriers.

- **Customer:** Used in customer-related business transactions.
- **Carrier:** Represents a transportation service provider.

**Example reference number:** 8999999492

Confirm the appropriate Business Partner role and number assignment in your training system.

## 10. Shipping Point Configuration and Assignment

### 10.1 Copy Shipping Point

**SPRO Path:**
Enterprise Structure → Definition → Logistics Execution → Copy, Delete and Check Shipping Point

**Example:**
- Reference shipping point: 4111
- New shipping point: THSC

### 10.2 Define Shipping Point

**SPRO Path:**
Enterprise Structure → Definition → Logistics Execution → Define Shipping Point

Change the shipping point name and maintain the required details.

### 10.3 Assign Shipping Point to Plant

**SPRO Path:**
Enterprise Structure → Assignment → Logistics Execution → Assign Shipping Point to Plant

Assign the shipping point to the appropriate plant.

### 10.4 Configure Shipping Point Determination

**SPRO Path:**
SAP Reference IMG → Logistics Execution → Shipping → Basic Shipping Functions → Shipping Points and Goods Receiving Point Determination → Assign Shipping Point

Maintain the relevant settings for shipping point determination.

## 11. Control Keys

Control keys determine how specific operations or business activities are processed.

The exact configuration depends on the control keys used in your SAP TM or logistics process. Confirm the relevant settings with your trainer.

## 12. Define LIP

**Status:** Covered in training

Topics mentioned:
- Creation of LIP.
- Definition of the sales document.

**Note:** Confirm the full form and exact configuration of LIP with your trainer because the abbreviation may depend on your course terminology.

## 13. Creation of Sales Order

**Transaction code:** VA01

### Steps
1. Open VA01.
2. Select the sales document type.
3. Enter the sales organization, distribution channel, and division.
4. Enter the sold-to party and ship-to party.
5. Enter the material and order quantity.
6. Maintain the required shipping and delivery details.
7. Check the order for errors.
8. Save.

**Important:** VA01 creates a sales order. A sales area is configured using the sales organization, distribution channel, and division.

## 14. FUBR Rule Configuration

**FUBR:** Freight Unit Building Rule

**Access:** /n/ui2/flp

### Steps
1. Open the SAP Fiori Launchpad.
2. Locate the Freight Unit Building Rule application.
3. Create or maintain the required FUBR.
4. Configure the rule parameters according to the business process.
5. Save and validate the rule.

FUBR determines how transportation-relevant documents or items are grouped into freight units based on configured conditions.

## 15. Creation of Freight Units Under FUBR

**Topic covered today**

Freight units are transportation planning objects in SAP TM. They represent goods or quantities that need to be transported.

### General Process
1. Configure the organizational structure.
2. Maintain master data, including materials, Business Partners, and locations.
3. Configure the required logistics and sales documents.
4. Define the Freight Unit Building Rule.
5. Create a transportation-relevant document, such as a sales order or delivery, depending on the integration scenario.
6. Trigger or execute freight unit building.
7. Verify that the freight units are generated correctly.
8. Continue with freight unit planning and transportation execution.

The exact steps depend on the SAP TM deployment, document integration, and FUBR configuration.

## 16. Quick Revision: Transaction Codes

| Transaction Code | Purpose |
|---|---|
| OBY6 | Check company code settings |
| KE51 | Create profit center |
| KS01 | Create cost center |
| MM01 | Create material master |
| BP | Create or maintain Business Partner |
| VA01 | Create sales order |
| OMX1, OMX2, OMX3 | Material Ledger configuration |
| CKMSTART | Material Ledger-related processing; verify usage in your system |
| /n/ui2/flp | Open SAP Fiori Launchpad |

## Recommended Learning Sequence

1. Company Code
2. Cost Center and Profit Center
3. MM Enterprise Structure
4. SD Enterprise Structure
5. Material Master
6. Business Partner
7. Organizational Model
8. Shipping Point Configuration
9. Sales Order Creation
10. FUBR Configuration
11. Freight Unit Creation
12. Freight Unit Planning and Transportation Execution


### Topics 
SAP Transportation Management with BN4L
Module 1: Overview of ERP and SAP
1. Overview of ERP
2. Introduction to SAP
3. Introduction to SAP S/4HANA, SAP GUI & SAP Fiori
Module 2: Sales & Distribution Overview
1. Sales & Distribution Overview
2. Organization Structure in Sales
3. Master Data in Sales
4. Sales Order Processing
5. Logistics Execution Data Determination
6. Delivery Scheduling
Module 3: Introduction to Transportation Management
1. Introduction to Transportation Management
Module 4: Transportation Management Master Data
1. General Master Data
2. Transportation Networks
Module 5: Transportation Requirements & Logistics Integration
1. Triggering the Transportation Management Process
Module 6: Transportation Planning
1. Documents and Decisions
2. Freight Units
3. Planning Strategies, Profiles & Settings
Module 7: Transportation Charge Management
1. Charge Calculation Master Data and Customizing
2. Freight Agreement Determination
Module 8: Transportation Charge Settlement
1. Charge Settlement and Billing
