---
layout: post
title: The 5 Ws and 1 H of Code Reviewing
categories: [Process]
tags: [code reviews, pull requests, reviewing]
---

Code reviews are hard. Whether you have a large team, a small team, a new team or an old team, getting code reviews right is, in my opinion, one of the hardest things about programming processes. I could write for a long time about various different tooling and methodologies for assisting the code review and pull request process. This, however is not what this article is about. Instead I'll be discussing what you can do as a developer when you're assigned a code review.

## The origins of this train of thought

Recently I was asked by a colleague "How can we improve our code review process?". During that conversation I described my experience reviewing a recent pull request. This pull request was a fairly harmless move of some utility functions, and the associated import updates that come with the move. There was nothing to suggest from the updates I could see in github that there would be any issues. We're just moving files around. No big deal. LGTM.

It was only when this branch was merged with another, and the approval was reset that I stopped and asked myself the question "Why was this change being made?". It was from that point that led me on a path of discovery about the code that was being changed. I remarked to my colleague that this moment of asking myself "Why?" was part of a personal goal of trying to improve my own approach to reviewing code. It was at this point that I said it was somewhat akin to the 5 Ws and 1 H I learned in school:

- Who
- What
- Where
- Why
- When
- How

That meandering train of thought was what eventually led me to write this.

The below is not an official framework or mindset to rush to implement in your team tomorrow. Hopefully, it is instead a way of looking at how to approach a code review, and the various aspects we can all improve on. There are always going to be more specific questions depending on how your team works and with what technologies, so I'll try to keep it as generic as possible.

## The 5 Ws and 1 H

> I've ordered the list loosely around what I assume people usually consider. Towards the bottom of the list is a little uncertain and could be in a different order from what I have assumed. I'm not actually basing this off of any hard numerical data and each developer may have their own order for these.
{: .prompt-info }

### How

We're starting out with everyone's favourite, and the "H" of our 5 Ws and 1 H.

- How is the change implemented?
- How is the performance?
- How is the reusability?
- How is the documentation?
- How is the test coverage?

These are all fairly common questions we ask ourselves when looking at a code review. As developers we're drawn to the technical implementation of changes, and as such these are the kinds of questions that regularly get asked and addressed in code reviews.

### What

- What is the change?
- What are the acceptance criteria?
- What is the potential impact?
- What needs to be tested?
- What should be included in this change?

This is the first step in taking in a wider perspective and context for the change. Checking what the linked acceptance criteria are and comparing those against what code was changed can help us understand the scope of this change. At this point we can also apply business specific knowledge we may have to determine that the code that is being changed will change the correct feature or features.

A number of these questions could have already been answered, and in a perfect world this information should be in the linked work item. Getting up to speed in this section could be as easy as having a quick read of the work item, and PR description. If you don't answer all the questions you had at this point, having a chat with the developer who asked for the code review is probably a good next step!

### Why

- Why is this change being made?
- Why has this been refactored?

Asking why changes have been made is one of the questions I think we should be asking ourselves before actually delving into how those changes were made. Sometimes code reviews contain changes that from a code quality standpoint make sense, and seem harmless, but for some other reason isn't appropriate. If we can answer this question first before looking into how a change was made, we could save ourselves some time!

### Where

- Where should these changes be?

For such a short question, we have so many possibilities. Is the code in the correct file? Does it need to be extracted to a new function, or file? Is the code being executed in the right location? Should it be in the browser, or back end? If we're doing validation, what level of the stack should it be done in?

### Who

- Who would be good to ask about this change?

In this wonderful world of agile we're living in, we don't often have set people required to review certain code. This, generally speaking is a good thing to aspire to do. We should be spreading application and technical knowledge within our teams to a point where everyone has the knowledge and confidence to review changes. However, sometimes there is a team member with more specific knowledge about an implementation or business logic used in certain features. Getting their input for a change could pay off in the long run.

This doesn't mean throwing this review over to another person and forgetting about it. Instead, try asking for feedback about a certain topic for aspect of the code. Not overwhelming certain team members with all of the code review load is very important too!

### When

We've reached the bottom of the list, and admittedly, to fit with my format, this one might be a bit of a stretch. Most likely the answer to this question will always be "yes", but still it takes very little time to think about this, and could save a lot of time in the future.

- When should we make this change?

Determining when a change should be made is a matter of forward planning. Are we changing or refactoring something that will be soon replaced by a different technology? Can we avoid having to do duplicate work in this area?

## Conclusion

Looking at the above list, I think that there's a way we can more effectively approach pull requests by changing the order in which we consider things.

1. What - Understand what the change is about
1. Why - Determine why this change is being made in this way
1. Where - Ensure this is the right place for these changes to be made
1. When - Think about if this is an appropriate time to make this change
1. How - Check that the code has been implemented in a correct, maintainable way
1. Who - Ask yourself if this would benefit from an additional check by someone with more specific knowledge

By using this mental checklist we can ensure we're not only reviewing the code itself, but also looking at the wider context of the changes being made.
