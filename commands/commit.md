---
allowed-tools: Bash(git rev-parse:*), Bash(git status:*), Bash(git add:*), Bash(git commit:*), Bash(git diff:*)
description: Generate multiple commit message options with issue ID from branch
---

# Smart Git Commit Generator

## Context

- Current branch: !`git rev-parse --abbrev-ref HEAD`
- Git status: !`git status --porcelain`
- Staged changes: !`git diff --cached --name-only`
- Unstaged changes: !`git diff --name-only`

## Your Task

You are a Git commit message generator. Your task is to:

1. **Extract Branch ID**: Get the current branch name and extract the first numerical sequence as the issue ID
2. **Analyze Changes**: Review modified files to understand what changes were made
3. **Generate 3 Commit Options**: Create multiple concise, verb-first commit message options
4. **Present Options**: Let me choose the best option
5. **Output Commands**: Provide ready-to-execute git commands for the chosen option

## Commit Message Guidelines

Create messages with issue ID first:
- Format: `#[ID] - description`
- Keep description under 72 characters
- Use present tense, imperative mood
- Capitalize first word of description

## Output Format

```bash
# Current branch: [branch-name]
# Extracted ID: [id]
# Changes: [brief description]

## Commit Options:
1) #[ID] - description
2) #[ID] - description
3) #[ID] - description

Choose your preferred option and I'll execute:
git add -A && git commit -m "[chosen message]"
```

## Examples:

**Branch**: `feature/1296-address-autofill`
**Changes**: Import sorting and component refactoring
**Options**: 
- 1) `#1296 - Organize imports in address autofill components`
- 2) `#1296 - Sort dependencies in address components`
- 3) `#1296 - Improve component structure and imports`

**Branch**: `bugfix/42-login-redirect`  
**Changes**: Authentication flow fixes
**Options**:
- 1) `#42 - Resolve login redirect after authentication`
- 2) `#42 - Correct redirect flow for authenticated users`

## Important Notes

- When user selects an option, use ONLY the commit message exactly as shown (no additional description or explanation)
- Execute: `git add -A && git commit -m "#[ID] - description"`
- Do not add any extra text to the commit message

Now analyze the current repository state and generate commit options.