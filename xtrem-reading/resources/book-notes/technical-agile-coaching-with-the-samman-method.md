---
description: from Emily Bache
---

# Technical Agile Coaching with the Samman Method

## Pitch

Agile Coaching helps an organization to be more successful, by increasing agility. 

Samman Technical Coaching is **a kind of Agile Coaching that specializes in technical questions concerning how code is written**. It's an aspect of agility that is often glossed over, and can be crucial for success. This book explains the best method I know of to increase agility amongst software developers. You help them improve coding practices and how they collaborate. It's fun and challenging for the coach too.

_The first part of the method is working in an ensemble with development teams, programming in their production codebase. To complement this hands-on mentoring, the second part of the method is short daily "learning hour" sessions to practice particular techniques_. In this book you will learn about the Samman coaching method and how to do it in practice. From the details of daily coaching work to marketing your services and how to find a suitable assignment. It is a practical handbook for an aspiring coach and contains fresh ideas for an experienced coach looking for new ways of working.

![](../../../.gitbook/assets/image%20%28464%29.png)

## Foreword by Kent Beck

* "Software development is best seen as a learning process where running programs are the proof of ****learning, rather than a factory or production process. That’s the first idea I found in Samman."
* "Walking a new path together along with an experienced guide reduces time spent not learning because of fear. That’s the second idea."

## Introduction

### Samman Technical Coaching

* A method for people who want to make a difference and **improve the way software is built**.
* **Focus ?**
  * Specifically on technical practices 
  * How people write code
* **Foundation / prerequisite ?** 
  * Cultivate good relationships with the people you work with
  * The rest is about effective ways to learn from one another and to change behaviours for the long term.
* **2 main parts to the method :**
  * **Learning Hour** : ****the coach uses exercises and active learning techniques to teach the theory and practice of skills like Test-Driven Development and Refactoring
  * **Ensemble Working** : In the Ensemble sessions 
    * Whole team collaborates together with the coach in applying agile development techniques in their usual production codebase
* **Samman and Ensemble ?**
  * ‘Samman’ word describes this coaching method
    * “Samman” is a Swedish word that means “together”
  * “Ensemble” is a French word meaning “together”
* Why use those words ? \(no Mob for instance\)
  * to distinguish this method from other ways to do coaching and make it easier to search for on the internet

### **Why would an organization engage in Samman Technical Coaching ?**

{% hint style="info" %}
_To increase business agility and success if a company is building a software product, then the way people write code actually matters quite a lot._
{% endhint %}

* **Good technical practices** : mean the organization can build new features with a shorter lead

  time and higher quality

  * Meeting deadlines 
  * Deliver reliable software.

  _**This brings happier customers and a successful business.**_

* Skilled developers will want to work for an organization with high quality code, effective development practices and a healthy culture.
* The company needs to avoid drowning in technical debt. 
  * If it piles up too much developers will ultimately be unable to deliver any new features in a timely or cost effective manner. 
  * Serious risk for any business.

### Elevator pitch for Samman Technical Coaching

In order to be successful in modern development organizations, software developers need new skills. These skills are not easily learnt on a short training course or at a university. Practices like Continuous Integration and Test-Driven Development require developers to change their minute-by-minute habits and ways of working.

As with any new skills, the way to learn is through a combination of teaching and practice. The Samman method includes a series of short lessons called ‘learning hour’. The coach uses active learning techniques that are proven to be more effective than lectures. We work together on code katas and other exercises so developers both understand the new techniques in theory and experience them in carefully chosen examples.

The Samman coaching method is also on-the-job, together with developers in their usual situation. In order to change the way developers work it’s often not enough to only practice on code katas and learn theory. The coach works together with development teams in a structured collaboration called an ‘ensemble’. We learn how to apply relevant techniques in the actual production code the team works with daily.

### Day in the life of a Samman Technical Coach

![Sample agenda when coaching 2 teams](../../../.gitbook/assets/image%20%28467%29.png)

### Development techniques 

