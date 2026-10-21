---
title: "The Task Matter premise: task-first AI"
date: 2026-10-11 10:00:00 +0100
---
Task Matter is software to help reach personal goals. This post talks about its foundational idea: task-first AI. 

In effect task-first AI is a fusion of AI with task management. The result is both better AI and better task management: our AI has purpose, and task management becomes a natural part of the work itself.

# We can do better

The current status quo for both AI and task management user experience feels sub-optimal. Let's see why.

## Specialising our AI chats

Most AI chat sessions correspond to an implicit task, itself part of a goal. Yet, we start from scratch every time. There are two problems with this approach:

1. over time, AI sessions become a mess of information, with many different levels of concern.
2. context building is inefficient guesswork based on the first few prompts and persistent historical memory.

Both issues are related to the same idea of specialising the AI chat towards a given task. And as we will see, both issues can be solved using the same solution, task-first AI.

## Task management is painful

Let's now look at the other side, the task management software. For simplicity, we'll focus on the simpler incarnation of it, the todo list. Todo lists are both a critical tool to our lives and a pain.

Why can't I and many others seem to be able to use todo lists consistently? I can answer for me, at least. And the reason is that most of the time my lists have been write-once-and-forget lists. I write a bunch of tasks and start the work. But, 1) I tend to not read the list, 2) I never update it with findings.

Why didn't I read or update my rare todo lists consistently? Doing the work tends to uncover the next obvious task, meaning the work just feeds itself. Until I realise I lost myself a little bit and didn't accomplish what I intended to do, and still actually intend to do.

Task management is necessary friction. What if we made task management a natural part of just doing the work? 

## TODOs feeding the HOWTOs feeding the TODOs

Summarising both paragraphs above, 
- AI interactions are often naturally task-focused and could get better context by being explicitly associated with a task,
- and task management could benefit from AI help to keep the plan fresh and relevant by making it part of the work.

Why hasn't a more unified task+AI experience become mainstream already?

I don't know. But I like guessing. Most AI-task management integration has been either task management with AI agents on top, or AI talking to task management as third-party MCP. And problem seemingly solved. But these solutions are not built on the opportunity of having both sides benefit each other natively, in one coherent piece of software.

The whole idea of task-first AI is to have AI help us make the plan which itself helps AI help us. That is the gist of it.

How did task-first AI emerge from the work on Task Matter? The journey is too long to detail in this post. But when that design emerged, it felt both like a result of many improvements and an aha moment. It felt like I found what I was looking for.

# What does the task-first AI experience look like?

How do we focus on a task to talk to AI and work inside the plan? The starting idea is obvious: we click on a task and prompt.

Now, how do we make the experience work in practice? For this, we'll need to answer a few key questions: 
- Do we even have an AI chat before the goal plan is even created?
- Where does the plan come from?
- What if we want to ask questions about the whole project? 
- Or what if we want to focus on an action item and ask that detail to death?
- What makes a task? There's more than AI conversations to a task, am I right?

Let's see how Task Matter answers them.

## The Task in Task Matter

In Task Matter, the plan is on the left in a panel we call "Task". And if you're tempted to joke that the right panel is called "Matter", you'd be 100% right, that's its name.

Plans are goal-oriented todo lists with 3 levels: goal, task, and action item. The title is all that's needed to create an item. Most todo apps have a similar hierarchy of plan items. A goal can be long or short term, it is completely up to the user. In practice, you (or AI) will want to detail the first few weeks and gradually specify higher level tasks the further away they are. And that's how the AI plan creation is tuned.

A task can be chosen to appear in the Focus area, which shows what we're working on. We can then work on our tasks and action items from Focus. In their Focus, one could have tasks from DIY, cooking, and software goals. It should look like your day.

The Task side is simple, and it should be.

### Man with an AI with a plan

To create a goal, we describe what we want to do, and a goal plan gets created. Or we can create any part of it manually.

Consider the prompt "My wife, my two boys, aged 9 and 11, and I are going to Paris for three weeks. Help me plan it.". Or "I want to refurnish my bathroom". We may get some follow-ups, but they are limited at creation time. Most of the time the first few generated tasks are about detailing what we want to do. We also get a goal description that helps us understand what the goal includes. The goal is also ours. We can add our own items, edit or delete anything AI creates, and undo changes.

