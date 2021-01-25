---
description: Kata from Sandro Mancuso
---

# Outside-in TDD \(London Style\)

### Objectives

* Learn and practice the double loop of TDD 
* Test application from outside, according to side effect

## Connection - 10'

* What does it bring to design classes as a consumer of the class ?
* What could it bring to do it in pair ?

## Concepts - 10'

{% hint style="success" %}
_**In outside-in TDD we only implement what is needed to serve the outside.**_
{% endhint %}

* Write an acceptance test that fails
  * Something that can be accepted by a stakeholder
  * The **feature test**
* Keep it red
  * It will indicate what to test
  * Drive to the next step
* _**This double loop continues till the feature test turns green**_

![](../../../.gitbook/assets/image%20%28517%29.png)

By using this practice :

* Think about what you want to test in isolation \(mocking\)
* Create unit tests
* What are your test boundaries ?

### Use mocks to design the collaborations

The test is used to design the system, and part of that design is deciding how the different components interact / how they are bounds to each others

![](../../../.gitbook/assets/image%20%28513%29.png)

## Concrete Practice - 2h minimum

Here are your instructions :

Create a simple bank application with the following features :

* Deposit money
* Withdraw money
* Print a bank statement to the console

#### Acceptance criteria

Statement should have the following the format :

```text
DATE       | AMOUNT  | BALANCE
10/04/2014 | 500.00  | 1400.00
02/04/2014 | -100.00 | 900.00
01/04/2014 | 1000.00 | 1000.00
```

#### How to start ?

In pair :

* Start with an acceptance test 
* Use int for money and String for dates
* Ignore the formatting of the statement for now

#### Start by designing Service contract

You cannot change the public interface of this class.

```java
public class AccountService {
    public void Deposit(int amount);
    public void Withdraw(int amount);
    public void PrintStatement();
}
```

As a coach use the Double Loop diagram to demo where the people are.

#### Sequence Diagram

Introduce the use of Sequence diagram after some time spend on the kata

![](../../../.gitbook/assets/image%20%28515%29.png)

Use sequence diagram to :

* Think about how the different objects will collaborate
* Identify what should be mock and when

#### Test Driven Development != Test Driven Design

{% hint style="success" %}
**Good design is driven by experience & principles, not by any TDD approach in and of itself.**
{% endhint %}

Take times to reflect on the design outside of the test : great to use diagrams for it

## Conclusion - 10'

* In pair, list _**all the pros / cons**_ of this Double Loop Approach
* Share it all together

#### Resources

* [Bank kata explained](https://katalyst.codurance.com/bank)
* [Sandro Mancuso's implementing the solution](https://www.codurance.com/publications/videos/2015-05-12-outside-in-tdd-part-1)
* [London vs Chicago \(video series\)](https://cleancoders.com/videos/comparativeDesign)
  * Sandro Mancuso and Uncle Bob
* [Mocking as a design tool article](https://codurance.com/2018/10/18/mocking-as-a-design-tool/)
* [Clean architecture through outside-in TDD](https://medium.com/@erik.sacre/clean-architecture-through-outside-in-tdd-64a31de17ccf)

![](../../../.gitbook/assets/image%20%28519%29.png)

