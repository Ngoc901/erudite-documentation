# Function Points - Erudite Platform

**Method:** IFPUG TinyTools (UFP × VAF)  
**VAF:** 1.02 (GSC sum = 37, typical modern web app)  
**Week 13 trendline:** k = 0.520 FP/h  
**Week 20 trendline:** k = 0.626 FP/h (R² = 0.67) → `predicted hours = AFP / k`

Due to the large number of small, structurally similar Use Cases, FP was calculated and tracked at **group level** rather than per-UC. This is consistent with the Berkling UCL methodology where each chart data point represents a UC group.

---

## Core Groups - Evolution (Week 13 → Week 20)

| Group | UCs | FP (W13) | Hours (W13) | FP (W20) | Hours (W20) |
|---|---|---|---|---|---|
| **authentication_authorisation** | register, login, logout, authenticate_user, changepassword (+google_oauth, reset_password, verify_email) | 32.64 | 54.35h | **73** | **103h** |
| **courses** | create_course, edit_course, delete_course, view_courses, manage_enrollments | 24.48 | 64.65h | **95** | **187h** |
| **topics** | create_topic, edit_topic, delete_topic, view_topic | 24.48 | 38.84h | **43** | **37h** |
| **challenges** | create_challenge, edit_challenge, delete_challenge, view_challenges, submit_challenge | 24.48 | 22.85h | **70** | **55h** |

> Week 13 predictions vs Week 20 actuals: auth ±12%, courses +9%, topics −22%, challenges −18%. Both models shown on chart - old (k=0.520) and new (k=0.626).

---

## Small Groups (Semester 2 additions)

These groups were added in Semester 2 and are plotted as individual points on the extended FP chart.

| Group | UCs | UFP | AFP (×1.02) |
|---|---|---|---|
| **profile** | edit_profile, change_password, view_profile | 49 | **49.98** |
| **lessons** | create_lesson, edit_lesson, delete_lesson, view_lesson | 54 | **55.08** |
| **lti** | lti_moodle_integration | 28 | **28.56** |
| **dashboard** | dashboard | 19 | **19.38** |
| **feedback** | course_feedback | 15 | **15.30** |
| **certificates** | course_certificate | 12 | **12.24** |
| **bookmarks** | bookmark_course | 13 | **13.26** |

---

## FP Calculation Method

Each UC was classified by its dominant transaction type:

| Type | Complexity | UFP weight | UCs |
|---|---|---|---|
| EI (External Input) | High | ×6 | create_course, create_topic, create_challenge, lti_moodle_integration |
| EI (External Input) | Average | ×4 | register, login, edit_* UCs, submit_challenge, authenticate_user, change_password, edit_profile, google_oauth, reset_password, verify_email, create_lesson, edit_lesson |
| EQ (External Inquiry) | Low/Avg | ×3–4 | logout, view_* UCs, delete_* UCs, dashboard, bookmark_course, view_lesson |
| ILF (Internal Logical File) | Low/Avg | ×7–10 | counted per UC: User, Course, Topic, Challenge, Lesson, Enrollment files |
| EIF (External Interface File) | Low/High | ×5–10 | JWT service (auth UCs), Moodle API (lti), Cloudinary (edit_profile) |
