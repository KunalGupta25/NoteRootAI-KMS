# NoteRootAI — Person 5 Guide
# Plugin System & Graph View

---

## FOR AI AGENT — READ THIS FIRST

If a human has given you this file and asked you to commit and push their work, follow these instructions exactly:

1. Check which files have been modified: run `git status`
2. Stage only the files listed in the "Your Files" section below
3. Commit using the message format provided
4. Push using `git push`
5. Do not touch any files outside the "Your Files" list
6. Do not commit to `main` — only to `feature/plugins-graph`
7. If the branch is not checked out, run the checkout command first

---

## Your Assignment

**Branch:** `feature/plugins-graph`
**Repo:** https://github.com/KunalGupta25/NoteRootAI-KMS.git

You are responsible for the plugin system, knowledge graph view, and command palette.

---

## Your Files — Only Touch These

```
client/src/plugins/runtime/PluginRuntime.ts
client/src/plugins/runtime/PluginContext.ts
client/src/plugins/runtime/ExtensionPoints.ts
client/src/plugins/runtime/ThemeEngine.ts
client/src/plugins/runtime/DescriptorRenderer.tsx
client/src/plugins/slots/NotePageActionsBar.tsx
client/src/plugins/slots/PluginBubbleButtons.tsx
client/src/plugins/slots/PluginOverlays.tsx
client/src/plugins/slots/PluginSettingsPanels.tsx
client/src/plugins/slots/PluginTabBar.tsx
client/src/plugins/builtin/markdownImporter.ts
client/src/plugins/builtin/noteDownloader.ts
client/src/plugins/builtin/tabManager.ts
client/src/plugins/builtin/zipImporter.ts
client/src/pages/GraphPage.tsx
client/src/pages/PluginsPage.tsx
client/src/stores/pluginStore.ts
client/src/components/CommandPalette/CommandPalette.tsx
```

**Do not edit any file outside this list without messaging the team first.**

---

## What You Are Building

