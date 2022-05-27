---
description: Understand what is technical debt? and how to deal with it
---

# Technical debt workshop

This workshop is a 2 hours workshop you can run in your team during a retrospective or ad-hoc to align on  this concept.&#x20;

{% hint style="info" %}
This workshop is designed to be accessible to technical and non technical people as well
{% endhint %}

Here is the facilitation support :

## Connection : 3 words

![](<../.gitbook/assets/image (109).png>)

Ask to the participants :

1. In solo : Write down three words that you associate to the expression "Technical debt"
2. In pair :
   * Share your thoughts
   * Agree on a definition
3. All together :&#x20;
   * Share your thoughts
   * Agree on a definition

## Concepts

### What is Technical debt ?

> “Some problems with code are like financial debt. It's OK to borrow against the future, as long as you pay it off.” - Ward Cunningham

Technical debt describes what results when development teams take actions to expedite the delivery of a piece of functionality or a project which later needs to be refactored. In other words, it’s the result of prioritizing speedy delivery over perfect code.

#### Difference between Bad code & Technical debt

{% hint style="info" %}
_"Just because some code is bad doesn't mean it's technical debt. It's not technical debt unless we have to pay interest on it, and interest rate is a function of time" - Adam Tornhill in **Software Design X-Rays**_
{% endhint %}

### Symptoms

![](<../.gitbook/assets/image (111).png>)

* Accumulate bugs
* Add a new functionality will cost a lot of money : reduced velocity

### How do we create this debt ?

#### "We don’t have time!"

One thing we hear the most in teams is the lack of time as an explanation of technical debt creation :

* “No time to rethink the design of this class, just keep adding new stuff to it!”
* “I didn’t have time to write the unit tests”
* No time to think about how someone else will fix or extend the code
* …

#### Other causes

