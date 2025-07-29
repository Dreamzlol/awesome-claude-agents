---
description: Analyzes GitLab MR discussions, applies the suggested code changes to the files, and generates a structured response file
argument-hint: '[GitLab Merge Request URL]'
---

# Task

1.  **Analyze Input**: Extract the project ID and merge request IID from the provided `[GitLab Merge Request URL]`.
2.  **Fetch Discussions**: Use the GitLab MCP Server to retrieve all unresolved discussion threads, including their permalinks, associated file paths, and original comments.
3.  **Synthesize Requirements and Formulate Plan**:
    a. Analyze all fetched discussions to understand the complete set of requested changes.
    b. Synthesize these requirements into a high-level, step-by-step implementation plan. This plan will guide the subsequent code modifications.
4.  **Execute Implementation Plan**: For each actionable item in the plan:
    a. Retrieve the full content of the affected file.
    b. Apply the suggested code modification directly to the file's content in memory.
5.  **Generate Confirmation Responses**: After a change has been successfully implemented, formulate a polite and friendly response in German confirming that the feedback has been addressed (e.g., "Danke für den Hinweis, das habe ich umgesetzt.").
6.  **Format and Create `DISCUSSIONS.md`**: Create a file named `DISCUSSIONS.md`. For each discussion that was addressed, populate the file by strictly adhering to the following Markdown structure:

    ```markdown
    # GitLab: Merge Request Discussions

    ## Discussion: [Discussion Link]

    ### File: [File Path]

    ### Comment

    [The original comment from the discussion thread]

    ### Response

    [The generated German confirmation response]
    ```

7.  **Finalize**: Present the complete, updated contents of all modified files and the `DISCUSSIONS.md` file, ready for the user to review, commit, and paste into GitLab.
