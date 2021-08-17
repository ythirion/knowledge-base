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

![](../../../.gitbook/assets/image%20%28658%29.png)

## **Part 1. On Reading Code Better**

### 1. Decoding your confusion while coding

* Confusion = part of programming.
  * When you learn a new programming language, concept, or framework
    * New ideas might scare you
  * When reading unfamiliar code or code that you wrote a long time ago, you might not understand what the code does or why it was written the way it is
  * Whenever you start to work in a new business domain, new terms and jargon can all bump into each other in your brain
* 3 types of confusion in code
  * Lack of knowledge

![](../../../.gitbook/assets/image%20%28656%29.png)

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

![](../../../.gitbook/assets/image%20%28657%29.png)

#### Different cognitive processes that affect coding

![](../../../.gitbook/assets/image%20%28659%29.png)

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

#### Remembering more code by using long-term memory

* Experts’ memories differ from beginners’
  * De groot chess experiment
    * When comparing the performance of average players with chess master
    * He found that expert players were much better at recreating the chess setups than average players if not random
    * Experts grouped info in logical ways -&gt; chunks
    * He considered “Sicilian opening,” for example, as one chunk,
      * Which can fit into one slot in short-term memory. 
  * The theory of chunks also adequately explains why both types of players performed equally in experiment 2 \(random setup\)

#### Chunking in code

{% hint style="success" %}
The more information you have stored about a specific topic, the easier it is to effectively divide information into chunks.
{% endhint %}

