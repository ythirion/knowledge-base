# Stack

### Objective

* Create production code from test
* Start from assertion
* Introduce naming convention

![](../../../.gitbook/assets/image%20%28485%29.png)

## Connection - 10'

What are the key principles to write good unit tests ?

## Concepts - 10'

{% hint style="info" %}
Tip for deciding the first test to write: The simplest possible.
{% endhint %}

* Red, Green, Refactor
  * Add a test
  * Run all tests and see if the new one fails - Red
  * Write the minimum amount of code to pass the failing test - 
  * Run tests - Green
  * Refactor code - Blue 
  * **Repeat**
* TDD Golden Rule
  * **Do not write any production code until you have a failing test that requires it**
* Arrange, Act, Assert
  * Arrange :
    * Setup everything needed for the testing code
    * Data initialization / mocks
  * Act :
    * Invoke the code under test / behavior
  * Assert :
    * Specify the pass criteria for the test

Define a test checklist for your team :

![](../../../.gitbook/assets/image%20%28486%29.png)

## Concrete Practice - 25'

* Implement a Stack class with the following public methods by  using TDD :

```text
void push(Object object)
Object pop()
```

* Stack should throw an exception if popped when empty
* Start by writing your assertions

#### Question to ask :

{% hint style="danger" %}
_**What is the value to test the push ?**_

Do not change your production code encapsulation for testing purpose
{% endhint %}

As a coach demonstrate how you write the Stack by using Live Coding

## Conclusion - 5

Note the main thing you want to remember about this session on a Sticky Note

