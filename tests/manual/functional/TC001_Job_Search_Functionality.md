### TC 001: Job Search Functionality (Keyword-based)  

* **Test Suite:** Manual / Functional  
* **Priority:** High  
* **Status:** Completed 

---

### 1. Description 

Verify that the search engine correctly filters job listings and provides appropriate feedback when results are found versus when no matches exist.

---

### 2. Preconditions

* The user is on the Vacancies/Jobs page.
* The system has active job listings (e.g., Warehouse, Logistics).
* Stable internet connection.

---

### 3. Test Steps & Data

| Step | Action | Test Data| 
| :--- | :--- | :--- | 
| 1 | Locate the search input field | -| 
| 2 | Enter a keyword with high vacancy volume | `warehouse` |
| 3 | Click the "Search" button | - |
| 4 | Clear the search and enter a non-existent category | `doctor` |
| 5 | Click the "Search" button | - |

---

### 4. Expected Results

* **For "warehouse":** The system should display a list of vacancies (e.g., 160 found) containing the keyword.
*	**For "doctor":** The system should display a "No results found" message (e.g., "Oops, we have not found any vacancies") and provide tips for better searching.

---

### 5. Actual Results (Findings)

* **Positive Scenario:** System returned 160 vacancies for "warehouse". Relevant job cards (Wasco, Tempo-Team) were displayed correctly.
* **Negative Scenario:** System correctly identified no matches for "doctor". Displayed a user-friendly error message with suggestions to refine the search.

### Final Status: PASS

---

### 6. Test Evidence
* **Scenario: High volume results ("warehouse")**
  ![Warehouse Results]<img width="1787" height="663" alt="Screenshot 2026-03-07 at 12-07-11 Jobs Tempo-Team" src="https://github.com/user-attachments/assets/a1debe59-87b9-4183-ac50-19f86b9329c4" />


* **Scenario: No results found ("doctor")**
  ![No Results](path/to/your/image_doctor.png)
<img width="1477" height="795" alt="Screenshot 2026-03-07 at 12-08-00 Jobs Tempo-Team" src="https://github.com/user-attachments/assets/ed24950a-2945-4342-835b-6e8e000289a1" />





