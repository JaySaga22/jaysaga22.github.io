---
layout: essay
type: essay
title: "Smart Questions, Good Answers"
# All dates must be YYYY-MM-DD format!
date: 2015-09-08
published: false
labels:
  - Questions
  - Answers
  - StackOverflow
---

<img width="300px" class="rounded float-start pe-4" src="../img/smart-questions/rtfm.png">

## Is there such thing as a stupid question?

We’ve all heard the phrase, “There’s no such thing as a stupid question.” But anyone who's spent time in technical forums like StackOverflow knows that poorly phrased or lazy questions can frustrate those who are trying to help. In contrast, well-formed questions can result in valuable responses, benefiting not just the asker, but the entire community. The key is learning to ask “smart” questions, as described by Eric Raymond in How to Ask Questions the Smart Way. Let’s look at two examples from StackOverflow—one that follows these principles and one that doesn’t—to illustrate the difference.


## What’s a smart question?

One example of a smart question comes from a user who was struggling with memory management in C++ smart pointers. They clearly explained their issue, included relevant code snippets, and shared what they had already tried. This effort helped the community understand the problem and provide targeted solutions.
```
Q: C++ Smart Pointers and Memory Management Issue

I am using C++ smart pointers for memory management in my application. Here is the code snippet where I believe the issue lies:
[Code snippet here]
I am getting a segmentation fault when trying to deallocate memory. I have already checked for circular references but couldn’t find any. Could someone point out if there’s something I am missing or if there’s a better way to handle this?
```
This question is well-constructed. It provides context, specifies the problem, and includes an example of the relevant code, allowing others to engage effectively. The responses were detailed, offering explanations about weak pointers, along with alternative solutions to the issue. This exchange demonstrates that well-asked questions not only solve problems but also add value to the entire community by fostering deeper discussions.

```
A: You might be running into issues with circular references even if you haven’t detected them. A common strategy is to use weak pointers in cases where you suspect two objects might be referencing each other. Here’s an example of how to modify your code:
[Code snippet here]
```
The conversation was productive, and the user received actionable advice. More importantly, future users facing similar problems can refer to this thread for a clear explanation.

## The foolproof way to get ignored.

In contrast, a poorly phrased question typically lacks context and effort. Here’s an example where a developer asked for advice on optimizing a C++ program without providing the necessary details.

```
Q: How to optimize my C++ program?

I have written a C++ program that takes too long to run. How can I optimize it?
```
This question is too vague. Without any details about what the program does or which part is slow, it’s nearly impossible to offer specific advice. Unsurprisingly, the responses were unhelpful, with some users pointing out that the question was too broad.

```
A: You need to provide more information. What does your program do? What parts of it are slow? Have you tried profiling to see where the bottlenecks are?
```
By failing to provide necessary context, the asker not only frustrated potential helpers but also missed out on getting useful guidance. This example shows how a lack of preparation results in minimal engagement from the community.

## Conclusion

The comparison between these two examples highlights how essential it is to ask well-thought-out questions when seeking help from a technical community. Smart questions, as Eric Raymond advises, are specific, show prior effort, and provide enough detail to allow others to understand the problem quickly. This approach benefits everyone, leading to more meaningful answers and fostering a collaborative spirit.

On the other hand, vague or poorly framed questions waste time and lead to frustration. This exercise reinforces the idea that smart questions lead to smarter solutions and a more productive environment. So, if you want good answers, it’s worth the effort to ask the right way.
