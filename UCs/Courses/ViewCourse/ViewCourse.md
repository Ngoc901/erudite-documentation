# 1 Use-Case Name
View Courses — CRUD: Read

## 1.1 Brief Description

This use case describes how a User views a paginated list of available Courses on the platform.
The list may include course titles, descriptions, language, difficulty level, and visibility status (only public courses visible to guests).

---

# 2 Flow of Events

## 2.1 Basic Flow
1. User opens the platform (Guest or authenticated User).
2. User navigates to the **Courses** page.
3. System retrieves a paginated list of available Courses.
4. System displays:
   - Course title  
   - Description  
   - Language  
   - Level (beginner/intermediate/advanced)  
   - Optional: cover image  
5. When the user changes page:
   - System loads the next page of results.
6. User selects a Course to view more details (optional).

### 2.1.1 Activity Diagram
![Activity Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/ViewCourses/ViewCoursesActivityDiagram.png)

### 2.1.2 Mock-up
![Mock-up](../../Images/Courses-lofi.png)

### 2.1.3 Narrative
The user navigates to the Courses section where the platform loads Courses in a paginated manner to ensure performance and scalability.  
Guests can only see **public** courses.  
Authenticated users can also see additional information depending on their role (e.g., teacher-owned courses).  
Users may select a Course to continue to Topics or view course details.

---

```gherkin
Feature: View list of courses with pagination

  As a User
  I want to view available courses
  So that I can choose a course to explore or enroll in.

  Scenario: Successfully view first page of courses
    When I send a GET request to "/api/platform/courses/?page=1"
    Then the response status code should be 200
    And the response should contain a list of courses

  Scenario: Navigate to another page
    When I send a GET request to "/api/platform/courses/?page=2"
    Then the response status code should be 200
    And the response should contain a list of courses on page 2

  Scenario: No courses available on a page
    When I send a GET request to "/api/platform/courses/?page=99"
    Then the response status code should be 200
    And the response should contain an empty list

  Scenario: Guest views only public courses
    Given I am a guest user
    When I send a GET request to "/api/platform/courses/"
    Then the response status code should be 200
    And the response should not include private or draft courses

```
## 2.2 Alternative Flows


- **No courses available**
- **Unauthorized access to private courses:**


---

# 3 Special Requirements

- Pagination must be implemented for performance.  
- Guests can only view **public** courses.  
- Teachers may view their own **draft** or **archived** courses.  


---

# 4 Preconditions

- The platform contains at least one public course (or returns an empty list).  
- User has access to the Courses page (Guest or authenticated).

---

# 5 Postconditions

- A list of courses is displayed to the user.  
- User may select a course for further viewing.  

---

# 6 Extension Points

- **Search Courses:** Search by title or keywords.  
- **View Course Details:** User selects a course to view detailed information.  
- **Enroll in Course:** (For students) user may enroll into a selected course.  
