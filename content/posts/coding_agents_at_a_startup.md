---
title: "Coding Agents at a Startup"
date: 2026-05-13
---

<br/><br/>

Personally, my own experience of using coding agents has been all over the place.  Claude Code helped create a product prototype in minutes that would have taken me at least a week, and then a few minutes later it's tripping over itself trying to import stdlib. It behaves like a hippie dev who is usually reasonably competent, sometimes takes ... ahem... mind enhancers to achieve extraordinary leaps of logic that leaves me taken aback, and at other times, crashes from that drug-induced high to generate such ridiculously dumb conclusions that I'm left scratching my head.

There is no doubt software engineering has changed with the advent of coding agents. Here are some observations I've noticed.


# AI increases prototyping speed
I used Claude Code to write a TypeScript UI without any prior experience. The docs reading and boilerplate that would have taken days just disappeared. However, this increase in speed and abstraction has some costs.

<img src="/images/boilerplate_claude.jpg" width="50%"/>

# AI coding tools are straining review processes
I've noticed we're shipping more code than ever, but our review habits haven't caught up. It is important to develop processes to support the larger volume of PRs. Not all code deserves the same scrutiny. A quick visualization script is not the same as critical api changes. More than ever, it is important for the PR author to communicate how the PR should be reviewed. Some approaches worth exploring: PR description templates that flag impact level and what to focus on, video walkthroughs where the author explains the code, and tiered review assignments where low impact PRs get a lighter pass and high impact ones get more eyes.

<img src="/images/prs_every_day.jpg" width="50%"/>

<br/>

# AI is changing engineering culture
There is less ownership over the codebase. Folks ship code without understanding why it works. When problems arise, they blame the coding agents. But I don't think the answer is to relinquish ownership. I think the definition of ownership is shifting. It used to mean "I wrote it and I understand every line." Now it might mean "I'm responsible for what it does, even if I didn't write every line."

# AI can reduce collaboration
Folks tend to ask Claude instead of their teammates for understanding the codebase, for second opinions, for things that used to require a conversation.

# AI amplifies skill distribution
AI amplifies both good and bad judgment. Strong engineers move faster and make better decisions. Knowing how to prompt and when to distrust the output has become a skill in itself.


</br>

---

The fundamentals still matter: good judgment, clear communication, ownership over your work. You can generate a week's worth of code in an afternoon, but you still have to understand what you're shipping, explain why it's correct, and own it when something breaks. That's something a coding agent can't replace (yet).

---

*Thanks to Michael Gira for proofreading and feedback.*
