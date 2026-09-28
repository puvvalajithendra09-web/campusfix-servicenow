# 🏛️ CampusFix — ServiceNow Enterprise Facility Management Application

[![Live Demo](https://img.shields.io/badge/Live_Portfolio-GitHub_Pages-2563eb?style=for-the-badge&logo=github)](https://puvvalajithendra09-web.github.io/campusfix-servicenow/)
[![ServiceNow](https://img.shields.io/badge/ServiceNow-Washington_DC-81B5A1?style=for-the-badge&logo=servicenow)](https://service-now.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

An enterprise-grade scoped ServiceNow application engineered to eliminate fragmented email chains and spreadsheet-based campus operations. **CampusFix** centralizes facility bookings, maintenance defect tracking, automated approval workflows, and role-based access governance.

---

## ⚡ Key Features

- **Self-Service Facility Reservation:** End-user portal to request seminar halls, computer labs, and auditoriums with conflict prevention.
- **Incident & Defect Logging:** Centralized intake for electrical, HVAC, and classroom repair requests.
- **Automated Multi-Branch Approvals:** Flow Designer engine routing requests dynamically to facility managers.
- **Transactional Notifications:** Real-time email updates delivered to requesters and approvers via `sys_email`.
- **Role-Based Security:** Custom Scoped ACLs and script validations safeguarding task and facility data.
- **Responsive Portal Interface:** Modern 4-card landing portal (`campusfix_home`) built on ServiceNow Service Portal.

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
    A["Portal Submission: Book Facility"] --> B["State: Open"]
    B --> C["Flow Designer: Approval Trigger"]
    C --> D{"Manager Approval"}
    D -- "Approved" --> E["State: Work in Progress"]
    D -- "Rejected" --> F["State: Closed Incomplete"]
    E --> G["Automated Email Notification"]
## Live Demo

🔗 **CampusFix Portal:**  
https://dev444036.service-now.com/sp?id=campusfix_home

## Demo Login

**Username:** `campus_demo`  
**Password:** `DemoUser@1234`
