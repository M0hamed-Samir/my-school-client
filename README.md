# Madarstna — School Management System (Client App)

> Public-facing web application for a school management platform. Built as a university graduation project using **Angular 14** and **Angular Material**, with three fully separated role-based portals: Admin, Teacher, and Student.

---

## Overview

Madarstna is a multi-role school management system that handles the core operational workflows of a school — from student records and fee management to attendance tracking and timetables — delivered through a single Angular SPA with route-level role enforcement.

This repository is the **client-side application**. It connects to a backend REST API and uses `json-server` for local development mocking. 

---

## Key Features

### Role-Based Access Control
Three distinct portals gated at the router level via `AuthGuard` and Angular's `CanActivate`. A user logging in as Admin, Teacher, or Student is routed to an entirely separate feature set — shared routes are inaccessible to unauthorized roles.

| Role    | Portal Scope |
|---------|-------------|
| Admin   | Full system management |
| Teacher | Lectures, exam schedule, leave requests |
| Student | Homework, timetable, leave requests |

### Admin Portal
- **Dashboard** — analytics charts (ApexCharts) with summary stats
- **Students & Teachers** — CRUD with data tables, search/filter, and paginated views (Angular Material + `@swimlane/ngx-datatable`)
- **Courses & Departments** — add/edit/delete with confirmation dialogs
- **Library** — asset management with full CRUD
- **Fees** — fee records with receipt generation view
- **Attendance** — staff attendance tracking with check-in/out, break time, and status per record
- **Holidays** — holiday calendar management

### Teacher Portal
- Lecture management
- Exam schedule view
- Leave request submission
- Personal settings

### Student Portal
- Homework view
- Timetable
- Leave request submission
- Personal settings

### UI & UX
- Built with **Angular Material** + **Bootstrap 5**
- Data tables with sort, filter, and paginator throughout
- ApexCharts for dashboard analytics
- FullCalendar integration for scheduling
- CKEditor 5 for rich text inputs
- Internationalisation support via `@ngx-translate` (EN, DE, ES locale files included)
- Drag-and-drop support via `ng2-dragula`
- SweetAlert2 for confirmation dialogs

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Angular 14 |
| UI Library | Angular Material 14, Bootstrap 5 |
| Charts | ApexCharts (`ng-apexcharts`), Chart.js, ngx-charts |
| Calendar | FullCalendar 5 |
| Rich Text | CKEditor 5 |
| i18n | @ngx-translate |
| State / Streams | RxJS 7, BehaviorSubject-based data sources |
| HTTP | Angular HttpClient |
| Auth | JWT stored in localStorage, role-based route guards |
| Dev API Mock | json-server |

---

## Architecture Notes

- **Lazy-loaded feature modules** — Admin, Teacher, and Student modules are loaded on demand, keeping the initial bundle lean
- **Custom DataSource classes** — several data tables implement `DataSource<T>` from `@angular/cdk/collections` directly, with live filter and sort wired to `BehaviorSubject`
- **`UnsubscribeOnDestroyAdapter`** — a shared base class used across components to prevent memory leaks from unmanaged subscriptions
- **Environment-based API config** — API base URL is injected from `environment.ts`, making it easy to switch between local mock and a real backend

---

## Getting Started

### Prerequisites
- Node.js ≥ 16
- Angular CLI 14

### Install & Run

```bash
# Install dependencies
npm install

# Start the local API mock (json-server)
npx json-server --watch db.json --port 8080

# Start the Angular dev server
ng serve
```

The app will be available at `http://localhost:4200`.  
Default API base: `http://localhost:8080/api/`

---

## Project Status

Completed as a university graduation project. The backend API is not deployed publicly; running locally requires `json-server` as described above. The codebase reflects the scope and constraints of an academic project — some areas (e.g., password handling in the User model) would need hardening before any production use.

---

## Team

Built as a university graduation project by two developers:


- **Mohamed Samir** ([@M0hamed-Samir](https://github.com/M0hamed-Samir)) 
- **Ahmed Hassan** ([@Ahmmed-Hassan](https://github.com/Ahmmed-Hassan)) 
