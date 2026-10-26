# FinTech Transaction & Reconciliation System

A Java and Spring Boot backend application designed to simulate financial transactions, maintain a transaction ledger, and identify data inconsistencies through automated reconciliation.

## Overview

The FinTech Transaction & Reconciliation System models the core backend operations of a digital wallet platform. It focuses on reliable transaction processing, database consistency, ledger integrity, secure REST APIs, and reconciliation reporting.

The system uses simulated wallet balances to demonstrate how financial records can be processed, verified, and audited using backend engineering principles.

## Key Features

- **Account Management:** Manage demo wallet accounts, account balances, and account ownership.
- **Transaction Processing:** Transfer simulated funds between accounts with validation and transaction status tracking.
- **Atomic Database Operations:** Keep balance updates, transaction records, and ledger entries consistent using database transactions.
- **Idempotent Transfers:** Prevent duplicate processing when the same transfer request is retried.
- **Ledger Management:** Maintain debit and credit entries associated with successful transfers.
- **Automated Reconciliation:** Compare transaction records, ledger entries, and stored account balances.
- **Discrepancy Detection:** Identify missing entries, duplicate entries, amount mismatches, and balance inconsistencies.
- **Reconciliation Reports:** Store reconciliation results and provide visibility into detected issues.
- **Authentication and Authorization:** Protect API endpoints using Spring Security and role-based access control.
- **Input Validation and Error Handling:** Validate incoming requests and return consistent API error responses.
- **Automated Testing:** Verify business logic, transactional behavior, authorization, and reconciliation rules.
- **Cloud Deployment:** Package the application with Docker and prepare it for deployment on AWS.

## Technology Stack

| Category | Technologies |
|---|---|
| Language | Java 21 |
| Backend Framework | Spring Boot |
| API Development | Spring Web, REST APIs |
| Database | MySQL |
| Persistence | Spring Data JPA, Hibernate |
| Security | Spring Security, JWT authentication |
| Validation | Jakarta Bean Validation |
| Database Migrations | Flyway |
| Build Tool | Maven |
| Testing | JUnit 5, Mockito, Spring Boot Test |
| API Documentation | Swagger / OpenAPI |
| API Testing | Postman |
| Containerization | Docker, Docker Compose |
| Cloud Platform | Amazon Web Services (AWS) |
| Version Control | Git, GitHub |

## System Architecture

The application follows a modular monolithic architecture with clearly separated responsibilities.

```text
Client / Postman / Dashboard
            |
            v
      Spring Security
            |
            v
      REST Controllers
            |
            v
       Service Layer
        /         \
       v           v
Transaction     Reconciliation
  Service          Service
       \           /
        v         v
       Repository Layer
              |
              v
            MySQL
              |
     ---------------------
     |        |          |
   Users   Accounts   Transactions
                         |
                         v
                   Ledger Entries
                         |
                         v
                Reconciliation Reports
```

### Core Components

- **Authentication Module:** User registration, login, and access control.
- **Account Module:** Account ownership, status, and balance management.
- **Transaction Module:** Transfer validation, idempotency, transaction lifecycle, and atomic database operations.
- **Ledger Module:** Traceable debit and credit records for successful transfers.
- **Reconciliation Module:** Validation of transaction records, ledger movements, and account balances.
- **Reporting Module:** Reconciliation run history, issue details, and resolution tracking.

## Database Design

The planned relational schema includes the following entities:

- `users` — user identity, password hashes, and roles.
- `accounts` — account ownership, currency, status, and balances.
- `transactions` — transfer references, amounts, statuses, and timestamps.
- `ledger_entries` — debit and credit movements associated with transfers.
- `reconciliation_runs` — execution details and summary statistics.
- `reconciliation_issues` — detected discrepancies and their review status.

Primary keys, foreign keys, indexes, uniqueness constraints, and appropriate transaction isolation will be used to protect data integrity.

## Transaction Consistency

For every successful simulated transfer, the system is designed to:

1. Validate the transfer request and account permissions.
2. Verify that the accounts are valid and the sender has sufficient funds.
3. Prevent duplicate processing using an idempotency key.
4. Update the sender's and receiver's balances atomically.
5. Save the transaction record and corresponding debit and credit ledger entries.
6. Roll back the transfer changes if a required database operation fails.

For an account, its ledger-derived balance is calculated as:

**Expected Balance = Opening Balance + Total Credits − Total Debits**

Reconciliation compares this expected balance with the stored account balance and reports discrepancies for investigation.

## REST API Design

The API surface is designed around the following operations:

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/auth/register` | Register a user |
| POST | `/api/auth/login` | Authenticate a user |
| GET | `/api/accounts` | List accessible accounts |
| GET | `/api/accounts/{id}/balance` | Retrieve an account balance |
| POST | `/api/transfers` | Initiate a simulated transfer |
| GET | `/api/transactions` | Retrieve transaction history |
| GET | `/api/transactions/{id}` | Retrieve transaction details |
| GET | `/api/accounts/{id}/ledger` | Retrieve account ledger entries |
| POST | `/api/admin/reconciliation-runs` | Start a reconciliation run |
| GET | `/api/admin/reconciliation-runs/{id}` | Retrieve reconciliation results |
| GET | `/api/admin/reconciliation-issues` | List detected discrepancies |

These endpoints describe the intended API contract; their implementation and availability depend on the corresponding development work.

## Testing Strategy

The testing strategy covers:

- Unit tests for transfer validation and reconciliation calculations.
- Integration tests for persistence, database constraints, and transaction rollback.
- API tests for request validation and response handling.
- Security tests for authentication, authorization, and account ownership.
- Idempotency tests for repeated transfer requests.
- Concurrency tests to help prevent overdrafts and duplicate processing.
- Reconciliation tests using deliberately inconsistent test records.

## Deployment Architecture

The deployment target is AWS, using Docker to package the application.

The planned deployment environment includes:

- **Amazon EC2:** Host the Spring Boot application.
- **Amazon RDS for MySQL:** Provide managed relational database storage.
- **Security Groups:** Restrict inbound application and database traffic.
- **HTTPS:** Secure client-to-application communication.
- **GitHub Actions:** Automate application builds and test execution.
- **Application Monitoring:** Health checks, application logs, and operational diagnostics.

Deployment configuration, credentials, and database access will be managed separately from source code.

## Getting Started

### Prerequisites

- JDK 21
- Git
- Internet access for downloading Maven dependencies
- MySQL for database integration
- IntelliJ IDEA or another Java IDE

### Clone the Repository

```bash
git clone https://github.com/Dev2D4V/fintech-transaction-reconciliation.git
cd fintech-transaction-reconciliation
```

### Build the Application

On Windows:

```powershell
.\mvnw.cmd clean package
```

On Linux or macOS:

```bash
./mvnw clean package
```

Run the build after the required database configuration and application implementation are in place. Database credentials should be supplied through local environment configuration rather than committed to the repository.

## Project Objectives

This project demonstrates practical knowledge of:

- Java and Spring Boot backend development.
- REST API design and layered application architecture.
- Relational database modelling and SQL.
- Transaction management and concurrency control.
- Idempotency and data integrity.
- Ledger-based reconciliation and discrepancy reporting.
- Authentication, authorization, and input validation.
- Automated testing, Git workflows, Docker, and AWS deployment.

## Scope and Disclaimer

This is an educational portfolio project that uses simulated wallet accounts and balances. It does not connect to real banking systems, process actual payments, or transfer real money.

## Repository

[GitHub: FinTech Transaction & Reconciliation System](https://github.com/Dev2D4V/fintech-transaction-reconciliation)