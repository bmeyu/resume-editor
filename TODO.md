# Project TODO

This file tracks future requirements and feature enhancements for the resume editor.

## Feature: Reverse Job Search (Find Matching Jobs)

**Objective:** Allow users to find relevant job postings on the web based on their current resume content.

**Workflow:**
1.  User finishes editing their resume.
2.  User clicks a "Find Matching Jobs" button.
3.  The system opens a new browser tab for one or more job search engines, pre-filled with search queries derived from the resume.

**Implementation Details:**

1.  **Extract Key Information from Resume:**
    -   Create a JavaScript function to parse the resume's text content.
    -   Extract key entities like:
        -   **Job Title / Role:** (e.g., "Senior Product Manager")
        -   **Key Skills:** (e.g., "User Growth", "SQL", "Data Analysis")
        -   **Location(s):** (e.g., "Shanghai", "Beijing")

2.  **Construct Search Queries:**
    -   Combine the extracted information into effective search strings suitable for job boards.
    -   Example: `"Senior Product Manager" "User Growth" "Shanghai"`

3.  **Launch Search (Implementation Method):**
    -   **Initial Recommended Approach (Simple & Robust):** Use the URL query parameters of major job boards.
    -   Identify the URL structure for sites like Boss Zhipin, Liepin, etc.
    -   Dynamically generate the search URL and open it in a new tab using `window.open()`.
    -   *Example URL (hypothetical): `https://www.zhipin.com/web/geek/job?query=产品经理&city=101020100`*

---

## Make "AI Optimization Tips" Dynamic

The current AI tips section is a static placeholder. The goal is to make it functional by implementing the following logic:

- **Real-time Content Analysis:** The script should read the text from all editable fields of the resume whenever the user makes a change.
- **Keyword Matching:** Compare the resume content against a predefined list of relevant industry keywords (e.g., "user growth", "data-driven", "GMV", "retention rate").
- **Quantified Achievement Calculation:** Analyze the text to identify and count quantified results (e.g., using regular expressions to find patterns like "increased by X%", "grew by Y million", "achieved Z%"). Calculate the percentage of job/project descriptions that contain such data.
- **Dynamic Suggestion Generation:** Based on the analysis, generate new, relevant tips. For example:
    - Suggest adding specific keywords that are missing but relevant to the job title.
    - Encourage adding more data if the quantified achievement ratio is low.
- **Update UI:** Dynamically update the content of the AI tips section with the newly generated suggestions.
