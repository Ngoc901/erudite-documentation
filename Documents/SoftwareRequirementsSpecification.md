# ERUDITE - Software Requirements Specification

## Table of contents
- [Table of contents](#table-of-contents)
- [Introduction](#1-introduction)
    - [Purpose](#11-purpose)
    - [Scope](#12-scope)
    - [Definitions, Acronyms and Abbreviations](#13-definitions-acronyms-and-abbreviations)
    - [References](#14-references)
    - [Overview](#15-overview)
- [Overall Description](#2-overall-description)
    - [Vision](#21-vision)
    - [Use Case Diagram](#22-use-case-diagram)
        - [Authentication & Authorization](#22-use-case-diagram)    
        - [Challenges](#22-use-case-diagram)
        - [Courses & Topics](#22-use-case-diagram)
    - [Technology Stack](#23-technology-stack)
- [Specific Requirements](#3-specific-requirements)
    - [Functionality](#31-functionality)
    - [Usability](#32-usability)
    - [Reliability](#33-reliability)
    - [Performance](#34-performance)
    - [Supportability](#35-supportability)
    - [Design Constraints](#36-design-constraints)
    - [Online User Documentation and Help System Requirements](#37-on-line-user-documentation-and-help-system-requirements)
    - [Purchased Components](#38-purchased-components)
    - [Interfaces](#39-interfaces)
    - [Licensing Requirements](#310-licensing-requirements)
    - [Legal, Copyright And Other Notices](#311-legal-copyright-and-other-notices)
    - [Applicable Standards](#312-applicable-standards)
- [Supporting Information](#4-supporting-information)

---

## 1. Introduction

### 1.1 Purpose
This Software Requirements Specification (SRS) describes all specifications for the application **ERUDITE**, a web-based platform for interactive learning with courses and challenges. It includes an overview of the system’s purpose, vision, features, and constraints.

### 1.2 Scope
The project will be implemented as a **web platform** with courses, modules, and challenges.  

Actors of this platform can be
- **Guest** – browse limited catalog, register.
- **Student** – enroll in courses, complete challenges, comment, view rankings.
- **Author/Instructor** – create courses/modules/challenges, configure availability, review/grade submissions, moderate comments in their courses.
- **Moderator** – global moderation of content/reports.
- **Administrator** – manage users, roles, settings.

Planned subsystems:  
- **Authentication & Profiles**: Registration/login (email, OAuth), profile with stats, privacy settings.  
- **Courses & Topics**: Catalog with filters, structured into topics and challenges.  
- **Challenges**: Multiple types (text, quiz).  
- **Answers & Grading**: Auto-check grading with rubric.  
- **Ranking & Gamification**: Points, badges, course-based leaderboards.  
- **Comments & Moderation**: Discussion threads, reports, moderation tools.  
- **Admin Panel**: Manage users, courses, system settings.  

### 1.3 Definitions, Acronyms and Abbreviations

| Abbreviation | Description                                      |
|--------------|--------------------------------------------------|
| SRS          | Software Requirements Specification              |
| UC           | Use Case                                         |
| JWT          | JSON Web Token                                   |
| a11y         | Accessibility                                    |
| i18n         | Internationalization                             |
| SPA          | Single Page Application                          |
| MVP          | Minimum Viable Product                           |
| OAuth        | Open Authorization                               |
| TTFB         | Time To First Byte                               |
| E2E          | End-to-End (testing)                             |
| WCAG         | Web Content Accessibility Guidelines             |
| GDPR         | General Data Protection Regulation               |


### 1.4 References
| Title                                                            |    Date    | Publishing organization   |
|------------------------------------------------------------------|:----------:| ------------------------- |
| ERUDITE Project Docs (internal)                                  | 30.09.2025 | ERUDITE Team              |
| [Django REST Framework](https://www.django-rest-framework.org/)  |   2025     | Django Software Foundation|
| [React](https://react.dev)                                       |    2025    | Meta Open Source          |

### 1.5 Overview
This document outlines the system's vision and high-level architecture, followed by detailed functional and non-functional requirements. It includes use cases, technology stack, interfaces, and supporting information to guide implementation and verification.

---
## 2. Overall Description

### 2.1 Vision
ERUDITE is a collaborative learning platform. Students join courses, complete challenges of various types, receive grades and points, and appear in rankings. Authors create structured learning experiences, while moderators ensure safe communication and fairness.

### 2.2 [Use Case Diagram](https://app.diagrams.net/#G1KlKqRBsCpliZRuRpVQTxwQJqvAv2_JSH#%7B%22pageId%22%3A%22QEc6X85PEJgYoR8-f0XZ%22%7D)

![Use Case Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/Diagrams/UCD_2025_11.jpg)

**Our Scope for the third semester**
[Use Case Diagram Scope](https://github.com/Ngoc901/erudite-documentation/blob/main/Diagrams/UCD_Scope.jpg)


## 2.2.1 Authentication & Authorization
[Register Use Case](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/CreateChallenges/CreateChallenges.md)

[Login Use Case](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[Logout Use Case](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[Authenticate User Use Case](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

## 2.2.2 Challenges
[Create Challenges Use Case CRUD: Create](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/CreateChallenges/CreateChallenges.md)

[Edit Challenges Use Case CRUD: Update](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[View Challenges Use Case CRUD: Read](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

## 2.2.3 Courses & Topics
### Courses
[Create Courses Use Case CRUD: Create](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/CreateCourse/CreateCourses.md)

[Edit Courses Use Case CRUD: Update](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[Delete Courses Use Case CRUD: Delete](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[View Courses Use Case CRUD: Read](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

### Topics

[Create Topics Use Case CRUD: Create](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/CreateCourse/CreateCourses.md)

[Edit Topics Use Case CRUD: Update](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[Delete Create Use Case CRUD: Delete](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

[View Topics Use Case CRUD: Read](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallenges.md)

### 2.3 Technology Stack
**Client**:  
- React(Vite) JavaScript, MUI
- Zustand for state management  

**Server**:  
- Django REST Framework  
- JWT authentication  
- Role-based permissions  

**Database**:  
- PostgreSQL  

**Storage & Media**:  
- Cloudinary for file uploads  

**CI/CD**:  
- GitHub Actions  
- Dockerized deployment  

**Monitoring**:  
- Grafana (planned, maybe)

**Testing**:  
- UNIT tests
- Cucumber Tests
- Linters

---

## 3. Specific Requirements

### 3.1 Functionality
Core features include:  
- **Registration & Authentication** (email+password, OAuth, password recovery).  
- **Profile Management** (nickname, photo, stats, badges).  
- **Courses & Topics** (structured catalog, enrollment, prerequisites).  
- **Challenges** (text, photo input, multiple choice).  
- **Answers & Submissions** (resubmission, validation, history).  
- **Grading & Points** (formula-based).  
- **Ranking** (leaderboards, progress tracking).  
- **Comments** (threaded, moderated, report system).  
- **Admin Panel** (manage users, courses, moderation).  

### 3.2 Usability
- Mobile-first responsive UI.  
- Familiar layouts (cards, progress bars).  
- Dark/light theme.  
- Accessibility (WCAG 2.1 AA).  

### 3.3 Reliability
- 100% uptime for API.  
- Data consistency and no submission loss.  

### 3.4 Performance
- TTFB < 500ms for ≥95% requests. (we will try)

### 3.5 Supportability
- Clean code standards, linting, typing (JavaScript for frontend).  
- Unit, integration, and E2E tests.  

### 3.6 Design Constraints
- REST API in JSON.  
- Role-based access control.  

### 3.7 On-line User Documentation and Help System Requirements
- FAQ section.  
- “Help” button inside app with contact form.  

### 3.8 Purchased Components
- Cloudinary subscription (file hosting).  

### 3.9 Interfaces
#### 3.9.1 User Interfaces (This part still in progress)
- **Landing page**: overview, registration/login.  
- **Dashboard**: list of courses, filters.  
- **Course Page**: topics, challenges, ranking.  
- **Challenge Page**: statement, answer form, attempts, comments.  
- **Profile**: personal data, stats, badges.  
- **Admin Panel**: Django admin for content/user management.  

#### 3.9.2 Hardware Interfaces
N/A  

#### 3.9.3 Software Interfaces
- REST API  
- OAuth (Google)  

#### 3.9.4 Communication Interfaces
- HTTPS (TLS 1.3)  

### 3.10 Licensing Requirements
MIT License (open-source components).  

### 3.11 Legal, Copyright and Other Notices (In research part)
- User-generated content remains property of authors.  

### 3.12 Applicable Standards
- WCAG 2.1 AA (accessibility).  
- GDPR (privacy).  
- PEP8 (Python), ESLint/Prettier (JS/TS).  

---

## 4. Supporting Information
For further details, please contact the ERUDITE Team.  

Team members:  
- Atai Mammut
- Niki Huawei
- Brian Maiami
