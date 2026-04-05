Analyze all pending changes in the current git repository and create a well-structured set of commits.

## Steps

1. **Gather context**
   - Run `git status` to see the working tree state.
   - Run `git diff HEAD` to see all unstaged and staged changes in detail.
   - Run `git log --oneline -10` to understand the existing commit style of the project.

2. **Group changes into logical commits**
   - Analyze the diff and group related changes together (e.g., a new feature + its tests, a bug fix, a refactor, a docs update).
   - Do NOT bundle unrelated changes into a single commit.
   - Determine the correct order for the commits (dependencies first).

3. **Draft commit messages in English**
   For each commit group, write:
   - A short **title** (imperative mood, max 72 characters, no period at end). Example: `Add user authentication via OAuth2`
   - A **description** (optional but recommended for non-trivial changes): explain *why*, not just *what*. Wrap at 72 characters.

4. **Present the plan**
   Show the user a clear numbered list of the planned commits, each with:
   - The files that will be staged for that commit
   - The commit title
   - The commit description (if any)

   Then ask: **"Proceed with these N commits? (yes / edit / cancel)"**

5. **Wait for confirmation**
   - If the user says **yes**: execute the commits in order using `git add <files>` + `git commit -m`.
   - If the user says **edit**: let the user specify what to change, then go back to step 4.
   - If the user says **cancel**: abort without making any changes.

6. **Execute (only after confirmation)**
   For each commit:
   - Stage only the files for that commit: `git add -- <file1> <file2> ...`
   - Commit using a heredoc to preserve formatting:
     ```
     git commit -m "$(cat <<'EOF'
     <title>

     <description>
     EOF
     )"
     ```
   - Report success or any error before moving to the next commit.

## Rules

- Never skip the confirmation step.
- Never use `git add -A` or `git add .` — always stage specific files per commit.
- Never amend existing commits.
- Never force-push.
- Commit messages must be in English regardless of the language used in the conversation.
- If the working tree is clean, say so and stop.
- If there are untracked files that look relevant (new source files, config, tests), include them in the analysis and ask the user whether to include them.
