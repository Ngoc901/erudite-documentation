# ERUDITE - Software Architecture Document

# Table of Contents
- [Introduction](#1-introduction)
    - [Purpose](#11-purpose)
    - [Scope](#12-scope)
    - [Definitions, Acronyms and Abbreviations](#13-definitions-acronyms-and-abbreviations)
    - [References](#14-references)
    - [Overview](#15-overview)
- [Architectural Representation](#2-architectural-representation)
- [Architectural Goals and Constraints](#3-architectural-goals-and-constraints)
- [Use-Case View](#4-use-case-view)
    - [Use-Case Realizations](#41-use-case-realizations)
- [Logical View](#5-logical-view)
    - [Overview](#51-overview)
    - [Architecturally Significant Design Packages](#52-architecturally-significant-design-packages)
- [Process View](#6-process-view)
- [Deployment View](#7-deployment-view)
- [Implementation View](#8-implementation-view)
    - [Overview](#81-overview)
    - [Layers](#82-layers)
- [Data View](#9-data-view)
- [Size and Performance](#10-size-and-performance)
- [Quality](#11-quality)

## 1. Introduction

### 1.1 Purpose

This document provides a detailed overview of the software architecture of **ERUDITE**, an interactive web-based learning platform designed 
to facilitate user engagement through challenges, and community interactions. 
It defines the architectural design, framework choices, logical structure, deployment view, and data model. 
The document serves as a technical reference for developers, and maintainers, ensuring alignment with the [Software Requirements Specification](Documents/SoftwareRequirementsSpecification.md) (SRS).

### 1.2 Scope

This document describes the architecture of the ERUDITE project, 
including the backend API, frontend user interface, database schema, 
and deployment strategy. 
It focuses on core components and excludes detailed implementation of third-party services (e.g., Cloudinary integration specifics), 
or external integrations beyond the REST API. Non-functional aspects like performance and quality are addressed at a high level.

### 1.3 Definitions, Acronyms and Abbreviations

| Abbreviation | Description                                      |
|--------------|--------------------------------------------------|
| API          | Application Programming Interface                |
| MVC          | Model View Controller                            |
| REST         | Representational State Transfer                  |
| JWT          | JSON Web Token                                   |
| DRF          | Django REST Framework                            |
| SPA          | Single Page Application                          |
| ORM          | Object Relational Mapper                         |
| CI/CD        | Continuous Integration / Continuous Deployment   |
| DBMS         | Database Management System                       |
| VCS          | Version Control System                           |
| SRS          | Software Requirements Specification              |
| MVS          | Model-View-Serializer (REST variant of MVT)      |
| MVVM         | Model-View-ViewModel                             |
| MUI          | Material UI                                      |

### 1.4 References

| Title                                                                           |    Date    | Publishing organization |
|---------------------------------------------------------------------------------|:----------:| ----------------------- |
| [ERUDITE SRS](Documents/SoftwareRequirementsSpecification.md)                   | 2025-09-30 | ERUDITE Team            |
| [ERUDITE Django Web App](https://github.com/coffee3333/erudite-django-web-app)  | 2025-09-30 | ERUDITE Team            |
| [ERUDITE React Web App](https://github.com/coffee3333/erudite-react-web-app)    | 2025-09-30 | ERUDITE Team            |
| [ERUDITE Blog](https://eruditedev.wordpress.com/)                               | 2025-09-30 | ERUDITE Team            |
| [Django REST Framework Documentation](https://www.django-rest-framework.org/)   |  Ongoing   | Django REST Community            |
| [React Vite Documentation](https://vite.dev/guide/)                             |  Ongoing   | VoidZero Inc.            |

### 1.5 Overview
This document explains **ERUDITE’s** layered architecture, emphasizing its separation of concerns between backend (Django REST), 
frontend (React SPA), and database (PostgreSQL). It provides a visual and conceptual breakdown of the Model–View–Serializer 
(MVS) pattern for the backend, MVVM for the frontend, UML diagrams, and the deployment setup. 
Sections cover logical, process, deployment, implementation, and data views, with emphasis on scalability and maintainability.

## 2. Architectural Representation
ERUDITE is built using the **MVS** pattern (a REST-oriented variant of MVC/MVT) for the backend and a **MVVM** pattern for the frontend to enable reactive state management.

### Backend (Django REST Framework)

Django REST Framework (DRF) is a toolkit built on Django for creating RESTful APIs. Traditionally, Django uses the MVT (Model–View–Template) pattern for web apps. In DRF, this evolves to MVS (Model–View–Serializer) for API-focused development, where serializers handle data conversion instead of templates.

Django follows the **MVT** (Model–View–Template) pattern, which in DRF becomes **MVS**:

![Difference between MVS and MVT](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/MVCvsMVT.png){ width="500" }

### Frontend (React + Zustand)
The frontend is a component-based SPA using React. While JavaScript supports OOP, ERUDITE adopts a functional/procedural approach for simplicity, avoiding complex class hierarchies. State is managed via Zustand (MVVM-inspired), with a layered structure for components, services, and utilities.

![Layered Frontend Project Structure](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/front-struct.png)

**MVVM Pattern**

![MVVM Pattern](Images/MVVMPattern.png)

## 3. Architectural Goals and Constraints

### Goals
- Achieve clear separation of concerns between data (models), logic (views), and presentation (serializers/components).
- Ensure maintainability, modularity, and extensibility for future features like gamification.
- Provide secure, RESTful communication with JWT authentication.
- Support responsive UI for diverse devices using MUI.

### Constraints
- Use open-source tools (e.g., Django, React) to minimize costs.
- Target web browsers (Chrome, Firefox, Safari) with no native mobile support initially.
- Limit team size to small-scale development, favoring lightweight frameworks.

### Front end
The frontend is built with **React** and **Vite**.
It follows a component-based, declarative structure and manages state globally through **Zustand**.
The UI is implemented using **Material UI (MUI)** for responsiveness and accessibility.

### Back end
The backend uses **Django REST Framework (DRF)** and **Django ORM** to define data models and API logic.
Authentication is handled via **JWT**, and user data is stored in **PostgreSQL**.
Media files (e.g., photos from challenges) are stored using **Cloudinary**.

#### MVS with Django
- Achieve a clear separation between data, logic, and presentation layers.
- Ensure maintainability and modularity.
- Provide RESTful communication between client and server.


## 4. Use-Case View
![Use-Case Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/Diagrams/UCD.png)
This view illustrates actors (e.g., User, Admin) and use cases (e.g., Create Course, Create Topic).

### 4.1 Use-Case Realizations

Authorization / Authentication
Create Course, Delete Course, Update Course, View Courses(Pagination)
Create Topic for Course, Delete Topic, Update Topic, View Topic
View Challenges with specific Topic

## 5. Logical View

### 5.1 Overview
ERUDITE follows a **modular Django architecture**, where each app corresponds to a functional domain.
**MVS Model**

- **Model**: Django ORM models (e.g., Post, User, Comment).
- **View**: APIView, ViewSet, or GenericViewSet — handle requests.
- **Template / Serializer**: Converts model data into JSON and vice versa.


![MVS Pattern in Django](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/MVS-pattern-in-django.png)


### 5.2 Architecturally Significant Design Packages

Django REST Framework provides ready-to-use libraries that allows you to generate a complete CRUD functionality with just a few lines of code. These are called ViewSets, available in the rest_framework.viewsets module. In addition to ViewSets, DRF also offers generic views, which we actively use in our backend application to simplify common API operations.

![Class diagram with MVS pattern](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/class-diagram-with-mvs-patterns.png)

## 6. Process View
Activity Diagram (conceptual): Request → Auth Check → Logic Execution → Response.

**n/a**
## 7. Deployment View
ERUDITE employs a containerized client-server architecture using Docker for component isolation and Nginx as a reverse proxy for routing. This setup supports both development and production environments, with scalability in mind.

#### Client-server Architecture 

![Client-Server-Architecture](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/client-server-architecture.png)

- Host Machine (Server): Runs Nginx (installed locally) as a reverse proxy. It routes root paths (/) to the frontend on port 3000 and API paths (/api) to the backend on port 8080. HTTPS is enforced on port 80 for client connections.
- Docker Environment: Contains isolated containers for the application components:
  - Frontend (React Container): Serves the static React build on port 3000.
  - Backend (API Container): Runs the Django application on port 8080, connecting to the database via an internal Docker network.
  - Database (DB Container): Uses PostgreSQL (or SQLite for lightweight testing) on port 5432.

- Client Device: Users access the web app via a browser, connecting over HTTPS on port 80.
- External Services: Media files are handled by Cloudinary (not shown in the diagram), integrated via API calls from the backend.
- Environments: Development uses local Docker Compose for orchestration; staging and production leverage cloud hosting (e.g., AWS EC2 or Heroku) with auto-scaling and load balancing.
- CI/CD: Automated via GitHub Actions, building and deploying containers.
- Networking and Security: Internal network for container communication; HTTPS termination at Nginx; rate limiting and firewalls for protection.

## 8. Implementation View
![Generated Class Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/generated-class-diagram.png)
### 8.1 Overview
Implementation focuses on code organization, build processes, and VCS (Git). Backend uses Django's app structure; frontend follows React best practices.

**n/a**
### 8.2 Layers
- Presentation Layer: Frontend components (React/MUI) and serializers (DRF).
- Business Logic Layer: Views/ViewSets in backend; services/hooks in frontend.
- Data Access Layer: ORM models and queries in backend.
- Infrastructure Layer: Database (PostgreSQL), storage (Cloudinary), auth (JWT).

**n/a**
## 9. Data View
Database Models for Backend
![DB Model for Backend](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/db-model.png)
![Generated DB Model for Backend](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/generated-db-model.png)
## 10. Size and Performance
**n/a**
## 11. Quality/Metrics
**n/a**
