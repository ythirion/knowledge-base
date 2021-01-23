# Fizzbuzz

## Connection

Introduce yourself to a person near you and discuss.

Is it easier to unit test :

```text
- a static method
- pure function
- method that modifies object state
- method that modifies its parameters
```

The reason for asking about what is easy to test is to get them prepared for designing a pure function or static method for calculating FizzBuzz. 

_**These kinds of functions are easier to test since all the outcomes are visible in the return value, the input value is not modified and there are no side effects.**_

## Concepts

### Bust the TDD myths

* TDD is too Time Consuming
  * The business team doesn’t care at all about the development process you use, as long as it’s effective.
  * TDD will :
    * improve developer productivity \(long term\)
    * Reduce customer abandonment
    * Reduce the costs of customer service 
* Writing test cases before the code, is not feasible
  * It forces you to have a direction in mind before you start charging into the fray, and having a direction in mind leads to better designs
* 100% code coverage
  * 100% of testing the wrong things is not a goal…
  * Focus on the value 
* TDD replaces QA
  * We can’t cover everything with TDD
  * For example : GUI E2E tests \(really hard to maintain\)
  * This is where QA has an important role.
* _**Write all tests before we start the code**_
  * _**Not at all : 1 test at a time**_

### 2 TDD schools

| Chicago / Detroit TDD \(Classic\) | London TDD \(Mockist approach\) |
| :--- | :--- |
| From the inside to outside | From the outside to inside |
| Starting from the model classes \(Core domain logic\) | Use external constraints as a starting point \(API endpoint, Services\) |
| No concern for how it might be integrated elsewhere |  |

## Concrete Practice

Write a method that returns for a number from 1 to 100 this given number, except that : 

* For multiples of 3 returns “_**Fizz**_”
* For the multiples of 5 returns “_**Buzz**_”
* For numbers which are multiples of both 3 and 5 returns “_**FizzBuzz**_”

![](../../../.gitbook/assets/image%20%28492%29.png)

Let them start for 10' then reflect you can then give them more guidance :

### 1\) Identify your Test Cases

By using the Test Cards in pair : identify test cases

![](../../../.gitbook/assets/image%20%28494%29.png)

Test cases :

```text
- shouldReturnTheNumber (ex : 1, 67, 82, ...)
- shouldReturnFizzForMultipleOf3 (ex : 3, 30, 99)
- shouldReturnBuzzForMultipleOf5 (ex : 5, 50, 85)
- shouldReturnFizzBuzzForMultipleOf3And5 (ex : 15, 30, 45)
- shouldThrowAnExceptionForNumberOutOfRange (ex : 0, -1, 101)
```

### 2\) Once identified the 5 Test Cases, write the code

By using TDD, write Test cases once at a time :

Trap to avoid : _**"do not write 1 test to rule them all"**_

* Talks about sampling
  * Tests are always a sample
  * You cannot cover every possible value
* Do not repeat the same complexity in your tests than in your Production Code

### 3\) A little bit to easy ?

* Remove “if” in your code
* Parameters version, implement this method : 
  * If you use a language authorizing default values :
    * int limit : 100
    * int fizz : 3
    * int buzz : 5

```java
public class FizzBuzz {
    public String fizzBuzz(int limit, int fizz, int buzz) {
        ...
    }
}
```

* Take a function in parameter
  * Create a Higher Order Function : function modulo\(dividend, divisor\){ return dividend%divisor; }
* Add a voice output
* Write it in an unknown language

### Reflect

* What happened to your code when implementing new tests ?

{% hint style="success" %}
_**Triangulation : The more specific tests you write, the more the code will become generic**_
{% endhint %}

## Conclusion

* In pairs, discuss how TDD felt, what was difficult and what was easier.
* Tell the other person the most useful thing you learnt so far.





