# 1 Use-Case Name
Create Course CRUD: Create

## 1.1 Brief Description

This use case describes how a Teacher creates a new course in the system. The course requires a title, description, language, and level. Optionally, the teacher can add a cover image. Once created, the course is added to the catalog and becomes available depending on if it's published or not.

# 2 Flow of Events
## 2.1 Basic Flow
1. Teacher logs into the system.
2. Teacher navigates to the **Courses** section.
3. Teacher clicks **“Create Course.”**
4. System displays a form with the following input fields:
   - Course title  
   - Description  
   - Language  
   - Level (beginner/intermediate/advanced)  
   - Optional: cover image  
   - Optional: visibility (draft/public/archived)
5. Teacher fills out the form and submits it.
6. System validates the inputs.
7. System inserts the new course record into the database.
8. System confirms: “Course created successfully.”

### 2.1.1 Activity Diagram

![Activity Diagram](../ActivityDiagram/CreateCourse:EditCourse.png)

### 2.1.2 Mock-up

![Mock-up](../../Images/Courses-lofi.png)

### 2.1.3 Narrative
The Teacher uses this form to create new courses on the platform. Once saved, the course is stored in the database and appears in the catalog when published. The Teacher can later add modules and challenges to the course.


```
Feature: Create a new course

  As a Teacher
  I want to create a course
  So that students can enroll and complete challenges.

  Background:
    Given I am logged in as an existing teacher with verified email

  Scenario: Successfully create a course
    When I send a POST request to "/api/platform/courses/create/" with the following data:
        |             |                                       |
        | title       | Math Basics                           |
        | description | Introduction to basic math principles |
        | language    | English                               |
        | level       | beginner                              |
        | status      | published                             |
    Then the course response status code should be 201
    And the course response should contain "Course created successfully."

  Scenario: Fail to create a course with missing title and description
    When I send a POST request to "/api/platform/courses/create/" with the following data:
      | title       |                                          |
      | description |                                          |
      | language    | English                                  |
      | level       | beginner                                 |
      | status      | draft                                    |
    Then the course response status code should be 400
    And the course response should contain "title"

```

## 2.2 Alternative Flows
- **Cancel:** Teacher clicks “Cancel”: Return to Courses page without saving.  
- **Validation error:** Missing or invalid input: Show error, no save.   
- **Draft mode:** Course saved but not visible to students until published.

# 3 Special Requirements

- Only authenticated users with **role = teacher** can create courses.

# 4 Preconditions

- Teacher is logged in and active.  
- The user has permission to create courses.

# 5 Postconditions

- A new course record exists in the database.  
- The course is visible in the catalog if published.  
- The Teacher can add topics and challenges later.

# 6 Extension Points

- **Edit Course:** Teacher can later modify course details.  
- **Delete Course:** Teacher can remove the course.  
- **Add Topics:** Teacher can add topics and challenges to the course.
