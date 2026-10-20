# DigiTuck

DigiTuck is a concept for a digital ordering system for school tuckshops, campus vendors, and local spaza shops. The goal is to let customers check products and prices, place orders before they arrive, and collect their purchases with less waiting time. The system is also intended to help vendors manage what is in stock and keep track of incoming orders more consistently.

## Project status

This repository currently contains the project documentation and planning material only. It does not yet include a working application, database schema, frontend implementation, backend service, or automated tests.

The items below are planned features and should be treated as future scope unless they are implemented in the codebase.

## Problem statement

Customers often have limited time to buy food and everyday items during school, campus, or work breaks. Queues, unclear prices, unavailable products, and informal ordering methods can cause delays and mistakes. Small vendors may also lack a simple and consistent way to track stock and incoming orders.

DigiTuck aims to provide a lightweight online ordering experience focused on quick ordering, clear availability, and convenient collection. Delivery is not part of the first version and can be considered later as an extension.

## Project objectives

- Allow customers to browse a vendor's products and prices.
- Help customers submit an order before arriving at the shop.
- Let vendors view and manage incoming orders.
- Improve product availability and order status visibility.
- Reduce queue time and order-entry errors.
- Keep the experience simple for small businesses and users with limited data.
- Build a foundation that can be extended after initial testing.

## Target users

### Customers and students

- Browse available products and prices.
- Add items to an order and review totals.
- Submit an order before arriving at the shop.
- Collect their order when it is ready.

### Tuckshop and spaza shop vendors

- Maintain item names, prices, and stock information.
- Review incoming orders.
- Accept or reject orders.
- Update order preparation status.

### Administrator (optional)

- Manage vendor listings and account access.
- Review reports or disputes.
- Monitor activity if such a module is added later.

## Planned features

The following features are part of the intended scope, but they are not confirmed as implemented in this repository:

- [ ] Customer-facing product catalogue
- [ ] Product prices and availability
- [ ] Shopping cart and order total
- [ ] Order submission and unique order reference
- [ ] Vendor view for incoming orders
- [ ] Order status updates (Pending, Accepted, Preparing, Ready, Collected, Cancelled)
- [ ] Vendor product and stock management
- [ ] Customer and vendor authentication
- [ ] Order history and basic reporting
- [ ] Responsive layout for mobile and desktop screens
- [ ] Input validation and helpful error messages
- [ ] Automated or documented tests

Payments and delivery are out of scope for the initial phase and should not be treated as available until they are implemented and tested.

## Typical order workflow

1. A customer opens DigiTuck and selects a shop.
2. The customer views the available products and prices.
3. The customer adds items to the cart and reviews quantities and totals.
4. The system validates the order against current stock.
5. The customer submits the order.
6. The vendor reviews the order and accepts or rejects it.
7. If accepted, the vendor prepares the order and updates its status.
8. The customer collects the order and the order is marked complete.

## Technology stack

No application stack has been selected or implemented in this repository yet.

This project has not yet confirmed a language, framework, database, or hosting approach. The technology stack should be added only after the implementation is created and verified in the repository.

## Repository structure

The repository currently contains the project documentation only.

```text
DigiTuck-
├── README.md
```

No source code, build files, environment files, database scripts, or tests are present at this time.

## Getting started

This repository does not yet contain a runnable application, so there are no validated installation or startup commands to document yet.

### Current state

- No backend code
- No frontend code
- No package manager files
- No database configuration
- No automated tests

### Recommended next steps

1. Choose the implementation stack.
2. Create the project structure.
3. Add configuration and environment files.
4. Implement the core order flow.
5. Add database schema and seed data if needed.
6. Write tests for catalogue, ordering, and vendor workflow.
7. Update this README once the project is implemented.

## Configuration and security

- Keep credentials and secrets out of source control.
- Add local environment files and generated output to `.gitignore`.
- Validate input on both client and server sides where relevant.
- Enforce access control for vendor and administrator functions.
- Do not store raw bank-card details.
- Use HTTPS in deployed environments.
- Collect only the data needed for the service.
- Use fictional or sample data in demos and screenshots.

## Testing

Testing should be added once the implementation exists. Before release, the project should validate at least the following:

- Product lists display the correct prices.
- Unavailable products cannot be ordered.
- Cart totals are calculated correctly.
- Invalid orders are rejected.
- Vendors can distinguish new, accepted, rejected, and completed orders.
- Customer access is restricted from vendor-only and administrator-only features.
- Errors are presented clearly to users.
- The interface remains usable on smaller screens.

No test results are currently recorded in this repository.

## Roadmap

1. Define requirements and confirm the product scope.
2. Create the catalogue and product data model.
3. Implement cart and order submission flows.
4. Build vendor workflow for stock and order management.
5. Add validation, access control, and error handling.
6. Add tests and documentation.
7. Pilot the system with a small group of vendors and customers.
8. Evaluate extensions such as payments, notifications, and delivery only after the core workflow is stable.

## Contributing

Contributions are welcome once the project implementation begins.

1. Create a branch for your update.
2. Keep changes focused and explain the reason for them.
3. Run the relevant tests.
4. Update documentation when behavior or setup changes.
5. Open a pull request describing the change and how it was tested.

## Limitations and important notes

- DigiTuck is intended for small local tuckshops and spaza shops, not large-scale delivery operations.
- Product availability depends on vendors keeping stock information up to date.
- A prototype may not yet support real customer accounts, payment processing, delivery, or production hosting.
- Any school-based pilot should have the necessary approval and account for relevant school rules.
- This repository's current implementation status takes precedence over any planned features described in this document.

## License

No license has been selected yet. Until a license is added, do not assume that others may reuse, distribute, or modify this project.

## Author

Project: DigiTuck

Repository: https://github.com/itprojectgroup53-commits/DigiTuck-
