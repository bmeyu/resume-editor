# Project TODO

This file tracks the status of features for the resume editor.

---

## Feature: Reverse Job Search (Find Matching Jobs)

- **Status:** ✅ Implemented
- **Objective:** Allow users to find relevant job postings based on their resume content.
- **Implementation:** The feature is live. It extracts the job title, location, and skills to generate search links for Boss Zhipin and Liepin.

---

## Feature: Dynamic AI Optimization Tips

- **Status:** ✅ Implemented
- **Objective:** Make the AI tips section functional and provide real-time feedback.
- **Implementation:** The feature is live. The `analyzeResume` function runs on every content change, calculating quantified achievement ratios and keyword matching for the specified job title. The UI is updated dynamically.

---

## Feature: Add English Template (Internationalization)

- **Status:** 📝 Planned
- **Objective:** Implement a language switching feature to support both Chinese and English resume templates.
- **Implementation Plan:**

  1.  **Refactor: Separate Content from Structure**
      -   Create a JavaScript object (or a separate JSON file) to store all display text for both languages (e.g., `i18n.js`).
      -   This object will have keys for each text element (e.g., `title`, `job_title`, `add_experience_btn`) and nested objects for each language (`en`, `zh`).
      -   Assign a unique `data-i18n-key` attribute to each text-bearing element in the HTML.

  2.  **Create Language Switcher**
      -   Add a language toggle button (e.g., "中 / EN") to the control panel.

  3.  **Implement Dynamic Rendering Logic**
      -   Write a JavaScript function `switchLanguage(lang)` that:
          -   Takes a language code (`'en'` or `'zh'`) as input.
          -   Iterates through all elements with a `data-i18n-key` attribute.
          -   Looks up the corresponding translation from the language object.
          -   Updates the `textContent` or `innerHTML` of the element.
      -   The function should also handle placeholder text in `contenteditable` fields.

  4.  **Update State Management**
      -   Modify the `saveToLocalStorage` and `loadFromLocalStorage` functions to handle the new data structure.
      -   Instead of saving the entire `innerHTML` of the resume, save the user-edited text content as a structured object. This keeps the user's data separate from the template's display language.
      -   The selected language should also be saved to local storage so the choice persists.

  5.  **Translate Content**
      -   Create the English version of the default resume template content and add it to the language object.
