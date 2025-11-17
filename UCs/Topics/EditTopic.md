# 1 Use-Case Name
Edit Topic — CRUD: Update

## 1.1 Brief Description

This use case describes how a Teacher edits an existing **Topic** within a course.
A Teacher may modify the Topic title. After saving, the updated Topic information appears in the course’s Topics list.

---

# 2 Flow of Events

## 2.1 Basic Flow
1. Teacher logs into the platform.
2. Teacher navigates to **Courses** and selects an existing course.
3. Teacher opens the **Topics** section for that course.
4. Teacher selects the Topic they want to edit.
5. Teacher clicks **“Edit Topic.”**
6. System displays an edit form containing:
   - Topic title (pre-filled)
7. Teacher updates the title and submits the form.
8. System validates the input.
9. System updates the Topic record in the database.
10. System displays confirmation: **“Topic updated successfully.”**

### 2.1.1 Activity Diagram
![Activity Diagram](../../ActivityDiagram/EditTopic.jpg)

### 2.1.2 Mock-up
![Mock-up](../../Images/Topics-lofi.png)

### 2.1.3 Narrative
The Teacher selects an existing Topic and opens the edit form.  
After updating the information, the Teacher submits the form, and the system applies the changes. 
The updated Topic is immediately reflected in the course’s Topics list.

---

```gherkin
Feature: Edit an existing topic/module

  As a Teacher
  I want to edit a topic in a course
  So that I can update or improve its content.

  Background:
    Given I am logged in as a teacher with verified email
    And a course with ID 10 exists
    And a topic with ID 5 exists for course 10

  Scenario: Successfully edit a topic
    When I send a PATCH request to "/api/platform/courses/10/topics/5/update/" with:
        | title | Updated Topic Title |
    Then the response status code should be 200
    And the response should contain "Topic updated successfully."

  Scenario: Fail to edit a topic with empty title
    When I send a PATCH request to "/api/platform/courses/10/topics/5/update/" with:
        | title |           |
    Then the response status code should be 400
    And the response should contain "title"

  Scenario: Attempt to edit a non-existing topic
    When I send a PATCH request to "/api/platform/courses/10/topics/999/update/" with:
        | title | Algebra Basics |
    Then the response status code should be 404
    And the response should contain "Topic not found"
```

## 2.2 Alternative Flows

- **Cancel:** Return to Topics list without saving.

- **Validation error:** Invalid input

- **Topic not found**

- **Permission error:** Teacher does not own the course.

---

# 3 Special Requirements

- Only authenticated users with **role = teacher** can edit Topics. 
- The Topic must belong to the selected course
- Topic titles must be unique within the same course.  

---

# 4 Preconditions

- Teacher is logged in and active.  
- The course exists and is active.  
- The Topic exists for the selected course.  
- Teacher has permission to modify the course.  

---

# 5 Postconditions

- The Topic record is updated in the database.  
- The updated Topic information appears in the Topics list.  

---

# 6 Extension Points

- **Delete Topic:** Teacher may delete the Topic after editing it.  
- **Add Challenge:** Teacher may add challenges to the updated Topic.  
- **View Topic:** Teacher can view the updated Topic details.  