* _Better unit tests_
  * Developers should deliver a suite of automated unit tests together with the code they write. 
  * Tests 
    * Demonstrate each part of the code works as the authors intended
    * Documents their assumptions
    * Provide **a safety-net for refactoring and make maintenance less costly**
* _Continuous Integration_
  * Know the incremental design and refactoring techniques 
  * To be able to integrate often : avoid merge conflicts
* _Safe refactoring in legacy code_
* _Incremental and Iterative Development_
  * Many developers struggle to iterate the design of the code
  * Don’t know
    * Refactoring tools
    * Design patterns 
    * Signs to look for that

### Leveling up a whole team together

{% hint style="info" %}
_**Software development these days is a team sport and it doesn’t work to only train individuals. Samman coaching aims to create a whole-team culture shift.**_
{% endhint %}

* With Samman coaching
  * Build consensus about how the team wants to work
  * In the learning hours, discover :
    * What development could be like if we used **new ways / different ways** of working
    * Awareness about a different future is possible
* The coach helps them gain the skills needed to go there.

### Expected outcomes

* First step
  * Awareness of what 
    * Good unit tests look like
    * What continuous integration actually is
  * Possible to safely refactor code you don’t initially understand
* Next
  * Aim for the insight that successfully meeting deadlines 
  * Delivering high quality code means learning iterative and incremental development techniques
* Timeline ?
  * After 10-20 coaching days most teams will have reached those insights
  * These are the first steps on the road to improving the way that team works and the quality of the code they deliver
  * After that, it’s about 
    * Building skills and anchoring ways of working in habits and culture

### Measuring outcomes

* 1st thing to measure is attitudes
  * Simple survey should suffice to show that after the coaching developers are more enthusiastic about using these techniques
* Teams meeting deadlines more reliably
* Reductions in production bugs
* Fewer calls from despairing developers who want to re-write the whole system from scratch
* Observe increased productivity :
  * Really difficult to measure the productivity of software developers

## Part 1: Ensemble Working

> _“All the brilliant minds working together on the same thing, at the same time, in the same space, and at the same computer - We call it ‘Mob Programming’“ – **Woody Zuill**_

### Ensemble vocabulary

* Ensemble instead of Mob
  * The word “ensemble” implies
    * Friendly people collaborating
    * Like a group of musicians
  * Much better describe what this activity is actually like in practice than the word “mob” \(affiliated to gangsters\)
* “typist” instead of “driver”
  * Make it clear the person with the keyboard is not in charge of the direction the group takes

### Roles in the "Ensemble"

#### Typist

* Person who has the keyboard and mouse
* Use the development tools and operate the computer

{% hint style="success" %}
The important rule here is that you are **not allowed to decide what code to write or what tests to perform.**
{% endhint %}

* The typist **listens** carefully to everyone present, and most particularly to the navigator
* You enter the code the ensemble has decided on, to the best of your ability
* Ask questions to clarify what is wanted and ask for more detail

#### Navigator

{% hint style="success" %}
The navigator speaks for the ensemble and explains to the typist what code they should enter into the computer.
{% endhint %}

* Speak in words, out loud, explaining the development activities they have in mind 
* Give enough detail that the typist knows what to do
* Everyone in the group both :
  * Hears the navigator explain the work
  * Sees the typist do the work
* _**We are not used to talking about code in this way :**_ 
  * An inexperienced lead might say things like “public int foo parenthesis int bar close parenthesis” 
  * Maybe better : “define a function called foo. It takes one argument, an integer called bar”.
  * Remind that you are talking to a the typist, not to a computer

#### Team-members

{% hint style="success" %}
Everyone who isn’t the typist is a co-navigator in the ensemble. We all develop the software together.
{% endhint %}

* Lead the work
* Talking and making the detailed decisions
* Always feel free to ask questions so you understand the code that’s being written.

#### Facilitator

* Working as an ensemble is a _**skill that takes some time for a group to learn**_
* It helps to have a facilitator whose job it is to keep things working smoothly
* Usually someone 
  * Different from the typist or navigator
* The facilitator will spend time :
  * Reminding people of the working agreements
  * Making sure roles rotate regularly
  * Helping the ensemble to reflect and improve their work together

