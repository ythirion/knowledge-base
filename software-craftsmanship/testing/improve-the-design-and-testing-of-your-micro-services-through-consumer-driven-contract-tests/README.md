---
description: >-
  In a micro-services world, testing the successful integration between services
  is critical for ensuring that the services won’t fail in production just
  because they’re not speaking the same language.
---

# Improve the design and testing of your micro-services through Consumer-Driven Contract Tests

## Why should you read this article ?

If you develop or maintain micro-services you already asked yourself those questions :

* How do we deal with testing? 
* How do we confirm all services are working well together ?

![](https://miro.medium.com/max/54/0*KOZHZDlUYxMYHWZv?q=20)

CDC is an answer to those questions.

> Let’s discover what is behind, let’s go to the upside-down !!!

## How can we test this simple integration ? <a id="5ed3"></a>

![](../../../.gitbook/assets/image%20%28215%29.png)

### Mocking

We can use a mock of the API to design our client integrations. With mocks, we do not need to set up a whole runtime environment. We can run isolated tests between the client and a mock of the API.

#### Limits of mocking

* What happens if there is **a change in the real producer** ?
  * _The system could perfectly run on a “test” environment could not be integrated in the real world._
* The owner of the mock is the consumer
  * _As a consumer I can not be sure that the API has not been changed by the API’s provider, so I am not able to adapt the mock accordingly._
* **Not trustworthy**
  * _How can we be sure that the mocks are valid ?_

![](../../../.gitbook/assets/image%20%28217%29.png)

## End to end testing <a id="b441"></a>

To test interfaces between a client and an API the most used technique is end-to-end testing. In end-to-end tests \(E2E tests\), real servers or containers are set up so that client and provider are available in a production-like runtime environment.

To execute integration tests, the client is usually triggered by providing certain input in the user interface. The consumer then calls the provider and the test asserts if the results meet the expectations defined in the contract.

![](https://miro.medium.com/max/2768/1*U_HaKuXIkCSutC5Yevc1mQ.png)

### Limits of E2E testing <a id="9a3f"></a>

* Slow
  * _The feedback loop of E2E testing is really long \(setup takes a while and the tests run as well\)._
* All services need to be **up before running the tests**
  * _This kind of tests requires a clean/dedicated integration environment. It’s really hard to get one in a lot of organizations at the moment._

## Consumer-Driven Contract approach as an alternative <a id="bcb5"></a>

![](../../../.gitbook/assets/image%20%28188%29.png)

If we take a look at the definition of an integration test : _“An integration test is a test between an **API provider** and an **API consumer** that asserts that the **provider returns expected responses** for a set of pre-defined requests by the consumer. **The set of pre-defined requests and expected responses is called a contract**.”_

This is the main focus of the approach : _**CONTRACTS**_.

{% hint style="success" %}
The whole idea behind CDC is to involve consumers of the future API in the creation of the API itself. API changes will be driven by consumers.
{% endhint %}

### Glossary <a id="2767"></a>

* **Producer :** Service that exposes an API.
* **Consumer :** Service that consumes the API of the producer.
* **Contract :** Agreement between producer and consumer on how the API will look like.
* **Consumer Driven Contracts :** Approach where the consumer drives the changes of the API of the producer.

![\`](../../../.gitbook/assets/image%20%28197%29.png)

### How does it work ? <a id="1dc8"></a>

* Define API contract on the _**consumer side**_.
  * _Write Unit tests that define clearly what are the interactions and behaviors expected from the provider._
* Enforce the contract on the _service **provider side**_.
  * _Unit tests on the provider side ensure that the provider implementation respect the expectations \(contract\) defined by the consumer._

## Benefits of CDC <a id="8f60"></a>

CDC makes your life easier :

* Make integrating and testing a service in a microservice world easier
* Drive the providers implementation through the contract
  * Start by enforcing the contract without the API, then design the API accordingly : you will write less code and avoid extra features.
* Help providers make changes without being scared of accidentally breaking their consumers
* Let consumer know that the APIs they consume won’t suddenly break
* Allows consumers to develop against API definitions before the provider API has actually been developed : **Design first approach**