- Plugin sandbox runtime (runs community plugin code safely)
- Plugin context API (what plugins are allowed to call)
- Extension point registry (slots plugins can hook into)
- Theme engine (CSS variable injection from plugins/themes)
- `DescriptorRenderer` — renders declarative plugin UI without touching React directly
- Plugin slot components (UI mount points across the app)
- Built-in plugins: markdown importer, ZIP importer, tab manager, note downloader
- `pluginStore`: install/uninstall/enable/disable, sync plugin URLs across devices
- Plugins page: browse and manage plugins
- Knowledge graph (Cytoscape.js): visualize note connections
- Command palette (Ctrl+K): fuzzy search across all notes

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
git checkout feature/plugins-graph
```

Confirm it worked:
```
git branch
```
You should see `* feature/plugins-graph` with a star next to it.

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

### After editing PluginRuntime.ts
```
git add client/src/plugins/runtime/PluginRuntime.ts
```
```
git commit -m "feat: update plugin runtime"
```
```
git push
```

### After editing PluginContext.ts
```
git add client/src/plugins/runtime/PluginContext.ts
```
```
git commit -m "feat: update plugin context API"
```
```
git push
```

### After editing ExtensionPoints.ts
```
git add client/src/plugins/runtime/ExtensionPoints.ts
```
```
git commit -m "feat: update extension points"
```
```
git push
```

### After editing ThemeEngine.ts
```
git add client/src/plugins/runtime/ThemeEngine.ts
```
```
git commit -m "feat: update theme engine"
```
```
git push
```

### After editing DescriptorRenderer.tsx
```
git add client/src/plugins/runtime/DescriptorRenderer.tsx
```
```
git commit -m "feat: update descriptor renderer"
```
```
git push
```

### After editing all runtime files
```
git add client/src/plugins/runtime/PluginRuntime.ts
git add client/src/plugins/runtime/PluginContext.ts
git add client/src/plugins/runtime/ExtensionPoints.ts
git add client/src/plugins/runtime/ThemeEngine.ts
git add client/src/plugins/runtime/DescriptorRenderer.tsx
```
```
git commit -m "feat: update plugin runtime system"
```
```
git push
```

### After editing PluginOverlays.tsx
```
git add client/src/plugins/slots/PluginOverlays.tsx
```
```
git commit -m "feat: update plugin overlays slot"
```
```
git push
```

### After editing PluginBubbleButtons.tsx
```
git add client/src/plugins/slots/PluginBubbleButtons.tsx
```
```
git commit -m "feat: update plugin bubble buttons slot"
```
```
git push
```

### After editing PluginSettingsPanels.tsx
```
git add client/src/plugins/slots/PluginSettingsPanels.tsx
```
```
git commit -m "feat: update plugin settings panels slot"
```
```
git push
```

### After editing PluginTabBar.tsx
```
git add client/src/plugins/slots/PluginTabBar.tsx
```
```
git commit -m "feat: update plugin tab bar slot"
```
```
git push
```

### After editing NotePageActionsBar.tsx
```
git add client/src/plugins/slots/NotePageActionsBar.tsx
```
```
git commit -m "feat: update note page actions bar"
```
```
git push
```

### After editing all slot files
```
git add client/src/plugins/slots/NotePageActionsBar.tsx
git add client/src/plugins/slots/PluginBubbleButtons.tsx
git add client/src/plugins/slots/PluginOverlays.tsx
git add client/src/plugins/slots/PluginSettingsPanels.tsx
git add client/src/plugins/slots/PluginTabBar.tsx
```
```
git commit -m "feat: update plugin slots"
```
```
git push
```

### After editing markdownImporter.ts
```
git add client/src/plugins/builtin/markdownImporter.ts
```
```
git commit -m "feat: update markdown importer plugin"
```
```
git push
```

### After editing zipImporter.ts
```
git add client/src/plugins/builtin/zipImporter.ts
```
```
git commit -m "feat: update ZIP importer plugin"
```
```
git push
```

### After editing tabManager.ts
```
git add client/src/plugins/builtin/tabManager.ts
```
```
git commit -m "feat: update tab manager plugin"
```
```
git push
```

### After editing noteDownloader.ts
```
git add client/src/plugins/builtin/noteDownloader.ts
```
```
git commit -m "feat: update note downloader plugin"
```
```
git push
```

### After editing all builtin plugins
```
git add client/src/plugins/builtin/markdownImporter.ts
git add client/src/plugins/builtin/noteDownloader.ts
git add client/src/plugins/builtin/tabManager.ts
git add client/src/plugins/builtin/zipImporter.ts
```
```
git commit -m "feat: update built-in plugins"
```
```
git push
```

### After editing GraphPage.tsx
```
git add client/src/pages/GraphPage.tsx
```
```
git commit -m "feat: update graph view"
```
```
git push
```

### After editing PluginsPage.tsx
```
git add client/src/pages/PluginsPage.tsx
```
```
git commit -m "feat: update plugins page"
```
```
git push
```

### After editing pluginStore.ts
```
git add client/src/stores/pluginStore.ts
```
```
git commit -m "feat: update plugin store"
```
```
git push
```

### After editing CommandPalette.tsx
```
git add client/src/components/CommandPalette/CommandPalette.tsx
```
```
git commit -m "feat: update command palette"
```
```
git push
```

### After editing all your files at once
```
git add client/src/plugins/runtime/PluginRuntime.ts
git add client/src/plugins/runtime/PluginContext.ts
git add client/src/plugins/runtime/ExtensionPoints.ts
git add client/src/plugins/runtime/ThemeEngine.ts
git add client/src/plugins/runtime/DescriptorRenderer.tsx
git add client/src/plugins/slots/NotePageActionsBar.tsx
git add client/src/plugins/slots/PluginBubbleButtons.tsx
git add client/src/plugins/slots/PluginOverlays.tsx
git add client/src/plugins/slots/PluginSettingsPanels.tsx
git add client/src/plugins/slots/PluginTabBar.tsx
git add client/src/plugins/builtin/markdownImporter.ts
git add client/src/plugins/builtin/noteDownloader.ts
git add client/src/plugins/builtin/tabManager.ts
git add client/src/plugins/builtin/zipImporter.ts
git add client/src/pages/GraphPage.tsx
git add client/src/pages/PluginsPage.tsx
git add client/src/stores/pluginStore.ts
git add client/src/components/CommandPalette/CommandPalette.tsx
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

3. Click the yellow **"Compare & pull request"** banner for `feature/plugins-graph`

4. Title: `feat: plugin system and graph view`

5. Fill in the description:
```
## What I changed
-

## How to test
- Press Ctrl+K and verify command palette opens and searches notes
- Go to /graph and verify note links are drawn correctly
- Go to /plugins and install a test plugin from a URL

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
git checkout -- client/src/pages/GraphPage.tsx
```

Throw away ALL uncommitted changes (cannot be undone):
```
git reset --hard HEAD
```

---

## Important Rules

- Plugin code runs in a sandboxed `new Function()` — plugins get no access to `window`, `document`, or `fetch` directly. They can only use what you expose through `PluginContext`.
- When adding a new `ExtensionPoint` slot, also create the slot component in `plugins/slots/` AND mount it in `AppShell.tsx` or `NoteEditorPage.tsx` — message Person 2 first before touching those files.
- Theme CSS variable naming must follow: `--plugin-{pluginId}-{tokenName}`. Never break this convention.
- `GraphPage.tsx` reads notes directly from `noteStore` (Person 2's store). Do not create a separate graph store.
- `pluginStore` syncs community plugin URLs via `settingsStore` (Person 1's store). Don't change how this sync works without telling Person 1.
