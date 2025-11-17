# 1 Use-Case Name
Create Challenges CRUD: Create

## 1.1 Brief Description

This use case describes how an Teacher creates a new challenge within a course topic. The challenge needs a title, body, points, difficulty, an optional photo and may include one or more correct answers. Once created, the challenge is available for students to attempt depending on course/topic status. The challenge becomes available to students once published and its visibility rules are met.

# 2 Flow of Events
## 2.1 Basic Flow
1. Teacher logs into the system.
2. Teacher navigates to a Course and selects a Topic.
3. Teacher clicks “Create Challenge.”
4. System displays a form with input fields:
- Challenge title
- Challenge body and description
- Difficulty (easy/medium/hard)
- Points
- Correct answers
- Optional: photo upload
5. Teacher fills out the form and submits it.
6. System validates inputs.
7. System inserts the new challenge (linked to the selected Topic).
8. System confirms: “Challenge created successfully.”

### 2.1.1 Activity Diagram

![Activity Diagram](../ActivityDiagram/CreateChallengesActivityDiagramCorrected.drawio.png)

### 2.1.2 Mock-up

![Mock-up](../Images/Challenges-Lofi.png)

### 2.1.3 Narrative
The Author uses this form to create structured learning tasks inside a topic. Once saved, the challenge is stored in the database and can later be edited or deleted. Auto-checking with correct answers.
```
Feature: Create a new challenge

  As a Teacher
  I want to create a challenge in a topic
  so that students can solve it.

  Background:
    I am logged in as a Teacher
    And I am on the "topic details" page

  Scenario: Create challenge
    When I click "add challenge"
    Then the "create challenge" form appears

  Scenario: Create a challenge with valid data
    When I enter "Challenge 1" as title
    And the exercise as body
    And "medium" as difficulty
    And "15" as points
    And upload "diagram.png"
    And set "42" as correct answer
    And press "create"
    Then I see the "challenge details" page
    And a success message

  Scenario: Fail to create a challenge with invalid data
    When I leave title and body empty
    And do not select a difficulty
    And enter "-10" as points
    And press "create"
    Then I stay on the "create challenge" page
    And an error message is shown
```
## 2.2 Alternative Flows
Invalid Data: Missing title, body, correct answers, or points: error message, no save.

Cancel: Teacher clicks Cancel: return to topic without saving.

Draft: Teacher does not publish the challenge.

Slug Conflict: If slug already exists in the topic, system generates a unique slug automatically.

# 3 Special Requirements

Only authenticated users with role = teacher can create challenges.

# 4 Preconditions

Teacher is logged in and active.

Target Course and Topic exist.

# 5 Postconditions

New Challenge row exists in DB linked to Topic.

Students will see the challenge once the parent course/topic is published and visible.

# 6 Extension Points

Edit Challenge: Teacher can later modify challenge fields.

Submit Answer: Students create submissions.

Review/Grade Submissions.

Comment on Challenge.
