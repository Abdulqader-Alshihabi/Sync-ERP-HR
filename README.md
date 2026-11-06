# Saaed (ساعد) - Enterprise HR & Payroll ERP Suite

[![Architecture](https://img.shields.io/badge/Architecture-Full--Stack%20Decoupled-blue?style=for-the-badge)](https://github.com/Abdulqader-Alshihabi/Sync-ERP-HR)
[![Frontend](https://img.shields.io/badge/Frontend-React%2019%20%7C%20TypeScript-61DAFB?style=for-the-badge)](https://github.com/Abdulqader-Alshihabi/Sync-ERP-HR)
[![Backend](https://img.shields.io/badge/Backend-Django%205%20%7C%20DRF-092E20?style=for-the-badge)](https://github.com/Abdulqader-Alshihabi/Sync-ERP-HR)
[![Database](https://img.shields.io/badge/Database-PostgreSQL%2015-336791?style=for-the-badge)](https://github.com/Abdulqader-Alshihabi/Sync-ERP-HR)
[![Security](https://img.shields.io/badge/Security-Fernet%20PII%20Encryption%20at%20Rest-red?style=for-the-badge)](https://github.com/Abdulqader-Alshihabi/Sync-ERP-HR)
[![Compliance](https://img.shields.io/badge/Compliance-Saudi%20Labor%20Law%20%7C%20WPS-006C35?style=for-the-badge)](https://github.com/Abdulqader-Alshihabi/Sync-ERP-HR)

Category: Enterprise Resource Planning (ERP) & Human Resource Management System (HRMS)  
Project Scope: Enterprise Summer Internship & Corporate Automation  
Lead Full-Stack Software Engineer: Abdulqader Alshihabi  

---

## Commercial Notice and Data Protection

> [!IMPORTANT]
> Proprietary Architecture Notice:  
> This repository serves as an Architectural Case Study and Technical Specification for the Saaed (ساعد) Enterprise HR & Payroll ERP platform. In compliance with commercial non-disclosure agreements (NDA), banking security protocols, and employee data privacy standards, production database dumps, proprietary payroll spreadsheets, cryptographic secret keys, and company server configurations are securely maintained in isolated enterprise infrastructure.

---

## Executive Summary

Saaed (ساعد) is an Arabic-first enterprise Human Resources and ERP platform engineered to streamline corporate workforce administration, automated payroll calculation, regulatory compliance, and cross-departmental approval workflows.

Built with a decoupled architecture featuring a React 19 Single Page Application (SPA) communicating over a secure REST API with a Django 5 backend running across 15 modular sub-applications and a PostgreSQL database, the system enforces end-to-end data integrity, field-level encryption, and strict role-based access controls.

### Key Capabilities
- **Saudi Labor Law Automation**: Automated calculation of General Organization for Social Insurance (GOSI) deductions, End-of-Service (EOS) gratuity accruals, and statutory overtime rates.
- **Wages Protection System (WPS) & Banking Automation**: Dynamic generation and validation of bank-compliant payroll workbooks (including Al Rajhi Bank WPS formats).
- **Unified Request Inbox & Polymorphic Assignment**: Multi-tier request routing handling leaves, financial expenses, salary certificates, promotions, transfers, disciplinary records, and resignations.
- **Enterprise PII Encryption at Rest**: Sensitive employee records (national IDs, bank IBANs, salary structures) encrypted using symmetric Fernet keys before database persistence.
- **Comprehensive Security & Audit Trails**: Hardened against penetration vulnerabilities (IDOR, CSRF, Session Fixation, Privilege Escalation) with immutable event logging.

---

## System Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│               Client-Side Web Application (React 19 + Vite)            │
│  - Navigation: TanStack Router (Type-Safe, Search-Param Validation)    │
│  - State & Caching: TanStack React Query v5 (Optimistic Updates)       │
│  - Design System: Tailwind CSS v4, Lucide Icons, Modern Dark/Light     │
│  - Localization: Native Arabic-first (RTL) with modular i18n support   │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼  HTTP / REST API (/api/v1/*)
┌────────────────────────────────────────────────────────────────────────┐
│                 Django 5 & Django REST Framework (DRF)                 │
│  - Authentication: JWT with refresh rotation & secure HTTP-only cookies │
│  - Access Control: Role-Based (RBAC) & Sector-Level Authorization      │
│  - Modules (15+ Apps): Employees, Attendance, Payroll, Leaves,         │
│                        Documents, Performance, Approvals, Reports      │
│  - Crypto Layer: Cryptography Fernet for PII Field Encryption          │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼  Relational Persistence
┌────────────────────────────────────────────────────────────────────────┐
│                   PostgreSQL 15 Enterprise Database                    │
│  - Schema: Normalized tables with polymorphic metadata JSON payloads   │
│  - Integrity: Strict foreign-key cascades, check constraints, & indexes│
│  - Audit Logging: Immutable tracking for all financial transactions    │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Core Technical Modules Implemented

### 1. Saudi Payroll Engine & WPS Banking Integration
- Automates monthly gross-to-net salary reconciliations factoring in base pay, housing allowances, transport stipends, unpaid leave deductions, and overtime matrices.
- Complies with Saudi GOSI calculation rules for Saudi nationals and expatriate workforces.
- Generates verified Microsoft Excel and CSV payroll data matching Saudi Wages Protection System (WPS) standards and commercial bank ingestion layouts.

### 2. Unified Request Engine & Assignment Queue
- Implemented a unified `hr_requests` architecture utilizing polymorphic JSON payloads (`metadata`) to eliminate schema duplication across leave, expense, promotion, and disciplinary requests.
- Multi-tier assignment matrix enforcing strict permission boundaries:
  - `HR Manager`: Oversees entire organization queues, assigns tasks, delegates approvals, and views executive reports.
  - `HR Specialist`: Handles specifically assigned requests and tasks.
  - `Line Manager`: Submits and authorizes requests on behalf of direct reports.
  - `Employee`: Self-service portal for leave submissions, document requests, and tracking.

### 3. PII Security & Pentest Hardening
- Integrated symmetric field-level encryption using Python `cryptography.fernet`. Personal Identifiable Information (PII) including national identification numbers and bank account numbers are stored encrypted at rest.
- Successfully remediated security penetration test findings, enforcing strict object-level permission verification on all API endpoints to eliminate Insecure Direct Object References (IDOR).
- Rate-limiting and CSRF protection on all mutating endpoints.

---

## Technology Stack

| Layer | Technologies and Libraries |
| :--- | :--- |
| **Frontend Framework** | React 19, TypeScript, Vite |
| **Frontend State & Router** | TanStack Router, TanStack React Query v5 |
| **Styling & UI Tokens** | Tailwind CSS v4, Lucide Icons, Radix Primitives |
| **Backend Framework** | Django 5.x, Django REST Framework (DRF), Python 3.11+ |
| **Database & ORM** | PostgreSQL 15, Django ORM |
| **Cryptography & Security** | Cryptography (Fernet symmetric encryption), SimpleJWT |
| **DevOps & Containers** | Docker, Docker Compose, Nginx |
| **Testing & Quality** | Vitest (Frontend), Django TestCase (Backend), ESLint, Prettier |

---

## Engineering Credits

**Abdulqader Alshihabi**  
Computer Science Graduate | Software & AI Engineer  
- Portfolio: [https://abdulqader-alshihabi.github.io/](https://abdulqader-alshihabi.github.io/)  
- GitHub: [@Abdulqader-Alshihabi](https://github.com/Abdulqader-Alshihabi)  
- Email: [abdulqader.moh.2003@gmail.com](mailto:abdulqader.moh.2003@gmail.com)  
