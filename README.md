# 🏛️ CampusFix — ServiceNow Enterprise Facility Management Application

[![Live Demo](https://img.shields.io/badge/Live_Portfolio-GitHub_Pages-2563eb?style=for-the-badge&logo=github)](https://puvvalajithendra09-web.github.io/campusfix-servicenow/)
[![ServiceNow](https://img.shields.io/badge/ServiceNow-Washington_DC-81B5A1?style=for-the-badge&logo=servicenow)](https://service-now.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

An enterprise-grade scoped ServiceNow application engineered to eliminate fragmented email chains and spreadsheet-based campus operations. **CampusFix** centralizes facility bookings, maintenance defect tracking, automated approval workflows, and role-based access governance.

---

## 📸 Solution Architecture & Interface

| Modern Service Portal (`/sp?id=campusfix_home`) | Record Producer Submission |
| :---: | :---: |
| ![Portal Home](https://raw.githubusercontent.com/puvvalajithendra09-web/campusfix-servicenow/main/assets/portal_home.png) | ![Record Producer](https://raw.githubusercontent.com/puvvalajithendra09-web/campusfix-servicenow/main/assets/producer.png) |

| Approval Routing (`sysapproval_approver`) | Automated State Transition (`Work in Progress`) |
| :---: | :---: |
| ![Approval](https://raw.githubusercontent.com/puvvalajithendra09-web/campusfix-servicenow/main/assets/approval.png) | ![Ticket Updated](https://raw.githubusercontent.com/puvvalajithendra09-web/campusfix-servicenow/main/assets/ticket_wip.png) |

---

## ⚡ Core Technical Features

- **Scoped Application Governance:** Built in an isolated scope (`x_2061193_campus_1_`), extending core `task` architecture to ensure clean upgrade paths and instance stability.
- **Custom Service Portal Landing Page:** Designed a clean 4-card modern responsive interface (`campusfix_home`) catering to booking, maintenance reporting, real-time ticket tracking, and direct administrative support.
- **End-to-End Workflow Engine:** Configured multi-condition Flow Designer triggers that automatically assign approvals to facility managers and transition record states from `Open` to `Work in Progress`.
- **Granular Security & ACLs:** Implemented scoped Access Control Lists (ACLs) to enforce row- and field-level security across students, faculty, and administrative personas.

---

## 🛠️ Data Schema & Architecture

| Table Name | Label | Extends | Scope | Description |
| :--- | :--- | :--- | :--- | :--- |
| `x_2061193_campus_1_facility_booking` | Facility Booking | `task` | `x_2061193_campus_1_` | Tracks room reservations, time slots, and approval states |
| `x_2061193_campus_1_facility` | Campus Facilities | None | `x_2061193_campus_1_` | Master record catalog for auditoriums, seminar halls, and labs |

---

## 🔄 Workflow Lifecycle

```mermaid
graph LR
    A[Portal Submission: Book Facility] --> B[State: Open]
    B --> C[Flow Designer: Approval Trigger]
    C --> D{Manager Approval}
    D -- Approved --> E[State: Work in Progress]
    D -- Rejected --> F[State: Closed Incomplete]
    E --> G[Automated Email Notification via sys_email]
