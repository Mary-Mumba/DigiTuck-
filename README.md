# DigiTuck-
# DigiTuck --- Online Tuckshop & Spaza Shop Ordering System

DigiTuck is a digital ordering concept for school tuckshops, campus
vendors, and local spaza shops. It is designed to help customers check
products and prices, place orders before reaching the shop, and collect
them with less waiting. It also aims to help vendors manage product
availability and incoming orders more consistently.

> **Project status:** This README documents the project vision and
> proposed functionality. Update the status and setup instructions to
> match the code that is actually present in this repository. Features
> described as planned are not claims that they have already been
> implemented.

## System flow diagram

The diagram below shows the intended DigiTuck workflow for students/customers and vendor/shop owners, including the MySQL database, order processing, and notifications.


*Figure 1. DigiTuck system flow diagram. The image is stored in this repository so GitHub can display it directly in the README.*

## Table of contents

-   [Problem statement](#problem-statement)
-   [Project objectives](#project-objectives)
-   [Target users](#target-users)
-   [Core features](#core-features)
-   [Typical order workflow](#typical-order-workflow)
-   [Technology stack](#technology-stack)
-   [Repository structure](#repository-structure)
-   [Getting started](#getting-started)
-   [Configuration and security](#configuration-and-security)
-   [Testing](#testing)
-   [Roadmap](#roadmap)
-   [Contributing](#contributing)
-   [Limitations and important notes](#limitations-and-important-notes)
-   [License](#license)
-   [Author](#author)

## Problem statement

Customers often have limited time to buy food and everyday items during
school, campus, or work breaks. Queues, unclear prices, unavailable
products, and orders handled through memory or informal messages can
lead to delays and mistakes. Small vendors may also lack simple tools
for tracking stock and incoming orders.

DigiTuck aims to provide a lightweight online ordering experience
focused on **quick ordering, accurate availability, and convenient
collection**. Delivery can be considered as a later extension rather
than a requirement for the first version.

## Project objectives

-   Allow customers to browse a vendor's products and prices.
-   Make it easier to submit an order before arriving at the shop.
-   Help vendors view and manage incoming orders.
-   Make product availability and order status clearer.
-   Reduce avoidable queue time and order-entry mistakes.
-   Keep the experience straightforward for small businesses and users
    with limited mobile data.
-   Provide a foundation that can be expanded after testing with
    customers and vendors.

## Target users

### Customers / students

-   Browse products, prices, and availability.
-   Add items to an order and review the total.
-   Submit an order and view its status, where implemented.
-   Collect an accepted order from the selected shop.

### Tuckshop / spaza shop vendors

-   Maintain product names, prices, and availability, where implemented.
-   Receive and review incoming orders.
-   Accept or reject orders and update preparation status, where
    implemented.
-   Review basic order or sales records, where implemented.

### Administrator (optional role)

-   Manage accounts and vendor listings.
-   Help review reports or disputes.
-   Monitor system activity, if an administrator module is included.

## Core features

The list below is the intended scope. Mark each item as complete only
after verifying it in the source code.

-   [ ] Customer-facing product catalogue
-   [ ] Product prices and availability
-   [ ] Shopping cart and order total
-   [ ] Order submission and unique order reference
-   [ ] Vendor view for incoming orders
-   [ ] Order status updates (for example: Pending, Accepted, Preparing,
    Ready, Collected, Cancelled)
-   [ ] Vendor product and stock management
-   [ ] Customer and vendor authentication
-   [ ] Order history and basic reporting
-   [ ] Responsive layout for mobile and desktop screens
-   [ ] Input validation and useful error messages
-   [ ] Automated or documented tests

**Payments and delivery:** Online payments, refunds, driver assignment,
live delivery tracking, and third-party integrations should be treated
as separate features. Do not describe them as available until they have
been implemented and tested.

## Typical order workflow

1.  A customer opens DigiTuck and selects a shop.
2.  The customer checks the available products and prices.
3.  The customer adds items to the cart and reviews quantities and the
    total.
4.  The system validates the order against the current product
    availability.
5.  The customer submits the order.
6.  The vendor reviews and accepts or rejects it.
7.  If accepted, the vendor prepares the order and updates its status.
8.  The customer collects the order and the order is marked as
    completed.

A future delivery-enabled version may add a delivery assignment and
delivery status flow.

## Technology stack

**The exact stack must match the files in this repository.** The project
history describes DigiTuck's product concept, but does not establish a
confirmed implementation language, framework, database, or payment
provider. Fill in this table after inspecting the project files.


Do not add a technology to this table just because it is planned. If the
project is a prototype with sample data or local storage, state that
clearly.

## Repository structure

Use a structure that reflects the actual source code. The example below
is a guide, not a requirement to move or rename existing files.

Avoid committing generated build folders, dependency directories, IDE
caches, logs, local databases containing personal data, or secrets.

## Getting started

Because the implementation stack has not been confirmed here, use the
steps below as a checklist and replace the placeholders with the exact
commands for this repository.

### Prerequisites

-   Git installed.
-   The runtime and tools required by the actual project (for example,
    the relevant language runtime, package manager, framework, or
    database).
-   A code editor or IDE compatible with the project.

### 1. Clone the repository

Replace `<YOUR-GITHUB-USERNAME>` with your GitHub username and
`<REPOSITORY-NAME>` with the repository's exact name.

``` bash
git clone https://github.com/<YOUR-GITHUB-USERNAME>/<REPOSITORY-NAME>.git
cd <REPOSITORY-NAME>
```

### 2. Install dependencies

Follow the command for the files that exist in the project. Do not run
all examples; use only the one matching your project.

-   **Node.js project:** if `package.json` exists, check its scripts and
    use the package manager specified by the lock file, for example
    `npm install`.
-   **Python project:** if `requirements.txt` exists, create and
    activate a virtual environment, then run
    `pip install -r requirements.txt`.
-   **Java project:** if `pom.xml` exists, use Maven; if `build.gradle`
    or `build.gradle.kts` exists, use Gradle.
-   **Other stack:** follow the project's existing configuration and
    documentation.

### 3. Configure environment variables

If the application requires configuration, copy the example environment
file if one is supplied (for example, `.env.example` to `.env`) and fill
in local development values. Never commit `.env` files containing
credentials.

### 4. Configure the database

If a database is used, follow the schema, migration, or setup scripts
included in the repository. Use development/test data only. Do not
connect a public repository to a production database.

### 5. Run the application

Use the start or run command defined by the project's existing
configuration. For example, Node.js projects commonly define scripts in
`package.json`; Java projects may use Maven or Gradle; Python projects
may define a framework-specific run command.

**Before publishing this README, replace this section with exact, tested
commands**, such as the required installation command, database
initialization command, and application start command. Do not invent
commands that the project does not support.

## Configuration and security

-   Keep passwords, API keys, database credentials, and payment secrets
    out of source control.
-   Add local environment files and generated output to `.gitignore`.
-   Validate user input on both the client and server where applicable.
-   Enforce role-based access checks for vendor and administrator
    functions.
-   Do not store raw bank-card details.
-   If a payment gateway is added, verify payment status on the server
    using the provider's documented verification mechanism; a browser
    success page alone is not proof of payment.
-   Use HTTPS in deployed environments and collect only the customer
    data needed to operate the service.
-   Use fictional/sample data in screenshots, demos, and tests.

## Testing

Before considering a release, test at least the following:

-   Product list loads and displays correct prices.
-   Unavailable products cannot be ordered.
-   Cart quantities and totals are calculated correctly.
-   Invalid or incomplete order details are rejected.
-   A customer cannot access vendor-only or administrator-only
    functions.
-   Vendors can distinguish new, accepted, rejected, and completed
    orders, where those statuses are implemented.
-   Failed requests and database errors produce understandable messages.
-   The interface remains usable on a small screen.
-   Any payment integration handles success, failure, cancellation, and
    repeated notifications safely.

Document which tests have actually been run and their results. Do not
claim tests passed unless they have been executed.

## Roadmap

Possible development stages:

1.  **Foundation:** confirm requirements, repository structure, and data
    model.
2.  **Catalogue:** display shop products, prices, and availability.
3.  **Ordering:** implement cart validation, order creation, and order
    references.
4.  **Vendor workflow:** allow vendors to manage stock and process
    incoming orders.
5.  **Quality and security:** add validation, access control, error
    handling, and tests.
6.  **Pilot:** test with a small number of willing vendors and
    customers; measure order accuracy, collection time, cancellations,
    and repeat usage.
7.  **Extensions:** evaluate payment integration, reporting,
    notifications, and delivery only after the core ordering workflow is
    reliable.

## Contributing

Contributions and suggestions are welcome.

1.  Create a branch for your change.
2.  Keep changes focused and explain the reason for them.
3.  Run the relevant tests.
4.  Update documentation when behaviour or setup changes.
5.  Open a pull request describing the change and how it was tested.

For a small academic or prototype project, the repository owner may
instead review changes directly before merging.

## Limitations and important notes

-   DigiTuck is intended to support ordering and collection from local
    tuckshops and spaza shops; the first release should stay focused on
    the core workflow.
-   Product availability depends on vendors keeping stock information up
    to date.
-   A prototype may not yet support real customer accounts, live stock
    synchronisation, online payments, delivery, or production hosting.
-   Any school-based pilot should obtain the relevant school's approval
    and account for rules affecting learners and phone use.
-   This repository's actual implementation and course requirements take
    precedence over proposed features in this README.

## License

No license has been selected yet. Until a license is added, do not
assume that other people have permission to reuse, distribute, or modify
this code. If this is an academic project, confirm the appropriate
license and any institutional requirements before publishing it.

## Author

**Project:** DigiTuck --- Online Tuckshop & Spaza Shop Ordering System\
**Maintainer:** `Add your preferred name or GitHub username`\
**Repository:** `Add the GitHub repository URL`

 
