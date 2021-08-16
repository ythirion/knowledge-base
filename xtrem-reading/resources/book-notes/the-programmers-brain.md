---
description: by Felienne Hermans
---

# The Programmer's Brain

## Pitch

**Your brain responds in a predictable way when it encounters new or difficult tasks. This unique book teaches you concrete techniques rooted in cognitive science that will improve the way you learn and think about code.**  
  
In The Programmer’s Brain: What every programmer needs to know about cognition you will learn:

* Fast and effective ways to master new programming languages
* Speed reading skills to quickly comprehend new code
* Techniques to unravel the meaning of complex code
* Ways to learn new syntax and keep it memorized
* Writing code that is easy for others to read
* Picking the right names for your variables
* Making your codebase more understandable to newcomers
* Onboarding new developers to your team

Learn how to optimize your brain’s natural cognitive processes to read code more easily, write code faster, and pick up new languages in much less time. This book will help you through the confusion you feel when faced with strange and complex code, and explain a codebase in ways that can make a new team member productive in days!

![](../../../.gitbook/assets/image%20%28657%29.png)

## **Part 1. On Reading Code Better**

### 1. Decoding your confusion while coding

* Confusion = part of programming.
  * When you learn a new programming language, concept, or framework
    * New ideas might scare you
  * When reading unfamiliar code or code that you wrote a long time ago, you might not understand what the code does or why it was written the way it is
  * Whenever you start to work in a new business domain, new terms and jargon can all bump into each other in your brain
* 3 types of confusion in code
  * Lack of knowledge

![](../../../.gitbook/assets/image%20%28655%29.png)

* Lack of easy-to-access information
  * The information about exactly how _toBinaryString\(\)_ works is not readily available
  * Needs to be found somewhere else in the code

```java
public class BinaryCalculator {
    public static void mian(Int n) {
        System.out.println(Integer.toBinaryString(n));
    }
}
```

* Lack of processing power in the brain
  * You cannot oversee all the small steps that are being executed
  * If you need to understand all the steps, you may likely use a memory aid like intermediate values of variables shown here

![](../../../.gitbook/assets/image%20%28656%29.png)

#### Different cognitive processes that affect coding

![](../../../.gitbook/assets/image%20%28658%29.png)

An overview of the three cognitive processes that this book covers: STM, LTM, and working memory.

1. Information coming into your brain. 
2. Information that proceeds into your STM
3. Information traveling from the STM into the working memory, where it’s combined with information from the LTM \(arrow 4\).

   > _Working memory is where the information is processed while you think about it._

#### Mapping between confusion and cognitive processes

* Lack of knowledge -&gt; Issue in long-term memory 
* Lack of information -&gt; Issue in short-term memory 
* Lack of processing power -&gt; Issue in working memory

#### Cognitive processes and programming

* Long-term memory
  * First cognitive process that is used while programming is long-term memory
  * This can store your memories for a very long time
  * Like the **hard drive** of your brain
* Short-term memory
  * Short-term memory is used to briefly hold incoming information
  * The estimates differ, but most scientists agree that just a few items fit in short-term memory, and certainly _**not more than a dozen**_
  * Like the computer's **RAM** or a **cache** that can be used to temporarily store values
* Working memory
  * The actual “thinking,” however, happens in working memory
  * Like the processor of the brain

#### When reading a program

* Use long-term memory when remembering meanings of keywords for example
* Use short-term memory to store some of the info you encounter
* Use working memory : trying to mentally execute the code / understand what is happening
  * That process is called tracing — the mental compiling and executing of code.
  * When tracing very complex programs, you might feel the need to note down the values of variables, either in the code or in a separate table. 
  * The fact that your brain feels the need to store information externally can be a sign that your working memory is too full to process more information.

### 2. Speed Reading for code

{% hint style="info" %}
Research indicates that almost **60% of programmers’ time** is spent understanding code, rather than writing code.\[[1](https://ieeexplore.ieee.org/abstract/document/7997917)\] Thus, improving how quickly you can read code, without losing accuracy, **can help you improve your programming skills substantially**.
{% endhint %}

> "Programs must be written for people to read and only incidentally for machines to execute.” - Structure and Interpretation of Computer Programs by Harold Abelson, Gerald Jay Sussman, and Julie Sussman \(MIT Press, 1996\)

* Reading code is done for a variety of reasons: 
  * to add a feature
  * to find a bug
  * or to build an understanding of a larger system

#### Why is reading unfamiliar code hard?

Limited capacity of your short-term memory :

* STM stores information that you read or hear for a brief period of time
  * Research indicates _**it cannot hold information for more than 30 seconds**_
* Limitation of size : just a few slots available for information
  * 7 + or - two
  * More research indicates that its capacity could be smaller : just 2 to 6 things



