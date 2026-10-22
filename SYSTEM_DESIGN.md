# DigiTuck Online Spaza Shop Ordering System
## System Design: Description of the Proposed System

**Project:** DigiTuck Online Spaza Shop Ordering System  
**Document:** System Design – Description of the Proposed System  
**Version:** 1.0

---

## 1. Introduction

DigiTuck is a proposed online ordering system designed to improve how spaza shops, tuck shops, and small convenience stores manage product sales, customer orders, and inventory. The system provides a digital platform through which students and other customers can browse products, create shopping carts, place orders, and monitor order progress. Vendors and shop owners use a separate management interface to maintain product information, manage stock, process orders, and review sales information.

The system is intended to address common problems associated with informal or manual ordering processes, including long queues, errors when recording orders, limited visibility of product availability, and time-consuming stock administration. DigiTuck aims to make ordering more convenient for customers and to provide vendors with a more organised way to manage day-to-day shop operations.

## 2. Purpose and Scope

The purpose of the proposed system is to centralise product browsing, order placement, inventory management, and order administration in one platform.

The initial scope includes:

- Customer and vendor registration and login.
- Product catalogue browsing and product search.
- Shopping-cart management and checkout.
- Order creation, order-status updates, and order-history access.
- Product, category, and inventory management for authorised vendors.
- Customer and order administration, subject to role permissions.
- Sales summaries and notifications relating to order activity.
- Persistent storage of system records in a MySQL relational database.

Payment gateways, delivery tracking, SMS or email integrations, and other external services should be treated as optional extensions unless they are explicitly included in the implemented project.

## 3. Overview of the Proposed System

DigiTuck will provide two main user interfaces: a customer-facing ordering interface and a vendor-facing management dashboard. Both interfaces will communicate with the application’s business logic, which validates requests and reads or updates information in the MySQL database.

Customers will be able to browse the catalogue, search for products, add items to a cart, review quantities and prices, and submit an order. The system will validate the order and stock availability before saving it. Customers can then view the order’s current status and access their previous orders.

Vendors will log in to a management dashboard where they can add or update products, maintain categories and stock quantities, review incoming orders, update order statuses, and access sales summaries. The application will enforce role-based permissions so that users can access only the functions appropriate to their roles.

### Proposed system flow diagram

The following diagram provides a high-level view of the proposed workflow.

![DigiTuck Online Spaza Shop Ordering System Flow Diagram](docs/diagrams/digituck-system-flow.png)

*Figure 1: DigiTuck Online Spaza Shop Ordering System – Proposed System Flow Diagram.*

## 4. System Users and Responsibilities

### 4.1 Students/Customers

Customers use DigiTuck to find and order products. Their main functions are:

- **Register and log in:** Create an account and authenticate before accessing protected features.
- **Browse the catalogue:** View products organised by category.
- **Search products:** Find specific products and review their details and availability.
- **Manage the shopping cart:** Add items, change quantities, remove items, and review selections.
- **Checkout:** Confirm the selected products, quantities, prices, and order total.
- **Place orders:** Submit a validated order for the vendor to process.
- **Track orders:** View the latest recorded order status.
- **View order history:** Review previous orders and their details.
- **Log out:** End the active session.

### 4.2 Vendors/Shop Owners

Vendors use the management dashboard to administer shop activities. Their main functions are:

- **Log in:** Authenticate before accessing vendor functions.
- **View the dashboard:** Access key shop-management functions and relevant order information.
- **Manage products:** Add products, edit descriptions and prices, update stock quantities, and deactivate or remove products where appropriate.
- **Manage categories:** Create, update, and maintain product categories.
- **Manage customer information:** View only the customer information required for legitimate shop operations and permitted by the system’s access rules.
- **Process orders:** Review incoming orders and update their statuses as they are handled.
- **View sales reports:** Review sales summaries for daily, weekly, and monthly periods.
- **Log out:** End the active session.

## 5. Description of the System Workflow

### 5.1 Application Entry and Authentication

The workflow begins when a user opens DigiTuck. The system presents the available login or registration options. After successful authentication, the application checks the user's role and directs them to the relevant interface.

Customers are directed to the shopping functionality, while vendors are directed to the management dashboard. Protected actions must be checked by the application, not merely hidden from view in the user interface.

### 5.2 Customer Ordering Process

1. **Browse products:** The customer views the available catalogue and product categories.
2. **Search and select products:** The customer finds products and checks their details and availability.
3. **Add to cart:** The customer adds selected products and adjusts quantities as needed.
4. **Review the cart:** The system displays the selected items, quantities, applicable prices, and calculated total.
5. **Checkout:** The customer confirms the order details before submission.
6. **Validate the order:** The application verifies that the products exist, quantities are valid, and sufficient stock is available.
7. **Save the order:** The system records the order and its individual order items in the database.
8. **Track the order:** The customer can view the latest order status recorded by the vendor.
9. **Review order history:** The customer can access previous orders.
10. **Log out:** The customer ends the session when finished.

Prices and totals must be recalculated and validated by the application during checkout. The system must not rely exclusively on values submitted by the customer's browser.

### 5.3 Vendor Management and Order Processing

After logging in, the vendor opens the management dashboard. The vendor can maintain product and category information, update inventory, review incoming orders, and view sales summaries.

When a new order is received, the vendor reviews its contents and determines whether it can be fulfilled. The vendor updates the order status as processing progresses. The system makes the updated status available to the customer.

When an order is accepted or fulfilled, stock quantities should be updated according to the project's defined business rules. Database transactions and validation should be used where possible to prevent inconsistent order and inventory records. If stock is insufficient, the application should reject or flag the affected order and explain the issue.

### 5.4 Notifications

