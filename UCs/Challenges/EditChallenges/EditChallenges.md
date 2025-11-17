# 1 Use-Case Name
Edit Challenges CRUD: Update

## 1.1 Brief Description

This use case describes how a Teacher edits an existing challenge within a course topic. The Teacher can modify the challenge title, body, difficulty, points, correct answers, or optional photo. Once saved, the changes are updated in the database. If the challenge is published, the update becomes visible to students.

# 2 Flow of Events
## 2.1 Basic Flow
1. Teacher logs into the system.
2. Teacher navigates to a Course and selects a Topic.
3. Teacher selects a Challenge to edit.
4. Teacher clicks “Edit Challenge.”
5. System displays a form pre-filled with the challenge’s existing data:
   - Challenge title  
   - Challenge body and description  
   - Difficulty (easy/medium/hard)  
   - Points  
   - Correct answers  
   - Optional: photo upload  
6. Teacher edits the desired fields and submits the form.  
7. System validates the updated inputs.  
8. System updates the challenge data in the database.  
9. System confirms: “Challenge updated successfully.”

### 2.1.1 Activity Diagram

![Activity Diagram](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/EditChallenges/EditChallengesActivityDiagramCorrected.drawio.png)

### 2.1.2 Mock-up

![Mock-up](https://github.com/Ngoc901/erudite-documentation/blob/main/UCs/CreateChallenges/Lo-Fi.png)

### 2.1.3 Narrative
The Author uses this form to create structured learning tasks inside a topic. Once saved, the challenge is stored in the database and can later be edited or deleted. Auto-checking with correct answers.
```
Feature: Edit an existing challenge

As a Teacher
I want to edit a challenge in a topic
So that I can fix errors or update its details.

Background:
I am logged in as a Teacher
And I am on the "challenge details" page

Scenario: Edit challenge successfully
When I click "Edit"
Then the "Edit Challenge" form appears
When I change the title to "Updated Challenge 1"
And update "Points" to "20"
And set "hard" as difficulty
And press "Save"
Then I see the updated "challenge details" page
And a success message is shown

Scenario: Fail to edit a challenge with invalid data
When I remove the title and press "Save"
Then I stay on the edit form
And an error message is shown

```
## 2.2 Alternative Flows
- **Invalid Data:** Missing or incorrect title, points, or difficulty → show error and remain on edit form.  
- **Cancel:** Teacher clicks Cancel → return to challenge details without saving.  
- **Draft Mode:** Unpublished challenge remains hidden from students until published.

# 3 Special Requirements

- Teacher is logged in and active.  
- Target Course, Topic, and Challenge exist.  
- Teacher is the author of the challenge or has permission to edit it.

# 4 Preconditions

- The updated challenge is stored in the database.  
- The changes appear in the topic’s challenge list.  
- If published, students will see the new version.

# 5 Postconditions

New Challenge row exists in DB linked to Topic.

Students will see the challenge once the parent course/topic is published and visible.

# 6 Extension Points

- **Delete Challenge:** Teacher can remove the challenge.  
