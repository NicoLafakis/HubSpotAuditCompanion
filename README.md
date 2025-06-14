# HubSpotAuditCompanion

A lightweight, automated audit tool leveraging HubSpot's CRM and Automation APIs to surface data-quality and configuration issues. This README provides instructions for installation, configuration, and usage for developers.

---

## Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Configuration](#configuration)
5. [Usage](#usage)
6. [Project Structure](#project-structure)
7. [Development](#development)
8. [Deployment](#deployment)
9. [Testing](#testing)
10. [License](#license)

---

## Features

* **Authentication**: HubSpot Private App token and OAuth support.
* **Data-Quality Checks**:

  * Contacts: Missing/invalid fields, duplicates.
  * Deals: Property validation, orphaned deals.
  * Properties: Audit custom property definitions and usage.
* **Process-Configuration Audits**:

  * Workflows: Identify deprecated actions, review enrollment metrics.
  * Webhooks: Detect stale or error-prone subscriptions.
* **Reporting & Alerts**:

  * Health-score dashboard.
  * CSV export of flagged records.
  * Automated HubSpot Tickets and email notifications.

---

## Prerequisites

* **Node.js** v16+ and **npm**
* **Python** 3.9+
* **PostgreSQL** (or another SQL-compliant database)
* HubSpot account with a **Private App** (scopes below):

  * `crm.objects.contacts.read`
  * `crm.objects.deals.read`
  * `crm.properties.read`
  * `automation.flows.read`
  * `webhooks.read`
  * `tickets.write`

---

## Installation

1. **Clone the repo**

   ```bash
   git clone https://github.com/your-org/hubspot-audit-companion.git
   cd hubspot-audit-companion
   ```

2. **Install dependencies**

   * **Backend**

     ```bash
     cd backend
     npm install
     ```
   * **Frontend**

     ```bash
     cd frontend
     npm install
     ```

3. **Database setup**

   ```sql
   CREATE DATABASE hubspot_audit;
   ```

   ```bash
   cd backend
   npm run migrate
   ```

---

## Configuration

1. **Environment variables**

   Create `backend/.env`:

   ```ini
   HUBSPOT_API_KEY=<your_private_app_token>
   HUBSPOT_OAUTH_CLIENT_ID=<your_oauth_client_id>
   HUBSPOT_OAUTH_CLIENT_SECRET=<your_oauth_client_secret>
   OAUTH_REDIRECT_URI=<your_redirect_uri>
   DATABASE_URL=postgresql://user:pass@host:port/hubspot_audit
   PORT=3000
   ```

---

## Usage

1. **Start backend**

   ```bash
   cd backend
   npm start
   ```
2. **Start frontend**

   ```bash
   cd frontend
   npm start
   ```
3. **Access dashboard**
   Navigate to `http://localhost:3000`, connect your HubSpot account, and run audits.
4. **Scheduling audits**
   Configure a cron or serverless scheduler to call:

   ```http
   POST /api/audit/run
   ```

---

## Project Structure

```
hubspot-audit-companion/
├── backend/        # Node.js API service
│   ├── src/        # Business logic and API wrappers
│   ├── migrations/ # Database schema
│   └── package.json
├── frontend/       # React dashboard app
│   ├── src/        # UI components and pages
│   └── package.json
├── docs/           # Design docs, endpoint references
├── scripts/        # Deployment and utility scripts
└── README.md       # This file
```

---

## Development

* **Linting & Formatting**: ESLint + Prettier.
* **Mocking**: `npm run mock` in backend for simulated HubSpot data.
* **Hot Reload**: Uses `nodemon` and React Fast Refresh.

---

## Deployment

* **Serverless**: Deploy backend via AWS Lambda (Serverless framework).
* **Containerized**: Dockerfiles included.
* **CI/CD**: GitHub Actions workflows for build, test, deploy.

---

## Testing

* **Unit Tests**: Jest (backend), React Testing Library (frontend).
* **Integration**: Postman collections in `scripts/`.

Run all tests:

```bash
npm test
```

---

## License

Licensed under the MIT License. © 2025 Your Company Name
