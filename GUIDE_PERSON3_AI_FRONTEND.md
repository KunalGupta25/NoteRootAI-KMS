# NoteRootAI — Person 3 Guide
# AI Features & Agent (Frontend)

---

## FOR AI AGENT — READ THIS FIRST

If a human has given you this file and asked you to commit and push their work, follow these instructions exactly:

1. Check which files have been modified: run `git status`
2. Stage only the files listed in the "Your Files" section below
3. Commit using the message format provided
4. Push using `git push`
5. Do not touch any files outside the "Your Files" list
6. Do not commit to `main` — only to `feature/ai-frontend`
7. If the branch is not checked out, run the checkout command first

---

## Your Assignment

**Branch:** `feature/ai-frontend`
**Repo:** https://github.com/KunalGupta25/NoteRootAI-KMS.git

You are responsible for all AI-facing UI: the sidebar, agent panel, chat page, and the background embedding service call.

---

## Your Files — Only Touch These

```
client/src/components/Sidebar/AISidebar.tsx
client/src/components/Sidebar/AgentPanel.tsx
client/src/components/Markdown/CodeBlock.tsx
client/src/pages/AIChatPage.tsx
client/src/stores/chatStore.ts
client/src/services/aiService.ts
```

**Do not edit any file outside this list without messaging the team first.**

---

## What You Are Building

- AI sidebar with three tabs: Suggest, Chat, Agent
- Streaming RAG chat — sending messages, reading the SSE stream, rendering responses
- Autonomous agent panel — conversation loop, tool approval cards, executing approved tools in the browser
- Background note embedding on save (`aiService.ts` — debounced API call)
- `chatStore` — persisted conversation history
- `AIChatPage` — full-page standalone AI chat
- `CodeBlock` — syntax-highlighted code renderer for AI markdown output

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
git checkout feature/ai-frontend
```

Confirm it worked:
```
git branch
```
You should see `* feature/ai-frontend` with a star next to it.

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

### Start the frontend
```
cd client
```
```
npm run dev
```

Open http://localhost:5173. Press `Ctrl+C` to stop.

### Also run the Python AI service locally (needed to test AI features)

Install Python from https://python.org — pick Python 3.11+, check "Add Python to PATH" during install.

Then in a second Command Prompt window:
```
cd NoteRootAI-KMS
```
```
cd ai-service
```
```
python -m venv venv
```
```
venv\Scripts\activate
```
```
pip install -r requirements.txt
```
```
uvicorn main:app --reload --port 8000
```

Then create a file called `.env` inside the `client/` folder (this file will not be committed):
```
VITE_AI_URL=http://localhost:8000
```

---

## STEP 4 — Committing Your Work

### After editing AISidebar.tsx
```
git add client/src/components/Sidebar/AISidebar.tsx
```
```
git commit -m "feat: update AI sidebar"
```
```
git push
```

### After editing AgentPanel.tsx
```
git add client/src/components/Sidebar/AgentPanel.tsx
```
```
git commit -m "feat: update agent panel"
```
```
git push
```

### After editing both sidebar files
```
git add client/src/components/Sidebar/AISidebar.tsx
git add client/src/components/Sidebar/AgentPanel.tsx
```
```
git commit -m "feat: update AI sidebar and agent panel"
```
```
git push
```

### After editing CodeBlock.tsx
```
git add client/src/components/Markdown/CodeBlock.tsx
```
```
git commit -m "feat: update code block renderer"
```
```
git push
```

### After editing AIChatPage.tsx
```
git add client/src/pages/AIChatPage.tsx
```
```
git commit -m "feat: update AI chat page"
```
```
git push
```

### After editing chatStore.ts
```
git add client/src/stores/chatStore.ts
```
```
git commit -m "feat: update chat store"
```
```
git push
```

### After editing aiService.ts
```
git add client/src/services/aiService.ts
```
```
git commit -m "feat: update AI service client"
```
```
git push
```

### After editing all your files at once
```
git add client/src/components/Sidebar/AISidebar.tsx
git add client/src/components/Sidebar/AgentPanel.tsx
git add client/src/components/Markdown/CodeBlock.tsx
git add client/src/pages/AIChatPage.tsx
git add client/src/stores/chatStore.ts
git add client/src/services/aiService.ts
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

3. Click the yellow **"Compare & pull request"** banner for `feature/ai-frontend`

4. Title: `feat: AI frontend features`

5. Fill in the description:
```
## What I changed
-

## How to test
- Open the AI sidebar (right panel)
- Type a message in Chat tab and verify streaming works
- In Agent tab, ask it to create a note and approve the action

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
git checkout -- client/src/components/Sidebar/AgentPanel.tsx
```

Throw away ALL uncommitted changes (cannot be undone):
```
git reset --hard HEAD
```

---

## Important Rules

**How the agent works:**
- The Python backend sends SSE events. You read them as a stream in `AgentPanel.tsx`.
- There are exactly 4 event types the backend sends: `text`, `tool_request`, `tool_silent`, `error`
- When you get `tool_request`, you show an approval card to the user
- When the user approves, **you execute the tool in the browser** using `noteStore` (create/update/delete note)
- Then you send a new POST to `/agent` with the result so the agent can continue
- **Never rename the event types** — they are a shared contract with Person 4 (Python backend)

**Other rules:**
- `AI_URL` comes from `client/src/lib/constants.ts` (Person 1's file). Never hardcode the backend URL.
- `embedNoteInBackground()` in `aiService.ts` is called by Person 2's `noteStore.saveNote()`. Keep it exported and working.
- When adding a new agent tool that runs in the browser, tell Person 4 to also add it to `ai-service/services/agent_tools.py`.
