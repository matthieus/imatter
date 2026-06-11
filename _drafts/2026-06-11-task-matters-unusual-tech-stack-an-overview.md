---
title: "Task Matter's unusual tech stack, an overview"
date: 2026-06-11 13:00:00 +0100
---
Task Matter has an unusual tech stack. It started less as a careful architecture decision and more as a "let's try things and have fun" experiment. Then the fun things ended up working. I was not expecting that.

So yes, this is partly a stack overview, and partly me retroactively justifying my choices now that they have become real product architecture.

The short version:

- **Language:** Scala on the server, Scala.js in the browser
- **Build system:** Mill
- **Frameworks:** ZIO on the server, Laminar in the browser
- **Persistence:** Postgres for profile and auth data, S3 objects for user data
- **Browser persistence:** IndexedDB
- **Data sync:** custom git-like commits
- **Data format:** RDF N-Quads
- **AI orchestration:** custom AI harness
- **Deployment:** one simple VPS for everything, for now

The stack is unusual, but it is not random. There are reasons and benefits behind each choice.

## Scala, server and browser

Scala is probably the most controversial choice. For web projects, it is now a niche language. I know this is not the default startup stack. I also know future me may one day curse present me for making hiring harder. But for now, I still think Scala holds its own.

The first reason is Scala.js. It works very well, and it lets me share code between the server and browser. That matters a lot for an app where the client is not just a thin UI, but a real local-first application.

The second reason is the ecosystem. Scala's ecosystem is smaller than it used to be, but the quality is high. Because the language has advanced features, it tends to attract engineers who enjoy thinking carefully about abstractions. 

The third reason is stability. Once on Scala 3, the ecosystem feels relatively settled. Because the community is smaller now, established libraries tend to remain established for a long time. ZIO and Laminar have both been relevant in the community for years.

And finally, there is the type system. This is the classic Scala argument, and it still applies. Types reduce the surface area for mistakes and document intent. Good for humans and AI. There is also some TypeScript in the codebase, and I haven't found that AI makes fewer mistakes or produces better abstractions with TypeScript. I haven't gone into the rabbit hole of measuring that, though.

## Mill, ZIO, and Laminar

I started with sbt and moved to Mill. The practical reasons were worktrees and monorepos. `sbt-git` had issues with my worktree workflow, and Mill has better support for partial builds and aggressive caching. This is not glamorous, but build tools become very emotional once they get in your way.

ZIO was new to me for this project. I picked it for the batteries-included approach: there is usually a ZIO sub-project for most infrastructure needs, and the same approach extends nicely to custom code. Server-side code isn't where most of Task Matter's logic is, though.

The browser side is where it matters. I chose Laminar partly because it is used by the Scala.js creator, and partly because it promised to handle complex shared state. In Task Matter, many UI elements reflect the same underlying state in many different parts of the app. Laminar makes those updates feel instantaneous, and that has been one of the pleasant surprises of the project.

## Offline-first data

Task Matter is offline-first for both reads and writes. The client keeps recent history locally. The server keeps the authoritative log.

Updates are stored as git-like commits. Whether a user or AI changes a plan, the change history is available for review, undo/redo, reporting, or AI context. That matters because plans in Task Matter are meant to adapt constantly to reality. A plan that cannot absorb reality is not much of a plan.

RDF N-Quads are the most exotic part. The benefit is generality. A commit is just a set of added and deleted quads, plus metadata. That makes applying sync updates independent of the application data model. And it's conceptually simple: the data is a set of quads, changes are lists of REMOVE and ADD quads, commit metadata is expressed as quads, and the schema is made of quads. Everything is a quad.

I'm not really using RDF to its full power, though. When I chose RDF, I also had in mind AI writing its own RDF to store and index context and knowledge related to plan entities. I haven't abandoned the idea. There is just so much to do!

On the storage front, for each user, Task Matter maintains a current-state file and a log file. The server sends commit deltas, keeping sync quick. When the server has moved on, the client rebases pending local commits onto the server state. Valid commits get new parents; redundant or invalid commits are dropped and surfaced to the user.

RDF sounds a bit strange, but in practice it gives me exactly what I wanted: offline edits, understandable history, and a data model that can evolve without rewriting the sync layer.

## AI orchestration

AI orchestration has been the hardest part. Compared to the git-like sync, it is another level of difficulty. Task Matter always runs AI in a known context: a focus area, a goal, a task, or an action item. That creates a real opportunity to minimise turns, tool calls, and context size by tailoring the interaction to where the user is in the plan.

Finding the right abstraction took a while. My first attempt was multi-agent orchestration with specialised agents. It sounded right, but it was non-deterministic and impossible to debug. It was the wrong abstraction. Claude Code and Codex were not especially helpful there either. They can implement any design you give them, and they will even compliment you on it (especially Claude), but they're as clueless as I am about agent orchestration.

What worked better was a set of built-in directives, each with its own recipe for system instructions, context, and available tools. A quick, cheap resolution step chooses the directive from the user prompt. The result is more boring and less magical than the multi-agent version, but it gives me much more control.

In that sense, Task Matter is a bit like a coding AI harness, but for goal plans.

## To conclude

I have used Claude Code, Codex, and more recently Pi Coding Agent to write the code. I tend to give small tasks and adjust the results a lot after the fact. Even if the tech stack is unusual, AI hasn't struggled one bit with understanding what the code does or writing code that compiles on the first try. At one stage, I was trying to find excuses to migrate to a more mainstream stack. I even tried to one-shot the rewrite of the codebase into TypeScript and React. The result was terrible. It made a completely different app that looked like the thousands of project management apps out there. Most of it didn't work anyway. At least with an unusual tech stack, AI can maybe forget some of its learned UI patterns and let itself be pulled towards something more original.
