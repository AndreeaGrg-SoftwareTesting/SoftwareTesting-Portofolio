## 📁 File Upload Testing - Strategy

**Objective:** To verify the security and functional constraints of the CV upload field.

### Test Scenarios:
1. **Unsupported File Format (Negative Testing):** Attempt to upload an image file (.jpg/.png) or a text file (.txt) instead of the required document formats (.pdf/.docx) to verify if the system has a "whitelist" of allowed extensions and if it displays a user-friendly error message.
2. **File Size Limit:** Attempt to upload a file larger than 5MB/10MB to check for error handling.
3. **Empty File:** Attempt to upload a 0 KB file.
4. **Special Characters:** Upload a file named `CV_!@#$%^&*().pdf` to see how the server handles the name.

----

5. ### Test Summary & Executive Overview

 The testing phase for the **"Apply for Job"** file upload functionality is concluded with a **FAIL** status. While the front-end (UI) correctly identifies invalid files through various triggers, there is a critical lack of server-side enforcement.

**Key Findings:**
* **Validation Bypass:** All negative test cases (unsupported formats, oversized files, empty content) resulted in successful form submissions despite visible UI warnings.
* **Logic Error:** The "TRIMITE" (Submit) button remains active and functional regardless of the validation state of the uploaded file.
* **Misleading UX:** The system displays a generic "illegal_extension" error for issues unrelated to the file type (e.g., 0 KB size or special characters in the name).
* **Risk Level:** **High**. The system is vulnerable to server storage abuse and potentially malicious file uploads.

-----

6. ## Test Results & Bug Reports

### Scenario 1: Unsupported File Format (.jpeg, .txt)
**Status:** ❌ **FAILED**

* **Observation:** I tested the system with multiple unsupported formats, including images (`.jpeg`) and plain text files (`.txt`).
* **The Bug:** In all cases, the system displayed an error message: *"Error: illegal_extension"*. However, the validation logic is not enforced; the **"TRIMITE"** button remains active, allowing the user to bypass the restriction and upload non-document files.

**Visual Proof:**
<img width="1197" height="623" alt="Screenshot 2026-02-24 at 17-24-46 Lucrător depozit – lucrător de completare comenzi - Work Force RO" src="https://github.com/user-attachments/assets/16a6027c-36f9-4b8c-98f0-c04a086dd0cf" />
<img width="1703" height="273" alt="Screenshot 2026-02-24 at 17-27-01 Lucrător depozit – lucrător de completare comenzi - Work Force RO" src="https://github.com/user-attachments/assets/a0c00e09-d175-403a-9bb5-cfae70a1b9a2" />

<img width="1187" height="828" alt="Screenshot 2026-02-25 at 04-26-07 LUCRĂTOR ÎN PRODUCȚIE - Work Force RO" src="https://github.com/user-attachments/assets/ca5c87bf-f488-4564-ad0d-25dd4fe9e89b" />
<img width="1647" height="308" alt="Screenshot 2026-02-25 at 04-26-26 LUCRĂTOR ÎN PRODUCȚIE - Work Force RO" src="https://github.com/user-attachments/assets/656ee71b-e8ae-4ec7-a1a2-89aee8d4470a" />


-------

### Scenario 2: File Size Limit (15 MB)
**Status:** ❌ **FAILED**

* **Observation:** When attempting to upload a 15 MB dummy file, the UI displayed a warning: *"test_large_file.pdf - File exceeds size limit"*.
* **The Bug:** Despite the warning, the "TRIMITE" (Submit) button remained active and functional. The system allowed the final submission of a file that exceeded its own specified limit.

* **Visual Proof:**
<img width="1383" height="802" alt="Screenshot 2026-02-24 at 18-09-58 LUCRĂTOR EXPEDIȚIE – STIVUITOR SAU EPT - Work Force RO" src="https://github.com/user-attachments/assets/e7fbea9b-8c83-42ad-ba7f-12b7c80b57d0" />

<img width="1807" height="537" alt="Screenshot 2026-02-24 at 18-10-21 LUCRĂTOR EXPEDIȚIE – STIVUITOR SAU EPT - Work Force RO" src="https://github.com/user-attachments/assets/f91a8d2b-84ca-41cf-a1a4-3e510c332462" />

-----

### Scenario 3: Empty File (0 KB)
**Status:** ❌ **FAILED**

* **Observation:** I attempted to upload a file with 0 KB content (`empty_cv.pdf`) to verify if the system requires a minimum file size for a valid CV.
* **The Bug:** The system displayed a confusing error message: *"Error: illegal_extension, Message: Sorry, this file extension is not permitted for security reasons"*, even though the file was a `.pdf`. Crucially, the system **did not block the submission**, allowing the empty file to be sent successfully.
* **Visual Proof:**
<img width="1440" height="812" alt="Screenshot 2026-02-24 at 18-43-33 LUCRĂTOR LOGISTICĂ – COMPLETARE COMENZI - Work Force RO" src="https://github.com/user-attachments/assets/6f373b10-41ac-4666-814d-8a76ccac781f" />

<img width="1616" height="311" alt="Screenshot 2026-02-24 at 18-44-39 LUCRĂTOR LOGISTICĂ – COMPLETARE COMENZI - Work Force RO" src="https://github.com/user-attachments/assets/5dfe5871-4133-4959-804b-4d4e92c6422d" />


-----

### Scenario 4: Special Characters in File Name
**Status:** ❌ **FAILED**

* **Observation:** I uploaded a valid PDF file renamed with a string of special characters (`CV_@$%$$#@()!.pdf`) to test how the server handles non-alphanumeric filenames.
* **The Bug:** The system triggered a **misleading error**: *"Error: illegal_extension"*. This is a technical inconsistency, as the extension was a standard `.pdf`. It appears the validation logic incorrectly identifies special characters in the filename as part of the extension or simply fails to parse the name correctly. 
* **Critical Flaw:** Despite the "illegal" warning, the **"TRIMITE"** button remained active, and the application was successfully submitted.
* **Visual Proof:**
  <img width="1355" height="822" alt="Screenshot 2026-02-24 at 18-55-47 Lucrător ambalare – Procesarea alimentelor - Work Force RO" src="https://github.com/user-attachments/assets/79687426-b95e-40ae-b9d4-3ab1457e22cb" />

  
<img width="1480" height="321" alt="Screenshot 2026-02-24 at 18-56-09 Lucrător ambalare – Procesarea alimentelor - Work Force RO" src="https://github.com/user-attachments/assets/230005e3-54b9-4728-b8f7-145b3de6c907" />



---

### 🚩 Final Bug Inventory

| ID | Issue Description | Severity | Status |
| :--- | :--- | :--- | :--- |
| **BUG-01** | **Critical Validation Bypass:** Submit button is not disabled when UI errors occur. | **Critical** | Open |
| **BUG-02** | **Server-Side Enforcement:** Server accepts files exceeding the 10MB limit. | **High** | Open |
| **BUG-03** | **Inaccurate Error Logic:** System reports "illegal_extension" for size and naming issues. | Medium | Open |
| **BUG-04** | **Localization Issue:** Validation messages are displayed in English on the RO site. | Low | Open |




