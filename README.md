# FinTech Transaction & Reconciliation System

A Java backend project for simulating financial transactions, managing ledger entries, and detecting inconsistencies through reconciliation.

> **Project status:** In Development

## Overview

This project aims to demonstrate backend engineering concepts through a simulated wallet transaction system. It will focus on transactional consistency, ledger integrity, secure REST APIs, and automated reconciliation.

## Technology Stack

- Java 21
- Spring Boot
- Maven
- Spring Web
- Spring Data JPA
- MySQL
- Spring Security
- Bean Validation
- Flyway Database Migrations
- Spring Boot Actuator
- Git and GitHub

## Planned Features

- [ ] User registration and authentication
- [ ] Demo wallet account management
- [ ] REST APIs for simulated money transfers
- [ ] Transaction history and status tracking
- [ ] Ledger entries for successful transfers
- [ ] Protection against duplicate transfer requests
- [ ] Database transaction rollback and consistency safeguards
- [ ] Reconciliation of transaction records, ledger entries, and account balances
- [ ] Detection and reporting of missing, duplicate, or mismatched entries
- [ ] Unit and integration testing
- [ ] Docker-based setup and AWS deployment

## Initial Progress

- [x] Generated the Spring Boot Maven project
- [x] Added the required starter dependencies
- [x] Created the Git repository and published the initial project scaffold

## Getting Started

### Prerequisites

- JDK 21
- Git
- MySQL (required when database integration is implemented)

The application setup and execution instructions will be added after the initial application and database configuration are verified.

## Project Scope

This is an educational portfolio project. Transactions will use simulated demo account balances; the application will not transfer real money or connect to real banking systems.

## Repository

[View the source code on GitHub](https://github.com/Dev2D4V/fintech-transaction-reconciliation)