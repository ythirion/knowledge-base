---
description: Xanpan is an agile method created by Allan Kelly.
---

# Xanpan - a team centric agile method story

Allan has really done a great job by explaining it in his book “[_Xanpan — Team Centric Agile software development_](https://leanpub.com/xanpan)”.

![](https://miro.medium.com/max/180/1\*DJ_AHZVr14v2BqVptG0rzg.png)

It differs from other agile methods or frameworks because it’s the **team itself at the center of the method** (not a product nor a process).

In this article I won’t explain the entire method (to do so I invite you to read the book), I will focus on the elements that differ from what we can experiment with other agile methods.

![](https://miro.medium.com/max/2698/1\*cq30jF72WCQWaG8j0XU0MQ.png)

## What is it? <a href="182f" id="182f"></a>

As you have probably already guessed by its name, Xanpan is a mix of Kanban, XP (eXtreme Programming), Lean, Scrum and Product Management.

Everything in Xanpan is based on a simple but hard to use principle: **pragmatism**.

![](https://miro.medium.com/max/2698/1\*iTdW5YNjMFQr121Tjez78g.png)

The building blocks of Xanpan are:

* Work in iterations
* Team-centric
* Work to improve Flow
* Quality is free (invest in quality)
* Visualize

## Work in iterations <a href="57a8" id="57a8"></a>

Just like in Scrum, you will use iterations in Xanpan. An iteration is a 2 weeks period _**from mid-week to mid-week**_.

![](https://miro.medium.com/max/1116/1\*FXpSLy81R27\_R0h0M-82GQ.png)

Allan explains in his book that many studies have proven **people are more effective at the start of a new week**. So, the idea is not to start the week with meetings but to work on the iteration backlog.

At the end of each iteration, the team should have produced a releasable product.

### Why use iterations? <a href="9231" id="9231"></a>

Well, with the iterations the team defines **small deadlines that help to focus**, it avoids multi-tasking and so limits the work in progress naturally and improve efficiency.

## Planning <a href="9a5d" id="9a5d"></a>

### 3 roles <a href="9708" id="9708"></a>

There are 3 roles in the planning:

* _**Product Owner**_: this role is usually played by a product manager, or a business analyst acting as a proxy for the real customer
* _**Creators**_: software engineers and testers mainly, although sometimes others, such as user interface designers are involved
* _**Facilitator**_: sometimes there is a dedicated facilitator who is not the Product Owner or a member of the building team. They may be, for example, a project manager, Scrum master or Agile coach.

![3 roles in the planning](https://miro.medium.com/max/2231/1\*UolRlEpd49GlFZLA2lQC_w.png)

> _**Product ownership is considered a practice rather than a role.**_

### Planning artefacts <a href="ddf1" id="ddf1"></a>

The outcome of the planning is cards that will be fixed onto the team board (it’s the iteration backlog), **like in Lean cards are Blue, White and Red**:

* Blue cards: vertical slices of business functionality from multiple projects or products
* White cards: Tasks related to blue cards. Those are written during the planning meeting, and there are usually multiple white task cards for each blue card.
* Red cards: those are bugs, defects that need to be handled

Blue and white cards are estimated in points in Xanpan, to do that teams use planning pokers like in XP. Because of their unpredictable nature, Red cards are those “estimated” after having been completed.

Those cards are then used to setup the Team board (physical or virtual).

### Planning meeting <a href="7677" id="7677"></a>

This is how it is suggested to run the end of each iteration:

![](https://miro.medium.com/max/1557/1\*mweO-Bu4F_GBXQLpUdT_eA.png)

## Retrospective <a href="5542" id="5542"></a>

Retrospective could be formal or not (simple dialogue). It could be held at the end of the iteration routine or not. It could happen or not… At the end it’s a team decision.

> _“Teams may also hold a retrospective as part of the iteration end routine, although not all teams hold retrospectives, and even those who do may not hold them at every iteration.” — Allan Kelly_

## Work in routine <a href="23ce" id="23ce"></a>

Here is the recommended routine:

![](https://miro.medium.com/max/2698/1\*NRiBrTGabeAZeAJdRXZGFQ.png)

## Plan beyond the iteration <a href="5b30" id="5b30"></a>

Quaterly plan is a plan for the 12 next weeks, filled to approximately the capacity of each iteration (consider it as the WIP limit of the iterations). Quaterly plan is a rolling plan; it is in a constant — perhaps daily — state of flux.

Allan explains something fundamental and often forgot : **planning is not scheduling**.

Plan: looking into the future to learn about what might happen.

It helps to prepare a possible future (For it we can use technics like Design thinking for example).

## Where is the Kanban part in it? <a href="8603" id="8603"></a>

![](https://miro.medium.com/max/2698/1\*DvN4oneQ8NeOecbYc07P7Q.png)

From here, I have explained mostly mechanisms you may already know from Scrum (iterations, planning, …) but Xanpan is also a **Kanban-style flow**:

* It allows both planned and unplanned work
* Work can flow from iteration to iteration

The Work can flow because we really want Blue cards to bring value. Often **by splitting too much them to make them pass in a single iteration we do not produce any value.** The idea is to keep them big enough to truly bring value.

### What about commitment? <a href="ba4a" id="ba4a"></a>

> Teams are encouraged to try and do more work than they expect to do. Everyone needs to accept that not all work taken into the iteration will get done.

Statements about what will be delivered at the end of the iteration are statements of probability.

### Team centric <a href="4683" id="4683"></a>

![](<../.gitbook/assets/image (147).png>)

{% hint style="info" %}
In Xanpan, we admit than a team can work on multiple work streams at a time it is more realistic don’t you think?
{% endhint %}

### Visualise <a href="cfca" id="cfca"></a>

To organize our work in Xanpan we use a big board that represent the state of the team, not the state of a particular project or product.

![](<../.gitbook/assets/image (148).png>)

* Planned: stock of cards for the current iteration
* Unplanned: stock of unplanned work
* Priority: work for today. Defined the morning of the day during the stand-up.
* Work in progress
* Test: cards under test
* Done: work has been done & respect the Definition of Done

### Unplanned work <a href="6104" id="6104"></a>

Unplanned work does not mean there is no value to do it. That’s why the unplanned work is stocked on the board and will be prioritized by BA or Product manager a few minutes before the stand-ups.

## What about technical practices? <a href="cc4f" id="cc4f"></a>

For Allan Kelly teams that deliver software should really embrace XP practices. It enables to inject quality for free.

If we try to define what is a successful software it’s the one that needs rework because we will want to: add new features, change existing features, extend it, …

**Successful software lives and needs to change over time**. If software is not changeable, then it cannot change as it needs to during its lifetime, and it will be hard to remove any defects that are found.

Rework is really part of the lifecycle of a successful software. _**The question is how easy is the rework?**_

{% hint style="info" %}
_Low quality makes rework harder, and therefore slower. High quality makes rework easier, and therefore faster._
{% endhint %}

### How to define quality of a software product? <a href="f52a" id="f52a"></a>

* Measure defects: quality is inversely proportional to the number of defects seen in a system
* Measure the maintainability: software needs to be easy to change so measure cost of changes and its evolution in time.

### Practices <a href="4fdb" id="4fdb"></a>

To inject quality in, Allan recommends those technical practices:

![](https://miro.medium.com/max/2698/1\*yz5MyV_gd5g4IRHCI8iFYQ.png)

It is not an exhaustive list and every developers should complete it with all the practices that make sense in their own context.

Me I would add others like Domain Driven Design, Mob Programming, Property-based Testing, Event Storming.

## Experiment <a href="f733" id="f733"></a>

Xanpan is a hybrid method built from pieces of other Agile processes and elsewhere. Do the same and create your own “xanpan”.

> **“Create your own process, don’t follow someone else’s prescription.” — Allan Kelly**

## Just do it: action over words <a href="e2eb" id="e2eb"></a>

* Identify a practice, tool, technique, whatever from somewhere else
* Decide what it would mean to your team: what would you do differently
* Set a time frame
* Make the change
* At the end of the frame: check
* Decide to keep or drop

You can use the [Agile Pick’mix](https://blog.nimbleapproach.com/agile-pick-n-mix/) to find inspiration for experiments.

![](https://miro.medium.com/max/2698/1\*0ct99tsif1KxwwGY_p3Tew.png)

## Wrap up <a href="208a" id="208a"></a>

Xanpan is not a prescription.

{% hint style="info" %}
_"Xanpan is the kind of stuff that should emerge from every agile teams when not constrained by some “agile” dogms." - _Yoan Thirion
{% endhint %}

## To go further

* Buy the book from Allan Kelly here : [https://www.amazon.fr/Xanpan-Centric-Agile-Software-Development/dp/1291852735](https://www.amazon.fr/Xanpan-Centric-Agile-Software-Development/dp/1291852735)
* Agnostic agile : [https://agnosticagile.org/](https://agnosticagile.org)
* Heart of agile : [https://heartofagile.com/](https://heartofagile.com)
* Discover slides of my talk about it here :

{% embed url="https://speakerdeck.com/thirion/xanpan-une-methode-agile-hybride-centree-sur-lequipe" %}

* Here is the video of my talk about Xanpan @AgileEnLigne : 

{% embed url="https://youtu.be/nUkanfJjL-o" %}