{% hint style="success" %}
As the ensemble gains experience the facilitator may need to intervene less often. It may become a part-time position or disappear altogether. 
{% endhint %}

#### Rotating roles

* Most ensembles have some kind of **timer** that alerts the group when it’s time to rotate roles

#### Other ensemble roles

_As well as typist and navigator, there are other roles that people can take as the need arises._ 

* Common one is “_**Researcher**_” : 
  * If the ensemble gets stuck because no-one remembers the exact syntax or library function to use
  * Someone can offer to research it
* Another useful role to have is “_**Archivist**_”
  * Can be helpful to have someone writing stuff down
    * Decisions the group makes
    * Alternatives we looked at
    * Designs

#### The Coach role

Coach can use this forum to promote better ways of working in the code.

### Let the Ensemble give you Superpowers

* You can spread 
  * Knowledge 
  * Ways of working to a team
* You can increase communication, and promote teamwork

{% hint style="success" %}
_**You learn as much from the team as they learn from you, and you can keep your technical skills sharp and and up-to-date as you continue to write code every day.**_
{% endhint %}

* Everyone understands the code
* Skills are multiplied
* Visitors are quickly contributors
  * Pick up loads of team norms and code details within minutes, almost without effort
* Joining a smoothly functioning ensemble
  * After a few hours you are working smoothly in the ensemble
  * You have **influenced** the code in many small ways
  * You have **contributed** some of what you know and learnt more about the struggles and challenges of this particular team.

### Coaching Behaviors in an Ensemble

* **Teach**
  * As well as prepared learning hours, you will sometimes teach in the ensemble sessions.
  * An ideal teachable moment might arise when you notice they need a particular technique
  * You can outline some theory
    * Go through some concepts
    * Then mentor them through using the technique straight afterwards
* **Mentor**
  * Where you help the team to :
  * Apply specific techniques in their codebase
  * Build their capabilities
* **Facilitate**
  * A facilitator conducts a process without having an opinion about the content.
  * In certain situations
    * Facilitation can be the best way to help the team to move forwards
* **Coach**
  * Work from the assumption that they have the answers within themselves
  * Your job is to help them to fulfill their promise
  * Key tool :
    * ‘coaching question’ : evokes action without telling them what you think the action should be.
* **Observe**
  * You may not need to intervene
  * If the ensemble is working well, your best strategy could be to stay in the background
  * **Observe the interactions and the code that is being produced**
* **Take Short Breaks**
  * Not need to be present all the time
* **Retrospect**
  * Around 15-25 minutes at the end
  * Preferably just after we made a commit
  * Spend some time reflecting on what happened
    * So they can realize consciously what they have learnt
* **Breathing space between and during sessions**
  * In the middle of a 2 hour session
    * Whole group take a 5 minute break

### Kindness, Consideration and Respect

{% hint style="success" %}
Adopt this golden rule : _**We treat everyone with kindness, consideration and respect**_
{% endhint %}

* Woody’s Legacy Code rule Honor : 
  * "_Honor the coder and their code. The constraints they endured are not mine to know."_
  * Assume they did the best they could with 
    * The knowledge they had
    * The circumstances they were in at the time
* Yes, and
  * Do not delete or undo what the previous navigators did before you
  * Refactor but do not rewrite
  * Say ‘Yes, and’ to whatever your colleagues give you.
* Too much thinking at the keyboard
  * Design should be spoken by the navigator before it is coded by the typist
* **I think &lt;name&gt; has a good idea we should listen to**
  * Listen to Everyone 
  * Sometimes you get good ideas being spoken but no-one pays attention
* Consideration means **paying attention**
  * Increase the rotation speed 
  * So they end up leading the navigating more often
* **Call out bad behavior that can’t wait until the retrospective**
  * A useful phrase is “we don’t do that here”

### Retrospectives

* Each ensemble session should be an improvement on the previous one
* You want to see 
  * Increasing collaboration
  * New skills being used
  * People feeling happier
