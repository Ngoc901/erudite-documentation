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
This document provides a detailed overview of the software architecture of **ERUDITE**, an interactive web-based learning platform.
It defines the architectural design, framework choices, logical structure, deployment view, and data model.
The document serves as a technical reference.

### 1.2 Scope
This document describes the architecture of the Erudite project.


### 1.3 Definitions, Acronyms and Abbreviations

| Abbreviation | Description                                    |
| -----------  | ---------------------------------------------- |
| API          | Application Programming Interface              |
| MVC          | Model View Controller                          |
| REST         | Representational State Transfer                |
| JWT          | JSON Web Token                                 |
| DRF          | Django REST Framework                          |
| SPA          | Single Page Application                        |
| ORM          | Object Relational Mapper                       |
| CI/CD        | Continuous Integration / Continuous Deployment |
| DBMS         | Database Management System                     |
| VCS          | Version Control System                         |
| SRS          | Software Requirements Specification            |

### 1.4 References

| Title                                                                              |    Date    | Publishing organization |
| ---------------------------------------------------------------------------------- |:----------:| ----------------------- |
| [ERUDITE SRS](Documents/SoftwareRequirementsSpecification.md)                      | 2025-09-30 | ERUDITE Team            |
| [ERUDITE Django Web App](https://github.com/coffee3333/erudite-django-web-app)     | 2025-09-30 | ERUDITE Team            |
| [ERUDITE React Web App](https://github.com/coffee3333/erudite-react-web-app)       | 2025-09-30 | ERUDITE Team            |
| [ERUDITE Blog](https://eruditedev.wordpress.com/)                                  | 2025-09-30 | ERUDITE Team            |


### 1.5 Overview
This document explains ERUDITE’s layered architecture, emphasizing its separation of concerns between backend, frontend, and database.
It provides a visual and conceptual breakdown of the Model–View–Serializer (MVS) pattern, UML diagrams, and the deployment setup for the Django REST and React system.

## 2. Architectural Representation
ERUDITE is built using the **MVS pattern** (a REST-oriented variant of MVC) for the backend and a **MVVM pattern** for the frontend. 


### Backend (Django REST Framework)

Django REST Framework (DRF) is a powerful and flexible toolkit built on top of Django that simplifies the creation of RESTful APIs. Django REST is a library for the Django Framework. Before APIs, Django was used as a web framework for building solid web applications, and it used the MVT pattern, which consists of Model View Template.

Django follows the **MVT** (Model–View–Template) pattern, which in DRF becomes **MVS**:

- **Model**: Django ORM models (e.g., Post, User, Comment).
- **View**: APIView, ViewSet, or GenericViewSet — handle requests.
- **Template / Serializer**: Converts model data into JSON and vice versa.

![Difference between MVS and MVT](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/MVCvsMVT.png)

![MVS Pattern in Django](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/MVS-pattern-in-django.png)

### Frontend (React + Zustand)
JavaScript is not a fully object-oriented language, technically, OOP can be implemented, however it was decided to keep the project procedural for simplicity. React codebases also rarely follow strict OOP patterns, therefore, generating a UML diagram based on class structures, simply is not relevant in our case. Instead, a layered project structure was designed, which is illustrated below.

![Layered Frontend Project Structure](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/front-struct.png)

#### Client-server Architecture 

![Client-Server-Architecture](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/client-server-architecture.png)




## 3. Architectural Goals and Constraints

### MVC
- Achieve a clear separation between data, logic, and presentation layers.
- Ensure maintainability and modularity.
- Provide RESTful communication between client and server.

### Front end
The frontend is built with **React** and **Vite**.
It follows a component-based, declarative structure and manages state globally through **Zustand**.
The UI is implemented using **Material UI (MUI)** for responsiveness and accessibility.


### Back end
The backend uses **Django REST Framework (DRF)** and **Django ORM** to define data models and API logic.
Authentication is handled via **JWT**, and user data is stored in **PostgreSQL**.
Media files (e.g., photos from challenges) are stored using **Cloudinary**.



## 4. Use-Case View
![Use-Case Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/Diagrams/UCD.png)

### 4.1 Use-Case Realizations
n/a

## 5. Logical View

### 5.1 Overview
ERUDITE follows a **modular Django architecture**, where each app corresponds to a functional domain.

### 5.2 Architecturally Significant Design Packages

![DB Model for Backend](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/db-model.png)
![Generated DB Model for Backend](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/generated-db-model.png)

Django REST Framework provides ready-to-use libraries that allows you to generate a complete CRUD functionality with just a few lines of code. These are called ViewSets, available in the rest_framework.viewsets module. In addition to ViewSets, DRF also offers generic views, which we actively use in our backend application to simplify common API operations.

![Class diagram with MVS pattern](https://github.com/Ngoc901/erudite-documentation/blob/main/Images/class-diagram-with-mvs-patterns.png)

## 6. Process View
n/a
## 7. Deployment View
n/a
## 8. Implementation View
n/a
### 8.1 Overview
n/a
### 8.2 Layers
n/a
## 9. Data View
n/a
## 10. Size and Performance
n/a
## 11. Quality/Metrics
n/a