I have played with very far-fetched goals like "I'd like to help my son become an astronaut". The result is concrete milestones and practical advice making the goal feel real. I did have to remind myself my son has no interest in being an astronaut. Point is the same applies to important goals we should do but always postpone. One of them was a very real one for me: doing the paperwork to get Irish citizenship. As an EU citizen, I don't _really_ need Irish citizenship. But I have been living in Ireland for 16 years, my wife and children are Irish, and I do feel at home in Ireland. Creating a goal in the app was a very low bar, and seeing the tasks made it concrete for the first time. And it helped me go through the steps to finally submit the paperwork.

Creating a goal and seeing the first steps as completable action items is astonishingly efficient at making a goal concrete and reachable.

### There are no missed deadlines

There is only the reality of our lives. Plans are not there to make us feel guilty. They are there to show us the path. Motivational speech aside, the way we change a plan is by clicking on the item that needs updating (which could be a goal), describing our reality, and asking to update the plan accordingly.

I have used Task Matter to try to run 5km in 20 minutes. It is a very common target for middle-aged men who refuse to admit they're ageing, like myself. I didn't make it. But the journey is what makes it worth it as they say. I didn't follow some of the plan, and generally ran my easy runs way too fast. But I've still had some of the most consistent training I've ever had, and got plenty of joy reaching a level of fitness I hadn't reached in years. At multiple stages, I reported not hitting milestones, and we reworked the plan to try to beat the plateauing I was experiencing, which did help.

AI doesn't blame us. It cannot fire us. It cannot even be disappointed in us. All AI does is look at what happened and devise the next best course of action. What's next to reach the stated goal is all that matters.

That being said, I did add an "Achievements" space to Task Matter to gaze at all the things I've done so far. And there is even a "Momentum Score", just to add a little tickle from our inner gamer mentality. And I have to admit I don't like it dipping under 90.

## The Matter in Task Matter

In Task Matter, the place where we have our AI conversations is called the "Matter". Every goal, task, and action item has its own Matter. The Matter can be as empty or rich as it needs to be. We will also see that the Matter contains more than AI conversations.

### Threads, like books on a shelf

Each Matter can contain multiple AI conversations as separate threads.

We can have (a lot) more than one request when working on a task. The thread is the perfect UI artefact to collapse a conversation stemming from a starting question. When dogfooding Task Matter, the need for threads became overwhelming. Adding threads with generated titles made the whole design fall into place.

Different threads can have different purposes. For example, a thread could be about understanding the work behind the task, with AI writing what will be used as a reference document. Another thread can be about giving feedback on an intermediate result. And yet another thread could be updating the plan given what we learned.

Besides tidying our conversations, threads help AI focus its context on the user intent. The more focused AI context is, the better the answer.

But conversation threads are not the only objects we can put on our Matter-shelf.

### The detail is in the Matter

As we've seen, on the right we have the Matter, and on the left we have the plan. We want our plan on the left to stay as lean as possible. Getting an overview of the work, prioritising, choosing the next task, that's what the left panel is for. Where do we put our plan item details then? When we click on a plan item, we see its Matter. Could we get away with having all our task details also inside the Matter, mixed with AI conversations? Or would that end up a mess?

As you might have guessed, Task Matter went for it.

The details present in the Matter include:
- Description at the top, written and edited by AI or the user
- Image and document attachments, for pieces of evidence, results, and reference material, can go anywhere
- Informal user notes, with updates, constraints, timelines, can go anywhere

The description is always at the top, the rest appears in chronological order of creation. Every entry can be deleted. And everything is undoable. The flow is:
- we add updates when they come 
- we ask questions when they come

In short, the Matter is a collaborative space for the user and AI. The selected plan item gives a starting scope, and the work may need us to add documents, pictures, notes, and ask AI a flurry of questions. That's what the Matter is for.

# Task-first AI, because our goals are worth it

Planning is not Task Matter's end goal. The plan gives the human-AI collaboration purpose and context. And it also gives a space to work in. In turn the human-AI collaboration helps refresh the plan, as results and constraints appear. I like to see it as a loop feeding itself, like a wheel rolling in the direction we set it to.

There is still plenty to improve on and build. But I am already thrilled with the foundation. Being able to work inside the plan is a mindshift that feels right.

Give it a try by registering for the beta at taskmatter.ai.
