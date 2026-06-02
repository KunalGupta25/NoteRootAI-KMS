# NoteRootAI — Person 2 Guide
# Note Editor & Vault UI

---

## FOR AI AGENT — READ THIS FIRST

If a human has given you this file and asked you to commit and push their work, follow these instructions exactly:

1. Check which files have been modified: run `git status`
2. Stage only the files listed in the "Your Files" section below
3. Commit using the message format provided
4. Push using `git push`
5. Do not touch any files outside the "Your Files" list
6. Do not commit to `main` — only to `feature/editor-vault`
7. If the branch is not checked out, run the checkout command first

---

## Your Assignment

**Branch:** `feature/editor-vault`
**Repo:** https://github.com/KunalGupta25/NoteRootAI-KMS.git

You are responsible for the note editing experience and the vault navigation sidebar.

---

## Your Files — Only Touch These

```
client/src/pages/NoteEditorPage.tsx
client/src/pages/Dashboard.tsx
client/src/components/Editor/NoteEditor.tsx
client/src/components/Editor/EditorToolbar.tsx
client/src/components/Editor/BlockMenu.tsx
client/src/components/Editor/SelectionToolbar.tsx
client/src/components/Editor/TableToolbar.tsx
client/src/components/Editor/DatabaseView.tsx
client/src/components/Editor/extensions/MentionList.tsx
client/src/components/Editor/extensions/PageMentionExtension.ts
client/src/components/Editor/extensions/slash-command.ts
client/src/components/Editor/extensions/SlashCommandList.tsx
client/src/components/Layout/AppShell.tsx
client/src/components/Layout/VaultTree.tsx
client/src/stores/noteStore.ts
```

**Do not edit any file outside this list without messaging the team first.**

---

## What You Are Building

- TipTap rich-text editor with all extensions
- Slash command menu (`/` key) for inserting blocks
- `@mention` page linking so users can link to other notes inline
- Formatting toolbar: bold, italic, headings, tables, code blocks
- Note properties panel, emoji icons, tags, breadcrumbs
- Vault tree sidebar: create, rename, delete, nest notes
- Dashboard: recent notes list, stats, tag cloud
- `noteStore`: note CRUD, offline-first IndexedDB save, cloud sync
- AppShell 3-column layout

---

## STEP 1 — One-Time Setup (Do this once, on your first day)

### Install Git
Download from https://git-scm.com/downloads — install with all defaults.

Open Command Prompt and verify:
```
git --version
```

### Install Node.js
Download from https://nodejs.org — pick the LTS version, install with defaults.

Verify:
```
node --version
```

### Set your Git identity
```
git config --global user.name "Your Full Name"
```
```
git config --global user.email "your@email.com"
```

### Clone the repository
```
git clone https://github.com/KunalGupta25/NoteRootAI-KMS.git
```
```
cd NoteRootAI-KMS
```

### Install frontend dependencies
```
cd client
```
```
npm install
```
```
cd ..
```

### Switch to your branch
```
git checkout feature/editor-vault
```

Confirm it worked:
```
git branch
```
You should see `* feature/editor-vault` with a star next to it.

---

## STEP 2 — Every Morning Before You Start Coding

```
git fetch origin
```
```
git merge origin/main
```

---

## STEP 3 — Run the App Locally

```
cd client
```
```
npm run dev
```

Open http://localhost:5173 in your browser. Press `Ctrl+C` to stop.

---

## STEP 4 — Committing Your Work

### After editing NoteEditor.tsx
```
git add client/src/components/Editor/NoteEditor.tsx
```
```
git commit -m "feat: update note editor"
```
```
git push
```

### After editing EditorToolbar.tsx
```
git add client/src/components/Editor/EditorToolbar.tsx
```
```
git commit -m "feat: update editor toolbar"
```
```
git push
```

### After editing BlockMenu.tsx
```
git add client/src/components/Editor/BlockMenu.tsx
```
```
git commit -m "feat: update block menu"
```
```
git push
```

### After editing SelectionToolbar.tsx
```
git add client/src/components/Editor/SelectionToolbar.tsx
```
```
git commit -m "feat: update selection toolbar"
```
```
git push
```

