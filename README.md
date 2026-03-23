# ansible-vault-vscodium — Build, Install & Cleanup

### Requirements

- [Node.js](https://nodejs.org/) (v18+)
- [Git](https://git-scm.com/)
- [VSCodium](https://vscodium.com/)

---

### 1. Clone the Repository

```bash
git clone https://github.com/ipierre1/ansible-vault-vscode
cd ansible-vault-vscode
```

---

### 2. Install Dependencies

```bash
npm install
```

---

### 3. Compile TypeScript

```bash
npm run compile
```

> If the command is not found, try the alternative:
> ```bash
> npx tsc -p tsconfig.json
> ```

---

### 4. Build the .vsix Package

```bash
npm install -g @vscode/vsce
vsce package
```

A file named `ansible-vault-vscode-X.X.X.vsix` will appear in the project folder.

---

### 5. Install in VSCodium

**Via command line:**
```bash
codium --install-extension ansible-vault-vscode-*.vsix
```

**Via GUI:**
1. Open VSCodium
2. Go to Extensions (`Ctrl+Shift+X`)
3. Click `...` → **Install from VSIX...**
4. Select the built `.vsix` file

After installation, reload the window: `Ctrl+Shift+P` → **Reload Window**

---

### 6. Cleanup After Build

Remove installed npm packages and generated files:

```bash
# Remove node_modules
rm -rf node_modules

# Remove compiled JavaScript (out or extension/out folder)
rm -rf out
rm -rf extension/out

# Remove the built .vsix (optional, if no longer needed)
rm -f *.vsix
```

Remove globally installed `vsce` (if it was installed only for this purpose):

```bash
npm uninstall -g @vscode/vsce
```

Full cleanup — remove the entire cloned repository:

```bash
cd ..
rm -rf ansible-vault-vscode
```
