# 🚛 Transport Management System (TMS)

[![Laravel](https://img.shields.io/badge/Laravel-10.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![PHP](https://img.shields.io/badge/PHP-8.1%2B-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![MySQL](https://img.shields.io/badge/MySQL-8.0%2B-4479A1?style=for-the-badge&logo=mysql&logoColor=white)](https://mysql.com)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)](https://getbootstrap.com)
[![License](https://img.shields.io/badge/License-Proprietary-red.svg?style=for-the-badge)]()
[![Copyright](https://img.shields.io/badge/Copyright-All_Rights_Reserved-black.svg?style=for-the-badge)]()

> ### ⚠️ STRICT PROPRIETARY & COPYRIGHT NOTICE
> **© 2026 Suyog. All Rights Reserved.**  
> This software, codebase, architecture, and documentation are strictly **proprietary and confidential**.  
> **NO ONE is permitted to copy, reproduce, clone, distribute, publish, modify, sell, or reuse any part of this project without explicit prior written authorization from the owner (Suyog).** Unauthorized copying, distribution, or reverse engineering constitutes copyright infringement and will lead to immediate legal action under applicable Cyber Laws, Intellectual Property Rights, and Copyright Acts.

A comprehensive, enterprise-grade, secure, and responsive **Transport Management System (TMS)** built for transport and logistics businesses that own commercial vehicles (e.g., *Tata 407, Mahindra Bolero Pickup, Ashok Leyland Dost, Eicher Pro, BharatBenz Trucks*) and attach them to client companies on contract or execute on-demand trips.

---

## 🌟 Key Highlights & Architecture

The application is structured into four integrated access interfaces:

1. **Admin & Fleet Operations Portal** — Complete management of vehicles, drivers, contracts, trips, fuel entries, maintenance, and full double-entry accounting.
2. **Customer / Client Portal** — Self-service portal where clients track contract trips, review real-time shipment status, download GST invoices, and pay online.
3. **Driver Mobile / PWA Portal** — Mobile-friendly dashboard for drivers to receive trip assignments, start/complete trips, submit odometer readings, and upload Proof of Delivery (POD).
4. **REST API v1 (Sanctum Auth)** — Secure REST endpoints for mobile apps, IoT GPS trackers, and third-party logistics integrations.

---

## 📋 Comprehensive Feature Breakdown

### 1. Fleet & Asset Management
- **Vehicle Profiles**: Detailed logs for registration number, vehicle type, chassis/engine number, load capacity, and fuel type.
- **Compliance & Expiry Monitoring**: Automatic tracking and proactive status alerts for:
  - Fitness Certificates
  - Commercial Insurance
  - PUC (Pollution Under Control)
  - State & National Permits
- **Driver Management**: Driver licensing details, emergency contacts, salary schedule, bank account records, and document repository.
- **Vehicle-Driver Assignment**: Dynamic association of drivers to primary and secondary vehicles.

### 2. Operations & Dispatch
- **Company / Client Directory**: Complete KYC tracking, billing type (`monthly_fixed`, `per_trip`, `per_km`), credit periods, and GSTIN validation.
- **Contract Management**: Rate contracts with start/end validity dates, terms, and billing configurations.
- **Trip Lifecycle**:
  - Scheduling & vehicle/driver dispatch
  - Start odometer & departure time logging
  - In-transit live status updates
  - Delivery completion & closing odometer logging
  - Digital Proof of Delivery (POD) photo upload and signature verification
- **GPS Tracking**: Real-time vehicle location recording and telemetry view.

### 3. Finance & Accounts
- **GST Invoicing**:
  - Auto-generated GST-compliant tax invoices with CGST, SGST, or IGST based on state codes.
  - Automated PDF invoice generation.
  - Invoice payment status lifecycle: `draft` ➔ `issued` ➔ `partially_paid` ➔ `paid` ➔ `cancelled`.
- **Payment Collection & QR**:
  - UPI QR code and online payment integration via Razorpay.
  - Webhook listener for verified transaction callbacks.
- **Disbursements & Payments Made**:
  - Driver salary disbursements and trip advances.
  - Fuel payments and workshop vendor bills.
- **Accounts Receivable & Payable**:
  - Outstanding balances per client with aging analysis.
  - Pending liabilities for vendors, workshops, and fuel pumps.
- **Bank Reconciliation**: Statement upload and reconciliation against recorded receipts and payments.
- **Profit & Loss (P&L)**: Real-time revenue vs. operating expense analytics broken down per vehicle and client.

### 4. Security & Administration
- **Role-Based Access Control (RBAC)**: Fine-grained permissions powered by roles (`super_admin`, `fleet_manager`, `accountant`, `driver`, `client`).
- **Audit Logs**: Immutable activity logs tracking sensitive operational and financial mutations.
- **Two-Factor Authentication (2FA)** & Session Monitoring.
- **Automated Database Backups**: One-click database dump and download.

---

## 🛠 Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Backend Framework** | Laravel 10.x |
| **Language** | PHP 8.1 / 8.2 |
| **Database** | MySQL 5.7+ / MariaDB 10.4+ |
| **Authentication** | Laravel Session Auth + Laravel Sanctum (Tokens) |
| **Authorization** | Spatie Laravel-Permission & Native Model Policies |
| **Frontend UI** | Blade Templates, Custom Dark Glassmorphism CSS, Bootstrap 5.3, Bootstrap Icons |
| **Charts & Visuals** | Chart.js 4.x |
| **Payments** | Razorpay SDK + UPI Integration + Webhooks |

---

## 🚀 Installation & Local Setup

### Prerequisites
- **PHP** >= 8.1 with `pdo_mysql`, `mbstring`, `openssl`, `curl`, `gd`, `fileinfo` extensions enabled in `php.ini`.
- **Composer** (v2+)
- **MySQL / MariaDB** (via XAMPP, Laragon, Docker, or native service)
- **Git**

### Step-by-Step Setup

#### 1. Navigate to the Project Root
```bash
cd "d:/Suyog project/tms"
```

#### 2. Install Composer Dependencies
```bash
composer install
```

#### 3. Environment Setup
Copy the sample environment file and configure your local settings:
```bash
cp .env.example .env
```

Ensure your `.env` contains your database credentials:
```env
APP_NAME="Transport Management System"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://127.0.0.1:8000

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=tms_db
DB_USERNAME=root
DB_PASSWORD=

# Payment Gateway (Optional / Sandbox)
RAZORPAY_KEY_ID=rzp_test_your_key_id
RAZORPAY_KEY_SECRET=your_key_secret
RAZORPAY_WEBHOOK_SECRET=your_webhook_secret
```

#### 4. Generate Application Key
```bash
php artisan key:generate
```

#### 5. Run Migrations & Seed Default Data
```bash
php artisan migrate --seed
```

#### 6. Create Storage Symlink
```bash
php artisan storage:link
```

#### 7. Start the Development Server
```bash
php artisan serve --host=127.0.0.1 --port=8000
```
The application will be accessible at: **[http://127.0.0.1:8000](http://127.0.0.1:8000)**

---

## 🔑 Default Login Credentials

All seed accounts come pre-configured with the standard password: **`Admin@123456`**

| Role | Username / Identifier | Password | Access Level & Scope |
| :--- | :--- | :--- | :--- |
| **Super Admin** | `admin@tms.com` or `admin` | `Admin@123456` | Full administrative, financial, operational, and system control |
| **Fleet Operations Manager** | `manager@tms.com` or `manager` | `Admin@123456` | Vehicles, drivers, trips, fuel, maintenance (no billing/admin access) |
| **Senior Accountant** | `accounts@tms.com` or `accountant` | `Admin@123456` | Invoices, payments, receivables, payables, financial reports |
| **Driver (Mobile / PWA)** | `driver@tms.com` or `driver` | `Admin@123456` | Driver mobile dashboard, trip assignments, POD upload |
| **Customer / Client Portal** | `client@tms.com` or `client` | `Admin@123456` | Client portal, active shipments, invoices, payment history |

---

## 🌐 Route & Endpoint Structure

### 1. Web Portal Routes

| Prefix | Access Level | Description |
| :--- | :--- | :--- |
| `/login`, `/logout` | Public / Auth | Authentication, session creation, forgot password recovery |
| `/admin/*` | `super_admin`, `fleet_manager`, `accountant` | Administrative portal protected by RBAC middleware |
| `/customer/*` | `client` / `company` | Client self-service portal |
| `/driver/*` | `driver` | Driver mobile portal |
| `/files/*` | Auth | Authenticated and authorized file downloads (PODs, RC, Permits) |

### 2. REST API v1 (`/api/v1/`)

Authenticate by sending `POST /api/v1/login` to receive a Bearer token. Include header: `Authorization: Bearer <token>` in subsequent requests.

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/v1/login` | Authenticate and obtain Sanctum Bearer token |
| `POST` | `/api/v1/logout` | Revoke current access token |
| `GET` | `/api/v1/user` | Fetch authenticated user profile |
| `GET` | `/api/v1/vehicles` | List fleet vehicles (supports `?status=available` query) |
| `GET` | `/api/v1/drivers` | List active drivers and contact details |
| `GET` | `/api/v1/companies` | List registered client companies |
| `GET` | `/api/v1/trips` | List trip records and dispatch states |
| `POST` | `/api/v1/trips/{id}/status` | Update trip progression (`started`, `completed`) |
| `POST` | `/api/v1/trips/{id}/location` | Post GPS telemetry updates |
| `POST` | `/api/v1/trips/{id}/pod` | Upload digital POD image file |
| `GET` | `/api/v1/invoices` | List invoices and billing statuses |
| `GET` | `/api/v1/gps/vehicles` | Get latest telemetry coordinates for active fleet |
| `POST` | `/webhooks/razorpay` | External payment gateway webhook listener |

---

## 📂 Directory Layout

```
tms/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Admin/             # Admin, fleet, and financial controllers
│   │   │   ├── Api/V1/            # REST API endpoints & Webhooks
│   │   │   ├── Auth/              # Login, logout, password resets
│   │   │   ├── Customer/          # Client self-service portal controllers
│   │   │   └── Driver/            # Driver mobile interface controllers
│   │   └── Middleware/            # RBAC, CSRF, and security middleware
│   └── Models/                    # Eloquent models (Vehicle, Trip, Invoice, etc.)
├── config/                        # Laravel core & package configuration
├── database/
│   ├── migrations/                # Database schema definitions
│   └── seeders/                   # Initial roles, settings, demo fleet & users
├── public/                        # Entry point (index.php) and compiled assets
├── resources/
│   ├── css/                       # Custom styles
│   └── views/
│       ├── admin/                 # Admin Blade templates
│       ├── customer/              # Customer portal views
│       ├── driver/                # Driver portal views
│       ├── layouts/               # Master layout templates with dark glassmorphic styling
│       └── auth/                  # Authentication screens
├── routes/
│   ├── web.php                    # Web routes (Admin, Customer, Driver)
│   └── api.php                    # Sanctum API & webhook routes
└── storage/                       # Uploaded PODs, vehicle documents, and logs
```

---

## 🔒 Security Best Practices Implemented

1. **SQL Injection Prevention**: 100% Eloquent ORM parameterized queries.
2. **CSRF Protection**: All state-modifying POST/PUT/DELETE forms protected with CSRF tokens; external webhooks use HMAC signature verification.
3. **Password Security**: Strong hashing with Bcrypt algorithm (`Hash::make`).
4. **Secure File Storage**: Uploaded driver licenses, vehicle RCs, and PODs are protected from direct web enumeration via an authenticated streaming proxy (`FileController`).
5. **Rate Limiting**: Built-in API throttling (`throttle:10,1` on login, `throttle:api` on data queries).
6. **Audit Trail**: Every create, update, and delete operation on critical financial or fleet models is captured in the `audit_logs` table.

---

## ⚖️ Legal & Copyright Notice

**Copyright © 2026 Suyog. All Rights Reserved.**

### 🛑 Prohibition of Unauthorized Copying & Distribution
This repository, its source code, database structures, UI/UX designs, workflows, business logic, and associated assets are the sole and exclusive intellectual property of **Suyog**.

- **No Unauthorized Duplication**: No individual, entity, or organization has permission to copy, clone, scrape, fork, mirror, download for re-distribution, decompile, or reverse engineer this codebase, whether in original or modified form.
- **No Commercial Exploitation**: It is strictly forbidden to use this software or any portion of its code for commercial products, client deployments, SaaS applications, or derivative works without an explicit, notarized written license agreement signed by **Suyog**.
- **No Plagiarism or Academic Misuse**: Using this project or any part thereof without attribution or as personal/academic submission is strictly forbidden.

### ⚖️ Legal Repercussions & Intellectual Property Enforcement
Any unauthorized copying, possession, display, distribution, or reproduction of this project constitutes direct **Copyright Infringement** and a violation of:
1. **The Indian Copyright Act, 1957** (Sections 51, 63, and 64 — punishable with fines and imprisonment).
2. **The Information Technology Act, 2000** (Sections 43, 66, and 66B — dealing with data theft and unauthorized access).
3. **International Copyright Treaties & Conventions** (Berne Convention & TRIPS Agreement).
4. **Digital Millennium Copyright Act (DMCA)**: Immediate takedown requests, repository removal, and DMCA strikes will be served against any unauthorized forks, mirrors, or published instances across GitHub, GitLab, Bitbucket, cloud hosting providers, and web platforms.

> Violators will be prosecuted to the maximum extent permitted by law, including claims for statutory damages, commercial profits recovery, injunctions, and legal expenses.

---

### 📩 Contact for Written Permission & Licensing
If you wish to obtain authorized commercial licensing, custom deployment, or partnership permissions, please contact the author directly:
- **Project Owner / Author**: Suyog
- **Email**: info@suyogtransport.com / admin@tms.com
