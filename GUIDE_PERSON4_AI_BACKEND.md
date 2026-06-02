# NoteRootAI — Person 4 Guide
# AI Service Backend (Python)

---

## FOR AI AGENT — READ THIS FIRST

If a human has given you this file and asked you to commit and push their work, follow these instructions exactly:

1. Check which files have been modified: run `git status`
2. Stage only the files listed in the "Your Files" section below
3. Commit using the message format provided
4. Push using `git push`
5. Do not touch any files outside the "Your Files" list
6. Do not commit to `main` — only to `feature/ai-backend`
7. If the branch is not checked out, run the checkout command first

---

## Your Assignment

**Branch:** `feature/ai-backend`
**Repo:** https://github.com/KunalGupta25/NoteRootAI-KMS.git

You are responsible for the entire Python AI microservice — providers, embeddings, RAG, and the agent loop.

---

## Your Files — Only Touch These

```
ai-service/providers/base.py
ai-service/providers/factory.py
ai-service/providers/openai_provider.py
ai-service/providers/anthropic_provider.py
ai-service/providers/openai_compatible_provider.py
ai-service/providers/local_embedding.py
ai-service/services/embedder.py
ai-service/services/retriever.py
ai-service/services/rag.py
ai-service/services/agent.py
ai-service/services/agent_tools.py
ai-service/services/suggest.py
ai-service/services/vector_store.py
```

The following files are already in the repo (common scaffold) but you can also edit them if needed:
```
ai-service/main.py
ai-service/models.py
ai-service/config.py
ai-service/requirements.txt
ai-service/Dockerfile
ai-service/railway.toml
```

**Do not edit any client/ files without messaging the team first.**

---

## What You Are Building

- All LLM provider classes: OpenAI, Anthropic, Gemini (OpenAI-compatible), Mistral, Groq, custom
- Provider factory: routes requests to the correct provider class
- HTML-to-text conversion, text chunking, and embedding pipeline
- ChromaDB vector store wrapper (per-provider collections)
- Semantic search across embedded notes
- RAG chat: inject relevant note chunks as LLM context, stream the response
- Agent tool-calling loop: decide what tool to call, execute server-side read tools silently
- Tool definitions in OpenAI function-calling format
- Related note suggestions

---

## STEP 1 — One-Time Setup (Do this once, on your first day)

### Install Git
Download from https://git-scm.com/downloads — install with all defaults.

Open Command Prompt and verify:
```
git --version
```

### Install Python
Download from https://python.org — pick Python 3.11 or newer.
During install, **check the box "Add Python to PATH"**.

