# CLAUDE.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 5. Principle Application Logging

**Purpose:** To ensure transparency and traceability of guideline adherence, maintain a log of when and how specific principles are applied.

**Log File:** A markdown file named `principle-log.md` will be maintained in the project's root directory.

**Procedure for Logging a Principle Application:**
When you apply a principle (e.g., "Simplicity First") to a specific task, request, or code change, append a new entry to the `principle-log.md` file using the following format:

1.  **Open `principle-log.md`** in your editor.
2.  **Navigate to the end of the file.**
3.  **Append the following structure:**
    ```markdown
    - **Request/Task:** [Brief description of the user request or task]
      - **Principle Applied:** [Name of the principle, e.g., "Simplicity First"]
      - **Justification:** [Brief explanation of how the principle was applied and why it was necessary]
      - **Date/Time:** [Timestamp of application]
    ```
    *   Replace the bracketed placeholders (`[...]`) with specific details.
    *   Ensure the log entry is correctly formatted as a markdown list item.
4.  **Save the file.**

**Example Entry:**
```markdown
- **Request/Task:** Refactoring the user authentication module.
  - **Principle Applied:** Simplicity First
  - **Justification:** Removed unnecessary abstraction layers to make the code more readable and maintainable.
  - **Date/Time:** 2026-04-28 14:30 UTC
```
This systematic logging ensures that the application of these guidelines is always documented.
