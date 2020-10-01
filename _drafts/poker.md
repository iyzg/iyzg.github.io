---
layout: post
title: Introducing CAPS (Completely Arbitrary Point System)
description: A new and revolutionary system for evaluation your competitive programming contest performances.
date: 2020-09-04
permalink: how-to-fail
---

We've all seen those posts about how to better calculate ELO and improved rating systems for competitive programming based on *actual* math with fancy academia jargon like TODO, this isn't one of those.

Reasons I'm not basing this off serious math:
1. I can't do math
2.

Jokes aside, CAPS may not be based off any complex mathematical model, but it **CAN** help you better evaluate your performances on a contest-to-contest basis. 

## What is CAPS?
CAPS (Completely Arbitrary Point System) is exactly what the name says. It's a system designed to better evaluate contest-to-contest basis while making sure to put special emphasis on your current weaknesses.

## Points System v1.0
- Right Idea: +5
- AC: +5
- WA/TLE/MLE: -1 each
- Wrong Idea: -1 each
- Missed Constraints : -1 each
- Overflow: -1 each



### How I Created This

At the crux of the system, we have 3 evaluations: right idea, AC, and WA/TLE/MLE. I currently give both getting the right idea and AC +5 each, but if antonygrub keeps coordinating contests, this may turn into Right Idea +10, AC +0. You'll notice that besides the 3 core things, I've also included what problems I currently am trying to fix. It might seem kind of cruel to double the punishment if I meet one of my extra citations and submit, but it's important to reinforce that these mistakes are costly to work on ironing them out.

It's all arbitrary. I knew that I wanted it on a scale of $ (-\inf, 10] $ and it's impossible to tell whether or not the implementation or thinking of idea will be harder in any given problem, so I've assigned both 5 points for getting them correct. Next obviously WA/TLE/MLE needed a punishment so I gave them -1 and then gave point values for the things I wanted to focus on. Overflowing, missing constraints, and getting wrong ideas are all mistakes I'm trying to fix, so although it seems cruel to double the punishment if I do one of the above and submit, it's to reinforce that these mistakes are costly. Besides the core of right idea, AC, and WA/TLE/MLE, you can adapt this scoring system however you'd like to focus on what you want to. Some ideas include -1 

## Customization

### Speed

I personally think that speed comes naturally with high accuracy in thinking and implementation, but if you want to penalize based on submission time some ideas are -1 for problems where you aren't one of the first x people to solve it or if you aren't in the first 10% of solves.

### 

You can really slap whatever you want on here, but to get you started, I've left some ideas here for expanding this. Let's say you want to focus on speed, maybe -1 for problems where you aren't one of the first x people to solve it or if you aren't the first 10% of solves. Maybe for some reason you have some debilitating, chronic disease that makes you unable to solve Bs in a timely fashion (completely relatable), maybe give a -1 for that too. Or maybe you figure out some better system that doesn't operate on this 10 point system, I'd love to hear your [ideas and modifications here]().


## Outro

As much as I love to talk smack about rating and how focusing solely on increasing rating is counterproductive, I still have a monkey brain which likes to see numbers and pretty graphs ticking upwards. Instead of focusing on short term rating gains by skipping contests where you see the name antonygrub as the coordinator, focusing on this point system just means working on your weaknesses for real long term rating gains. You can decide which of those is more important. Until next time, have a good arbitrary amount of time between my sporadic posts.