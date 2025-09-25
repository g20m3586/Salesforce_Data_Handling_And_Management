# Salesforce_Data_Handling_And_Management
This project was built as part of Section 2 Assessment – Data Modeling and Management.
The goal is to give the sales team a system to track leads, convert them into opportunities, and generate accurate reports.
## Features Implemented
1. Custom Objects

  Lead__c – stores prospective customer details.
  
  Opportunity__c – stores sales opportunities linked to leads.

2. Custom Fields

  Lead Fields
  
  Full Name (standard Name field)
  
  Email (required, validation enforced)
  
  Phone
  
  Company
  
  Lead Source (picklist: Web, Phone Inquiry, Trade Show, Referral, Other)
  
  Lead Status (picklist: New, Contacted, Qualified, Converted, Unqualified) – required
  
  Industry, City, State (text/picklist for extra info)

3. Opportunity Fields

  Opportunity Name (standard Name field)
  
  Amount (currency)
  
  Stage (picklist: Prospecting, Qualification, Proposal, Negotiation, Closed Won, Closed Lost)
  
  Close Date (date)
  
  Probability (percent)
  
  Source Lead (Lookup to Lead__c)

4. Relationships

  Lookup from Opportunity → Lead (Source_Lead__c)
  
  This allows Opportunities to be traced back to the Lead they came from.

5. Validation Rules

  Require Email on every Lead:
  
  ISBLANK( Email__c )

  (Optional) Enforce email format using REGEX.

  Require Lead Status for new Leads:
  
  ISNEW() && ISBLANK( TEXT( Lead_Status__c ) )


6. Duplicate Management

  Matching Rule: exact match on Email.
  
  Duplicate Rule: block duplicate Leads with the same email.

7. Picklists

  Lead Status picklist made required on record creation.
  
  Stage picklist added to Opportunity for consistent tracking.
  
  Data Import
  
  Imported 5 sample Leads via Data Import Wizard using CSV.
  
  Each Lead record contained Name, Email, Phone, Company, Lead Source, Lead Status, etc.

8. Report

  Custom Report Type: Leads with Opportunities (Lead as parent, Opportunity as child).
  
  Report filters:
  
  Lead Status = Converted
  
  Date Range = All Time
  
  Report columns:
  
  From Lead: Full Name, Email, Company, Status
  
  From Opportunity: Name, Stage, Amount, Close Date
  
  Shows all Opportunities created from converted Leads.

  ## How to reproduce
  Set up objects

Go to Setup → Object Manager → Create custom objects Lead__c and Opportunity__c.

Add fields as listed above.

Add relationships

Create a Lookup on Opportunity (Source_Lead__c) pointing to Lead.

Validation & Duplicate Rules

Add validation rules in Lead to require Email & Lead Status.

Add matching/duplicate rules to prevent duplicate emails.

Import Data

Use Data Import Wizard → Leads → Upload CSV with at least 5 sample records.

Test Conversion

Create at least one Opportunity linked to a Lead.

Update Lead Status = Converted.

Run Report

Create new report with type: Leads with Opportunities.

Add filters & columns as listed above.

Run the report to confirm converted Leads show their Opportunities.

### Snapshot Images:
<img width="2160" height="1440" alt="image" src="https://github.com/user-attachments/assets/5da923b7-2943-4f14-b04a-cfeec1f3df49" />
<img width="2160" height="1440" alt="image" src="https://github.com/user-attachments/assets/349b0f89-ecb0-4c89-ae62-02e4bea065a1" />
<img width="2160" height="1440" alt="image" src="https://github.com/user-attachments/assets/bffd59a8-f219-4972-8d62-8e8e8f74977e" />
<img width="2160" height="1440" alt="image" src="https://github.com/user-attachments/assets/e67032e1-f630-4c03-a097-18069812e481" />
<img width="2160" height="1440" alt="image" src="https://github.com/user-attachments/assets/9350f8f8-1e52-493d-8b51-27ff236d3386" />
<img width="2160" height="1440" alt="image" src="https://github.com/user-attachments/assets/8e25a28a-8d49-4c48-83f3-48a09f6fdf95" />




