---
layout: post
title: Visual Studio Code
subtitle: How to use Visual Studio Code
date: 2018-02-01 19:16:01 -0800
categories: [DevTools]
tags: [DevTools, VSCode, ECMAScript, Python, AspDotNetCore]
---

# Visual Studio Code

## Must-have plugins

[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

[Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)

[prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) see more on <https://prettier.io/>

[vscode-icons](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons)

## Settings

`Ctrl + ,` => launch settings

There are two settings: workplace and user setting

### setting.json

## Tasks

[Integrate with External Tools via Tasks](https://code.visualstudio.com/docs/editor/tasks#vscode)

## Editor

> [EditorConfig](https://editorconfig.org/) helps maintain consistent coding styles for multiple developers working on the same project across various editors and IDEs.

Settings can be accessed via menu File->Preferences->Settings->User Settings / Workspace Settings->Text Editor.

[keyboard shortcuts in windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) provide the list of the shortcuts.

[tips-and-tricks](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)

### Layout and View related

- Ctrl + b => Toggle Sidebar
- Ctrl + K, z => Zen Mode, Esc to exit
- Ctrl + Shift + v => switch between files opened

[markdown in VSCode](https://code.visualstudio.com/docs/languages/markdown)

For markdowns, you can view the preview side-by-side (Ctrl+K, v) with the file you are editing and see changes reflected in real-time as you edit.

### Code writing

#### Emmet for web development

[Emmet](https://emmet.io/) is the successor of HTML zen coding which saves tedious type for coding html, css.

[emmet](https://code.visualstudio.com/docs/editor/emmet)

[emmet-2.0](https://code.visualstudio.com/blogs/2017/08/07/emmet-2.0)

[emmet cheat sheet](https://docs.emmet.io/cheat-sheet/)

### Code formating

- Shift + Alt + F => formats the whole document.
- Ctrl + K, Ctrl + F => formats the currently selected source code.

#### editor.formatOnSave

In settings, editor.formatOnSave can be turned on.

#### Beautify

[Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify) javascript, JSON, CSS, Sass, and HTML in Visual Studio Code.

#### prettier

[Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) is another tool to format your JavaScript / TypeScript / CSS.

In case you have both installed, you need to specify certain file types.

```json
{
  "beautify.language": {
    "html": ["html", "htm"],
    "css": [],
    "js": []
  }
}
```

### Debug the app locally

[Debugging in VS Code](https://code.visualstudio.com/docs/editor/debugging)

- Ctrl + Shift + b => Build
- Ctrl + Shift + d => Debug
- F1 or Ctrl + Shift + p => Command Palette, prompts the available commands
- Ctrl + ` => launch Terminal

## Extensions

Don't install too many extensions. Only install the extensions you need.

Some must-have extensions for a web-developer.

[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

[TSLint](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin)

[prettier](https://github.com/prettier/prettier)

## Common issues

Run one Visual Studio Code at one time. If you have multiple VS Code instances open at the same time, sometimes you will see wierd issues.

## Resources

[Official](https://code.visualstudio.com/)

[Source code](https://github.com/Microsoft/vscode)
