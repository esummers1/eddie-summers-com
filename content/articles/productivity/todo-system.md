---
date: 2022-02-16 16:00:00 +0000
title: "Designing a Useful To-Do List"
summary: "How best to avoid procrastination, and maximize the amount you actually get done."
type: "post"
categories: ["Productivity"]
series: "To-Do System Design"
---

Procrastination has had a significant impact on me at several points in my life. The most egregious example happened during my final year at university, on my undergrad degree in sport & exercise science. My dissertation - the write-up for my final-year project - was due in April, and I had had the whole academic year since October to work on it. However, at the start of April, all I had managed to do was the experimental trial itself - a simple study of the effect of a certain kind of warm-up drill on activation of the target muscles during subsequent exercise. I had done very little background research, and none of the write-up.

You might think that the looming deadline, coupled with the enormous amount of work left to do, would encourage me to do some of it. However, it had the opposite effect; the closer the deadline got, the less inclined I felt to do anything, despite my increasing fear. The *week of the deadline* arrived, and I still hadn't started work. In the end, I had to work from about 2 PM on the Wednesday, right up until the hand-in deadline at 5 PM on Thursday. My memory of this period is quite foggy, but I think I fell into a routine of working for three hours, taking a caffeine pill, and having a 20-minute nap. As you might imagine, I could have done a lot better on that piece of work than I did.

Tim Urban of [Wait But Why](https://waitbutwhy.com/) wrote a [fantastic article](https://waitbutwhy.com/2013/10/why-procrastinators-procrastinate.html) later that year exploring this phenomenon, although I didn't come across it until a few years later. He does a much better job of explaining it than I could, but to me the root of procrastination is fear: any time I realize I'm putting off the time I have to do something, it's because I'm worried about it. This is either because I know it will be unpleasant, or - as is so much more likely - I'm uncertain about how one part of it will work, or what I will need to do, and am afraid of that uncertainty.

In the years since then, I've done a reasonable job of curing this behaviour in myself, though I have lapses every now and then. Somewhat unhelpfully, one of the things that helped was arranging my life in such a way that the things I have to do are more likely to be things I want to do: I enjoy my work and I choose the side projects I work on. However, for everything else, the systems by which I organize myself help enough for me to get by.

## To-Do Lists

The classic idea of a to-do list is just a list of things you need to do, on paper. You can develop this idea by having separate lists for different projects, or work contexts, or any number of other different ways. Much has been said about this topic, so I'm just going to focus on things that have helped me.

The most important benefit of the to-do list is strongly related to the need for [note-taking]({{< ref "./never-forget-anything.md" >}}): the fact that the brain is for thinking, not for remembering. As long as something you want to remember exists only in your head, it's at risk.

## Ingress

Therefore, to me, the first requirement for a good to-do system is that it must be easy and fast to add items to it, wherever you are. The more steps are required for this, the less likely you are to add things, meaning they will stay at-risk in your mind. I have experimented with things like [bullet journalling](https://bulletjournal.com/) for managing tasks, but have always gone back towards using an electronic system - specifically Todoist, though I will leave the reasons to choose it over others for another time.

Something that can live as an app on your phone, and on your desktop machine (whether that be natively or in the browser), is so superior for task ingress to anything else that there is no competition. Note that this also excludes digital versions of the paper to-do list, including using plain text lists, or more sophisticated (and admittedly excellent) things like [org-mode](https://orgmode.org/).

## Access

While you must be able to add a new item from anywhere, it is not necessarily true that you should be able to use all the features of your system from anywhere. Usually, entering tasks and actually doing the work they tell you to are separate activities. Personally, I find that I'm almost always at a computer when actually getting stuff done - meaning my phone is more for adding tasks, or being reminded of time- or location-sensitive things that don't really live in the to-do system. This means that you can combine systems usefully - there is no particular reason that your task inbox needs to live in the same application that handles your filtering and displays tasks to you, although it makes things a lot simpler.

## Filtering

Even fairly complex to-do systems are not suitable as project management tools, in my opinion - the real value of to-do applications that organize tasks into "projects" (usually in the [GTD sense](https://gettingthingsdone.com/)) is that it allows you to compartmentalize and **hide** tasks when you don't need to look at them. Non-trivial projects are too non-linear and require too much supporting thought to be managed purely by a to-do list, although you can certainly use to-do lists to collect next actions in the same place that you look for other actions.

Most people have surely had the experience of feeling like they have too many things to do at once, deciding to write these things down, and realizing that these things were far more manageable than they thought. The real value of using a proper system for managing your tasks is that once these things are out of your mind and on paper, this feeling of overwhelm goes away, or at least reduces.

However, the danger with a simplistic to-do system is that a very long list of tasks - even if they are quite small - conjures a similar feeling to having three or four things swirling around your head at once. The enlightened to-do system designer designs the system to do two things well: accept new items, and hide ones you don't need to work on now.

A common way people use to-do managers is to try to assign every task a due date, so nothing gets forgotten. However, we all have days where little gets done, or you don't end up having the amount of time you thought you did, so lists like this quickly end up with lots of items in "Overdue", which is really not much better than having them in your head. To me, the correct approach is to only assign due dates where necessary, and instead have tasks enter your "do now / this week" list deliberately.

>Incidentally, my only real frustration with Todoist is that it doesn't support the notion of start/defer dates, as [Omnifocus](https://www.omnigroup.com/omnifocus/) does, but I have a workaround which I'll write about another time.

The way I do this is using a [Todoist filter](https://todoist.com/help/articles/introduction-to-filters), i.e. a custom view defined using a simple query language. I have a tag I assign to tasks that I want to work on "soon", and I have a view that shows me tasks that are due soon, plus those that have this tag. Everything else is hidden, and I only go through those tasks once a week, tagging more tasks that I want to work on, to assign them back to the main view (this can be made easier by filtering for tasks that have neither tags nor due dates!). This "now" view is roughly arranged in order: first tasks due today, then tasks with this tag, then tasks due on days later in the week.

This way, there can be hundreds of tasks in the system that I can *safely forget about*, because I have a system for reviewing them regularly when I'm in the frame of mind for prioritizing and refining tasks, which makes it easy to reason about work in the knowledge that I don't have to do it right now. This separation is important: this is quite a different mode to the daily mode of opening the task manager and seeing what past-me thought it was important to work on.

This system is naturally imperfect, in that I am imperfect: sometimes I still procrastinate on items in the list, but this becomes much more obvious when there are only 5-10 items due this week, and a particular task is lingering from week to week. When this happens, it often helps to write down what's causing me to worry about it, since I often know, but am lying to myself about it. Once this is out in the open, it feels a lot less threatening, and I often find the task gets done.

## Summary

Your system must respect the following truths:

- People are bad at remembering things
- People are bad at thinking about more than one thing at once
- An intimidating amount of work to do can seem infinite, **but** work that is out of sight is out of mind

And therefore do the following before all else:

- Allow you to add items frictionlessly
- Hide items that can't or shouldn't be worked on right now
