---
description: Abstract of a talk of Sandro Mancuso
---

# Aligning Product & Software Design

## Context

### Average company

* Strong boundaries between Technical and Business 
* Technical debt ? 
  * Developers 
    * "We don't have time to improve our system" 
    * "We are struggling with technical debt" 
      * Vicious circle
  * Business
    * "We need more features"

### How to avoid that ? 

* Problem ?
  * **Project mindset**
    * Get to that end
    * Great for something with a start and an end
    * Optimize the means to that end
* Software product
  * Continuous evolution
    * Not a great fit for project
    * Sequence of valuable increment
  * **Should look at**
    * **Not only cost **
    * **Continuous investment**

{% hint style="warning" %}
_**"There is a tension between the way we manage project and the way we manage product"**_
{% endhint %}

* Product strategy
  * Defined isolated from technology
  * Product backlog created
    * By the business
  * Only there the Dev team is coming in 
    * Not part of the product definition 
  * So the **result = Reactive design **
    * Do not have time to architect
    * End by begging for time
      * To refactor for example
* As **developers**
  * We must explain the value of designing software
  * Part of the meeting **to contribute**
    * BUT we don't know exactly HOW
  * We need to have something to add
    *  Be able to explain Biz value of design
      * Not only to be able to organize our code
      * Can have a huge role
        * Examples
          * Enable different teams to work in parallel
          * Need to design our code to do so 
          * Be able to automate -> for CD purpose
    * Enable the way that we need to work

### Different levels of design

* Enterprise Architecture
  * How your product fits in a larger ecosystem 
* Solutions Architecture
  * Solution of your product
  * How we re gonna do / split
* Technical Architecture 
  * What technology
  * SLA
  * ... 
* Macro Design
  * Components
  * Overall structure 
* Micro Design
  * Classes
  * Functions
  * Methods

#### When we design ?

{% hint style="info" %}
_"We often struggle to find the time"_
{% endhint %}

### Understand Product design

![](<../.gitbook/assets/image (220).png>)

* Looks a lot like Waterfall
  * _**Make it iterative**_

![](<../.gitbook/assets/image (221).png>)

* Devs involved only in the development
  * Through the product backlog
  * Not able to create the technical strategy
    * Not have time here

![](<../.gitbook/assets/image (222).png>)

## 1) Ideation

In startup product is part of the company

### Build a vision for the product: NOT A PLAN

* A direction
  * Guiding our work
  * Create a context to offer services

### Product Definition

![](<../.gitbook/assets/image (223).png>)

### Value Proposition Canvas

* Shape the scope of our product 
* 1 canvas per customer segmentation

![](<../.gitbook/assets/image (224).png>)

### Technical Feasibility

* Build a technical vision
* Create a unified view with business & technology

![](<../.gitbook/assets/image (225).png>)

### Results

{% hint style="success" %}
* Business & technology alignment
* Shared & more realistic product vision
* Context for pro-active & supportive tech strategy
{% endhint %}

## 2) Strategy

![](<../.gitbook/assets/image (226).png>)

### Create a roadmap

* Use Lean Startup approach

![](<../.gitbook/assets/image (227).png>)

### Create an architecture

* Define the technology stack
* Refine what has been done in Tech feasibility 
* Design to support the way of the business

### Results

{% hint style="success" %}
* Common understanding of business & technical strategy
* Technical architecture created to support the business 
* More realistic & sustainable product roadmap with Biz and tech 
* High level modularisation makes it easier to plan
{% endhint %}

## 3) Planning

* Use the term Minimum Valuable Increment 
  * Need to invest in technical things

![](<../.gitbook/assets/image (228).png>)

### [Impact Mapping](https://www.impactmapping.org)

* Validate the value towards the goal
* Validate the things we want to build by value

> Generate your backlog from the Impact Mapping

![](<../.gitbook/assets/image (229).png>)

### Create a plan

* Achieve Continuous Delivery
* Several teams working in parallel

![](<../.gitbook/assets/image (230).png>)

* Discover a lot of unknown
* Help to reshape our backlog

## Results

{% hint style="success" %}
* Technical effort, risks & dependencies impact prioritization of MVI's 
* Easier to size MVI's when high level technical details are known
* Helps to distribute work across teams efficiently
* Technical solution designed to support Continuous Delivery (goal of Agile)
{% endhint %}

## 4) Development

![](<../.gitbook/assets/image (231).png>)

* Design Apis from your mockup 
  * Outside IN 
  * What is the outside world expecting from us

### Results

{% hint style="success" %}
* Test & deployment strategies for each increment
* Enables CD
* Detailed design helps to identify risks, dependencies & unknown
* Enable safe evolution of the code
  * Keeping it maintainable 
* Pro-active & continuous technical improvement aligned with biz value 
  * Always improve
* Prevents accumulation of technical debt
{% endhint %}

## Conclusion

![](<../.gitbook/assets/image (232).png>)

* Often POs
  * They have
    * No good vision
    * Don't own it 
    * Product definition is vague
  * Product roadmap
    * No milestones
    * Create a big plan
    * Rigid product backlog 
  * From High level strategy to Product backlog
* Architects
  * Architecture are created without biz inputs
  * No connection with dev teams
* Introduce technical milestones to balance the graph
* Make sure than each phases are done 
  * with Biz & technology 
  * As a single team

{% hint style="success" %}
_**"In a software product, software design should be an explicit part of the business strategy"**_
{% endhint %}

## The talk

{% embed url="https://youtu.be/PGsW9qFb-_M" %}



