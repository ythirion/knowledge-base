# CDC testing made simple with Pact

## What is Pact ?

{% hint style="success" %}
Pact is _**a contract testing tool**_. Contract testing is a way to ensure that services (such as an API provider and a client) can communicate with each other. Without contract testing, the only way to know that services can communicate is by using expensive and brittle integration tests.
{% endhint %}

Pact provides a testing button for your code, allowing you to safely confirm that your applications will work together without having to deploy the world first.

It is available on a lot of platforms and languages :

![](<../../../.gitbook/assets/image (193).png>)

Pact comes with its own specification regarding the format of the contracts between consumers and providers :

![](<../../../.gitbook/assets/image (194).png>)

## How can we implement a new service with Pact ? <a href="f329" id="f329"></a>

Because we use a CDC approach we start with the consumer and here is what we want as a consumer :

{% hint style="info" %}
_As a consumer, I want a Rest API that returns “Hello world v1” when I GET “api/v1.0/helloworld”_
{% endhint %}

### 1) Start with the consumer <a href="15af" id="15af"></a>

Let’s implement a simple consumer by :

* Writing Test(s)
* Define interactions / Expectations

![](<../../../.gitbook/assets/image (195).png>)

**Concretely **:

* Build your client : here we call it **consumer-js**

![](<../../../.gitbook/assets/image (196).png>)

* Describe and configure the interactions (behaviors and expectations)

![](<../../../.gitbook/assets/image (197).png>)

Once you have defined it you can run the tests. From those expectations Pact will create a contract file : a JSON file that will look like this :

### 2) Contract Driven Development <a href="0d10" id="0d10"></a>

* Design Your **API** From The Contract
* Write a RED test

![](<../../../.gitbook/assets/image (199).png>)

#### **The RED test (in .NET Core)**

![](<../../../.gitbook/assets/image (200).png>)

The test will be launched and interactions will be verified based on the contract that has been defined on the consumer side.

![](<../../../.gitbook/assets/image (201).png>)

#### **Make the test GREEN**

![](<../../../.gitbook/assets/image (202).png>)

## Features offered by Pact <a href="f090" id="f090"></a>

In this simple example we have just checked a GET interaction with simple string matcher but you can achieve much more complex and more realistic verifications with the tool :

![](<../../../.gitbook/assets/image (203).png>)

## S.W.O.T <a href="eaa4" id="eaa4"></a>

Based on our experience with Pact here is our S.W.O.T :

![](<../../../.gitbook/assets/image (204).png>)

## Resources <a href="abaa" id="abaa"></a>

Please find the code samples in this repository : [**https://github.com/agilepartner/pact-sandbox**](https://github.com/agilepartner/pact-sandbox)

To go further check the implementation guide in your favorite language : [https://docs.pact.io/implementation_guides](https://docs.pact.io/implementation_guides)

## Conclusion <a href="2692" id="2692"></a>

Pact is a really good tool to start a CDC approach. It is easy to use but there is one problem that needs to be solved before starting using it in enterprise :

{% hint style="danger" %}
**Where the hell do we store the contracts ?**
{% endhint %}
