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

![](../.gitbook/assets/image%20%28236%29.png)

![Alistair Cockburn](../.gitbook/assets/image%20%28237%29.png)

#### Onion architecture

![](../.gitbook/assets/image%20%28243%29.png)

![Jeffrey Palermo](../.gitbook/assets/image%20%28242%29.png)

## Concepts

### Hexagonal Architecture

![](../.gitbook/assets/image%20%28238%29.png)

{% hint style="info" %}
_Allow an application to equally be driven by users, programs, automated test or batch scripts, and to be developed and tested in isolation from its eventual run-time devices and databases._
{% endhint %}

![](../.gitbook/assets/image%20%28240%29.png)

Source : [https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/](https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/)

### Onion Architecture

#### Layers

![](../.gitbook/assets/image%20%28247%29.png)

* _**Domain Model layer**_, where our entities and classes closely related to them e.g. value objects reside
* _**Domain Services layer**_, where domain-defined processes reside
* _**Application Services layer**_, where application-specific logic i.e. our use cases reside
* _**Outer layer**_, which keeps peripheral concerns like UI, databases or tests

#### Dependency Inversion Principle \(at Architecture Level\)

![](../.gitbook/assets/image%20%28241%29.png)

This means that when writing our high-level business logic, we don’t want to depend directly on low-level stuff like databases, file systems, network connections, provider contracts, and such.

![](../.gitbook/assets/image%20%28239%29.png)

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

_\*\*\*\*_

## Resources

* Hexagonal Architecture : [https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/](https://blog.octo.com/architecture-hexagonale-trois-principes-et-un-exemple-dimplementation/)
* Onion Architecture : [https://bitbucket.org/jeffreypalermo/onion-architecture/src](https://bitbucket.org/jeffreypalermo/onion-architecture/src
  )
* 






