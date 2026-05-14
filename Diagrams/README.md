# Diagrams

This folder contains all diagrams for the Erudite platform documentation, written in **PlantUML** format.

---

## How to Render PlantUML Files

### Option 1 — VS Code (recommended)
Install the [PlantUML extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml), open any `.puml` file, and press `Alt+D` to preview.

### Option 2 — Online Renderer
Copy the contents of any `.puml` file into [plantuml.com/plantuml](https://www.plantuml.com/plantuml/uml/).

### Option 3 — CLI (batch render all to PNG)
```bash
# macOS
brew install plantuml

# Render all diagrams to PNG
plantuml Diagrams/ActivityDiagrams/*.puml
plantuml Diagrams/UseCaseDiagram.puml
```

---

## Use Case Diagram

| File | Description |
|---|---|
| ![Use Case Diagram](UseCaseDiagram.png)

[Source: UseCaseDiagram.puml](UseCaseDiagram.puml) | Full overview of all actors and use cases across all 11 feature groups |

---

## Activity Diagrams

All activity diagrams are in `ActivityDiagrams/`. Each is linked from the corresponding Use Case document.

### Authentication & Authorization

| File | Use Case |
|---|---|
| [Register.puml](ActivityDiagrams/Register.puml) | [Register](../UCs/Authentication/Register.md) |
| [Login.puml](ActivityDiagrams/Login.puml) | [Login](../UCs/Authentication/Login.md) |
| [Logout.puml](ActivityDiagrams/Logout.puml) | [Logout](../UCs/Authentication/Logout.md) |
| [VerifyEmail.puml](ActivityDiagrams/VerifyEmail.puml) | [Verify Email](../UCs/Authentication/VerifyEmail.md) |
| [ResetPassword.puml](ActivityDiagrams/ResetPassword.puml) | [Reset Password](../UCs/Authentication/ResetPassword.md) |
| [GoogleOAuth.puml](ActivityDiagrams/GoogleOAuth.puml) | [Google OAuth Sign-In](../UCs/Authentication/GoogleOAuth.md) |

### Courses

| File | Use Case |
|---|---|
| [CreateCourse.puml](ActivityDiagrams/CreateCourse.puml) | [Create Course](../UCs/Courses/CreateCourse.md) |
| [ViewCourse.puml](ActivityDiagrams/ViewCourse.puml) | [View Courses](../UCs/Courses/ViewCourses.md) |
| [EditCourse.puml](ActivityDiagrams/EditCourse.puml) | [Edit Course](../UCs/Courses/EditCourse.md) |
| [DeleteCourse.puml](ActivityDiagrams/DeleteCourse.puml) | [Delete Course](../UCs/Courses/DeleteCourse.md) |
| [ManageEnrollments.puml](ActivityDiagrams/ManageEnrollments.puml) | [Manage Enrollments](../UCs/Courses/ManageEnrollments.md) |

### Topics

| File | Use Case |
|---|---|
| [CreateTopic.puml](ActivityDiagrams/CreateTopic.puml) | [Create Topic](../UCs/Topics/CreateTopic.md) |
| [ViewTopic.puml](ActivityDiagrams/ViewTopic.puml) | [View Topic Items](../UCs/Topics/ViewTopic.md) |
| [EditTopic.puml](ActivityDiagrams/EditTopic.puml) | [Edit Topic](../UCs/Topics/EditTopic.md) |
| [DeleteTopic.puml](ActivityDiagrams/DeleteTopic.puml) | [Delete Topic](../UCs/Topics/DeleteTopic.md) |

### Lessons

| File | Use Case |
|---|---|
| [CreateLesson.puml](ActivityDiagrams/CreateLesson.puml) | [Create Lesson](../UCs/Lessons/CreateLesson.md) |
| [EditLesson.puml](ActivityDiagrams/EditLesson.puml) | [Edit Lesson](../UCs/Lessons/EditLesson.md) |
| [DeleteLesson.puml](ActivityDiagrams/DeleteLesson.puml) | [Delete Lesson](../UCs/Lessons/DeleteLesson.md) |

### Challenges

| File | Use Case |
|---|---|
| [CreateChallenge.puml](ActivityDiagrams/CreateChallenge.puml) | [Create Challenge](../UCs/Challenges/CreateChallenge.md) |
| [EditChallenge.puml](ActivityDiagrams/EditChallenge.puml) | [Edit Challenge](../UCs/Challenges/EditChallenge.md) |
| [SubmitChallenge.puml](ActivityDiagrams/SubmitChallenge.puml) | [Submit Challenge](../UCs/Challenges/SubmitChallenge.md) |

### Bookmarks

| File | Use Case |
|---|---|
| [BookmarkCourse.puml](ActivityDiagrams/BookmarkCourse.puml) | [Bookmark Course](../UCs/Bookmarks/BookmarkCourse.md) |

### Feedback

| File | Use Case |
|---|---|
| [CourseFeedback.puml](ActivityDiagrams/CourseFeedback.puml) | [Course Feedback](../UCs/Feedback/CourseFeedback.md) |

### Profile

| File | Use Case |
|---|---|
| [EditProfile.puml](ActivityDiagrams/EditProfile.puml) | [Edit Profile](../UCs/Profile/EditProfile.md) |
| [ChangePassword.puml](ActivityDiagrams/ChangePassword.puml) | [Change Password](../UCs/Profile/ChangePassword.md) |

### Certificates

| File | Use Case |
|---|---|
| [CourseCertificate.puml](ActivityDiagrams/CourseCertificate.puml) | [Course Certificate](../UCs/Certificates/CourseCertificate.md) |

### Dashboard & Leaderboard

| File | Use Case |
|---|---|
| [Dashboard.puml](ActivityDiagrams/Dashboard.puml) | [Dashboard](../UCs/Dashboard/Dashboard.md) |

### LTI / Moodle Integration

| File | Use Case |
|---|---|
| [LTI-MoodleIntegration.puml](ActivityDiagrams/LTI-MoodleIntegration.puml) | [LTI Integration](../UCs/LTI/LTI-MoodleIntegration.md) |

---

## Mockup Wireframes

Lo-fi wireframe images referenced by UC documents should be placed directly in `Diagrams/` with these filenames:

| Filename | Used in |
|---|---|
| `Auth-lofi.png` | Authentication UCs |
| `Courses-lofi.png` | Course UCs |
| `Topics-lofi.png` | Topic UCs |
| `Challenges-lofi.png` | Challenge UCs |

> These images exist in the old documentation at:
> `documentation-erudite/erudite-documentation/UCs/Images/`
