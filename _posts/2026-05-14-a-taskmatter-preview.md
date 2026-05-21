---
title: "Task Matter preview"
date: 2026-05-14 10:00:00 +0100
---
If I don't catch myself, I can babble for hours about what I want to do, imagining and promising the moon. I already wrote 5 drafts about the origin, the vision, or the reasoning behind the project. The truth is I already have something significant, unique, and from my experience, useful. Some things still don't work and need work, but I can at least give a preview.

The AI software I'm building is both an enhanced AI chat, and a traditional UI to maintain a plan. Why do we need the traditional UI to maintain the plan? A plan is not code. It is a lot more trivial to complete a task, remove action items, or modify a title than doing any code change. And AI is also incredibly useful to magically create the plan, or adjust it. While using TaskMatter, I have realised manual and AI driven actions are astonishingly balanced.

Enough babble, here comes the preview.

Creating goals is either manual or AI led.

<video autoplay loop muted playsinline controls preload="metadata" style="max-width: 100%; height: auto; border-radius: 12px;">
  <source src="/assets/videos/posts/simple_create_goal_ai.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

![screenshot of user creating a goal plan](/assets/images/posts/TODO-create-goal-user.png) ![screenshot of AI creating the goal plan](/assets/images/posts/TODO-create-goal-ai.png)

User or AI then move tasks in "Focus" for the coming week:

![screenshot of user checking a task to go in focus](/assets/images/posts/TODO-focus-user.png) ![screenshot of AI helping decide what to do for the week](/assets/images/posts/TODO-focus-ai.png)

Users click on a task or action item to get guidance on that task or action item:

![screenshot of user getting guidance on an action item](/assets/images/posts/TODO-guidance.png)

Achievements show where you stand on your different goals, and the pace of completion for your different tasks and action items:

![screenshots of achievement screen](/assets/images/posts/TODO-achievements.png)

Under the hood, a dedicated AI harness interacts with the goals, tasks, and action items. User intent drives the AI workflows to get the info it needs, how the context is built, and what tools can be used. Each goal, task and action item scoped chat also gets a tailored context to be as useful as possible to the user.

Above shows the main capabilities as of today. It is the first feature scope I want to release through invites. But there is a lot more I am working on.

AI starts to shine when it is prompted to go deep on a subject. The concept of AI skill exists because of that behaviour. In traditional AI apps, AI has to guess what skills it is going to need based on previous prompting. No context, no skills. You may or may not have caught on the fact there is a different AI chat instance for every goal, task, action item, and a global focus area chat. This means before any prompt, AI knows what we are focusing on from the system prompt. This also means the skills or third-party integration relevant to the scope are automatically loaded. In other words, you click on a goal/task/action item, and you get the right coach, consultant, or manager for the job. Tailoring the AI interaction, and UI, to the type of task at hand is what really get me excited about this app. Possibilities are infinite, and where there's infinite possibilities there's an opportunity to open to plugins and third-party developers.

That's all for today. For the next post, we'll come back to the TaskMatter origin story, where the whole "I matter" therapeutic side of the meaning might make more sense (see [the About page](/about/) for the meanings of "I matter").
