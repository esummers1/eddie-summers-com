---
date: 2020-05-22 18:00:00 +0000
title: "How to Never Forget Anything"
summary: "How I have attained note-taking perfection, and am finally at peace."
category: "Productivity"
---

I have struggled for many years with how best to do and record things like the following:

- Notes about things I've learned or studied
- Planning projects or events
- Lists of stuff e.g. books to read
- Other random junk

There are lots of tools available to help you keep track of this sort of thing. Evernote, for example, does a great job of capturing *stuff* of every kind. Google Keep lets you add notes quickly and easily from anywhere. Notion allows you to build a personal wiki with all sorts of pages. OneNote seems to be able to just about anything. The list goes on.

But I've found with every one of these - and others - that nothing felt just right. Evernote is clunky, slow and does not produce pleasant-looking notes. Google Keep just doesn't work for long-form notes. Notion has high aspirations but was - at least to my monkey fingers - virtually unusable. OneNote just never felt right - my notes felt hidden and siloed. I even worked for a while writing notes by hand in notebooks, and while this is nice while writing, it's very hard to go back and find what you wrote in a physical book quickly.

What I needed was something that was lightweight, flexible, pleasing, fast, and easy to access. And, for someone with a compulsive streak such as me, configurable.

## Enter Markdown

Markdown is a markup language originally developed to generate HTML easily. It's readable, easy to type in and contains features like formatting, hyperlinks to web pages or other files, images, lists and - if you use the GitHub flavour - tables. It will even support mathematical typesetting in LaTeX in some versions.

Plain text has a big advantage over proprietary solutions. If you want to migrate your junk from Evernote to Google Keep, good luck. However if you want to use a different text editor to view and write your notes, no problem!

## Visual Studio Code

My choice for writing, viewing and managing notes is VS Code. There are excellent extensions for working with Markdown - specifically Yu Zhang's [**Markdown All in One**](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one), David Anson's [**markdownlint**](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) and Matt Bierner's necessary [**Markdown Emoji**](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-emoji), to name a few.

VS Code already has a Markdown Preview feature, which can sit beside a document you're working on and show you a live rendering, with synchronized scrolling and so on. Better yet, since almost every aspect of VS Code is configurable, you can get the preview pane looking just so: the right font, the right size, the right line spacing.

Since it's designed first as a text/code editor, its features for navigating through files for text blow other note-taking apps out of the water. You can traverse the headings and subheadings in a Markdown file using the `Go to symbol in editor` action, or quickly jump to a file by name. The usual ability to find/replace text across files using plain search terms or regular expressions is a given. If you like to use Vim or Emacs, there are emulator/keymap plugins avaiable.

## Source Control

This method of file-based notes lends itself to file syncing using e.g. Dropbox or OneDrive, or to version control using something like a private GitHub repository. At the moment I use Dropbox to synchronize Markdown notes between my different machines.

## Drawbacks

Yes, if you go this route, it isn't really possible to take notes on anything that doesn't run a desktop OS. Also, it doesn't play very nicely with diverse file types, although there are e.g. PDF viewer extensions available.

Ultimately, though, I've found that these don't bother me. On the rare occasion I want to note something down while nowhere near a computer, I can just add a quick note using Todoist, Keep, or paper, and transcribe/expand on it at some later point.

The ability to enter my thoughts quickly using a powerful text editor - and easily search through everything I have notes and ideas on - is worth any inconvenience. I used to get frustrated with my setup and change everything every few months, but so far it's been clear skies and smooth sailing on the HMS Markdown.
