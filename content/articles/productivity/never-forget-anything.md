---
date: 2020-05-22 18:00:00 +0000
title: "How to Never Forget Anything"
summary: "How I have attained note-taking perfection, and am finally at peace."
type: "post"
categories: ["Productivity"]
---

I have struggled for many years with how best to do and record things like the following:

- Notes about things I've learned or studied
- Planning projects or events
- Lists of stuff e.g. books to read
- Other random junk

There are lots of tools available to help you keep track of this sort of thing. Evernote, for example, does a great job of capturing *stuff* of every kind. Google Keep lets you add notes quickly and easily from anywhere. Notion allows you to build a personal wiki with all sorts of pages. OneNote seems to be able to just about anything. The list goes on.

But I've found with every one of these - and others - that nothing felt just right. Evernote is clunky, slow and does not produce pleasant-looking notes. Google Keep just doesn't work for long-form notes. Notion has high aspirations but was - at least to my monkey fingers - virtually unusable. OneNote just never felt right - my notes felt hidden and siloed. I even worked for a while writing notes by hand in notebooks, and while this is nice while writing, it's very hard to go back and find what you wrote in a physical book quickly.

What I needed was something that was lightweight, flexible, and easy to access. And, for someone with a compulsive streak such as me, configurable.

## Enter Markdown

Markdown is a widely-used markup language. It's readable, easy to type in and contains features like formatting, hyperlinks to web pages or other files, images, lists and - if you use the GitHub flavour - tables. It will even support LaTeX-brand mathematical typesetting in some versions.

Plain text has a big advantage over proprietary solutions. If you want to migrate your junk from Evernote to Google Keep, good luck. However if you want to use a different text editor to view and write your notes, no problem!

## Visual Studio Code

My choice for writing, viewing and managing notes is VS Code. There are excellent extensions for working with Markdown - specifically Yu Zhang's [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one), David Anson's [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) and Matt Bierner's necessary [Markdown Emoji](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-emoji), to name a few.

VS Code already has a Markdown Preview feature, which can sit beside a document you're working on and show you a live rendering, with synchronized scrolling and so on. Better yet, since almost every aspect of VS Code is configurable, you can get the preview pane looking just so: the right font, the right size, the right line spacing.

Since it's designed first as a text/code editor, its features for navigating through files for text blow traditional note-taking apps out of the water. You can traverse the headings and subheadings in a Markdown file using the `Go to symbol in editor` action, or quickly jump to a file by name. The usual ability to find/replace text across files using plain search terms or regular expressions is a given. If you like to use Vim or Emacs, there are emulator/keymap plugins available.

Its colour scheme customizations are also very powerful, which I find a big plus. You can even define custom CSS for the preview pane.

![Markdown notes in VS Code](/images/markdown-notes.png "Markdown notes in VS Code")
*I've found it very handy for studying*

## Source Control

This method of file-based notes lends itself to file syncing using e.g. Dropbox or OneDrive, or to version control using something like a private GitHub repository. At the moment I use Dropbox to synchronize Markdown notes between my different machines.

## Drawbacks

Yes, if you go this route, it isn't really possible to take notes on anything that doesn't run a desktop OS. Also, it doesn't play very nicely with diverse file types, although there are extensions available for viewing things like PDFs.

Ultimately, though, I've found that these don't bother me. On the rare occasion I want to note something down while nowhere near a computer, I can just add a quick note using Todoist, Keep, or paper, and transcribe/expand on it at some later point.

The ability to enter my thoughts quickly using a powerful text editor - and easily search through everything I have notes and ideas on - is worth any inconvenience. I used to get frustrated with my setup and change everything every few months, but so far it's been clear skies and smooth sailing on the HMS Markdown.

## My Setup

I use a folder in Dropbox that is also a VS Code workspace. VS Code allows you to define settings specific to a workspace, and while I tend to prefer reading and writing code in a dark theme, I much prefer a light theme for reading and writing normal text. The workspace contains these settings:

```json
"settings": {
  "workbench.colorTheme": "Solarized Light+",
  "files.exclude": {
    "**/*.xlsx": true,
    "**/*.docx": true
  },
  "editor.codeActionsOnSave": {
    "source.fixAll.markdownlint": true
  },
  "markdown.styles": [
    "./.workspace/markdown.css"
  ]
}
```

A benefit of including the workspace configuration in your method of synchronization (Dropbox, GitHub, etc.) is that it will look the same on all machines. This can be enhanced by using [Peacock](https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock) to give your notes workspace a distinctive colour.

You will note the inclusion of my custom `markdown.css` file, included in the workspace directory (which in this case is within the project root). I find the default Markdown preview a little hard to read, so I added the following extra padding:

```css
.vscode-body p {
  margin-top: 0.3em;
}

.vscode-body h1 {
  font-weight: bold;
}

.vscode-body h2 {
  margin-top: 1.1em;
  font-weight: bold;
}

.vscode-body h3 {
  margin-top: 1em;
  font-weight: bold;
}

.vscode-body h4 {
  margin-top: 0.8em;
  font-weight: bold;
}

.vscode-body blockquote {
  margin-top: 0.8em;
  margin-bottom: 0.8em;
}

.vscode-body table {
  margin-top: 1.2em;
  margin-bottom: 1.2em;
}
```

Meanwhile, in the User settings (remember to enable [Settings Sync](https://code.visualstudio.com/docs/editor/settings-sync)!) I include the following, among many others that are not relevant:

```json
"settings": {
  "markdown.preview.lineHeight": 1.45,
  "markdown.preview.fontFamily": "Roboto Slab",
  "markdown.preview.fontSize": 18,
  "[markdown]": {
    "editor.wordWrap": "on",
    "editor.rulers": []
  },
  "markdownlint.config": {
    "MD024": false,
    "MD026": false,
    "MD036": false
  },
  "workbench.colorCustomizations": {
    "[Solarized Light+]": {
      "editorGutter.background": "#fdf6e3"
    }
  },
  "[Solarized Light+]": {
      "textMateRules": [
        {
          "scope": "comment",
          "settings": {
            "fontStyle": ""
          }
        },
        {
          "scope": "punctuation.definition.comment",
          "settings": {
            "fontStyle": ""
          }
        },
      ]
    }
  },
}
```

I keep a "Fonts" folder in the same place, so that whenever I want to change to a new font, I can easily install it on other machines.
