---
description: >-
  Enables you to deal with unavoidable complexities in manageable pieces during
  your refactorings
---

# Mikado method

Sometimes it is easy to see small improvements that can be made to the code and to see how these small improvements might eventually lead to the bigger design changes that we want, but there are often cases where _**making a large design change can seem impenetrable**_. 

Maybe we can see the long-term goal, but it’s not clear any one step we can take that will send us in the right direction. Likewise, we may be able to see various small improvements we can make, but _**we’re not sure if they will directly help with our ultimate goal**_.

## Different kinds of refactoring

### Bottom-up refactoring

Tackle a complex refactoring by thinking about aspects of the code :

* That makes the change difficult
* Try to address them one at a time

There could be assumptions that have propagated through the code base that would now be violated, and each one of those assumptions needs to be addressed to make the code more amenable to change. 

{% hint style="warning" %}
_**Maybe there are parts of the code base that are difficult to understand, making it unclear how to make the larger change. We’ll need to improve these parts to make dependencies clearer.**_
{% endhint %}

> With this approach, we only make changes which we know will not break anything.

We :

* Extract functions
* Slide statements
* Split loops
* Do any other micro-refactoring necessary to make the code easier to work with

If everything goes well, these small changes lead to other improvements, and our large design change starts to seem less daunting. We’ll eventually find that the code base is in a good enough state that our original desired change is now easy.

These are good goals, but like with any bottom-up approach, the risk is that _**a lot of time could be spent in ways that ultimately doesn’t help with the final goal.**_

### Big Bang Refactoring

{% hint style="info" %}
We do a little up-front planning to try to define the goal and a general approach, but instead of working out every detail, **we just make the most important changes first and try to fix everything that breaks**. 
{% endhint %}

Maybe we create a new class which has the kind of API we wished for. 

Then we try to move code from various places in our codebase to implement the new class and we change old code to use the new class. _**Everything doesn’t work on the first try of course.**_ 

With Big Bang Refactoring, it is expected that it is going to take a few iterations to get everything working again. Maybe functionality is missing from the new class that we didn’t initially realize needed to be there, so we add that. Maybe the new class needs to have access to certain data that we didn’t expect, so we provide ways to pass that data around. And of course, we made some mistakes along the way and we’ve introduced bugs, so we have to fix those, but eventually we chase down all the little problems and fix them and everything is working again. At least we hope.

#### There is a big risk with this approach

* The code may be in an unusable state for an indefinite period of time. 
* Making changes in one place leads to changes in others, which leads to changes in others.
* As we continue chasing down issues and making changes, we could start to get the feeling that maybe we made a mistake. 

Maybe this is harder than it should be, or maybe we should have taken a different approach. We may also find that we’ve introduced a bug that is difficult to reproduce. We are faced with a difficult decision. 

Should we try to make a course correction, partially reverting what we’ve done? Should we throw everything that we’ve done away and start over? Or should we press ahead in the hope that you’ll eventually be able to get code back under control? Much work could be wasted if we make the wrong decision.  


## The Mikado Method to our rescue

{% hint style="success" %}
The [Mikado Method](http://mikadomethod.info/) is a technique for **breaking up large refactoring tasks into smaller ones in a systematic way, such that the code is practically NEVER IN A BROKEN STATE**.
{% endhint %}

![](../../../.gitbook/assets/image%20%28151%29.png)

With this method we :

* Start like we are going for the Big Bang
  * Making a big change and dealing with the consequences
* Instead of fixing the unexpected side-effects that inevitably arise 
  * We stop, make a note of the issues we are running into
  * Then **undo** our changes
* Back to a code base that works
  * With some new knowledge

We have some additional insight into what is going to make this change difficult.

![](../../../.gitbook/assets/image%20%28150%29.png)

{% hint style="success" %}
_**FAIL FAST BUT SMARTLY**_
{% endhint %}

Now, with the code still in a good state, we can take the time to think about the issues we ran into. 

* What made these issues occur? 
* What could be done differently? 

#### Example of learning : 

* We realize that if certain logic was factored out and centralized, our main change would have been much easier.
* Perhaps we realize that if some hidden dependencies were made more explicit, then it would have been easier to make the change at a higher level.

This ultimately leads to a new refactoring decision. We are back to wanting to make a refactoring, just a more basic one. Perhaps this is still a large refactoring, where all the possible side-effects are unclear. 

{% hint style="info" %}
_"Enables you to deal with unavoidable complexities in manageable pieces." -_ **Tom Poppendiek**
{% endhint %}

This is where the Mikado Method starts to take form : 

* Applying the same principle again, _**we make the change and see what happens**_. 
* If there are issues
  * We make a note of the unexpected consequences and what we could do about them
  * Then we revert to the last working state

### A tree structure of refactoring

#### The root of the tree

It is the main change that we wanted to make. 

#### Children

The immediate children are the changes necessary to make the root change easy. 

#### Grandchildren

The grandchildren are the changes necessary to make the child changes easy, and so forth.

#### Leaf nodes of the tree

* Atomic refactoring steps that we can take
* Are easy and quick steps that have no side-effects

Applying the leaf refactoring and pruning them from the tree, new leaf changes are revealed. 

These leaf changes should now have become easy atomic refactoring themselves. If we continue this process, we eventually end up back at our root change. The root change is the reason we set this whole process in motion, but it is now itself an easy change, and we are done.

![](../../../.gitbook/assets/image%20%28156%29.png)

### Advantages

* Incremental process
* Lightweight
  * Goal focus
  * Do only the necessary
* Visibility
  * Everyone can see what happens and its status
* Stability
  * You are never in an unstable state
* Continuous deployment
  * Always deliverable from the main branch
  * No more merging hell
* Learning
  * Fail fast but smartly
  * Learn as soon as possible and revert
  * Define your plan based on real life
* Visualization
  * Easy cooperation

## To go further

* [Mikado Refactoring with C++ Feature Macros](https://www.fluentcpp.com/2020/01/24/mikado-refactoring-with-c-feature-macros/)
* [Mikado method website](http://mikadomethod.info/)
* [Mikado method book](https://www.manning.com/books/the-mikado-method)
* [Kata in java](https://github.com/mikadomethod/kata-java)
* [Make Testing Legacy Code Viral: Mikado Method and Test Data Builders](https://philippe.bourgau.net/make-testing-legacy-code-viral-mikado-method-and-test-data-builders/)