### After editing TableToolbar.tsx
```
git add client/src/components/Editor/TableToolbar.tsx
```
```
git commit -m "feat: update table toolbar"
```
```
git push
```

### After editing DatabaseView.tsx
```
git add client/src/components/Editor/DatabaseView.tsx
```
```
git commit -m "feat: update database view"
```
```
git push
```

### After editing slash commands
```
git add client/src/components/Editor/extensions/slash-command.ts
git add client/src/components/Editor/extensions/SlashCommandList.tsx
```
```
git commit -m "feat: update slash commands"
```
```
git push
```

### After editing @mention / page linking
```
git add client/src/components/Editor/extensions/MentionList.tsx
git add client/src/components/Editor/extensions/PageMentionExtension.ts
```
```
git commit -m "feat: update page mention extension"
```
```
git push
```

### After editing NoteEditorPage.tsx
```
git add client/src/pages/NoteEditorPage.tsx
```
```
git commit -m "feat: update note editor page"
```
```
git push
```

### After editing Dashboard.tsx
```
git add client/src/pages/Dashboard.tsx
```
```
git commit -m "feat: update dashboard"
```
```
git push
```

### After editing VaultTree.tsx
```
git add client/src/components/Layout/VaultTree.tsx
```
```
git commit -m "feat: update vault tree"
```
```
git push
```

### After editing AppShell.tsx
```
git add client/src/components/Layout/AppShell.tsx
```
```
git commit -m "feat: update app shell layout"
```
```
git push
```

### After editing noteStore.ts
```
git add client/src/stores/noteStore.ts
```
```
git commit -m "feat: update note store"
```
```
git push
```

### After editing all your files at once
```
git add client/src/pages/NoteEditorPage.tsx
git add client/src/pages/Dashboard.tsx
git add client/src/components/Editor/NoteEditor.tsx
git add client/src/components/Editor/EditorToolbar.tsx
git add client/src/components/Editor/BlockMenu.tsx
git add client/src/components/Editor/SelectionToolbar.tsx
git add client/src/components/Editor/TableToolbar.tsx
git add client/src/components/Editor/DatabaseView.tsx
git add client/src/components/Editor/extensions/slash-command.ts
git add client/src/components/Editor/extensions/SlashCommandList.tsx
git add client/src/components/Editor/extensions/MentionList.tsx
git add client/src/components/Editor/extensions/PageMentionExtension.ts
git add client/src/components/Layout/AppShell.tsx
git add client/src/components/Layout/VaultTree.tsx
git add client/src/stores/noteStore.ts
```
```
git commit -m "feat: describe today's changes"
```
```
git push
```

---

## STEP 5 — Opening a Pull Request (When Your Work Is Ready)

1. Push all your latest work:
```
git push
```

2. Go to https://github.com/KunalGupta25/NoteRootAI-KMS

3. Click the yellow **"Compare & pull request"** banner for `feature/editor-vault`

4. Title: `feat: editor and vault UI`

5. Fill in the description:
```
## What I changed
-

## How to test
- Create a new note and verify editor works
- Test slash commands with / key
- Test vault tree: create, rename, delete notes

## Screenshots
(paste screenshots here)
```

6. Click **Reviewers** → select **KunalGupta25**

7. Click **Create pull request**

---

## STEP 6 — After Someone Else's Code Gets Merged

```
git fetch origin
```
```
git merge origin/main
```

---

## Undo a Mistake

Undo your last commit but keep file changes:
```
git reset --soft HEAD~1
```

Throw away changes to one specific file:
```
git checkout -- client/src/stores/noteStore.ts
```

Throw away ALL uncommitted changes (cannot be undone):
```
git reset --hard HEAD
```

---

## Important Rules

- `noteStore.saveNote()` calls `embedNoteInBackground()` at the end of the function. **Do not remove this line** — it's what keeps AI search working.
- The editor stores content as **HTML strings** (like `<p>Hello</p>`), not raw markdown. Keep it this way.
- If you change the `Note` interface (add/remove a field) in `noteStore.ts`, message the whole team immediately — Person 3 and Person 4 both depend on it.
