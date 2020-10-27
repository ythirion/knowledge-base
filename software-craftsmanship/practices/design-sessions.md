---
description: A technic to better design solutions in a collaborative way
---

# Design sessions

When I was fully in Dev Teams it is a practice we used to define the implementations of our features. It consists in brainstorming and aligning at the beginning of each feature implementation.

### How to ?

![](../../.gitbook/assets/image%20%28409%29.png)

Once a team member wants to open a new Product Backlog Item, User Story or feature implementation, we do an instant meeting in front of a whiteboard and a computer.

![](../../.gitbook/assets/image%20%28414%29.png)

* We start by agreeing on its definition
* Be sure we are all aligned on what needs to be done

![](../../.gitbook/assets/image%20%28411%29.png)

We use the whiteboard to align ourselves on the different flows to implement

![](../../.gitbook/assets/image%20%28408%29.png)

* We open the source code or create a new one and start designing the contracts :
  * From our external layers \(APIs for example\) to our Domain model
  * POCOs / POJOs
  * DTOs / Commands
* We don't implement anything except of the contracts
  * We throw exceptions `throw new NotImplementedException()`
* BUT we agree on the naming / parameters
  * We put TODOs in the code to be clear what is expected to implement
  * Later on I have learned that this TODO approach to implementation had a name : [Puzzle Driven Development](https://www.yegor256.com/2010/03/04/pdd.html)

![](../../.gitbook/assets/image%20%28410%29.png)

The whole team or part of it can now work on the implementation by knowing exactly what to do.

### Advantages

* Instant alignment feedback on what needs to be done
* Increased knowledge sharing
  * Quick up-skilling for new-joiners
* Better solution when designed collaboratively
  * "Alone we go faster together we go further"
* Save a lot of times
  * Avoid feedback loops \(in code reviews for example\) when no team alignment
* Reinforce the collective ownership feeling inside the team
* Help to shape a real team spirit as well
  * Everyone is involved at the beginning of everything

### Infography

![](../../.gitbook/assets/image%20%28412%29.png)

