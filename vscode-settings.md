# Vs-Code Settings
This is a vs code essential settings file that will improve coding efforts.

## Steps
#### Step 1: Create a .vscode folder at the root of the project.
#### Step 2: Create a settings.json file at the .vscode folder.
#### Step 3: Copy and paste the code down bellow.

```jsx
{
  "typescript.tsdk": "node_modules/typescript/lib",
  "files.eol": "\n",
  "editor.codeActionsOnSave": {
    "source.addMissingImports": "explicit",
    "source.fixAll": "explicit",
    "source.organizeImports": "explicit",
    "source.sortMembers": "explicit"
  },
  "editor.formatOnSave": true,
  "editor.tabSize": 2,
  "cSpell.words": ["dtos", "signin", "typeorm", "nextjs", "nextui"],
  "javascript.preferences.quoteStyle": "single",
  "typescript.preferences.quoteStyle": "single",
  "prettier.singleQuote": true,
  "prettier.printWidth": 500,
  "editor.insertSpaces": true,
  "prettier.useTabs": false
}
```
