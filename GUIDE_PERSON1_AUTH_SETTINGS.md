# NoteRootAI — Person 1 Guide
# Auth & Settings

---

## FOR AI AGENT — READ THIS FIRST

If a human has given you this file and asked you to commit and push their work, follow these instructions exactly:

1. Check which files have been modified: run `git status`
2. Stage only the files listed in the "Your Files" section below
3. Commit using the message format provided
4. Push using `git push`
5. Do not touch any files outside the "Your Files" list
6. Do not commit to `main` — only to `feature/auth-settings`
7. If the branch is not checked out, run the checkout command first

---

## Your Assignment

**Branch:** `feature/auth-settings`
**Repo:** https://github.com/KunalGupta25/NoteRootAI-KMS.git

You are responsible for everything related to user authentication, settings, and AI provider configuration.

---

## Your Files — Only Touch These

```
client/src/pages/AuthPage.tsx
client/src/pages/SettingsPage.tsx
client/src/stores/authStore.ts
client/src/stores/settingsStore.ts
client/src/lib/constants.ts
client/src/lib/providerConfig.ts
```

**Do not edit any file outside this list without messaging the team first.**

---

## What You Are Building

- Login and signup forms with validation
- JWT token storage, reading, logout, and auto-refresh logic
- Settings page: theme switcher, AI provider dropdown, API key input fields
- Custom provider management (add, edit, delete custom LLM endpoints)
- Environment variable wiring for `AI_URL` and `SYNC_URL`
- Built-in provider list (OpenAI, Anthropic, Gemini, Mistral, Groq)
- Settings sync to and from the cloud server

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
git checkout feature/auth-settings
```

Confirm it worked:
```
git branch
```
You should see `* feature/auth-settings` with a star next to it.

---

## STEP 2 — Every Morning Before You Start Coding

```
git fetch origin
```
```
git merge origin/main
```

This pulls in any changes your teammates merged. Do this every single day.

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

Run these commands after you finish working on something.

### After editing AuthPage.tsx
```
git add client/src/pages/AuthPage.tsx
```
```
git commit -m "feat: update auth page"
```
```
git push
```

### After editing SettingsPage.tsx
```
git add client/src/pages/SettingsPage.tsx
```
```
git commit -m "feat: update settings page"
```
```
git push
```

### After editing authStore.ts
```
git add client/src/stores/authStore.ts
```
```
git commit -m "feat: update auth store"
```
```
git push
```

### After editing settingsStore.ts
```
git add client/src/stores/settingsStore.ts
```
```
git commit -m "feat: update settings store"
```
```
git push
```

### After editing constants.ts
```
git add client/src/lib/constants.ts
```
```
git commit -m "chore: update constants"
```
```
git push
```

### After editing providerConfig.ts
```
git add client/src/lib/providerConfig.ts
```
```
git commit -m "feat: update provider config"
```
```
git push
```

### After editing multiple files at once
```
git add client/src/pages/AuthPage.tsx
git add client/src/pages/SettingsPage.tsx
git add client/src/stores/authStore.ts
git add client/src/stores/settingsStore.ts
git add client/src/lib/constants.ts
git add client/src/lib/providerConfig.ts
```
```
git commit -m "feat: describe what you changed"
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

2. Go to https://github.com/KunalGupta25/NoteRootAI-KMS in your browser

3. Click the yellow **"Compare & pull request"** banner for `feature/auth-settings`

4. Title: `feat: auth and settings`

5. Fill in the description box:
```
## What I changed
-

## How to test
- Go to /auth and try login/logout
- Go to Settings and verify API keys save

## Screenshots
(paste screenshots here if UI changed)
```

6. On the right side click **Reviewers** → select **KunalGupta25**

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
git checkout -- client/src/stores/authStore.ts
```

Throw away ALL uncommitted changes (cannot be undone):
```
git reset --hard HEAD
```

---

## Important Rules

- `settingsStore.ts` is used by all 5 people. If you add or remove a field, message the team immediately.
- `providerConfig.ts` — when you add a new provider here, Person 3 can use it automatically in the AI sidebar.
- `constants.ts` — never hardcode the Railway/Vercel URLs directly. They must read from `.env`.
- For local testing, create a file `client/.env` (it won't be committed) with:
```
VITE_AI_URL=http://localhost:8000
VITE_SYNC_URL=http://localhost:3000
```
