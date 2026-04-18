---
layout: post
title: "Theory of mind"
date: 2026-04-14 21:02:17 -0700
permalink: "/theory-of-mind"
description: "TLDR; Agents can't tell the difference between you and them"
---

# Theory of mind

If a developer prompts in the forest, does the agent become a self
{: .fs-6}

A couple weeks ago I was doing an experiment in Codex where I was trying to create a subagent tree. One of the techniques that people have tried to preserve context is splitting off side quests into a new agent. In the industry that's evolved the newest pattern is to create that main/subagent relationship as an adversarial one. The main agent assigns the work and then rejects and forces a retry when the subagent is non-compliant. I wanted to take it a bit further. For a complex task could you split off a tree of work, not for parallelism, but for context preservation.

The answer, before you try this is, 'no'. Please don't try this at home. The clients are not very sophisticated. MCP servers have costly startup times that hit each agent. Clients don't clean up these subagents and that does lead to Rust kernel panic. When I resolved that by adding "close agent" to the instructions, the client still was leaving all the MCP servers around. And yes, that did create so many processes that I was unable to open even a blank zsh shell. Permission problems in lighter weight custom subagents blocked that direction, even when I was able to remove the MCP related problems.

There was another problem though, theory of mind. The agent struggles to understand the boundaries of work between itself and a subagent. Going to the third level in that tree was a constant struggle. In order to create the workflows I had to create a BOUNDARIES.md document so that I could get the agent to understand which agent level was responsible for what. That's a useful document, because when the agent (even a fresh one) started wandering around lost, unable to find its ass with both its hands, I could say, look at this document. You are conflating agent A with agent B. Since I was creating this tree of three deep agents with an agent, my collaborating agent in this scheme was at four hops of abstraction of self.

Robin Dunbar, a scientist of many categories created a theory for abstraction called "Levels of intentionality":

Some levels are:

1. Awareness of own thoughts: I think X
2. Theory of mind: I believe you think X
3. Thinking about what someone else is thinking that another person is thinking.
And so on. Higher levels get increasingly hard to think about, and write about.

Shakespeare was a master of these abstraction leaps:

1. The audience thought
2. Iago wants
3. Othello to believe
4. Desdemona loves Cassio
5. And Desdemona believes Cassio loves her back

That's five levels, and most humans struggle with that in a fun brain tickling way. Shakespeare, though was operating at 6, since he was creating this experience for the audience.

This is all to say, agents struggle with the abstraction leaps. They struggle with boundaries. Who is doing what is quite confusing for them if they aren't the doers. This even happens in that adversarial divide between the top level agent and a subagent with a task. Given a fork that shares context, the subagent will finish off the work that should be done afterwards by the parent. Sometimes the parent will go ahead and do all or part of the subagent task. I had been thinking these bad boundaries were part of the dude-bro code of ethics trained into the models. Maybe not.

Today, in my haste and clumsiness on a DVORAK keyboard. I wrote to the agent:

> That's not light
{: .card .chat-bubble .user}

Before I could send my fixed message, the agent was spinning off. It was so doggedly solving random and unasked for things, that I had to stop the flow and have a meta-conversation: 

> What problem are you trying to solve?
{: .card .chat-bubble .user}

In tracing its steps it said:

> I said, 'That's not light.', but I meant, 'That's not right'
{: .card .chat-bubble .agent}

The agent was not quoting me or speaking from my point of view, which would have been some third level intentionality for sure. The agent lost its place in the conversation and believed it had made that mistype. 

I followed up with, "No that was me". It was back to itself again, with a pandering apology about how I was "absolutely right" and it had made a mistake.

Wait, what?!?

I know that the model is an LLM trained with very terrible incentives. I know it's not actually intelligent, but I assumed the system had to be trained into a very strong theory of mind in order to simulate conversations. We can talk to ourselves, but when a conversation is geared towards getting things done we need to have a conversation where we can distinguish ourselves from the other. 

I don't think it's safe to assume that agents have a theory of mind. 

Possibly everything they process is them, including me.
