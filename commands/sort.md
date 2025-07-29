---
description: Sort imports and in the currently changed files
---

# Sort Imports
Sort all imports in the currently changed files according to the project's import order specification:

1. Type imports from scoped packages (@)
2. Type imports from Node.js built-in modules (node:)
3. Type imports from third-party modules
4. Type imports from relative paths (.)
5. Regular imports from scoped packages (@)
6. Regular imports from Svelte
7. Regular imports from Node.js built-in modules
8. Regular imports from third-party modules
9. Regular imports from relative paths (.)

Each group should be sorted alphabetically by import path.

## Svelte Script Organization
For Svelte files, the contents of the `<script lang="ts">` tag MUST be organized in this exact sequence (compatible with both Svelte 4 and Svelte 5):

1. **Imports** (Sorted according to the import order rules above)
2. **Props** 
   - Svelte 4: `export let data: ...`
   - Svelte 5: `let { data }: { data: ... } = $props()`
3. **Component State**
   - Svelte 4: `let variableName = ...`
   - Svelte 5: `let variableName = $state(...)`
4. **Derived State** (`$derived`, `$derived.by`) - Computed values based on state
5. **Reactive Statements** (`$: ...`) - Maintain relative order but group together
6. **Constants** (`const ...`)
7. **Functions** (Event handlers, helpers, etc.)
8. **Component Events**
   - Svelte 4: `const dispatch = createEventDispatcher()`
   - Svelte 5: Event handlers as functions
9. **Stores** (`writable`, `readable`, etc.)
10. **Lifecycle Functions** (`onMount`, `onDestroy`, `beforeUpdate`, `afterUpdate`)

## Command Actions

The command will:
- Identify all currently changed files (modified and untracked)
- Analyze the import structure in TypeScript and Svelte files
- Reorganize imports according to the specified order
- For Svelte files, reorganize the entire `<script>` section according to the organization rules
- Maintain proper spacing between import groups and script sections
- Preserve existing reactive statement order within their group
- Handle both Svelte 4 and Svelte 5 syntax patterns

