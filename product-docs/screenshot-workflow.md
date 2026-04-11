# Screenshot Workflow

Screenshots are optional. If they cannot be captured for any reason, skip this step entirely and continue to synthesis and writing. Never block or fail the document generation process due to screenshot issues.

---

## When to attempt screenshots

Attempt to capture screenshots when:
- The feature is live in the PathFactory environment
- The user can provide a direct URL to the feature
- The user confirms they are logged in

Skip screenshots without asking if:
- The feature is not yet live ("Coming Soon")
- No URL is provided and the user cannot navigate to the feature
- The browser encounters an error, login wall, or unexpected page state

---

## How to capture screenshots

1. Ask the user: "Can you share the PathFactory URL where this feature is accessible, and confirm you are logged in? If not, I'll note where screenshots should be added manually."

2. If a URL is provided, navigate using agent-browser and take a full-page screenshot at the starting point of the workflow.

3. Walk through each key step of the primary workflow identified in Step 3 of the main skill. Take a screenshot at each meaningful state change — for example, after opening a panel, completing a configuration, or viewing a result. Aim for 3–6 screenshots that cover the workflow end to end.

4. Save screenshots to `~/pm-playground/product-docs/screenshots/[feature-name]/` with descriptive filenames that match the step (e.g. `step-1-open-campaign.png`, `step-2-configure-settings.png`).

5. Note the file path of each screenshot alongside the step it corresponds to for reference in the article.

---

## If screenshots fail or are skipped

Do not stop or flag an error. Continue with document generation as normal. In the "How to Use It" section, insert a placeholder at each step where a screenshot would be relevant:

`[Screenshot: insert image of [brief description] here]`

At the end of the output, include a note:

> **Screenshots:** Screenshots were not captured during this session. Add images manually in WordPress at each placeholder marked above before publishing.
