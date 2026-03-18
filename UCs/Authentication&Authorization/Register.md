# 1 Use-Case Name: Registration
Use-case: User Registration - Authentication (Create Account)

## 1.1 Brief Description

This use case describes how a new User creates an account on the platform.

---

# 2 Flow of Events

## 2.1 Basic Flow
1. User navigates to the **Registration** page.
2. User enters the required fields:
   - Email  
   - Password  
3. User clicks **“Register”**.
4. System validates the input fields.
5. System checks whether the email is already in use.
6. System creates a new user account in the database with:
   - status = *unverified*
8. System displays confirmation

### 2.1.1 Activity Diagram
![Activity Diagram](../ActivityDiagram/Register.jpg)

### 2.1.2 Mock-up
![Mock-up](../Images/Auth-lofi.png)

### 2.1.3 Narrative
The User fills out the registration form with an email and password.  
The system ensures the data is valid and that the email is not already used.  
A new unverified account is created.

---

```gherkin
Feature: User Authentication
  As a registered user
  I want to log in and log out
  So that I can access protected resources securely

  Background:
    Given a registered user exists with email "test@example.com" and password "secret123@A"

  Scenario: Successful login
    When I send a POST request to "/api/users/auth/login/" with email "test@example.com" and password "secret123@A"
    Then the response status code should be 200
    And the response should contain "access" and "refresh" tokens

  Scenario: Failed login with invalid credentials
    When I send a POST request to "/api/users/auth/login/" with email "test@example.com" and password "wrongpass"
    Then the response status code should be 401

  Scenario: Successful logout
    Given a registered user exists with email "test@example.com" and password "secret123@A"
    Given I am logged in with email "test@example.com" and password "secret123@A"
    When I send a POST request to "/api/users/auth/logout/" with a valid refresh token
    Then the response status code should be 205
    And the response should contain "Successfully logged out"
```
[Link to feature file](https://github.com/coffee3333/erudite-django-web-app/blob/main/features/authentication.feature)

## 2.2 Alternative Flows

- **Email already in use** 

- **Invalid email format**

- **Weak password**

- **Email sending failure**

---

# 3 Special Requirements

- Registration form must follow security rules.

---

# 4 Preconditions

- User is **not logged in**.
- User provides a **valid email and password**.

---

# 5 Postconditions

- A new user account is created with **unverified** status.

---

# 6 Extension Points

- **Login:** User logs in after successful verification.