* Prefer to bring up positive things that have happened that I liked and want to encourage
* **Turn up the good**
  * In circle and each person says one thing that happened in the session that was good
  * Encourage one another to behave like this again

## Part 2 : Learning Hours

* Short training sessions where :
  * People practice coding skills
  * Learn new techniques

{% hint style="success" %}
**When working with a team ensemble you’re primarily a mentor and facilitator. In the learning hour you’re more often acting as teacher and coach.**
{% endhint %}

* Why ?
  * For an organization to succeed in the modern world
    * It needs to be a learning organization
* Why should you spend a whole hour every day on learning?
  * Become more productive and happier
  * Everyone benefits!
    * Small increases in productivity 
      * Quickly add up to more than compensate the time you spent on the learning sessions.
  * With the right tools
    * Refactor easily and safely
* **As a software developer, learning is part of your job**
  * Always 
    * New tools and frameworks appearing that you should know about
    * Better designs and ways of working being invented
  * To remain competitive in a fast-moving world, **where you are being paid for knowledge-intensive**, skilled work
    * You must keep learning to stay relevant and useful
* **Who should come to the Learning Hour?** 
  * In the first place, invite the teams who you are coaching
  * Can have joint sessions depending on teams interests

### The Theory and Practice of Teaching and Learning

#### Learning Outcomes and Objectives

* What really matters about your training 
  * Is actually what happens afterwards
  * When people return to their desk
  * Will they be able to apply what they’ve learnt in a useful way?
  * **Start with the end in mind.** 
  * **What is the outcome you’re hoping to achieve?**

#### Bloom’s taxonomy

* Can describe thinking skills in terms of six broad categories: 
  * Remembering
  * Understanding
  * Applying
  * Analyzing
  * Evaluating
  * Creating
* There is an implied hierarchy and order of categories. 
  * For example ‘Remembering’ is easier to achieve in a student’s journey than ‘Analyzing’ or ‘Creating’

### ‘4C’ learning model

Check Sharon Bowman’s ‘4C’ learning model and her book ‘Training from the Back of the Room’.

* People are active participants
  * With their own goals and motivations to learn things
* When you plan a learning hour, you include activities for each of

  the 4C’s:

  * **Connect**: Get people in the right head-space for learning about the topic together.
  * **Concept**: Introduce the new skills or ideas or information you want the participants to learn.
  * **Concrete**: Hands-on exercises to practice skills or figure out how things work.
  * **Conclusions**: An opportunity for people to consolidate and internalize what they’ve learnt.

#### Design learning experiences that fit with how the brain works

* When teaching, it helps to understand how the human brain works
* Cognitive neuroscience is the study of how the brain 
  * Takes in
  * Stores
  * Retrieves and Uses information
* Some neuroscience learnings :
  * What you pay attention to is strongly affected by subconscious processes. \(ie out of your conscious control\)
  * What you learn is **filtered through emotions**
    * Stronger emotions are more likely to cause longterm memories to form. 
    * Content that evokes no emotion is less likely to be remembered.
  * **Physical movement improves brain performance** - the brain is part of the body, so increased oxygen in the blood helps it function better.

### Six ‘trumps’ to help remember useful rules about how the brain works

![](../../../.gitbook/assets/image%20%28468%29.png)

* Movement trumps Sitting
  * Learn more when you’re feeling awake
  * _**Incorporate movement into the content**_ of the training so that it doesn’t take much time
* Talking trumps Listening
  * _When you talk about what you just heard it reinforces your memory of it_.
  * Talking also gives opportunities for feedback 
    * From others about how well you seem to understand the topic
* Images trump Words
  * Images easily capture attention
  * **Telling stories that bring pictures into your mind has a similar effect**
  * Tell stories about a time you used a particular refactoring or design pattern
    * Better than only explaining the theory
* Writing trumps Reading
  * When you are writing you can’t think about anything else, _**it forces you to concentrate**_
  * Makes the information multi-sensory
  * Provide handouts, notes and quizzes that people can annotate
  * Ask people to write conclusions and observations on sticky notes
