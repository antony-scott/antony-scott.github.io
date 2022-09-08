---
layout: post
title:  "Making VSCode nicer"
date:   2022-09-08 12:53
categories: VSCode
---

# VSCode - making it a nicer place to be

## Settings
**(accessed via `Ctrl` + `,`)**
- Increase the indentation - the default of 8 pixels is way too small (for me)
  
  Workbench > Tree: Index = `20`

- Change title bar style - when using dark mode, to make it easier to see the title bar

  Window: Title Bar Style = `native`

- Change title bar test - to make multiple instance easier to switch between

  Window: Title = `${rootName}${separator}${appName}`

- Remove current line highlight - personal preference for me

  Editor: Render Line Highlight = `none`

## Useful Extensions
- [.NET Core Test Explorer](https://marketplace.visualstudio.com/items?itemName=formulahendry.dotnet-test-explorer)
- [Auto-Using for C#](https://marketplace.visualstudio.com/items?itemName=Fudge.auto-using)
- [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
- [C# Interpolated String Converter](https://marketplace.visualstudio.com/items?itemName=corylulu.csharp-interpolated-string-converter)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Import Cost](https://marketplace.visualstudio.com/items?itemName=wix.vscode-import-cost)
- [Inline YAML Syntax Highlighting](https://marketplace.visualstudio.com/items?itemName=monotykamary.inline-yaml)
- [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=monotykamary.inline-yaml)
- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
- [PDF Preview](https://marketplace.visualstudio.com/items?itemName=analytic-signal.preview-pdf)
- [Python Test Explorer for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=LittleFoxTeam.vscode-python-test-adapter)
- [string-highlight](https://marketplace.visualstudio.com/items?itemName=Jenkey2011.string-highlight)
- [Test Explorer UI](https://marketplace.visualstudio.com/items?itemName=hbenl.vscode-test-explorer)

## "Bad" Extensions
- [Error Lens](https://marketplace.visualstudio.com/items?itemName=usernamehw.errorlens) - although it looks useful I found it would show me code error for perfectly fine code (example - using NUnit.Framework would show an error, when it was fine)