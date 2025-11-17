# 1 Use-Case Name
Delete Course — CRUD: Delete

## 1.1 Brief Description

This use case describes how a Teacher deletes an existing **Course** from the platform.
Deleting a course removes its entire structure, including Topics and Challenges.
---

# 2 Flow of Events

## 2.1 Basic Flow
1. Teacher logs into the platform.
2. Teacher navigates to the **Courses** section.
3. Teacher selects the Course they want to delete.
4. Teacher clicks **“Delete Course.”**
5. Teacher confirms the deletion.
6. System checks permissions and verifies whether deletion is allowed.
7. System deletes the Course record from the database.
8. System displays confirmation: **“Course deleted successfully.”**

### 2.1.1 Activity Diagram
![Activity Diagram](../../ActivityDiagram/DeleteCourse.jpg)

### 2.1.2 Mock-up
![Mock-up](../../Images/Courses-lofi.png)

### 2.1.3 Narrative
The Teacher selects a Course from their list and initiates the delete action.
The system presents a warning because deletion is irreversible.  
Upon confirmation, the system removes the Course and all associated data (e.g., Topics, Challenges).
The Course is no longer visible on the platform.

---

```gherkin
Feature: Delete an existing course

  As a Teacher
  I want to delete a course
  So that I can remove outdated or unnecessary content.

  Background:
    Given I am logged in as a teacher
    And a course with ID 15 exists

  Scenario: Successfully delete a course
    When I send a DELETE request to "/api/platform/courses/15/delete/"
    Then the response status code should be 204
    And the course should no longer exist in the database

  Scenario: Attempt to delete a non-existing course
    When I send a DELETE request to "/api/platform/courses/999/delete/"
    Then the response status code should be 404
    And the response should contain "Course not found"

  Scenario: Permission denied
    Given I am logged in as a student
    When I send a DELETE request to "/api/platform/courses/15/delete/"
    Then the response status code should be 403
    And the response should contain "Not authorized"
```

## 2.2 Alternative Flows

- **Cancel:** No deletion occurs.

- **Course not found**  
- **Permission error** 

- **Dependency error:** Course cannot be deleted because Topics or Challenges are protected.

---

# 3 Special Requirements

- Only authenticated users with **role = teacher** can delete courses.
- Course deletion may cascade to Topics and Challenges.
- System must display a clear confirmation prompt before deletion.  


---

# 4 Preconditions

- Teacher is logged in and active.
- The Course exists.
- Teacher owns the course or has deletion permissions.

---

# 5 Postconditions

- The Course record is removed from the database.  
- The Course no longer appears in the Courses list.  
- Topics and Challenges associated with the Course may also be removed.  

---

# 6 Extension Points

- **Edit Course:** Teacher may modify course content before deletion.
- **View Courses:** User may return to the course list after deletion.
- **Delete Topics:** Some systems may require deleting Topics before removing the Course.
