
# Appliances.lk — Project Documentation

**Software Requirements, System Design, Testing, Security, Deployment Evidence & Sprint Retrospectives**

Documentation repository for **Appliances.lk**, a full-stack mobile accessories e-commerce and device repair service management platform developed as part of **SENG 34213 — System Development Project** at the University of Kelaniya, Sri Lanka.

This repository contains the academic documentation, technical specifications, software testing reports, security compliance evidence, performance evaluations, and sprint retrospective reports prepared throughout the project lifecycle.

The documentation follows the guidelines provided by the **Software Engineering Teaching Unit, Faculty of Science, University of Kelaniya**.

---

## Project Overview

**Appliances.lk** is a single-vendor e-commerce and repair service management platform designed for a mobile accessories retail business.

The system enables customers to browse and purchase products, manage shopping carts, place orders, make online payments, request device repairs, track service progress, and communicate with administrators through real-time support chat.

It also provides an administrative dashboard for managing products, inventory, customer orders, repairs, promotional campaigns, and storefront content.

The platform integrates **Google Gemini AI** to assist customers with product-related questions.

### Main Features

**E-Commerce**
- Product catalogue, categories, search and filtering
- Product details, images and customer reviews
- Shopping cart and checkout
- PayHere payment integration and Cash on Delivery
- Order management and tracking
- Loyalty points and rewards

**Repair Services**
- Online repair request submission
- Administrative repair approval and rejection
- Repairer assignment and repair progress updates
- Customer repair history and notifications

**Administration**
- Product, category and inventory management
- Order and repair management
- Customer and user administration
- Promotional campaigns and banners
- Seasonal storefront themes
- Live customer support management

**Additional Features**
- Registration, login and email verification
- Forgot-password and password-reset functionality
- Role-based authentication and authorization
- Real-time communication using Socket.IO
- Google Gemini-powered AI product assistant
- Email and in-app notifications

---

## Development Team

| Name | Student Number |
|---|---|
| G.G. Lakshitha Madushan | SE/2021/033 |
| H. Buddhika Madumali | SE/2021/042 |
| Praveen Dedigama | SE/2021/031 |
| Induwara Mihisara | SE/2021/025 |

**Degree:** B.Sc. (Hons) Software Engineering  
**University:** University of Kelaniya  
**Faculty:** Faculty of Science  
**Academic Year:** 2026

---

## Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite, Tailwind CSS |
| Backend | NestJS, Node.js, TypeScript |
| Database | PostgreSQL |
| ORM | TypeORM |
| Authentication | bcrypt, server-side sessions, HTTP-only cookies, RBAC |
| Real-Time Communication | Socket.IO |
| AI Integration | Google Gemini API |
| Payment Gateway | PayHere |
| Email Notifications | Gmail-based email integration |
| File Storage | Azure Blob Storage |
| Containerization | Docker |
| Frontend Web Server | Nginx |
| Cloud Platform | Microsoft Azure |
| Cloud Hosting | Azure Container Apps |
| Container Registry | Azure Container Registry |
| Infrastructure as Code | Terraform |
| Monitoring | Azure Log Analytics |
| CI/CD | GitHub Actions |
| Unit Testing | Jest, Vitest |
| Performance Testing | Grafana k6 |
| Web Quality Assessment | Google Lighthouse |
| Version Control | Git and GitHub |

---

## System Architecture

Appliances.lk follows a **layered modular-monolith architecture**.

The frontend communicates with the NestJS backend through REST APIs and Socket.IO. The backend uses TypeORM to manage application data in PostgreSQL and connects to external services for payments, AI functionality, email notifications, and product-image storage.

```text
                  Customers / Administrators / Repairers
                                |
                              HTTPS
                                |
                   React + TypeScript Frontend
                                |
                         Nginx Reverse Proxy
                                |
                       NestJS Backend API
                                |
              +-----------------+----------------+
              |                 |                |
          PostgreSQL       Azure Blob       External Services
           Database          Storage         - PayHere
                                            - Google Gemini
                                            - Email Provider
```