Verify:
```
python --version
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

### Set up the Python virtual environment
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

### Switch to your branch
```
cd ..
```
```
git checkout feature/ai-backend
```

Confirm it worked:
```
git branch
```
You should see `* feature/ai-backend` with a star next to it.

---

## STEP 2 — Create Your Local .env File

Create a file called `.env` inside the `ai-service/` folder.
This file will NOT be committed (it is in .gitignore).

Put this content in the file:
```
DEFAULT_PROVIDER=openai
DEFAULT_CHAT_MODEL_OPENAI=gpt-4o
DEFAULT_CHAT_MODEL_GEMINI=gemini-2.0-flash
DEFAULT_CHAT_MODEL_MISTRAL=mistral-large-latest
DEFAULT_CHAT_MODEL_GROQ=llama-3.3-70b-versatile
```

---

## STEP 3 — Every Morning Before You Start Coding

```
git fetch origin
```
```
git merge origin/main
```

---

## STEP 4 — Run the Server Locally

Every time you want to test your changes:
```
cd ai-service
```
```
venv\Scripts\activate
```
```
uvicorn main:app --reload --port 8000
```

Go to http://localhost:8000/docs in your browser — FastAPI shows all routes with an interactive tester.

Press `Ctrl+C` to stop.

---

## STEP 5 — Committing Your Work

### After editing base.py
```
git add ai-service/providers/base.py
```
```
git commit -m "refactor: update base provider"
```
```
git push
```

### After editing factory.py
```
git add ai-service/providers/factory.py
```
```
git commit -m "feat: update provider factory"
```
```
git push
```

### After editing openai_provider.py
```
git add ai-service/providers/openai_provider.py
```
```
git commit -m "feat: update OpenAI provider"
```
```
git push
```

### After editing anthropic_provider.py
```
git add ai-service/providers/anthropic_provider.py
```
```
git commit -m "feat: update Anthropic provider"
```
```
git push
```

### After editing openai_compatible_provider.py
```
git add ai-service/providers/openai_compatible_provider.py
```
```
git commit -m "feat: update OpenAI-compatible provider"
```
```
git push
```

### After editing local_embedding.py
```
git add ai-service/providers/local_embedding.py
```
```
git commit -m "feat: update local embedding provider"
```
```
git push
```

### After editing embedder.py
```
git add ai-service/services/embedder.py
```
```
git commit -m "feat: update embedding pipeline"
```
```
git push
```

### After editing vector_store.py
```
git add ai-service/services/vector_store.py
```
```
git commit -m "feat: update vector store"
```
```
git push
```

### After editing retriever.py
```
git add ai-service/services/retriever.py
```
```
git commit -m "feat: update semantic search retriever"
```
```
git push
```

### After editing rag.py
```
git add ai-service/services/rag.py
```
```
git commit -m "feat: update RAG chat service"
```
```
git push
```

### After editing agent.py
```
git add ai-service/services/agent.py
```
```
git commit -m "feat: update agent service"
```
```
git push
```

### After editing agent_tools.py
```
git add ai-service/services/agent_tools.py
```
```
git commit -m "feat: update agent tool definitions"
```
```
git push
```

### After editing both agent files
```
git add ai-service/services/agent.py
git add ai-service/services/agent_tools.py
```
```
git commit -m "feat: update agent loop and tools"
```
```
git push
```

### After editing suggest.py
```
git add ai-service/services/suggest.py
```
```
git commit -m "feat: update suggestions service"
```
```
git push
```

### After editing main.py or models.py
```
git add ai-service/main.py
git add ai-service/models.py
```
```
git commit -m "feat: update API routes and models"
```
```
git push
```

### After adding a new Python package
```
pip install package-name
```
```
pip freeze > ai-service/requirements.txt
```
```
git add ai-service/requirements.txt
```
```
git commit -m "chore: add package-name dependency"
```
```
git push
```

### After editing all your files at once
```
git add ai-service/providers/base.py
git add ai-service/providers/factory.py
git add ai-service/providers/openai_provider.py
git add ai-service/providers/anthropic_provider.py
git add ai-service/providers/openai_compatible_provider.py
git add ai-service/providers/local_embedding.py
git add ai-service/services/embedder.py
git add ai-service/services/retriever.py
git add ai-service/services/rag.py
git add ai-service/services/agent.py
git add ai-service/services/agent_tools.py
git add ai-service/services/suggest.py
git add ai-service/services/vector_store.py
```
```
git commit -m "feat: describe today's changes"
```
```
git push
```

---

## STEP 6 — Opening a Pull Request (When Your Work Is Ready)

1. Push all your latest work:
```
git push
```

2. Go to https://github.com/KunalGupta25/NoteRootAI-KMS

3. Click the yellow **"Compare & pull request"** banner for `feature/ai-backend`

4. Title: `feat: AI service backend`

5. Fill in the description:
```
## What I changed
-

## How to test
- Run: uvicorn main:app --reload --port 8000
- Go to http://localhost:8000/docs
- Test /health endpoint
- Test /embed with a sample note payload
- Test /search with a sample query

## Screenshots
(paste API docs screenshots here)
```

6. Click **Reviewers** → select **KunalGupta25**

7. Click **Create pull request**

---

## STEP 7 — After Someone Else's Code Gets Merged

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
git checkout -- ai-service/services/agent.py
```

Throw away ALL uncommitted changes (cannot be undone):
```
git reset --hard HEAD
```

---

## Important Rules

- **Never log API keys.** Every request has an `api_key` field. Use it, never print it, never store it.
- **ChromaDB collections per provider:** Each provider uses `notes_{provider}_{embedding_dim}`. Changing the embedding dimension orphans existing data — warn the team before doing this.
- **SSE event types are a contract with Person 3.** The frontend parses exactly: `text`, `tool_request`, `tool_silent`, `error`, `[DONE]`. Never rename these without telling Person 3.
- **`SERVER_SIDE_TOOLS` in agent.py** — only add tools here if they are 100% read-only. Write tools must always go through the frontend approval flow.
- When adding a new agent tool: add the definition in `agent_tools.py`, then tell Person 3 to add the browser-side execution in `AgentPanel.tsx`.
