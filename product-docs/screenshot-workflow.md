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

## Before you capture

Screenshots must reflect the feature in its initial state. If the user has already run the workflow on the same data, the UI will show post-run state rather than the starting point — which makes the screenshots misleading in a how-to context. Before starting, ask the user to confirm they are working with a fresh or reset environment so that each step captures the correct state.

---

## How to capture screenshots

1. Ask the user: "Can you share the PathFactory URL where this feature is accessible, and confirm you are logged in? If not, I'll note where screenshots should be added manually."

2. If a URL is provided, attempt screenshots using the following order:

   **Primary — agent-browser skill:**
   Invoke the agent-browser skill via the `Skill` tool. Provide it with the feature URL, the primary workflow steps identified in Step 3 of the main skill, and the save path `~/pm-playground/product-docs/[feature-slug]/screenshots/`. Instruct it to take a screenshot at each meaningful state change and save files with descriptive names matching the step (e.g. `step-1-open-campaign.png`). Aim for 3–6 screenshots that cover the workflow end to end.

   **Fallback — browser MCP tools:**
   If agent-browser fails, errors, or does not return usable screenshots, switch to browser MCP tools directly.

   **Important:** `mcp__claude-in-chrome__computer` with `save_to_disk: true` does NOT write files to the local filesystem. It stores screenshots in the MCP server's memory for in-conversation display only. To save screenshots to disk, use the following approach after each capture:

   a. Use `mcp__claude-in-chrome__computer` (action: `screenshot`) to view the current state.
   b. Immediately after, use `mcp__claude-in-chrome__javascript_tool` to trigger a browser download of the visible page content:

   ```javascript
   // Load html2canvas from CDN, capture the page, and trigger a download
   const script = document.createElement('script');
   script.src = 'https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js';
   script.onload = () => {
     html2canvas(document.body).then(canvas => {
       const a = document.createElement('a');
       a.download = 'step-N-description.png';
       a.href = canvas.toDataURL('image/png');
       a.click();
     });
   };
   document.head.appendChild(script);
   ```

   Replace `step-N-description.png` with the appropriate filename for each step. The file will download to the user's default Downloads folder. After all screenshots are captured, use Bash to move them from `~/Downloads/` to `~/pm-playground/product-docs/[feature-slug]/screenshots/` with correct step names.

3. Note the file path of each screenshot alongside the step it corresponds to for reference in the article.

---

## If screenshots fail or are skipped

Do not stop or flag an error. Continue with document generation as normal. In the "How to Use It" section, insert a placeholder at each step where a screenshot would be relevant:

`[Screenshot: insert image of [brief description] here]`

At the end of the output, include a note:

> **Screenshots:** Screenshots were not captured during this session. Add images manually in WordPress at each placeholder marked above before publishing.
