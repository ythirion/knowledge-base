# Code Review

## Connection - 10'

* Describe what are your objectives when you review peer’s code ?
* How do you do it ?
* Share in pair

## Concepts - 10'

![](<../../.gitbook/assets/image (502).png>)

### How to do it ?

* Don't review anything that we can automate
  * Spell check
  * Code beautifier
* Small batches
  * No more than 200 to 400 lines of code (LOC) at a time
  * Brain cannot process and detect errors if too much data
* At least two developers sitting together
  * Junior Dev should pair with a more experienced one
  * Whole team when the feature is risky or complex

### Who ?

* Everyone code can be reviewed
  * Any Dev can review
  * The code of the most senior is also reviewed
* The reviewer&#x20;
  * should be :
    * Humble
    * Give feedback
    * Don’t blame
  * Need to get knowledge of the functional analysis
  * Checkout the code on his/her workstation and run it

### When ?

* Could be on-demand
* Or, if the CI quality gate not passed
* And anyway, before a story can be considered “Done”

### Why ?

* Better code
  * Ensure code meets standards
  * Find bugs
  * Ensure code does what it’s supposed to
  * Check code is understandable
* Share Knowledge
  * Spread code Ownership
  * No better way to learn the right practices and promote the company’s code guidelines and requirements
* Collaborate on Design
* Improve communication inside the team
  * Every team members talk to each others
  * Foster companionship and improve team cohesion
* Motivate to progress
  * If you keep in mind that your code will be reviewed by some colleagues, you will put more care into it
  * You will take the time to properly :
    * Name identifiers
    * Write tests
    * Introduce well-fitted abstractions&#x20;
    * Use carefully the enterprise wide patterns

### Different Workflows

#### [Gateway review](https://blog.jetbrains.com/upsource/2017/01/18/code-review-as-a-gateway/)

A developer :

* Picks up or is assigned a task
* Implements the code to the best of his/her ability
* Submits it for review

The reviewer checks the code and, if everything is OK : the code is merged into the main development branch.

![](<../../.gitbook/assets/image (505).png>)

#### [Knowledge Sharing](https://blog.jetbrains.com/upsource/2017/03/14/code-review-for-knowledge-sharing/)

* Learning at the center of the process
* The purpose is not to check if the code is correct
* But to share with other developers what changes have been made

![](<../../.gitbook/assets/image (506).png>)

#### Early Design Feedback

* A collaborative and iterative approach to&#x20;
  * Check the code frequently while it’s being built
  * So design feedback comes at the right time

![](<../../.gitbook/assets/image (507).png>)

### Anti-patterns (List from Trisha Gee)

* My job as a Reviewer is to find problem
  * When you try to find problems, you will always find more problems
  * Always remember that you bring you own preferences / biases
* Nit picking
  * Spacing is wrong / Formatting
  * Automate this kind of check
  * Waste of time for a human
* Design changes when the code works
  * You find it too late
  * Design must be discussed early on
* Inconsistent feedback
  * Feedback biased because I have followed a security training
  * Next week it will be on compliance for example…
  * To avoid this :
    * Have clear guidelines
    * Use checklists
* The Ghost Reviewer
  * No time for it
  * _**The bigger the code review, the more likely it will receive a green check**_
* Ping Pong Reviews (Between reviewer and author)
  * Happens when you goal is to find problems
  * Have a Definition of Done
  * Clear guidelines

### Use a checklist

![](<../../.gitbook/assets/image (503).png>)

#### Example

* [ ] **Compliance**
  * [ ] With internal tech radar (Lombok, MapStruct, ..)&#x20;
  * [ ] Right version of the libraries (Java 8)
  * [ ] Pass internal automatic quality gates&#x20;
* [ ] **Operability**
  * [ ] Exceptions are easily understood
  * [ ] Logging give context for debugging
  * [ ] Configuration is separated from the code
* [ ] Is the code **readable**
  * [ ] The names covey **intent**&#x20;
  * [ ] APIs are documented
* [ ] Is the code **SOLID** ?
  * [ ] Team **conventions** are followed
  * [ ] There is **no obsolete code**/function
  * [ ] There is **no commented out code** or TODOs&#x20;
  * [ ] Use of design patterns when appropriate (modularity, simplicity, ..)&#x20;
* [ ] Is the code testable ?
* [ ] Do the tests
  * [ ] Cover requirements
  * [ ] Cover confusing / complicated and limits of the code
  * [ ] Checks the performance

## Concrete Practice - Code vengers 30'

* Form groups of 3
* Each team member take :
  * A role card : _**keep it secret**_&#x20;
  * A checklist
  * A code sample
* 5’ in solo :
  * Prepare a code review as a code-venger : role-play based on your role card.
* Review time :
  * Each member explains his/her discovery in the code to the two others.
  * They have to guess who is the code-venger
    * And keep note how they feel during the review

#### Here are the cards

![](<../../.gitbook/assets/image (508).png>)

{% file src="../../.gitbook/assets/code-review-cards.pdf" %}
Download pdf cards here
{% endfile %}

{% file src="../../.gitbook/assets/code samples for code review.zip" %}
Code samples for code reviews
{% endfile %}

### Debriefing round 1 :

* Who was who in your group ?
* How did you feel during feedback session ?

#### Explain things to avoid during code review

![](<../../.gitbook/assets/image (509).png>)

* Judgmental questions :
  * Avoid to say : Why didn’t you just do \_\_\_ here?
  * Try it : What do you think about \_\_\_, which has the benefit of\_\_\_\_?
* Being sarcastic
  * Avoid to say : Did you even test this code before you checked it in
  * Try it : This breaks when \_\_\_. Can you please address this case?
* Passing off opinion as fact
* Avoid to say : This component should be \_\_\_.
* Try it : Since this component \_\_\_, it could be made \_\_\_. This will improve\_\_\_

### Lets do a second round

* Prepare once again the review of the code by being yourself
  * Try to avoid behavior sentences explained before

## Conclusion - 10'

* Bootstrap your team check-list
  * What / When to review ?

#### Don’t let code reviews be an ego match

{% hint style="success" %}
_**“Being the most senior person on the team does not imply that your code does not need review...”**_
{% endhint %}

### Resources

* [Code Review Best Practices by Trisha Gee](https://blog.jetbrains.com/upsource/2018/08/30/code-review-best-practices/)
* [Code Review Worflows](https://blog.jetbrains.com/upsource/tag/code-review-workflows/)
* [Code Review Guidelines by Patrick Smacchia](https://blog.ndepend.com/what-is-code-review-guidelines-best-practices/)
* [Ebook "What to look for in a code review"](http://jb.gg/book/codereview)
* [Video](https://youtu.be/3pth05Rgr8U)