The notification component is intended to communicate relevant events to customers and vendors. Examples include confirmation that an order was submitted, notification of a status change, or an alert that a new order requires vendor attention.

The notification method—such as in-application messages, email, or SMS—depends on the services implemented in the final version. The system should not claim that an external notification has been sent unless the relevant integration is configured and working.

## 6. Proposed Database Design

DigiTuck will use a MySQL relational database to store and organise the records required by the application. A relational database is suitable because users, categories, products, orders, and order items are connected through defined relationships.

### 6.1 Main Database Entities

| Entity | Purpose | Example attributes |
|---|---|---|
| **Users** | Stores customer and vendor account records. | User ID, name, contact details, password hash, role |
| **Categories** | Groups products into meaningful categories. | Category ID, category name, description |
| **Products** | Stores catalogue and inventory information. | Product ID, name, description, price, category ID, stock quantity, availability |
| **Orders** | Stores the main record for each customer order. | Order ID, customer ID, order date, total amount, order status |
| **Order Items** | Stores the products and quantities included in each order. | Order-item ID, order ID, product ID, quantity, unit price |

The exact fields may be adjusted to match the implemented database schema.

### 6.2 Entity Relationships

The proposed database will support these relationships:

- One customer can place many orders.
- One category can contain many products.
- One order can contain many order items.
- Each order item refers to a product.
- A product can appear in order items belonging to multiple orders.
- User roles determine which application functions a user is permitted to access.

Primary keys will uniquely identify records, while foreign keys will connect related records. Appropriate constraints and transaction handling should be used to protect data integrity. The order item should retain the applicable unit price at the time of purchase so that historical order totals remain meaningful if the product price changes later.

## 7. Proposed System Architecture

The system is organised into three logical layers.

### 7.1 Presentation Layer

The presentation layer contains the interfaces through which customers and vendors use the system. It includes registration and login screens, product catalogue pages, search, the shopping cart, checkout, order tracking, order history, and the vendor dashboard.

The interface should be consistent, understandable, and responsive on the supported devices and browsers.

### 7.2 Application and Business Logic Layer

The application layer processes requests and enforces business rules. Its responsibilities include authentication, role and permission checks, product searches, cart validation, checkout, order creation, stock updates, order-status management, notifications, and sales calculations.

The application layer validates data before it is stored and prevents users from performing operations outside their permissions.

### 7.3 Data Layer

The data layer consists of the MySQL database and the controlled operations used to create, retrieve, update, and delete records. It stores user accounts, categories, products, stock quantities, orders, and order items.

The application should access the database through controlled queries or data-access functions. Database credentials and other secrets must not be exposed in public source code.

## 8. Functional Requirements

The proposed system should:

1. Allow customers and vendors to authenticate using their assigned roles.
2. Allow customers to browse and search available products.
3. Allow customers to manage a shopping cart and review quantities.
4. Validate product availability and calculate order totals at checkout.
5. Save valid orders and their associated order items.
6. Allow customers to view order status and order history.
7. Allow authorised vendors to add, update, and manage products.
8. Allow authorised vendors to maintain product categories and inventory.
9. Allow vendors to review and process orders.
10. Record order-status changes and present the latest status to customers.
11. Provide sales summaries for daily, weekly, and monthly periods.
12. Protect restricted functions through authentication and role-based access control.
13. Handle invalid input and processing errors with clear feedback.

## 9. Non-Functional Requirements

- **Usability:** The interface should be easy to learn and use.
- **Performance:** Common actions, such as catalogue browsing and order lookup, should respond within reasonable times under normal operating conditions.
- **Reliability:** Valid order information should be saved consistently, and errors should not silently produce incomplete transactions.
- **Security:** Passwords, account information, and vendor functions must be protected against unauthorised access.
- **Maintainability:** Code should be organised into clear components and documented where necessary.
- **Scalability:** The design should allow the application to accommodate growth in products, users, vendors, and orders.
- **Compatibility:** The interface should work on the browsers and devices supported by the project.
- **Data integrity:** Database relationships, validation, and transaction handling should reduce inconsistent records.
- **Privacy:** Customer information should be limited to authorised purposes and protected from unnecessary access.

## 10. Security and Data Protection

The system should use secure password hashing, server-side input validation, parameterised database queries, session management, and role-based access control. Sensitive vendor functions, customer records, and sales reports must be accessible only to authorised users.

The application should validate product prices, quantities, and stock availability on the server side. Database credentials should be stored outside publicly committed source files, such as in environment-specific configuration that is excluded from version control. Appropriate backups and recovery procedures should be considered.

## 11. Expected Benefits

DigiTuck is expected to:

- Reduce dependence on manual or informal order-taking.
- Make product browsing and ordering more convenient for customers.
- Reduce errors through structured cart and checkout steps.
- Improve visibility of stock levels and product availability.
- Help vendors organise incoming orders and update order statuses.
- Give customers access to order progress and previous orders.
- Provide useful sales summaries to support shop-management decisions.
- Create a foundation for future enhancements, such as additional notification channels or integrations, if they are included in later development.

## 12. Conclusion

The proposed DigiTuck Online Spaza Shop Ordering System provides a structured approach to online product browsing, order placement, inventory management, and vendor administration. It separates customer-facing functions from vendor-management functions while connecting both through application business logic and a central MySQL database.

The design includes authentication, role-based access, catalogue management, cart and checkout processing, order tracking, inventory updates, notifications, and sales reporting. These capabilities are intended to improve the convenience of ordering and the organisation of small-shop operations.

The accompanying system flow diagram presents the high-level workflow for the proposed solution. The final implementation should ensure that its database schema, business logic, interfaces, and security controls work together consistently. Any feature described as part of the implemented system should be verified against the actual project code before submission.
