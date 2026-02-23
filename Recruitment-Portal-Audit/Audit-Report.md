QA Test Analysis: Candidate Application Flow

Target: Recruitment Portal Application Form

Type: Functional & Localization Testing

Status: FAILED (Critical issues identified)

1. Test Objective
To verify the end-to-end process of applying for a job offer, ensuring that data validation, user interface consistency, and system stability meet quality standards.

2. Step-by-Step Execution & Findings

Step 1: Contact Information Input

    Action: Entered email address and phone number.

    Observation: The system accepted the email andreea.doipunctunu@dumnezescu.com (non-existent domain) and the phone number string abcdefghijkkkkkkk... (alphabetical characters).

  <img width="1345" height="405" alt="Screenshot 2026-02-23 at 19-39-37 E A Muncă în Olanda Aplicarea la ofertă" src="https://github.com/user-attachments/assets/52055b47-8b02-4e01-a5f8-e05fdd760c6c" />
  

    Defect: Missing Input Validation. The fields do not restrict the type of characters or verify the format (RegEx missing).

Step 2: Personal Details & Dropdown Selection

    Action: Navigated to the personal details section and opened the "How did you find us?" (Cum ai ajuns la noi?) dropdown.
    
    Observation: The interface is in Romanian, but the dropdown options (e.g., Ulorka, Znajomi i rodzina, Prasa) are displayed in Polish.

  <img width="653" height="824" alt="Capture2" src="https://github.com/user-attachments/assets/ae65d297-bfc3-49ae-91af-e6bed7d77eae" />

   Defect: Localization/Internationalization Error. Language inconsistency creates a poor User Experience (UX) and potential confusion for Romanian candidates.

Step 3: Mandatory Fields Validation

    Action: Attempted to proceed without filling in the Postal Code.

    Observation: An error message appeared: "Câmpul Cod poștal este obligatoriu".
    
<img width="765" height="856" alt="Screenshot 2026-02-23 at 19-50-17 E A Muncă în Olanda Aplicarea la ofertă" src="https://github.com/user-attachments/assets/94d3b892-b25b-4934-9dd5-e1e62448df6a" />

    Note: This confirms that some validation exists, but it is inconsistently applied across the form.

Step 4: Form Submission

    Action: Clicked the "APLICĂ" (Apply) button after filling in the required fields.

    Observation: The system redirected to a page displaying a generic error message: "A apărut o eroare neașteptată" (An unexpected error has occurred).
<img width="1920" height="406" alt="Screenshot 2026-02-23 at 19-51-57 E A Muncă în Olanda" src="https://github.com/user-attachments/assets/66941c01-5a10-4f0e-ba50-83da70f9afbb" />

    Defect: Unhandled Exception / System Crash. The back-end likely failed to process the invalid data strings (from Step 1) that the front-end failed to filter.

3. Final Conclusion & Severity Assessment

    Overall Assessment: CRITICAL

    The application form fails to provide a reliable path for candidates. The combination of weak front-end validation and unhandled server-side exceptions results in a complete system failure. Furthermore, the language inconsistency in the dropdown menus indicates a lack of thorough regression testing after localization updates.

    Recommendation: Implement strict character masks for the phone field, add email syntax verification, and sync the database translation strings for the Romanian locale.

    Observation: The interface is in Romanian, but the dropdown options (e.g., Ulorka, Znajomi i rodzina, Prasa) are displayed in Polish.

    Defect: Localization/Internationalization Error. Language inconsistency creates a poor User Experience (UX) and potential confusion for Romanian candidates.
