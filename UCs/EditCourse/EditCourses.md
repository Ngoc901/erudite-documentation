# 1 Use-Case Name
Edit Course CRUD: Update

## 1.1 Brief Description

This use case describes how a Teacher edits an existing course. The Teacher can modify the course’s title, description, language, level, visibility, or cover image. Once saved, the changes are updated in the database. If the course is already published, updates become visible to students.

# 2 Flow of Events
## 2.1 Basic Flow
1. Teacher logs into the system.
2. Teacher navigates to the **Courses** section.
3. Teacher selects a course to edit.
4. Teacher clicks **“Edit Course.”**
5. System displays a form pre-filled with the course’s existing information:
   - Course title  
   - Description  
   - Language  
   - Level (beginner/intermediate/advanced)  
   - Optional: cover image  
   - Optional: visibility (draft/public/private)
6. Teacher edits the desired fields and submits the form.
7. System validates the updated data.
8. System updates the course record in the database.
9. System confirms: “Course updated successfully.”

### 2.1.1 Activity Diagram

![Activity Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditCourse/EditCouresesActivityDiagram.drawio.png)

### 2.1.2 Mock-up

![Mock-up](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/CreateCourse/CreateCourse%3AEditCourse.png)

### 2.1.3 Narrative
The Teacher uses this form to maintain and update existing courses. Once saved, the modified course data is stored in the database and updated in the course catalog if published.
```
Feature: Update an existing course
  As a Teacher
  I want to edit a course
  So that I can change its title or details after creation.

  Background:
    Given I am logged in as an existing teacher with verified email for updating
    And a course already exists with title "Math Basics" and slug "math-basics"

  Scenario: Successfully update a course
    When I send a PATCH request to "/api/platform/courses/{course_slug}/update/" with the following data:
      |             |                              |
      | title       | Advanced Math Basics 2       |
      | description | Updated course description   |
      | level       | intermediate                 |
      | status      | published                    |
    Then the course update response status code should be 200
    And the course response should contain "Advanced Math Basics"

  Scenario: Fail to update course with invalid data
    When I send a PATCH request to "/api/platform/courses/{course_slug}/update/" with the following data:
      |             |                              |
      | title       |                              |
      | description |                              |
    Then the course update response should contain "No changes detected"
    And the course response should contain "title"

```
## 2.2 Alternative Flows
- **Invalid Data:** Missing title or description: Show validation error.  
- **Cancel:** Teacher clicks “Cancel”: Return to course details without saving.   
- **Draft Mode:** Changes saved but hidden until published.

# 3 Special Requirements
- Only authenticated users with **role = teacher** can edit courses.

# 4 Preconditions

- Teacher is logged in and active.  
- Target course exists.  
- Teacher is the author of the course or has permission to edit it.

# 5 Postconditions
- The updated course record is saved in the database.  
- Changes are reflected in the catalog if the course is published.  

# 6 Extension Points

- **Delete Course:** Teacher can remove the course.  
- **Add/Remove Topics:** Teacher can manage topics within the course.  

