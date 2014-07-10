# Introduction

website_b2b is an Odoo module that provides a simplified front end CMS driven interface for sales and purchases for resellers, allowing them to order products and register sales.

It is entirely "data" driven, meaning there are no python files, and therefore can be uploaded to the SaaS. It makes use of the CMS feature that allows server actions to provide the controller entry points for web pages. These server actions are stored in XML files and their ID's correspond to their page URL.

# Setup Instructions

### A. Setup a new retailer account

- Create the retailer as a contact in the database.
- Create a stock location with "Stock" as parent and the retailer contact as address.
- For all the products, add a Reordering rule dedicated to this new location and set an objective as minimal value. Use the import template I sent you. Then import this template in Warehouse > Configuration > Reordering rules in order to update data.
- Assign a portal access right to the retailer (from the Customers list view, more menu).
- In the Users menu, find the new retailer user and add the permissions Warehouse: User, Accounting: Invoicing & Payment and HR: Employee (won't be necessary in the production database). Also assign a password.

### B. Connect as the retailer

- Connect to the website
- Click on Sign In & log in with the credentails of the retailer user
- Open the Website application menu, then click on B2B Portal
- First check your initial stock in Overview
- Start first by encoding an initial order by clicking on "Make an Inventory". Skip the first inventory page and fill in the additional order form.
- Then feel free to encode sales or an inventory. You only see the products you have ordered initially.

### C. Report sales (i.e. once a month)

- 1st page: Fill in the sales report & validate it -> DRAFT DELIVERY ORDER (INVENTORY UPDATE, Retailer location -> client)
- 2nd page: Confirm the sales report -> CONFIRMED DELIVERY ORDER & CONFIRMED INVOICE
- 3rd page: Trigger a new delivery based on our targets and your additional whishes -> VALIDATED DELIVERY ORDER (Stock -> Retailer)

Note: It is not allowed to enter a sold quantity higher than the recorded stock. The user has to update his inventory first.

### D. Report an inventory (in case of inventory error or client return)

- 1st page: Fill in the inventory form -> DRAFT DELIVERY ORDER (INVENTORY UPDATE)
- In the delivery order lines: 
  - (a) FROM Retailer location TO Customer if the new inventory is smaller than the former one
  - (b) FROM Customer TO Retailer location if the new inventory is higher than the former one
- 2nd page: Confirm the sales report -> CONFIRMED DELIVERY ORDER & CONFIRMED INVOICE
  - (a) positive amount (= invoice)
  - (b) negative amount (= credit note)
- 3rd page: Trigger a new delivery based on our targets and your additional whishes -> VALIDATED DELIVERY ORDER (Stock -> Retailer)

