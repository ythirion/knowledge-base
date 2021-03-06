---
description: A Craftsman's Guide to Software Structure and Design
---

# Clean Architecture

## Connection

* Split the group in 4 :
* Ask this question
  * What characteristics do these architectures have in common? - 5'
  * Craft as many post-its as they can
* Review what has been produced

#### Hexagonal architecture

![](../../.gitbook/assets/image%20%28237%29.png)

![Alistair Cockburn](../../.gitbook/assets/image%20%28248%29.png)

#### Onion architecture

![](../../.gitbook/assets/image%20%28266%29.png)

![Jeffrey Palermo](../../.gitbook/assets/image%20%28265%29.png)

## Concepts

### Hexagonal Architecture

![](../../.gitbook/assets/image%20%28254%29.png)

{% hint style="info" %}
_Allow an application to equally be driven by users, programs, automated test or batch scripts, and to be developed and tested in isolation from its eventual run-time devices and databases._
{% endhint %}

![](../../.gitbook/assets/image%20%28259%29.png)

Source : [https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/](https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/)

### Onion Architecture

#### Layers

![](../../.gitbook/assets/image%20%28279%29.png)

* _**Domain Model layer**_, where our entities and classes closely related to them e.g. value objects reside
* _**Domain Services layer**_, where domain-defined processes reside
* _**Application Services layer**_, where application-specific logic i.e. our use cases reside
* _**Outer layer**_, which keeps peripheral concerns like UI, databases or tests

#### Dependency Inversion Principle \(at Architecture Level\)

![](../../.gitbook/assets/image%20%28260%29.png)

This means that when writing our high-level business logic, we don’t want to depend directly on low-level stuff like databases, file systems, network connections, provider contracts, and such.

![](../../.gitbook/assets/image%20%28256%29.png)

{% hint style="success" %}
_Instead, we should expose an abstraction that represents a higher-level business need and implements it using these low-level mechanisms._
{% endhint %}

### What characteristics do these architectures have in common?

Here is some answers to the connection question :

* Independent of frameworks
  * Does not depend on the existence of libraries
  * Allow us to use frameworks as tools \(not a constraint\)
* Independent of the front-end
  * Can easily change the UI \(from web to console\)
* Independent of the database
  * Business rules not bound to Database logic
* Independent of any external agency
  * Business rules don’t know anything about outside world

{% hint style="success" %}
_**Business rules can be tested without external components**_
{% endhint %}

### Use Case Driven Approach

![](../../.gitbook/assets/image%20%28264%29.png)

Ivar Jacobson in his book below explained we should map 1 Business Use case / 1 Application Use case. We should implement Application Use Case with the BCE "pattern" : Boundary Controller Entity :

![BCE](../../.gitbook/assets/image%20%28236%29.png)

![](../../.gitbook/assets/image%20%28262%29.png)

### Clean Architecture

![Uncle Bob&apos;s book](../../.gitbook/assets/image%20%28242%29.png)

The Clean Architecture as expressed by Robert C. Martin is a mix of the 3 architecture ideas explained before :

![](../../.gitbook/assets/image%20%28252%29.png)

#### Entities \(Enterprise business rules\)

* Encapsulate Enterprise wide business rules
  * Can be
    * Object with methods
    * Set of data structures and functions 
* Could be used by many different applications in the enterprise.

![](../../.gitbook/assets/image%20%28243%29.png)

#### Use cases \(Application business rules\)

* Capture business rules 
* Structure should indicate what the application is, not how it does it 
* Application specific business rules

![](../../.gitbook/assets/image%20%28271%29.png)

#### Interface adapters

* Set of adapters
  * Convert data from the format most convenient for the use cases and entities
  * To the format most convenient for some external agency such as the Database or the Web 
* In a MVC architecture : Presenters, Views, and Controllers

![](../../.gitbook/assets/image%20%28258%29.png)

#### Frameworks & drivers

* Frameworks and tools such as
  * Database
  * Web Framework

{% hint style="info" %}
_Glue code that communicates to the next circle inwards._
{% endhint %}

* This layer is where all the details go
  * Keep these things on the outside where they can do little harm

#### The dependency rule

![](../../.gitbook/assets/image%20%28240%29.png)

{% hint style="success" %}
Source code dependencies can only point inwards.
{% endhint %}

![](../../.gitbook/assets/image%20%28245%29.png)

## Concrete Practice

* Clone the repository at : [https://github.com/ivanpaulovich/clean-architecture-kata-dojo](https://github.com/ivanpaulovich/clean-architecture-kata-dojo)
* Checkout the branch “kata-initial”

### Objective

Learn and practice the concepts behind Clean Architecture

### Part 1

Each participant :

* Position projects on the Clean Architecture Diagram
* Draw the sequence diagram of the Register Use Case
  * They can use :
    * [https://sequencediagram.org/      ](https://sequencediagram.org/
      )
    * [https://plantuml.com/](https://plantuml.com/)
    * [https://app.diagrams.net/](https://app.diagrams.net/)

![Empty Clean architecture Diagram](../../.gitbook/assets/image%20%28247%29.png)

#### Correction

![](../../.gitbook/assets/image%20%28241%29.png)

![Register User Case](../../.gitbook/assets/image%20%28255%29.png)

### Part 2

Cover the following use cases and requirements:

* The customer can register a new account. 
* Allow to get the customer details. 
* Allow to get the account details. 
* Allow to deposit into an existing account. 
* Allow to withdraw from an existing account. 
* Accounts can be closed only if they have zero balance. 
* Accounts does not allow to withdraw more than the current account balance.

![](../../.gitbook/assets/image%20%28273%29.png)

You can check in the branch **final-solution** to see one possible implementation of those Use Cases

## Conclusion

* What benefits do you see? 
* Pros and cons ?

![](../../.gitbook/assets/image%20%28275%29.png)

### Pros & Cons

| Pros | Cons |
| :--- | :--- |
| _**Plays well with DDD**_ – architecture that builds everything on top of a domain model | _**Learning curve**_ – People tend to mess up splitting responsibilities between layers, especially harming the domain model |
| _**Directed coupling**_ – the most important code in our application depends on nothing, everything depends on it | _**Indirection**_ – interfaces everywhere! |
| _**Flexibility**_ – from an inner-layer perspective, you can swap out anything in any of the outer layers and things should work just fine | _**Potentially heavy**_ |
| _**Testability**_ – since your application core does not depend on anything else, it can be easily and quickly tested in isolation |  |

## Support

{% embed url="https://speakerdeck.com/thirion/clean-architecture-hands-on?slide=1" %}

## Resources

* Hexagonal Architecture : [https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/](https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/)
* Onion Architecture : [https://bitbucket.org/jeffreypalermo/onion-architecture/src](https://bitbucket.org/jeffreypalermo/onion-architecture/src
  )
* Clean Architecture : [https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
* A simple template for Onion Architecture with .NET 5 : [https://pereiren.medium.com/a-simple-template-for-onion-architecture-with-net-5-6c0e2f3b29c8](https://pereiren.medium.com/a-simple-template-for-onion-architecture-with-net-5-6c0e2f3b29c8)

![](../../.gitbook/assets/image%20%28567%29.png)



