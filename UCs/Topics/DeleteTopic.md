# 1 Use-Case Name
Delete Topic / Module — CRUD: Delete

## 1.1 Brief Description

This use case describes how a Teacher removes an existing **Topic** from a course.  
A Topic may contain challenges. Once deleted, the Topic is no longer shown in the course structure.
---

# 2 Flow of Events

## 2.1 Basic Flow
1. Teacher logs into the platform.  
2. Teacher navigates to **Courses** and selects an existing course.  
3. Teacher opens the **Topics** section for that course.  
4. Teacher selects the Topic they want to delete.  
5. Teacher clicks **“Delete Topic.”**  
6. System displays a confirmation dialog.
7. Teacher confirms the deletion.  
8. System verifies permissions and checks if deletion is allowed (e.g., topic not locked).  
9. System deletes the Topic record from the database.  
10. System shows confirmation: **“Topic deleted successfully.”**

### 2.1.1 Activity Diagram
![Activity Diagram](../../ActivityDiagram/DeleteTopic.jpg)

### 2.1.2 Mock-up
![Mock-up](../../Images/Topics-lofi.png)

### 2.1.3 Narrative
The Teacher opens the Topics list of a course and selects a Topic to delete.  
If the Topic contains challenges, the system may either delete them automatically or prevent deletion until they are removed.  
Once confirmed, the Topic is removed from the database and no longer appears in the course structure.

---

```gherkin
Feature: Delete an existing topic/module

  As a Teacher
  I want to delete a topic from a course
  So that I can reorganize or remove outdated course content.

  Background:
    Given I am logged in as a teacher with verified email
    And a course with ID 10 exists
    And a topic with ID 5 exists for course 10

  Scenario: Successfully delete a topic
    When I send a DELETE request to "/api/platform/courses/10/topics/5/delete/"
    Then the response status code should be 204
    And the topic should no longer exist in the database

  Scenario: Fail to delete a topic that does not exist
    When I send a DELETE request to "/api/platform/courses/10/topics/999/delete/"
    Then the response status code should be 404
    And the response should contain "Topic not found"

  Scenario: Fail to delete a topic due to insufficient permissions
    Given I am logged in as a student
    When I send a DELETE request to "/api/platform/courses/10/topics/5/delete/"
    Then the response status code should be 403
    And the response should contain "Not authorized"
```
## 2.2 Alternative Flows

- **Cancel:** No deletion occurs.

- **Validation/Dependency error:** Topic cannot be deleted because it contains challenges.

- **Permission error:** Teacher does not own the course.

---

# 3 Special Requirements

- Only authenticated users with **role = teacher** can delete topics.
- The Topic must belong to the selected course.
- The system may require challenges under the topic to be removed first.

---

# 4 Preconditions

- Teacher is logged in and active.
- The course exists and is active.
- The topic exists and belongs to the selected course.
- Teacher has permission to modify the course.

---

# 5 Postconditions

- The Topic record is removed from the database.
- The Topic no longer appears in the Topics list for the course.
- Associated challenges may also be removed.

---

# 6 Extension Points

- **Edit Topic:** Not available after deletion. 
- **View Topic:** System returns an error because the topic no longer exists. 
- **Delete Challenges:** May occur before or during topic deletion depending on rules. 

