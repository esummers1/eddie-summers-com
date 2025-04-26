---
date: 2022-06-06 13:00:00 +0000
title: "Creating a Useful Todoist Dashboard"
summary: "How to use tags and filters to create a minimal overview of tasks that matter at the moment."
type: "post"
categories: ["Productivity"]
series: "To-Do System Design"
---

>Fair warning: if you don't use [Todoist](https://todoist.com/app/), this may not be very helpful. The concepts discussed here can probably be applied to other task managers, but I make no guarantees!

As I mentioned in [the previous article]({{< ref "./todo-system.md" >}} "the previous article"), one of the key design concepts for a helpful to-do system is the ability to hide tasks that aren't relevant right now. This is important for realizing the power a to-do system has for unblocking procrastination: if your workload feels manageable, you are much more able to manage doing it.

I alluded to the idea of using something like [Todoist filters](https://todoist.com/help/articles/introduction-to-filters) to create a view that presents you only the tasks you care about at the moment. This ability to define arbitrarily complex and detailed views is for me the killer Todoist feature.

The way this works in my system is that tasks are only assigned a due date if necessary; otherwise, I deliberately go through my projects once a week (or some other regular basis) to assign tasks to the queue of "current" or "active" ones. It's up to me to keep this queue to a length I think is manageable.

Then, the dashboard can display the following groups of tasks, in order:

- Those that are overdue
- Those that are due today
- Those that have been tagged for the queue
- Those that are due later this week
- Those that are blocked

This way, I only see the minimum set of tasks I need to, and I can focus on them more easily. You can move these blocks around by editing the query. This order makes sense to me - tasks that are due on a certain date appear at the bottom and make their way up until they leapfrog the queue and are due today.

I use a tag called `Queue` to designate tasks for this queue, and one called `Blocked` to visually separate tasks I can't work on right now. The following query can accomplish this (I call this filter view **Now**):

```text
!@Blocked & !Subtask & (Overdue | Today),
!@Blocked & !Subtask & !Today & !Overdue & @Queue,
!@Blocked & !Subtask & !@Queue & !Today & !Overdue & due before: Sunday,
!@Blocked & !Subtask & !@Queue & !Today & !Overdue & Sunday,
@Blocked & !Subtask & @Queue
```

You will probably also want a dedicated filter to list tasks for your regular refinement/tagging, which I call **Backlog**:

```text
!@Blocked & !Subtask & !@Queue & No due date
```

## Supporting Separate Projects

If, like me, you also manage your work at your job using the same system, you probably don't want your work tasks to appear in the **Now** view, or in your **Backlog**. You may also have other projects you want to exclude from the system, e.g. school work or a side business project that you handle differently.

Rather than explicitly excluding such projects from your filters, you can instead group all "normal" projects under a project called e.g. `Queueable`, and add this as another condition in your filters:

### Now

```text
##Queueable & !@Blocked & !Subtask & (Overdue | Today),
##Queueable & !@Blocked & !Subtask & !Today & !Overdue & @Queue,
##Queueable & !@Blocked & !Subtask & !@Queue & !Today & !Overdue & due before: Sunday,
##Queueable & !@Blocked & !Subtask & !@Queue & !Today & !Overdue & Sunday,
##Queueable & @Blocked & !Subtask & @Queue
```

### Backlog

```text
##Queueable & !@Blocked & !Subtask & !@Queue & No due date
```

## Start Dates

Eagle-eyed readers may have noticed that my system only allows a week's notice before something becomes overdue: tasks with due dates only enter the **Now** view when they are due before or on the end of this week. Ideally, we would like to be able to specify a longer lead time for some tasks, as some may take more thought, planning, or effort than others. Some task managers, like [Omnifocus](https://www.omnigroup.com/omnifocus/), have a dedicated notion of start dates (called "defer dates" in Omnifocus), but Todoist unfortunately lacks them.

Many people have proposed clever workarounds, but I've stuck with a fairly simple one. I have three tags called `1w`, `2w` and `4w`. These represent the lead time I want a task to have. If I want a task that has a due date to show up in the **Now** view before it would naturally fall into it, I can add one of these tags, and adjust the **Now** filter to the following monster:

```text
##Queueable & !@Blocked & !Subtask & (Overdue | Today),
##Queueable & !@Blocked & !Subtask & !Today & !Overdue & (
  @Queue |
  (
    (
      (@1w & due before: +1 weeks)
      | (@2w & due before: +2 weeks)
      | (@4w & due before: +4 weeks)
    )
    & !(due before: Sunday | Sunday)
  )
),
##Queueable & !@Blocked & !Subtask & !@Queue & !Today & !Overdue & due before: Sunday,
##Queueable & !@Blocked & !Subtask & !@Queue & !Today & !Overdue & Sunday,
##Queueable & @Blocked & !Subtask & (
  @Queue |
  (
    due before: Sunday
    | Sunday
    | (@1w & due before: +1 weeks)
    | (@2w & due before: +2 weeks)
    | (@4w & due before: +4 weeks)
  )
)
```

In other words, the queue section now shows tasks that are inside the defined window but not due within the next week. Now, if a task is due in two weeks' time and is tagged with `2w`, it will appear in the queue section. As we arrive on the Monday of the week in which it's due, it will leave the queue section and appear on its due date with the other tasks due that day. I find this flow quite intuitive, and often use these for things like preparing for a loved one's birthday (`4w`) or renewing my car insurance (`2w`).

This idea pairs particularly well with recurring tasks. With the car insurance example, I can set a task to renew it `every 15th July` and tag it with `2w`, safe in the knowledge that I can completely forget about it until it appears in my **Now** view again.
