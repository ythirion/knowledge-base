---
description: Maude Lemaire
---

# Refactoring at Scale

## Pitch

![](../../../.gitbook/assets/image%20%28620%29.png)

Making significant changes to large, complex codebases is a daunting task--one that's nearly impossible to do successfully unless you have the right team, tools, and mindset. If your application is in need of a substantial overhaul and you're unsure how to go about implementing those changes in a sustainable way, then this book is for you.

Software engineer Maude Lemaire walks you through the entire refactoring process from start to finish. You'll learn from her experience driving performance and refactoring efforts at Slack during a period of critical growth, including two case studies illustrating the impact these techniques can have in the real world. This book will help you achieve a newfound ability to productively introduce important changes in your codebase.

## Notes

### Chapter 1 : Refactoring

* What Is Refactoring?
  * Process by which we restructure existing code \(the factoring\) without changing its external behavior

![](../../../.gitbook/assets/image%20%28621%29.png)

Refactored version

![](../../../.gitbook/assets/image%20%28619%29.png)

* What Is _**Refactoring at Scale**_?
  * One that affects a substantial surface area of your systems
    * Typically \(but not exclusively\) involves a large codebase \(a million or more lines of code\)

      powering applications with many users
  * About identifying a systemic problem in your codebase
    * Conceiving of a better solution
    * Executing on that solution in a strategic, disciplined way
  * To identify systemic problems and their corresponding solutions :
    * need a solid understanding of one or more broad sections of an application
    * need high stamina to propagate the solution properly to the entire affected area
* Benefits of Refactoring
  * 2 majors :
    * Increased developer productivity
    * Greater ease identifying bugs
* Risks of Refactoring
  * Serious Regressions : with every change, large or small, we disrupt the equilibrium of the system in a measurable way
    * Might lead to unanticipated regression
  * Unearthing Dormant Bugs
  * Scope Creep : 
    * The larger the surface area of the planned refactor
    * the more problems you’ll encounter that you likely haven’t anticipated
    * Keeping to a well-defined plan
* WHEN to refactor ?
  * Small Scope
    * When looking to refactor a small, straightforward section of well-tested code,
    * Should be very little holding you back
  * Code Complexity Actively Hinders Development
    * Every time we read over the code our brows furrow, our hearts pound, our neurons start

      firing
  * Shift in Product Requirements : can frequently map to drastic shifts in code
  * Performance
  * Using a new Technology
* WHEN NOT TO refactor ?
  * For Fun or Out of Boredom : _"Is it the most important thing you could be doing right now?"_
  * Because You Happened to Be Passing By
  * To Making Code More Extendable :  rewriting code for the sake of future malleability is likely unwise
  * When You Don’t Have Time

### Chapter 2 : How code degrades

{% hint style="success" %}
a high level of vigilance over the state of the codebase and any external influences is key to minimizing setbacks and ultimately ensuring a smooth path to the finish line.
{% endhint %}

* _Code has degraded when its **perceived utility has decreased**_
* 2 ways in which code can degrade either :
  * The requirements for what the code needs to do or how it needs to behave have changed,
  * Or your organization has been cutting corners in an attempt to achieve more in a short

    period
* We refer to these as “requirement shifts” and “tech debt,” respectively
* **Requirement shifts** : Scalability, Accessibility, Device Compatibility, Environmental changes, External Dependencies, Unused code, Changes in Product Requirements
* **Tech Debt** : Working around Tech Choices, Persistent Lack of organization, Moving too quickly

_Part 2 : Planning_

### Chapter 3 : Measuring our Starting State



