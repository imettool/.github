# Integrated Management Effectiveness Tool (IMET)

<p align="center"><img alt="logo" src="icon.png" style="width: 200px;"></p>

## Overview

*Integrated Management Effectiveness Tool (IMET)* is a _Protected Area Management Effectiveness (PAME)_ tool that allows  
an in-depth assessment of marine and terrestrial protected areas, regardless of their management categories and governance  
type. As a decision-support tool, it helps protected area managers take analysis-based management decisions for improved  
conservation outcomes.

The objective of the IMET conserved areas tool is to enhancing conservation efforts and sustaining governance in  
community areas such as Other Effective area-based Conservation Measures (OECMs), Locally-Managed Marine Areas (LMMAs),  
Indigenous and Community Conserved Areas (ICCAs), Community Forests, etc., Community Forests, etc.,  
and in buffer areas of Protected Areas. The IMET conserved areas tool:

- Integrates context, management and governance dimensions for improved knowledge, planning, governance and monitoring
- Sustains data collection and establishes baselines
- Supports identification of stakeholders
- Identifies key conservation elements and ecosystem services, prioritising stakeholders implication, management and governance activities
- Allows understanding community awareness in the management and governance of the conserved area and promotes dialogue, governance and shared planning
- Empowers local communities for effective conservation
- Encourages participation from local communities, government agencies, and NGOs, fostering collaboration and shared responsibility

## Repository Ecosystem

The IMET platform is organized across multiple repositories. The **imet-core** library contains all assessment logic and is shared by host applications

```
┌────────────────────────────────────────────────────┐
│                      imet-core                     │
│            (Laravel Composer package)              │
└─────────────────────────┬──────────────────────────┘
                          │  integrated via Composer
              ┌───────────┴────────────┐
              ▼                        ▼
     ┌──────────────────┐     ┌──────────────────┐
     │   imet-offline   │     │   imet-online    │
     │   Desktop app    │     │  Web application │
     │   (NativePHP)    │     │    (Laravel)     │
     └──────────────────┘     └──────────────────┘
```

### [`imet-core`](https://github.com/imettool/imet-core) — Core Library

The shared heart of the platform which provides all assessment functionality consumed by both host applications including models, database migrations, routes, controllers, views and frontend assets.

> [!IMPORTANT]
> **This is not a standalone application.** In order to execute the code this codebase, you need to integrate it into a hosting application such as `imet-offline` or `imet-online`.

---

### [`imet-offline`](https://github.com/imettool/imet-offline) — Desktop Application

A **desktop application** built with [NativePHP](https://nativephp.com), enabling fully offline IMET assessments without any internet connection or server infrastructure.
- Integrates `imet-core` as a Composer dependency
- Runs entirely on the local machine (only Windows for now)
- Uses **SQLite** as the local database
- The most widely known implementation of IMET

---

### [`imet-online`](https://github.com/imettool/imet-online) — Web Application

A **hosted web application** built on Laravel, enabling multi-user online access to IMET assessments.
- Integrates `imet-core` as a Composer dependency
- Standard server-based deployment
- Uses **PostgreSQL** as the database
- Designed for organizations managing assessments centrally or collaboratively

---

## Technology Stack

| Layer           | Technologies                           |
|-----------------|----------------------------------------|
| Backend         | PHP 8.4+, Laravel                      |
| Frontend        | Vue.js 3, Pinia, Tailwind CSS, Vite    |
| Database        | SQLite (offline) · PostgreSQL (online) |
| Desktop         | NativePHP                              |
| Package manager | Composer (PHP) · npm (JS)              |