* **Poor Conception** : No time for architecture and design.
* **Poor Business understanding** : It is impossible to design something you do not understand...
* **Poor Scheduling / Underestimating** : No testing effort in estimations.&#x20;
* **Bad Development Practices** : Development team needs to have a set of practices and conventions so that there is a little or no significant difference in design and implementation from feature to feature.
* **Outdated Technology** : As technology evolves, software standards become higher every day : No technology watch, innovation time
* **No team rules / conventions**
* Only Michel knows this piece of code, no one else can update it (SPOF
* …

The technical debt creation can be deliberate or inadvertent. That's what Martin Fowler explains with the Technical Debt Quadrant :

![](<../.gitbook/assets/image (112).png>)

Read more about it here : [https://martinfowler.com/bliki/TechnicalDebtQuadrant.html](https://martinfowler.com/bliki/TechnicalDebtQuadrant.html)

### Some examples of technical debt

* **Source Code Formatting**&#x20;
* **Bad naming** : Source code is not understandable by anyone.&#x20;
* **Low/No Test Coverage** : Tests ensure that each part of the code is behaving the intended way.
* **Code duplication**
* **Lack of Modularity** : Some code sometimes serves different business logic. The more codes developers write, the more lack of modularity can bottleneck.&#x20;
* **Code Complexity** : Complexity can be measured in several different ways, but it measures the dependence and path length to perform an operation. A long path leads to complex code.
* **No automation** : Deployments and tests are done manually.

## Concrete practice : Dice of debt

Dice of debt is a serious game that demonstrates the importance of managing technical debt. It has been documented on the agile alliance website here : [https://www.agilealliance.org/dice-of-debt-game/](https://www.agilealliance.org/dice-of-debt-game/)

### How to play ?

#### Material

Everything is available here : [https://www.agilealliance.org/wp-content/uploads/2016/04/Dice-of-Debt-materials-AA-v2.pdf](https://www.agilealliance.org/wp-content/uploads/2016/04/Dice-of-Debt-materials-AA-v2.pdf)

#### Context

* You are a scrum team that rocks.
* Your mission : create the highest amount of new software value by the end of the project.
* You have a strong dead line : 10 sprints of 2 weeks.

{% hint style="danger" %}
Technical debt can reduce that value dramatically.
{% endhint %}

#### Rules

* Sprint = 1 turn
* You have a finite capacity in each sprint represented by **12 dice**
  * 8 dice to create new value (NV)
  * 4 dice for technical debt creation (TD)

You must run the technical debt dice at each turn.

#### Technical debt reduction measures

You can lower the burden of technical debt during the game by investing in some reducing tech debt measure :

* Continuous integration (CI)
* Test-driven development (TDD)
* Code review
* Increase test coverage

| Cost                                                                           | Benefits                  |
| ------------------------------------------------------------------------------ | ------------------------- |
| Each investment in a TD-reducing measure reduces your NV dice for a few turns. | Get the associated effect |

#### Scoring sheet

![](<../.gitbook/assets/image (113).png>)

#### Tracking sheet

![](<../.gitbook/assets/image (114).png>)

#### How to play ?

At each turn (x 10) , each team must :

* Choose a strategy (use the investment effort or no)
* Roll the NV dice
* Roll the TD dice
* Update the score sheet
* Update the tracking sheet
* Small retrospective
  * What do we need to adapt ?

## Conclusion

### Debrief the game with the participants

{% content-ref url="../serious-games/how-to-debrief-a-game.md" %}
[how-to-debrief-a-game.md](../serious-games/how-to-debrief-a-game.md)
{% endcontent-ref %}

### Explain what the trends are indicating

![](<../.gitbook/assets/image (115).png>)

### You will always face some Technical Debt

* Some amount is to be expected (Unintentional)
* The amount of technical debt will never be zero&#x20;

BUT it has to be **manageable**.

{% hint style="info" %}
We must build quality in by using great development practices
{% endhint %}

### How to manage it ?

Ask questions to the participants / small technical retrospective :

* Which examples of technical debt do you identify i our code base ?
* How do you materialize it in the backlog ?
* How can we improve the management of the technical debt ?&#x20;
* How could we reduce it ?
  * A concrete action that we could implement tomorrow

#### Measure things

We can easily measure things that can help us quantify our technical debt :

* **Functionalities** : Measure the performance of the system for each period of time (iterations) by measuring the number of functionalities (User stories) done / delivered.
* **Bugs** : Number of "stuff" to fix in the code : bugs, fixes.
* **Technical debt** : Number of refactoring or technical improvements identified by the team.
  * The definition of this measure can differ from one team to another and it’s fine. The only things is that this definition must be constant for the team.

![](<../.gitbook/assets/image (117).png>)

#### Use static code analysis tool

Tools like Sonar can give an idea on the health of your code base (some trends to follow). It calculates technical debt indicator :

![](<../.gitbook/assets/image (118).png>)

#### Make the debt visible

Create items in a backlog for everything that is identified and monitored by the team as a subject for refactoring or technical improvement.

#### Invest

Dedicate time to technical debt reduction and prevention.

#### Technical retrospective : Focus on the technical/architectural improvement

**Objectives** : Find technical improvement actions / prioritize technical items.

**Questions during those sessions** :&#x20;

* Where are the defects?
* Where are the 'hard bits' ? What makes them hard ?
* Where are the 'easy bits' ? What makes them easy ?
* What keeps changing ? Why ?
* Could we better quantify our technical debt ?
* ...

#### Apply the boy scout rule

{% hint style="info" %}
_“Always leave the code you’re editing a little better than you found it.”_ - Uncle Bob
{% endhint %}

![](<../.gitbook/assets/image (119).png>)

#### Use great development practices

There are a lot of them in [XP](http://www.extremeprogramming.org/)

{% hint style="info" %}
_“I'm not a great programmer; I'm just a good programmer with great habits.”_ - Kent Beck
{% endhint %}

Some of those practices :&#x20;

* Follow Clean Code rules
* Test Driven Development
* Static code analysis
* Pair/Mob programming
* Knowledge sharing
* Code review
* Mentoring
* Coding style guides
* ...

## To go further :

* Communicate the Effects of Technical Improvements to Non-Technical Stakeholders : [https://codescene.com/blog/communicate-technical-improvements-to-non-technical-stakeholders/](https://codescene.com/blog/communicate-technical-improvements-to-non-technical-stakeholders/)
* Culture code by Octo : [https://www.octo.com/publications/culture-code/](https://www.octo.com/publications/culture-code/)