The production environment is hosted using Azure Container Apps, with infrastructure provisioned through Terraform.

---

## Documentation Deliverables

The following documents are organized according to their respective academic and technical categories.

| # | Deliverable | Repository Location | Current Status |
|---|---|---|---|
| 1 | Software Requirements Specification (SRS) | `srs/srs-final.pdf` | Final revision under review |
| 2 | Software Design Specification (SDS) | `sds/sds-final.pdf` | Updated draft prepared; final verification pending |
| 3 | Test Coverage Report | `testing/coverage-report.pdf` | Report prepared |
| 4 | Test Case Register | `testing/test-register.pdf` | Report prepared |
| 5 | OWASP Top 10 Compliance Evidence | `security/owasp-checklist.pdf` | Report prepared; remaining controls documented |
| 6 | Performance Testing Report | `testing/performance-report.pdf` | Report prepared |
| 7 | Sprint 5–Sprint 8 Retrospective Report | `retrospectives/` | Report prepared from project-board evidence |

**Documentation note:** The locations above represent the intended repository structure. File names and publication statuses should be confirmed against the files committed to this repository. A prepared report does not necessarily mean every requirement has passed verification.

### Recommended Repository Structure

```text
documents/
|
|-- README.md
|
|-- srs/
|   `-- srs-final.pdf
|
|-- sds/
|   `-- sds-final.pdf
|
|-- testing/
|   |-- coverage-report.pdf
|   |-- test-register.pdf
|   `-- performance-report.pdf
|
|-- security/
|   `-- owasp-checklist.pdf
|
`-- retrospectives/
    `-- sprint-5-to-8-retrospective.pdf
```

---

## Source Code Repositories

