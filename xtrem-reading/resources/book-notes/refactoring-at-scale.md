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

{% hint style="info" %}
Quantifying the impact of refactoring motivated by performance is often the easiest
{% endhint %}

#### Measuring Code Complexity

* **Halstead Metrics \(1975\)** : counting the number of operators and operands in a given computer program
  * **Operators** are constructs that behave like functions, but differ syntactically or semantically from typical functions. 
    * These include arithmetic symbols like - and +, logical

      operators like &&, comparison operators like &gt;, and assignment operators like =
  * **Operands :** any entities we operate on, using our set of operators
  * He proposed a set of metrics to calculate a set of characteristics :
    * _Program’s volume_ : or how much information the reader of the code has to

      absorb in order to understand its meaning.

    * _Program’s difficulty_ : or the amount of mental effort required to re-create the

      software; also commonly referred to as the Halstead effort metric.

    * _The number of bugs_ you are likely to find in the system.

![](../../../.gitbook/assets/image%20%28624%29.png)

* **Cyclomatic Complexity \(1976\) :** _****_it is a quantitative measure of the number of linearly independent paths through a program’s source code
  * Essentially a count of the number of control flow statements within a program
  * This includes _if_ statements, _while_ and _for_ loops, and _case_ statements in side

    switch blocks

![](../../../.gitbook/assets/image%20%28627%29.png)

* **NPath Complexity \(1988\) :** Nejmeh asserts that _**not all control flow structures are equal**_; some are more difficult to understand use properly than others

  * For example, a while loop might be trickier for a developer to reason about than a switch statement.
  * Nesting can influence the psychological complexity of the function
  * Psychological complexity can have a large impact on our ability to maintain software

  quality

  * The calculation is recursive and can quickly balloon

* **Lines of Code :** Control flow graph metrics can be difficult to calculate
  * Program size can help us locate likely pain points in our application
  * If we’re looking for a pragmatic, low-effort approach to quantifying the complexity of our code, then size-based metrics are the way to go
  * _LOC \(lines of code\) per file_ : capture the psychological overhead required to

    understand their contents and responsibilities when a developer pops them open

    in their editor.

  * _Function length :_ Measuring the length of functions or methods within your application can be a helpful way of approximating their individual complexities.
  * _Average function length per file, module, or class :_ Knowing the average length of the smaller logical components contained within it can give you an indication of the relative complexity of that unit as a whole.

#### **Test Coverage Metrics**

Whatever our approach, the desired outcome ****is the same: a new feature, fully backed by a quality set of tests

* We can evaluate test coverage in two ways: quantitatively and qualitatively
  * **Quantitatively** : calculate a percentage representing the proportion of code that is executed when the test suite is run against it
    * We can collect metrics for both the number of functional lines of code and the number of execution paths tested
    * _test coverage alone is not an indication of how well-tested something is_
  * **Qualitatively :** suitable test quality has been attained if the following points hold true:
    * The tests are _**reliable**_. From one run to the next, they consistently produce passing results when run against unchanged code and catch bugs during

      development.

    * The tests are _**resilient**_. They are not so tightly coupled to implementation that

      they stifle change.

    * _**A range of test types exercise the code**_. Having unit, integration, and end-to-end

      tests can help us assert that our code is functioning as intended with different levels of fidelity.

#### **Documentation**

* _Formal Documentation_ : everything you most likely think of as documentation
  * We can use things like technical specs as evidence that our refactor is necessary or useful by referencing design decisions, assumptions, or other designs considered or

    rejected.
* _Informal Documentation_ : 
  * _Chat and email transcripts_ : can provide insightful information about the code you’re

    seeking to refactor

  * Bug Tracking system
  * Project Management System

#### Version Control

* _Commit Messages_ : set of keywords or by isolating commit messages associated with changes to a set of files we’re interested in
* _Commits in Aggregate_ : ref Software Design X-Rays
  * _Change frequencies_ : are the number of commits made to each file over the complete version history of your application
  * Code authorship

#### Reputation

A simple, low-effort means of collecting reputation data is to interview fellow developers :

![](../../../.gitbook/assets/image%20%28628%29.png)

#### Building a complete Picture

I recommend picking one metric from every category :

* Generate some test coverage metrics to make sure you start off on the right foot
* Identify a source of formal documentation you can use to illustrate the problems your refactor aims to solve; back it up with some informal documentation as well. 
* Gather information about your hotspots and programming patterns by slicing and dicing version control data. 
* Consider the code’s reputation by chatting with your colleagues

### Chapter 4 : Drafting a Plan

* Defining your end state : Our execution plan should clearly outline all starting metrics and target end metrics

{% hint style="info" %}
Feel free to provide both an ideal end state and an acceptable end state. Sometimes, getting 80 percent of the way there gives you 99 percent of the benefit of the refactor.
{% endhint %}

![](../../../.gitbook/assets/image%20%28622%29.png)

* **Mapping the Shortest Distance :** a few alternatives
  * Open a blank document :
    * For 15 to 20 minutes : write down every step you can come up with
    * Set the document aside for at the very least a few hours \(ideally a day or two\)
    * Open it up again and try to order each step in chronological order
  * _Gather a few coworkers_ who are either interested in the project or you know will

    be contributing

    * Set aside an hour or so : grab a pack of sticky notes and a pen for

      each of you

      * For 15 to 20' \(or until everyone’s pens are down\), write

        down every step you think is required, each on individual sticky notes

      * Then, have a first person lay out their steps in chronological order
      * Subsequent teammates go through each of their own sticky notes and either :
        * Pair them up with their duplicates 
        * or insert them into the appropriate spot within the timeline
      * Once everyone’s organized all of their notes :
        * Go through each step
        * Ask the room whether they believe that the step is absolutely required in order to reach the goal
        * If not, discard it
      * The final product should be a reasonable set of minimal steps
      * Final output of the exercise should be a written document that is easy to distribute and collaboratively improve