In 1981 [Katherine McKeithen](https://www.researchgate.net/publication/222462455_Knowledge_Organization_and_Skill_Differences_in_Computer_Programmers), a researcher at Bell Labs, tried to repeat de Groot’s experiments on programmers :

![](../../../.gitbook/assets/image%20%28655%29.png)

Main takeaway : _**beginners will be able to process a lot less code than experts**_

#### **How to write "chunkable" code**

* **Use Design Patterns**
  * Having a design pattern present in the code was more helpful for performing maintenance tasks when the programmers knew that the pattern was present in the code
  * Gaining knowledge about design patterns
    * Going to improve your chunking ability
    * Helps you to process code faster
* **Write comments**
  * When code contains comments
    * Programmers will take more time to read it
      * You might think that is a bad thing—that comments “slow you down”—
      * In fact, this is a sign that comments are being read when programmers read code
  * High-level comments like “this function prints a given binary tree in order” 
    * can help programmers to chunk larger pieces of code
  * Low-level comments such as “increment i \(by one\)” after a line that reads i++;
    * can create a burden on the chunking process
* **Leave Beacons**
  * Beacons are parts of a program that help a programmer to understand what the code does like a line of code even part of a line of code, that your eye falls on which "Now I see"
  * Provide an important signaling service for programmers during the comprehension process
    * They often act as a trigger for programmers to confirm or refute hypotheses about the source
  * 2 types
    * Simple beacons :
      * Self-explaining syntactic code elements : meaningful variable names, operators such as +, &gt;, and && and structural statements such as if, else, and so on can be considered simple beacons too
    * Compound beacons : larger code structures comprised of simple beacons. Compound beacons provide semantic meaning for

{% code title="Beacons example" %}
```python
# A class that represents a node in a tree
class Node:
    def __init__(self, key):
    self.left = None
    self.right = None
    self.val = key
    # A function to do in-order tree traversal
        
def print_in_order(root):
    if root:
    # First recur on left child
    print_in_order(root.left)
    # then print the data of node
    print(root.val),
    # now recur on right child
    print_in_order(root.right)
    print("Contents of the tree are")
    print_in_order(tree)
    
1. Comments using the word “tree”
2. Variables called root and tree
3. Fields called left and right
4. String contents in the code that concern trees
```
{% endcode %}

### 3. How to learn programming syntax more quickly

* What you already know impacts to a large extent how efficiently you can read and understand code
  * The more concepts, data structures, and syntax you know
  * The more code you can easily chunk, and thus remember and process

{% hint style="success" %}
_**4 Techniques** that will help you memorize programming concepts better and more_
{% endhint %}

#### A word on interruptions

* Parnin determined that interruptions are, unsurprisingly, quite disruptive to productivity
* His study showed that 
  * It typically takes about a quarter of an hour to get back to editing code after an interruption
* When interrupted during an edit of a method
  * Programmers were able to resume their work in less than a minute in only 10% of cases

#### Technique 1 : Flashcards

* A great way to learn anything, including syntax, fast is to use flashcards
* Simply paper cards or Post-its of which you use both sides
  * One side has a prompt on it—the thing that you want to learn
  * The other side has the corresponding knowledge on it

![example of flashcards on Brainscape](../../../.gitbook/assets/image%20%28661%29.png)

_**When to use them ?**_

* Use them often to practice
* Use Apps like [**Brainscape**](https://www.brainscape.com/), Anki, Quizlet, that allow you to create your own digital flashcards
  * They will remind you when to practice again
* After a few weeks your syntactic vocabulary will have increased

_**Expanding the set of flashcards**_

* 2 good times to add flashcards to your set
  * When you’re learning a new programming language, framework, or library
    * You can add a card each time you encounter a new concept
  * When you’re about to Google a certain concept
    * That is a signal that you do not yet know that concept by heart

_**Thinning the set of Flashcards**_

* To keep track of how well you know certain concepts
  * You can keep a little tally on each card of your right and wrong answers
  * Demonstrate what knowledge is already reliably stored in your long-term memory

![Tally on flashcards](../../../.gitbook/assets/image%20%28662%29.png)

#### How to not forget things

* The big problem with your **LTM** : _you cannot remember things for a long time without extra practice_
* The decay for LTM is not seconds, like that of the STM
  * But it is still a lot shorter than you might think
  * `After 2 days, just 25% of the knowledge remains in your LTM`

![Forgetting curve](../../../.gitbook/assets/image%20%28660%29.png)

#### Why do we forget memories?

* Storage of memories in the brain is not based on zeros and ones
  * BUT it does share a name with how we store information to disk: encoding
* Memories in the brain are organized in a network structure
  * Because facts are connected to large numbers of other facts

![on the left, a hierarchical filesystem; on the right, memories organized as a network](../../../.gitbook/assets/image%20%28663%29.png)

* Memories are stored with associations, or relationships to each other

#### Spaced Repetition

* You remember the longest if you study over a longer period of time
  * In contrast with formal education, where we try to cram all the knowledge into one semester
* **Revisiting your set of flashcards once a month** 
  * Will be enough to help your memory in the long run, and it’s also relatively doable!

{% hint style="success" %}
The biggest takeaway from this section is that the best way that science knows to prevent forgetting is to practice regularly. _****_Each repetition strengthens your memory. 

After several repetitions spaced out over a long period, the knowledge should remain in your long-term memory forever.
{% endhint %}

#### How to remember syntax longer ?

* Don’t try to memorize all of your flashcards in a day
  * But spread your study out over a longer period of time
  * Research has shown that actively trying to remember makes memories stronger
* 2 techniques **to strengthen memories** :
  * **Retrieval practice** : actively trying to remember something
    * Retrieval is a more formal word for remembering
  * **Elaboration** : actively connecting new knowledge to existing memories
* How to measure memories strength ?
  * _**Storage strength**_ : indicates how well something is stored in long-term memory
    * The more you study something
    * The stronger the memory of it is
    * Until it becomes virtually impossible to ever forget it
  * _**Retrieval strength**_ : indicates how easy it is to remember something
    * Have you already have the feeling where you’re sure you know something 
      * a name, a song, a phone number, the syntax of the filter\(\) function in JavaScript
      * But you can’t quite recall it; the answer is on the tip of your tongue
      * > Information for which the storage strength is high— and retrieval strength is low