* Shorter trumps Longer
  * Divide your presentations into 10-20 minute chunks
  * In between spend at least 1-2 minutes on some other activity
* Different trumps Same
  * Anything new or unexpected will catch people’s attention
  * Emotions generally and surprise in particular
    * Help learning to stick
  * **Vary the format of your learning hours so that they are not too predictable**
    * Games
    * Simulations
    * Exercises

### Sample Learning Hours

A lot of great sessions are described in the book with plenty of great ideas :

* Incremental working, Driven by Tests
* Selecting and ordering test cases
* Make a test list
  * _**To try with the Option "game"**_
* Arrange - Act - Assert
* Inspirational Demo
* ...

{% hint style="success" %}
Each coach has their own perspective and background. Use what you know and put together your own learning hours. Look through your bookshelf and technical video collection. 
{% endhint %}

## Part 3: Samman Coaching Engagements

### Finding an Organization and Teams to Engage with

* The department striving for Technical Excellence
* The company struggling with defects
  * Root cause of defects is often 
    * Technical debt
    * Code hard to understand and change
  * In the company example :
    * Were spending about 50% of their developer effort on investigating and fixing defects
    * Only perhaps 20% on new feature development
* The twenty-year-old codebase
* Too stressed out and busy
  * **You have to be able to slow down before you can speed up.**

### Sales and Marketing principle

* Your network is crucial
  * People hire people they know
* Listen first to discover what their specific problems are
* Adapt your pitch for the audience and their specific problems
* They have to be willing to invest their time
  * which can’t happen if they are too stressed out
* _**Your best marketing department should be your previous customers**_

### **Sales Pitch**

![](../../../.gitbook/assets/image%20%28469%29.png)

### Beginning Coaching with a New Organization

* Present yourself
  * Tell stories and anecdotes of successful agile teams applying technical practices
  * Explain what ensemble working is and why it is such a useful forum for a coach.

#### **Kick-off Workshop** with each team

* With your sponsor, identify which teams would be good to approach about coaching
* Probably want to talk to : 
  * Line manager
  * Product Owner
  * Scrum Master 
  * The team members themselves

**Kick- of agenda :**

* Team introduction round \(10 minutes\)
* Architecture overview \(15 minutes\)
  * Asked people to sketch the architecture on a piece of paper or a whiteboard.
* Issues in the codebase \(45 minutes\)
  * Ask them to show a :
    * Typical unit test \(if there are any\)
    * Typical automated system or functional test \(if there are any\)
    * Any class or function that you feel is well designed and would like to see more like that
    * A class or function that doesn’t have any unit tests, which you would like to have tests for
    * Any class or function that is notorious for having bugs in.
    * Any code that you’ve been working with recently that represents your current design thinking.
* Structured discussion \(30-40 minutes\)
* Takeaways \(5 minutes\)

#### Takeaways

* Have gathered: 
  * Everyone’s names in a format you can use to learn them
  * A sketch of the architecture information about the build, test and deployment process 
  * Some insights into the code notes about the main problems facing the team from their POV

{% hint style="info" %}
Tip: organize your notes by team.
{% endhint %}

### Preparing for a Technical Coaching Career

* Core skills :
  * Test-Driven Development and Refactoring
  * Software Design with loose coupling and high cohesion
  * Continuous Integration \(commit and sync many times a day\)
  * Pair programming, including strong-style pairing and pairing with a more junior developer
  * Designing test cases both at unit level and larger
  * Standing in front of a group and presenting about a topic you care about
  * Chairing a meeting and facilitating a retrospective
  * Standing at a whiteboard sketching and explaining a design to your team while they ask questions
  * Live code a prepared demo of a coding technique to a group of your peers
* Ideas to improve :
  * Start a regular Coding Dojo with your team
  * Attend a Code Retreat
  * Study books and videos on agile development practices
  * Go to agile conferences
  * Attend formal training for a Scrum Master or Agile Coach role
  * Join a meetup and organize meetings
  * Give presentations at an internal Community of Practice or meetup

### Resources for Samman coaching

[https://sammancoaching.org/](https://sammancoaching.org/)

