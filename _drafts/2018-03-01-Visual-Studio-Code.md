---
layout: post
title: Visual Studio Code
subtitle: How to use Visual Studio Code
date: 2018-02-01 19:16:01 -0800
categories: [DevTools]
tags: [DevTools, VSCode, ECMAScript, Python, AspDotNetCore]
---

# Visual Studio Code

Visual Studio Code is for code writing, code formating, code linting, code testing, code building, code publishing...

## Must-have plugins

[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

[Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)

[prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) see more on <https://prettier.io/>

[vscode-icons](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons)

## Code writing and editor

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

### Emmet for web development

[Emmet](https://emmet.io/) is the successor of HTML zen coding which saves tedious type for coding html, css.

[emmet](https://code.visualstudio.com/docs/editor/emmet)

[emmet-2.0](https://code.visualstudio.com/blogs/2017/08/07/emmet-2.0)

[emmet cheat sheet](https://docs.emmet.io/cheat-sheet/)

## Code formating

VS Code's built-in JavaScript formatter providers basic code formatting with reasonable defaults.

- Shift + Alt + F => formats the whole document.
- Ctrl + K, Ctrl + F => formats the currently selected source code.

In settings, editor.formatOnSave can be turned on.

### HTML formatting

The HTML formatter by default is based on [js-beautify](https://www.npmjs.com/package/js-beautify).

The Marketplace has several alternative formatters to choose from. If you want to use a different formatter, define "html.format.enable": false in your settings to turn off the built-in formatter.

### javascript formatting

The javascript.format.\* settings configure the built-in formatter. Or, if the built-in formatter is getting in the way, set "javascript.format.enable" to false to disable it.

### Beautify

[Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify) javascript, JSON, CSS, Sass, and HTML in Visual Studio Code.

### prettier

[prettier](https://github.com/prettier/prettier)

[Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) is another tool to format your JavaScript / TypeScript / CSS.

In case you have both installed, you need to specify certain file types in settings.json.

```json
{
  "beautify.language": {
    "html": ["html", "htm"],
    "css": [],
    "js": []
  }
}
```

In the above, beautify will not touch js files and prettier will take over the js formatting.

## Linting

[ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
[eslint](https://eslint.org/)

[TSLint](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-typescript-tslint-plugin)

## Debug the app locally

[Debugging in VS Code](https://code.visualstudio.com/docs/editor/debugging)

- Ctrl + Shift + b => Build
- Ctrl + Shift + d => Debug
- F1 or Ctrl + Shift + p => Command Palette, prompts the available commands
- Ctrl + ` => launch Terminal

## Extensions

Don't install too many extensions. Only install the extensions you need.

Some must-have extensions for a web-developer.

## Settings

`Ctrl + ,` => launch settings

There are two settings: workplace and user setting

### setting.json

## Tasks

[Integrate with External Tools via Tasks](https://code.visualstudio.com/docs/editor/tasks#vscode)

## Common issues

Run one Visual Studio Code at one time. If you have multiple VS Code instances open at the same time, sometimes you will see wierd issues.

## Resources

[Official](https://code.visualstudio.com/)

[Source code](https://github.com/Microsoft/vscode)
