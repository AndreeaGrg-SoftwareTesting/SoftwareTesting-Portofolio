# Test Case: TC-005 - Upload Invalid File Format

| Attribute | Details |
| :--- | :--- |
| **Test Case ID** | TC-005 |
| **Priority** | High |
| **Component** | User Profile / Photo Upload |
| **Type** | Negative Testing |

###  Test Objective
Verify that the system correctly rejects non-image file formats (e.g., .pdf) and displays an appropriate error message.

###  Preconditions
1. User is authenticated.
2. User has navigated to the 'Edit Profile' section.

###  Execution Steps
1. Click on the profile picture upload area.
2. From the file picker, select a document in `.pdf` format.
3. Observe the system's reaction.

### ✔️ Expected Result
* **System Action:** The file is not uploaded to the server.
* **User Interface:** An error toast or message is displayed: *"Invalid file type. Please select an image (JPG, PNG)."*
* **Integrity:** The previous profile picture (if any) remains unchanged.


### 🚩 Actual Behavior (See Screenshot)
The system correctly blocks the **.pdf** upload, but provides a **generic error message** instead of a specific format warning.
<img width="740" height="1130" alt="Screenshot 2026-03-02 at 22-19-32 Fotografie de profil – Informații personale – Yahoo Setările contului" src="https://github.com/user-attachments/assets/784747d2-61a1-4eb5-9c8b-29695cb2904a" />

### 📝 My QA Analysis
While the functional requirement ("Block non-images") is met, the **User Experience (UX)** is suboptimal. 
- **The Issue:** The message "Nu se poate încărca această fotografie" suggests a problem with the file content, not the file type.
- **Improvement Suggestion:** The system should explicitly state which formats are allowed upon rejection.
