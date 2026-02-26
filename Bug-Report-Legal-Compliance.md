🧰Bug Report: Server Error (508) on Terms & Conditions Access

Status: Open 🔴

Severity: Critical (Blocker)

Priority: High

## 1. Description

When attempting to access the "Termenii si conditiile site-ului" link from the registration/login page, the server fails to load the content and displays a 508 Resource Limit Is Reached error page. This prevents users from legally consenting to the terms, effectively blocking the onboarding process.

## 2. Steps to Reproduce

1.Navigate to the login/registration page of the application.

2.Locate the "Termeni Si Conditii" section.

3.Click on the hyperlinked text: "termenii si conditiile site-ului *".

4.Observe the page redirection.

## 3. Expected Result

The user should be redirected to a page displaying the legal Terms and Conditions text or a modal window should open with the relevant information.

## 4. Actual Result

The user is redirected to a blank page with the message: "508 Resource Limit Is Reached - The website is temporarily unable to service your request".

## 5. Environment

   - URL: aptjob.ro (according to screenshot)

   - Browser: Chrome / Any

   - Date: February 26, 2026

## 6. Attachments

<img width="1920" height="443" alt="Screenshot 2026-02-26 at 21-09-37 Teste online -" src="https://github.com/user-attachments/assets/3b837986-dca4-4f97-b5af-216aa5a0fa7d" />

<img width="1900" height="96" alt="Screenshot 2026-02-26 at 17-51-36 508 Resource Limit Is Reached" src="https://github.com/user-attachments/assets/6d5425b9-b11c-456d-a8b2-34eace2344b7" />

    
