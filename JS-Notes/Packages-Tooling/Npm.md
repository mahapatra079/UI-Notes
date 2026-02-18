# Node Package Managers

## npm vs npx

### npm (Node Package Manager)

Used to **install packages**

**Use Cases:**
- Install packages
- Manage node_modules (`npm i`)
- Maintain package.json
- Run scripts (`npm run build`, `npm start`)

**Example:**

```bash
npm install react
```

**What happens:**
- ✅ Installs React
- ✅ Saves it in node_modules
- ✅ Updates package.json

---

### npx (Node Package eXecute)

Used to **execute packages without installing globally**

**Use Cases:**
- Run CLI tools directly
- Avoid global installs
- Run one-time commands

> **Note:** CLI (Command-Line Interface) is a text-based interface for interacting with software. The CLI is the central entry point for frontend development, used to transpile and bundle code.

**Example:**

```bash
npx create-react-app myApp
```

**What happens:**
- ✅ Downloads create-react-app
- ✅ Executes it
- ✅ Deletes it after use (if not cached)

---

## When to Use What?

| Tool | Use For |
|------|--------|
| **npm** | Dependencies (react, vue, etc.) |
| **npx** | CLI tools (create-react-app, vite, eslint, prettier) |

---

## Yarn vs pnpm

### Yarn

Alternative to npm with improved performance

**Features:**
- Uses `yarn.lock` for dependency locking
- Parallel installation
- Deterministic dependency tree
- Faster than npm

**Example:**

```bash
yarn add react
yarn install
yarn build
```

---

### pnpm

Performant npm with efficient disk space usage

**Features:**
- Uses hard links and symlinks
- Saves disk space (shared dependencies)
- Faster installation
- Strict dependency resolution

**Example:**

```bash
pnpm add react
pnpm install
pnpm build
```

---

## Comparison Table

| Feature | npm | yarn | pnpm |
|---------|-----|------|------|
| **Speed** | Moderate | Fast | Fastest |
| **Disk Space** | High | High | Low |
| **Lock File** | package-lock.json | yarn.lock | pnpm-lock.yaml |
| **Workspaces** | ✅ | ✅ | ✅ |
| **Offline Mode** | ❌ | ✅ | ✅ |

---

## Quick Commands

| Action | npm | yarn | pnpm |
|--------|-----|------|------|
| Install | `npm install` | `yarn` | `pnpm install` |
| Add package | `npm install <pkg>` | `yarn add <pkg>` | `pnpm add <pkg>` |
| Remove package | `npm uninstall <pkg>` | `yarn remove <pkg>` | `pnpm remove <pkg>` |
| Run script | `npm run <script>` | `yarn <script>` | `pnpm <script>` |