The project is maintained under the [AppliancesLk GitHub Organization](https://github.com/AppliancesLk).

| Repository | Description |
|---|---|
| [Frontend](https://github.com/AppliancesLk/frontend) | React customer storefront, admin dashboard and repairer interfaces |
| [Backend](https://github.com/AppliancesLk/backend) | NestJS REST APIs, business logic, authentication, PostgreSQL and service integrations |
| [Infrastructure](https://github.com/AppliancesLk/infra) | Azure provisioning, infrastructure configuration and deployment resources |
| [GitHub Project Board](https://github.com/orgs/AppliancesLk/projects/1/views/1) | Project tasks, issue tracking, planning and progress |

---

## Deployment Environments

Appliances.lk has separate development/staging and production environments deployed using Microsoft Azure.

### Development / Staging

**Frontend:**  
https://appliances-web-dev.graysky-2e2a33e6.centralindia.azurecontainerapps.io

**Backend API:**  
https://appliances-api-dev.graysky-2e2a33e6.centralindia.azurecontainerapps.io

**Azure Resource Group:** `rg-appliances-dev`

This environment is used for development integration, functional testing and deployment validation.

### Production

**Frontend:**  
https://appliances-web-prod.nicehill-aa13b60f.centralindia.azurecontainerapps.io

**Backend API:**  
https://appliances-api-prod.nicehill-aa13b60f.centralindia.azurecontainerapps.io

**Azure Resource Group:** `rg-appliances-prod`

**Azure Region:** Central India

Production infrastructure includes:

- Azure Container Apps for frontend and backend hosting
- Azure Database for PostgreSQL Flexible Server
- Azure Container Registry
- Azure Blob Storage
- Azure Log Analytics
- User-assigned managed identities and Azure RBAC
- Terraform-managed infrastructure

The production frontend and backend database-health endpoints have been verified successfully.

**Payment note:** PayHere is configured in sandbox mode in the recorded production configuration. This should not be interpreted as verification of live financial transactions.

---

## Software Testing and Quality Assurance

Software quality assurance was carried out using automated tests, documented functional test cases, performance tests and security reviews.

### Automated Testing

| Metric | Recorded Result |
|---|---:|
| Backend Test Suites | 28 |
| Backend Automated Tests | 382 |
| Frontend Test Files | 24 |
| Frontend Automated Tests | 307 |
| Backend Line Coverage | 60.04% |
| Frontend Line Coverage | 6.30% |

Coverage figures describe the recorded coverage scope and should not be interpreted as proof of compliance with all new-code coverage targets.

### Functional Test Case Register

| Metric | Recorded Result |
|---|---:|
| Total Test Cases | 82 |
| Passed | 67 |
| Blocked | 15 |
| Failed | 0 |
| Pass Rate Across All Documented Cases | 81.71% |

Blocked cases remain pending verification and are not counted as passed cases.

The full test-case register records scenarios, expected results, actual outcomes and available supporting evidence.

---

## Performance Testing

Performance testing was performed using **Grafana k6** to evaluate API response times, throughput and system behavior under simulated concurrent users.

### Recorded Load-Test Results

| Test Scenario | Average Response Time |
|---|---:|
| Single-User Baseline | 769.805 ms |
| 10 Concurrent Users | 739.061 ms |
| 25 Concurrent Users | 736.257 ms |
| 50 Concurrent Users | 768.231 ms |

**50-User Test Summary**

- Average response time: **768.231 ms**
- 95th-percentile response time: **748.280 ms**
- Throughput: **44.177 requests/second**
- Recorded request failures: **0**

The measured average response time under the 50-user workload did not exceed the baseline by the permitted 10% degradation threshold.

These results apply to the tested workload and do not establish performance compliance for every API endpoint or user journey.

---

## Security and OWASP Compliance

Appliances.lk was reviewed against the **OWASP Top 10 (2021)** security categories.

The security review covers:

- Broken access control
- Cryptographic failures
- Injection vulnerabilities
- Insecure design
- Security misconfiguration
- Vulnerable and outdated components
- Identification and authentication failures
- Software and data integrity failures
- Security logging and monitoring failures
- Server-side Request Forgery (SSRF)

Implemented security controls include:

- bcrypt password hashing
- Hashed authentication/session tokens
- Server-side session expiration and revocation
- NestJS authentication and role-based guards
- TypeORM-based database access
- HTTPS production endpoints
- Azure secret configuration
- Managed identity and role-based cloud access

The OWASP evidence report also identifies controls requiring further verification, including final dependency vulnerability results, login-abuse protections and security logging evidence.

**The security report records implementation evidence and remaining gaps; it is not a claim of complete OWASP certification.**

---

## Sprint Retrospectives

The project followed an iterative development process, using GitHub Projects for planning and task management.

The Sprint 5–Sprint 8 retrospective report documents:

- Work completed
- Successful practices
- Challenges and improvements
- Proposed action items
- Available sprint metrics
- Completed task records

The exported GitHub Project view contained **39 distinct tasks marked Done**, comprising **20 backend tasks and 19 frontend tasks**, with **23 linked pull requests**.

Because the export did not contain original sprint assignments or sprint-start snapshots, the retrospective distinguishes verified task records from reconstructed development-phase groupings.

The [project tracking board](https://github.com/orgs/AppliancesLk/projects/1/views/1) provides additional development history.

---

## Academic Information

**Module Code:** SENG 34213  
**Module Name:** System Development Project  
**Degree Programme:** B.Sc. (Hons) Software Engineering  
**Academic Unit:** Software Engineering Teaching Unit  
**Faculty:** Faculty of Science  
**University:** University of Kelaniya  
**Country:** Sri Lanka  
**Project Year:** 2026

The documentation in this repository supports the university's project assessment process by providing requirements, design, implementation traceability, test evidence, security assessment, performance evaluation and sprint-review records.

---

## Project Links

- **GitHub Organization:** https://github.com/AppliancesLk
- **Project Board:** https://github.com/orgs/AppliancesLk/projects/1/views/1
- **Production Application:** https://appliances-web-prod.nicehill-aa13b60f.centralindia.azurecontainerapps.io
- **Development Application:** https://appliances-web-dev.graysky-2e2a33e6.centralindia.azurecontainerapps.io

---

## Project Team

Developed by the **Appliances.lk Development Team** as part of the SENG 34213 System Development Project.

**University of Kelaniya — Faculty of Science — 2026**

*Shop Smart · Repair Easy · Stay Connected*
