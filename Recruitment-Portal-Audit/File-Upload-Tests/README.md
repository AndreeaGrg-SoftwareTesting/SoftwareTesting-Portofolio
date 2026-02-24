## 📁 File Upload Testing - Strategy

**Objective:** To verify the security and functional constraints of the CV upload field.

### Test Scenarios:
1. **Unsupported File Format (Negative Testing):** Attempt to upload an image file (.jpg/.png) or a text file (.txt) instead of the required document formats (.pdf/.docx) to verify if the system has a "whitelist" of allowed extensions and if it displays a user-friendly error message.
2. **File Size Limit:** Attempt to upload a file larger than 5MB/10MB to check for error handling.
3. **Empty File:** Attempt to upload a 0 KB file.
4. **Special Characters:** Upload a file named `CV_!@#$%^&*().pdf` to see how the server handles the name.

5. ----------

6. ## 🐞 Test Results & Bug Reports

### Scenario 1: Unsupported File Format
**Status:** ❌ FAILED

**Bug Report:**
* **Title:** System accepts .jpeg files despite restricting to pdf, docx, doc.
* **Severity:** Medium
* **Steps to Reproduce:**
    1. Select a .jpeg file.
    2. Click Upload.
* **Actual Result:** File uploaded 100% and form submitted successfully.
* **Expected Result:** System should block the upload and show an error.

**Visual Proof:**
<img width="1197" height="623" alt="Screenshot 2026-02-24 at 17-24-46 Lucrător depozit – lucrător de completare comenzi - Work Force RO" src="https://github.com/user-attachments/assets/16a6027c-36f9-4b8c-98f0-c04a086dd0cf" />
<img width="1703" height="273" alt="Screenshot 2026-02-24 at 17-27-01 Lucrător depozit – lucrător de completare comenzi - Work Force RO" src="https://github.com/user-attachments/assets/a0c00e09-d175-403a-9bb5-cfae70a1b9a2" />

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

---

### Scenario 4: Special Characters in File Name
**Status:** ❌ **FAILED**

* **Observation:** I uploaded a valid PDF file renamed with a string of special characters (`CV_@$%$$#@()!.pdf`) to test how the server handles non-alphanumeric filenames.
* **The Bug:** The system triggered a **misleading error**: *"Error: illegal_extension"*. This is a technical inconsistency, as the extension was a standard `.pdf`. It appears the validation logic incorrectly identifies special characters in the filename as part of the extension or simply fails to parse the name correctly. 
* **Critical Flaw:** Despite the "illegal" warning, the **"TRIMITE"** button remained active, and the application was successfully submitted.
* **Visual Proof:**
  <img width="1355" height="822" alt="Screenshot 2026-02-24 at 18-55-47 Lucrător ambalare – Procesarea alimentelor - Work Force RO" src="https://github.com/user-attachments/assets/79687426-b95e-40ae-b9d4-3ab1457e22cb" />

  
<img width="1480" height="321" alt="Screenshot 2026-02-24 at 18-56-09 Lucrător ambalare – Procesarea alimentelor - Work Force RO" src="https://github.com/user-attachments/assets/230005e3-54b9-4728-b8f7-145b3de6c907" />



---



