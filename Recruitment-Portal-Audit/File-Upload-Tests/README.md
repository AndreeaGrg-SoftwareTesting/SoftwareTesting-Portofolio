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
![Success Upload](link-poza-1)
![Success Submission](link-poza-2)
