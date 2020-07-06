---
description: 'Pact broker : the missing piece of your CDC approach'
---

# Pact broker : the missing piece of your Consumer-Driven Contract approach

_The Pact Broker is an application for **sharing for consumer driven contracts and verification results**._

_It is optimized for use with “pacts” \(contracts created by the_ [_Pact_](http://docs.pact.io/) _framework\), but can be used for any type of contract that can be serialized to JSON._

![](../../../.gitbook/assets/image%20%28201%29.png)

Let’s deep dive into the functionalities offered by the broker :

## A RESTful API for **publishing and retrieving pacts** <a id="3f81"></a>

The question that you can ask yourself when you start a CDC approach is where do I store the contracts ? In the consumer repository ? in a dedicated repository for the contracts ? in external libraries ? Where ?

The broker has been implemented to solve this question. The only source of truth is the broker where I can :

* Publish a contract

![](../../../.gitbook/assets/image%20%28209%29.png)

* Retrieve a contract

![](../../../.gitbook/assets/image%20%28206%29.png)

## An embedded API **browser for navigating the API** <a id="69d8"></a>

The Pact Broker API uses [HAL](http://stateless.co/hal_specification.html) \(Hypertext Application Language\) as its hypermedia implementation \(that is, the method of providing links within a resource to navigate from that resource to related resources\).

The Broker comes with an embedded HAL browser that lets you navigate the API in your browser window by using the HAL relations in each resource.

**The HAL specification also provides a built in method for providing documentation about a relation**. You can navigate to this documentation in the HAL browser by clicking on the book icon next to that relation in the HAL browser.

![](../../../.gitbook/assets/image%20%28199%29.png)

## Displays provider **verification results** <a id="45b6"></a>

When a pact is verified against a provider, the outcome of that verification \(pass or fail\) needs to be made available to the consumer and provider teams, so they know whether or not the code in either project **can be safely deployed**.

The pact verification tool can automatically publish the verification results back to the broker, and they will be displayed on the index page next to the pact details.

{% hint style="success" %}
By displaying verification results you know if you can deploy safely
{% endhint %}

![](../../../.gitbook/assets/image%20%28213%29.png)

## **Auto-generated documentation** for each contract <a id="568d"></a>

A human readable version of the pact can be browsed from the broker :

![](../../../.gitbook/assets/image%20%28208%29.png)



## Provides a **“matrix” of compatible consumer and provider versions** <a id="5c45"></a>

When publishing a pact or a verification, the resource is associated with a particular version of the pacticipant \(application\), which is identified by a version number.

A pacticipant version number:

* is expected to change \(almost\) every time a pact is published
* should uniquely identify or be able to be mapped back to the commit of the code base that published a pact or verification \(so that you can use tags to identify and checkout the the `prod` version of your provider if you wish to [test the "matrix"](http://rea.tech/enter-the-pact-matrix-or-how-to-decouple-the-release-cycles-of-your-microservices/).\)
* should exist only on one branch of your code
* should be known at release time \(so you can pass it in to `can-i-deploy` to ensure that you are safe to release\)

![](../../../.gitbook/assets/image%20%28205%29.png)

## Visualize your microservices <a id="1504"></a>

Dynamically generated network diagrams so you can **visualise your microservice network.**

![](../../../.gitbook/assets/image%20%28191%29.png)

## A CLI for your CI/CD <a id="8e86"></a>

A [**CLI**](https://github.com/pact-foundation/pact-ruby-standalone/releases) ****for incorporating the Pact workflow into your continuous integration process.

{% hint style="success" %}
By using the _can-i-deploy_ feature of the Pact Broker CLI, it will give you a definitive answer if the version of your consumer that is being deployed, is compatible with all of its providers.
{% endhint %}

> This functionality can definitely save your life by avoiding an integration problem to arrive in production.

![](../../../.gitbook/assets/image%20%28194%29.png)

## **Docker Pact Broker** <a id="23fb"></a>

There is an official image for the broker available here : [https://hub.docker.com/r/pactfoundation/pact-broker/](https://hub.docker.com/r/pactfoundation/pact-broker/)

So it is really easy to setup and play with it with just a few lines of YAML :

![](../../../.gitbook/assets/image%20%28192%29.png)

## Webhooks <a id="1d25"></a>

Provides **webhooks to trigger actions when pacts change** eg. run provider build, notify a Slack channel. __You can trigger a webhook for those events :

![](../../../.gitbook/assets/image%20%28216%29.png)

To create a new webhook you just need to POST it to your broker :

![](../../../.gitbook/assets/image%20%28214%29.png)

In the broker you will have feedback on it :

![](../../../.gitbook/assets/image%20%28211%29.png)

## Conclusion

To conclude those articles I would like to say that Pact and Pact broker together are really great tools BUT **I would like to remind that consumer-driven contract testing is a technique that requires no special tool to implement**. If you want to start without tooling go ahead, tools are just there to support the approach.

{% hint style="success" %}
_**Once again it is all about communication.**_

_Communication between teams :_

* _Team that will need to consume a service_
* _Team that will provide the service_
{% endhint %}