* **Identifying Strategic Intermediate Milestones** : 
  * 1\) Does this step feel attainable in a reasonable period?
  * 2\) Is this step valuable on its own?
  * 3\) If something comes up, could we stop at this step and pick it back up easily later?

![](../../../.gitbook/assets/image%20%28625%29.png)

* **Choosing a Rollout Strategy** :
  * One of the key success metrics is that _no behavior has changed_
  * **Dark Mode / Light Mode** : We can compare pre-refactor and post-refactor behavior by employing what we’ve coined at Slack as the light/dark technique
    * Dark mode : 
      * Both implementations are called
      * The results are compared
      * The results from the **old implementation are returned**
    * Light mode :
      * Both implementations are called
      * The results are compared
      * The results from the **new implementation are returned**
    * **How To ?**
      * Once the abstraction has been properly put in place
        * Start enabling dark mode
          * Monitor any differences being logged between the two result sets
          * Track down and fix any potential bugs in the new implementation causing those discrepancies
          * Repeat this process until you’ve properly handled all discrepancies,
        * Enabling dark mode to broader groups of users
        * Once all users have been opted in to dark mode
          * Continue logging any differences in the result sets
          * Continue to opt broader groups of users into light mode, _**until everyone is successfully processing results**_ from the new implementation.
        * Disable execution of both code paths
        * Remove the old logic altogether : only the new implementation

          should remain
    * **Cons :** If the code you are refactoring is performance-sensitive, and you’re operating in an environment that does not enable true multi-threading \(PHP, Python, or Node\), then running two versions of the same logic side by side might not be a great option
* **Cleaning Up Artifacts**
  * No refactor is complete unless all remaining transitional artifacts are properly cleaned up. 
  * _**Examples**_ : Feature Flags, Abstractions, Dead Code, Comments \(TODOs\), Unit Tests \(duplicative ones\)
* **Referencing Metrics in your Plan**
  * To support the initiative, not only does your problem statement need to be convincing with clear success criteria
  * Your proposal also needs to include definitive progress metrics
    * Showing that you have a strong direction should ease any concerns they might have about giving the go-ahead on a lengthy refactor.

![](../../../.gitbook/assets/image%20%28623%29.png)

* **Estimating**
  * Simple technique :
    * Go through each of the milestones and assign a number from 1 to 10
    * where 1 denotes a relatively short task
    * 10 denotes a lengthy task
  * The larger the software project, the greater the chance something won’t go quite to plan
* **Sharing Your Plan with Other Teams**
  * Large refactoring projects typically affect a large number of engineering groups
  * Brainstorm with your team \(or a small group of trusted colleagues\) to make sure you’ve covered a variety of disciplines and departments
  * 2 primary reasons : 
    * Provide transparency
    * Gather perspective on your plan to strengthen it

### Chapter 5 : Getting Buy-In

* Why Your Manager Is Not Onboard ?
  * Managers Aren’t Coding
  * Managers Are Evaluated Differently
  * Managers See the Risk
  * Managers Need to Coordinate
* Strategies for Making a Compelling Argument \(With our Manager\)
  * First, have an initial investigatory conversation :
    * It helps you understand which factors are weighing most heavily on your manager
    * It gives you a sense of whether your manager might be more readily convinced by an emotional or logical argument
    * This conversation will give you the preliminary context you need to choose the most effective strategies to convince your manager
    * **HOW TO ?**
      * 1 to 1 conversation
      * _"I’ve been thinking about how X is affecting our ability to do Y and I wanted to know whether you had any thoughts about it.”_
  * _AFTER THAT_

#### 4 persuasion techniques

* **Using Conversational Devices**
  * Compliment their thought process
    * Very few of us are immune to flattery, your manager included
  * Present the counter-argument :
    * A few benefits to presenting
      * Demonstrating your thoughtfulness and thoroughness around the effort
      * You’re reaffirming your manager’s concerns
        * Confirming that their apprehension is legitimate
    * Your manager will be more open to hearing about your ideas if they feel that their own ideas are well understood
* **Building an Alignment Sandwich**
  * Do it by securing the support of your teammates
  * Along with the support of upper management
  * sandwiching your manager between the two
* **Relying on Evidence**
  * If your manager is partial to logical arguments :
    * Use the evidence you gathered in Chapter 3 to bolster your position
* **Playing Hardball**
  * If you are exceedingly confident that your refactor is critical to the business and your manager is unwilling to budge
    * Stop doing unrewarded maintenance work
    * Giving an ultimatum
      * If all else fails, you can suggest to your manager that if they continue to oppose the

        refactor, you’ll either transfer to another team or outright quit the company.

{% hint style="info" %}
**Rewarding Refactoring**

_No engineer should be told that refactoring is equivalent to career suicide; instead, work with engineering promotion committees and human resources to include \(and encourage\) code maintenance. \(requiring managers to include maintenance efforts in their quarterly planning\)_
{% endhint %}

### Chapter 6 : Building the Right Team

* To execute on a large refactoring effort successfully, we need our own Ocean’s 11
  * Assembling a team just the right size with just the right skills
  * they cut down on their execution time and increased their chances of success

