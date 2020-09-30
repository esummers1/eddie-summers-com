---
date: 2020-09-30 12:00:00 +0000
title: "Networked Notes"
summary: "How to structure information in a way that makes sense to you."
type: "post"
categories: ["Productivity"]
---

I have [written previously]({{< ref "/never-forget-anything.md" >}}) about how I have found VS Code and Markdown to be just the right way for me to take notes about things. To have claimed to have attained "note-taking perfection" was probably ambitious, but  so far not actually wrong - what needs fixing next is access to the information in the notes.

If you take notes on a computer, they will probably be filed in some kind of directory structure. This is true in a symbolic sense for note-taking applications that organise notes into Notebooks and so on (e.g. Evernote, OneNote), and true in a more literal sense for the Markdown approach I advocated last time.

The trouble with this is that while it feels productive and "organized" to file away notes in just the right place, your notes should probably not be modelled on an archive. You should think about your notes as a second human memory, or *knowledge base* (as the trendy term is at the moment). Thoughts relate to one another in disorganized, unstructured ways, and surely the best way for you to remember what's in your notes (the point of having them) is to structure them in a manner that feels natural to the brain.

## Networked Notes

Being a [Cortex](https://www.relay.fm/cortex/) fan, I have been [recently introduced](https://www.relay.fm/cortex/105) to the idea of [Zettelkasten](https://en.wikipedia.org/wiki/Zettelkasten). In short this is a way of organising notes by means of the connections between them, not by means of some external structure.

I found that this idea stuck with me - it makes a lot of sense. Advocates of Zettelkasten claim that after a large enough number of notes have built up in your system, you start to see emergent links between distant ideas, and make new connections.

## Tooling

I decided to try out this type of system for myself, so the next question was how to integrate this into my current workflow. There are tools that can do this for you e.g. [Roam](https://roamresearch.com/) and [Obsidian](https://obsidian.md/), but as I said, I have already achieved note-taking perfection. The first step was to pull all my notes out into a single directory, so new notes could be added without the friction of having to find a place to file them. But how could I link notes together in a useful fashion in VS Code?

Luckily I stumbled across [this article](https://kortina.nyc/essays/suping-up-vs-code-as-a-markdown-notebook/) by Andy Kortina, which describes an extension he made for VS Code called [Markdown Notes](https://marketplace.visualstudio.com/items?itemName=kortina.vscode-markdown-notes). It supports wikilink syntax, e.g. `[[my-cool-note]]` to link to `./my-cool-note.md`, among other things.

I tried this at first, and it has some very handy features, but I found that it didn't support navigation through wikilinks in the preview pane. To do this you need an extension that completely replaces the preview, e.g. [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced) by Yiyi Wang. This did not allow me to style the preview in a manner that I liked, and the feel and readability of the environment were two of the main reasons for picking this way of taking notes.

Luckily I then discovered [Markdown Memo](https://marketplace.visualstudio.com/items?itemName=svsool.markdown-memo) by Svyat Sobol. This - crucially - allows you to specify labels for wikilinks (as the double-bracket links are known), e.g. `[[my-cool-note|My Cool Note]]`. These links are also navigable in the native preview pane. Like Markdown Notes, it also supports bi-directional navigation: when a Markdown file is open, the Backlinks context menu (in the Explorer pane) lets you see all the references to the file and navigate backwards by clicking them.

Unlike Markdown Notes, Markdown Memo does not offer workspace support for tags in notes - ideally they would be understood as symbols by VS Code and searchable using the References feature, but you can still search using the standard search. I keep tags in the header of each file as front matter:

```markdown
---
tags: #kotlin #object-orientation
---

# My Note's Heading

...
```

## Style

I am reliably informed that short, atomic notes - i.e. those on a single, confined subject - are easiest to network properly. The best summary of these ideas I've seen is on [Andy Matuschak's notes website](https://notes.andymatuschak.org/z4SDCZQeRo4xFEQ8H4qrSqd68ucpgE6LU155C).

What I find helpful about this style is now that I don't feel as if I have to write long-form notes, or find a place for them to go. If I have an idea that I want to keep and think more about later, I can just start writing - and if I remember that I've written something related before, I can link to it from this note, and visit that other one to see if it needs refining or expanding. As I develop these notes, they may well end up getting expanded into articles for this website, since I can sometimes feel that I want to say more about a topic.
