---
title: "The task-first paradigm"
date: 2026-07-21 10:00:00 +0100
---
AI chats, in particular Claude Code and OpenClaw, have mainstreamed something every shell user already knew: we can use prompts to perform many actions that would otherwise take significant time in specialised software. AI chats have also adopted the same session lifecycle as shells. We tend to create a new session for every task, and dispose of it when we're done.

We quickly realised that keeping some state across sessions has value, and many memory implementations have sprouted. But there is another way, and it unlocks a lot more than context.

## Task first, session second. Or is it really a session?

One direction of integrating AI remains underexplored: reversing the usual order of creating the session first and then specialising it for a task. The task comes first, and there is exactly one persistent AI session attached to it. Once that session is made persistent, it can become a lot more than an AI session. Task Matter calls this larger scoped workspace a "Matter." Each Matter can contain multiple persistent AI threads, with each thread dedicated to one purpose within that Matter.

Now, the above might make you wince a little bit. Does this mean we need a plan for everything now? Even if they are the right thing to do, plans are a pain to create and maintain. There is no question about it. The answer to making plans is a combination of 
- AI,
- and being smart about it.

AI helps a lot in creating and maintaining the plan. "My wife, my two boys, aged 9 and 11, and I are going to France for three weeks. Help me plan it." "The holiday needs to be postponed by a week. Update the plan." These kinds of things. Not all items are relevant, so clean-up is necessary, but it will add steps where I think "yep, didn't think about that".

And "being smart about it" is allowing flexibility to the idea of 1 task = 1 Matter. The model which I found works best in practice is:
- 1 global Matter, which is also the Matter for the "Focus" area. That's where you run regular syncs, create goals, and ask ad hoc questions.
- 1 Matter per goal: the highest level in a plan.
- 1 Matter per task: the level below a goal.
- 1 Matter per action item: the level below a task.

In practice, you always have a space where to work in. I tend to use the task level most. Goal level is great for re-organising the plan. Action item level can be handy when there's a detail I want to query to death.

So what do we get with this persistent Matter per scope? Because the Matter isn't disposable, you can put things in it! Besides AI threads, we can store task descriptions, attachments, and notes in the Matter. That's what Task Matter currently supports.

## From workspace to platform

The above design opens up a very powerful capability. Remember that AI knows the purpose of the Matter before even starting. This means that for every kind of work, we can have a corresponding plugin that's automatically loaded. It is like software that recognises a file with a known extension and adapts the UI and behaviour accordingly. The available plugins are installed by the user from a marketplace. In Task Matter, I want to call these plugins "Matter Apps."

A Matter Apps marketplace is what transforms Task Matter from a task-management app into an extensible Goal OS, one that can theoretically adapt to any set of goals. The Matter is an environment in which any sort of application can run and any sort of integration can happen.

Let's take Coding Matter, the Matter App for coding currently in development. It is inspired by similar products like Herdr. Integrated with Task Matter, it maintains a 1:1 mapping between the plan action items and worktree branches. Implementation status gets constantly updated in the Task Matter UI. If findings warrant plan changes, these are brought to Task Matter as well. The user can connect to a coding session anytime to direct the implementation more closely if needed.

As another proof of concept, I want to target a kind of goal I tend to struggle with. Completing a DIY project is such a goal. A DIY Matter App could support modelling a plan based on a picture and measurements, giving a list of tools, material estimates, and covering safety guidance. Though to be fair, even without the dedicated Matter App, Task Matter does well on DIY projects.

These are two concrete examples, but the category and variety of apps that can be created has a similar breadth as what the App Store has to offer. Think learning apps, for subject matters, languages, music. Think admin apps, for taxes, company creation, government procedures. Think traveling apps, for itinerary planning, local history, kids entertainment. Behind all these apps are goals which are series of steps, with each step benefiting from external feedback, help and prioritisation.

## Why this matters

Task Matter's aim is to become such an AI task-management system, and I'm hoping other projects also go in the same direction. Today's AI chat is fundamentally aimless, it exists to answer whatever question happens to come next. The task-first paradigm gives AI a purpose, persistence, and a workspace. Now we have concrete matter on which we can build something.
