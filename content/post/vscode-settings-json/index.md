---
title: VScode config file
summary: Settings.json for my VScode config
date: 2025-02-07
authors:
  - admin
tags:
  - VScode
  - Code
  - Programming
commentable: true
# image:
#   caption: 'Image credit: [**ChatGPT**](https://chatgpt.com)'
---

### These configs help me easily navigate VScode.

```json
{
  "remote.SSH.remotePlatform": {
    "*.unity.rc.umass.edu": "linux",
    "Horizon": "linux",
    "rps2.cscdr.umassd.edu": "linux",
    "RPS2": "linux",
    "unity": "linux"
  },
  "files.autoSave": "afterDelay",
  "search.showLineNumbers": true,
  "notebook.lineNumbers": "on",
  "security.allowedUNCHosts": [
    "wsl$"
  ],
  "editor.cursorSmoothCaretAnimation": "on",
  "editor.cursorSurroundingLines": 2,
  "editor.find.seedSearchStringFromSelection": "selection",
  "editor.fontFamily": "Fira Mono, monospace, MesloLGS NF, Noto Color Emoji",
  "editor.fontLigatures": true,
  "editor.formatOnSave": true,
  "editor.guides.bracketPairs": true,
  "editor.inlineSuggest.enabled": true,
  "editor.insertSpaces": false,
  "editor.lightbulb.enabled": "onCode",
  "editor.minimap.showMarkSectionHeaders": false,
  "editor.semanticHighlighting.enabled": true,
  "editor.smoothScrolling": true,
  "editor.suggestSelection": "first",
  "editor.tabSize": 2,
  "editor.unicodeHighlight.allowedCharacters": {
    "×": true
  },
  "explorer.compactFolders": false,
  "explorer.copyRelativePathSeparator": "/",
  "explorer.fileNesting.enabled": true,
  "explorer.fileNesting.patterns": {
    "*.ex": "${capture}.eex, ${capture}.html.heex",
    "*.go": "${capture}_test.go",
    "*.js": "${capture}.d.ts, ${capture}.d.ts.map, ${capture}.js.map, ${capture}.min.js, ${capture}.test.d.ts.map",
    "*.mjs": "${capture}.d.mts, ${capture}.d.mts.map, ${capture}.mjs.map",
    "*.mts": "${capture}.d.mts, ${capture}.d.mts.map, ${capture}.mjs, ${capture}.mjs.map",
    "*.svelte": "${capture}.css, ${capture}.stories.js, ${capture}.stories.ts, ${capture}.svelte.d.ts, ${capture}.svelte.d.ts.map, ${capture}.test.ts",
    "*.ts": "${capture}.test.ts, ${capture}.test.ts.map, ${capture}.js",
    ".env": ".env.*",
    ".env.*": ".env.${capture}.local",
    "compose.yaml": "compose.override.yaml, *.compose.yaml, *.compose.override.yaml",
    "minepkg.toml": ".minepkg-lock.toml",
    "mix.exs": "mix.lock",
    "package.json": "bun.lockb, package-lock.json, pnpm-lock.yaml, yarn.lock",
    "tailwind.config.cjs": "tailwind.*.cjs, tailwind.*.json",
    "tsconfig.json": "tsconfig.*.json, tsconfig.tsbuildinfo",
    "tsconfig.tsbuildinfo": "tsconfig.*.tsbuildinfo"
  },
  "explorer.incrementalNaming": "smart",
  "explorer.openEditors.sortOrder": "alphabetical",
  "security.workspace.trust.untrustedFiles": "open",
  "terminal.integrated.commandsToSkipShell": [
    "matlab.interrupt",
    "language-julia.interrupt"
  ],
  "MATLAB.showFeatureNotAvailableError": false,
  "julia.symbolCacheDownload": true,
  "julia.enableTelemetry": false,
  "editor.accessibilitySupport": "off",
  "terminal.integrated.tabs.defaultColor": "terminal.ansiGreen",
  "workbench.colorCustomizations": {

     "tab.activeBorderTop": "#00FF00", // bright green top border
    "tab.activeBorderLeft": "#00FF00", // bright green left border
    "tab.activeBorderRight": "#00FF00", // bright green right border
    "tab.activeBorderBottom": "#00FF00", // bright green bottom border
    // "tab.activeBorder": "#00FF00",     // bright green border all around
    "tab.activeBorder": "#00FF00", // green border all around (VS Code Insiders / newer versions)
    "editorGroup.border": "#00FF00", // optional, green border around the editor group
    
    "terminal.foreground": "#00FD61",
    "terminal.background": "#383737",
    "terminal.ansiBlack": "#1D2021",
    "terminal.ansiBrightBlack": "#665C54",
    "terminal.ansiBrightBlue": "#0D6678",
    "terminal.ansiBrightCyan": "#8BA59B",
    "terminal.ansiBrightGreen": "#237e02",
    "terminal.ansiBrightMagenta": "#8F4673",
    "terminal.ansiBrightRed": "#FB543F",
    "terminal.ansiBrightWhite": "#FDF4C1",
    "terminal.ansiBrightYellow": "#FAC03B",
    "terminal.ansiBlue": "#00a1f9",
    "terminal.ansiCyan": "#8BA59B",
    "terminal.ansiGreen": "#95C085",
    "terminal.ansiMagenta": "#8F4673",
    "terminal.ansiRed": "#FB543F",
    "terminal.ansiWhite": "#A89984",
    "terminal.ansiYellow": "#FAC03B",
    "focusBorder": "#00FD61",
    "activityBar.background": "#083c8a",
    "statusBar.background": "#083c8a",
    "titleBar.activeBackground": "#083c8a"
  }
}
```