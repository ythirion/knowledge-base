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

#### Technique : Flashcards

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

#### Strengthen memories by actively thinking

By actively thinking about and reflecting on the information

{% hint style="success" %}
_The process of thinking about information that you have just learned is called elaboration._
{% endhint %}

**Schemata**

* The ways in which thoughts and the relationships between them are organized in our minds are called schemas, or schemata
* When we save memories
  * the memories can even be changed to adapt themselves to existing schemata

**Technique : Elaboration**

* One thing you can do to strengthen the initial encoding of memories is called elaboration
* Elaboration means thinking about what you want to remember
  * Relating it to existing memories
  * Making the new memories fit into schemata already stored in your long-term memory
* Using elaboration to learn new programming concepts
  * For example, you might try thinking of related concepts in other programming languages
    * **T**hinking of alternative concepts in Python or other programming languages
    * Or thinking of how this concept relates to other paradigms

### 4. How to read complex code

* What’s the difference between working memory and short-term memory?
  * **Working memory = the short-term memory applied to a problem**
  * **Example :**
    * Remember a phone number -&gt; use your STM
    * Add integers -&gt; use your working memory
* What happens in the working memory when you read code?
  * Like the short-term memory, the working memory is only capable of processing between 2 and 6 things at a time
  * In the context of working memory, this capacity is known as the _**cognitive load**_.

Different types of cognitive load :

| Load Type | Description |
| :--- | :--- |
| Intrinsic load | How complex the problem is in itself |
| Extraneous load | What outside distractions add to the problem |
| Germane load | Cognitive load created by having to store your thought to LTM |

#### Intrinsic cognitive load when reading code

Intrinsic cognitive load is cognitive load caused by features of a problem that the problem contains by nature

Example : A geometry problem in which the lengths of two sides of a triangle are given and the third one needs to be calculated. This can be a problem that is hard to solve, depending on your prior knowledge. However, _**the problem itself cannot be made any simpler without changing it.**_ 

#### Extraneous cognitive load

* we can think of this type of extraneous load as similar to accidental complexity :
  * Aspects of a program that make a problem harder than it needs to be
* What creates extraneous load is not the same for every programmer
* The more experience you have using a certain concept, the less cognitive load it creates for you.

#### Refactoring code to reduce cognitive load

* In most cases, refactoring is done to make it easier to maintain the resulting code
  * But code that is more maintainable in the long run is not always more readable now.
* In many cases these refactorings are temporary
  * only meant to allow you understand the code
  * can be rolled back once your understanding is solidified

#### Refactoring 1 - Inlining Code

* When reading a call to a method with a vague name, you will need to spend some time up front to understand what the method does
* Inlining the method lowers your extraneous cognitive load
  * Within the new context, you might also be able to choose better name for the method

#### Refactoring 2 - Replacing unfamiliar language constructs

Example - **Lambdas** : if lambdas are new to you, this code might cause too much extraneous cognitive load

* If you feel that you are struggling with the lambda expression :
  * Simply rewrite the code to use a regular function temporarily
  * Other examples : Ternary operators

{% tabs %}
{% tab title="Lambdas" %}
```java
Optional<Product> product = productList.stream()
        .filter(p -> p.getId() == id)
        .findFirst();
```
{% endtab %}

{% tab title="Reduced load" %}
```java
public static class Toetsie implements Predicate <Product>{
    private int id;
    Toetsie(int id){
        this.id = id
    }
    boolean test(Product p){
        return p.getID() == this.id;
    }
}

Optional<Product> product = productList.stream().
        filter(new Toetsie(id)).
        findFirst();
```
{% endtab %}
{% endtabs %}

* What is easy to read depends on your prior knowledge
  * There is no shame in helping yourself understand code by translating it to a more familiar form

{% hint style="success" %}
**CODE SYNONYMS ARE GREAT ADDITIONS TO A FLASHCARD DECK** 

While there’s no shame in changing code temporarily to aid comprehension, this does point to a limitation in your understanding.
{% endhint %}

#### Marking dependencies

There are two ways in which code with a complicated structure can overload the working memory :

* You do not know exactly which parts of the code you need to read
  * read more of the code than is needed
  * may be more than your working memory is able to process
* With code that is highly connected, your brain is trying to do two things at the same time : 
  * Understand individual lines of code
  * Understand the structure of the code to decide where to continue reading

{% hint style="success" %}
When you reach the limits of your working memory, you can **use a memory aid** to help you focus on the right parts of the code. 
{% endhint %}

#### Marking dependencies - Create a dependency graph

* Print out the code, or convert it to a PDF
* Open it on a tablet so you can make annotations digitally
* Circle all the variables

![](../../../.gitbook/assets/image%20%28672%29.png)

* Link similar variables
  * draw lines between occurrences of the same variable
  * helps you to understand where data is used in the program

![](../../../.gitbook/assets/image%20%28671%29.png)

* Circle all method/function calls
* Link methods/functions to their definitions
* Circle all instances of classes
* Draw a link between classes and their instances

Now have a reference that you can refer to for information about the code’s structure :

* Saving you the effort of, for example, having to search for definitions 
* While also deciphering the meaning of the code

#### Marking dependencies - Using a state table

{% hint style="success" %}
A state table focuses on the values of variables rather than the structure of the code. It has columns for each variable and lines for each step in the code.
{% endhint %}

**How to ?**

1. Make a list of all the variables
2. Create a table and give each variable its own column
3. Add one row to the table for each distinct part of the execution of the code.
   * Rows in the state table represent separate parts of the dependencies
4. Execute each part of the code and write down the value each variable has afterward in the correct row and column. 

![](../../../.gitbook/assets/image%20%28669%29.png)

  
Once you’ve prepared the table, work your way through the code and calculate the new value of each variable for each row in the state table. 

> The process of mentally executing code is called _**tracing or cognitive compiling.**_

#### Combining state tables and dependency graphs

These techniques focus on different parts of the code :

* Dependency graph draws your attention to how the code is organized
* The state table captures the calculations in the code

## Part 2. On thinking about code

### 5. Reaching a deeper understanding of code

#### Roles of variables \(play a central role\)

{% hint style="success" %}
Understanding what types of information variables hold is key to being able to reason about and make changes to code.
{% endhint %}

The reason that variables are hard to understand is that most programmers do not have a good schema in their long-term memory to relate variables.

With just **11 roles**, you can describe almost all variables : \(distinguished by Sajaniemi\)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Role</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Examples</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Fixed value</td>
      <td style="text-align:left">Variable whose value does not change after initialization plays the role
        of a fixed value.</td>
      <td style="text-align:left">
        <ul>
          <li>pi</li>
          <li>data read from a file</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Stepper</td>
      <td style="text-align:left">When iterating in a loop : always a variable that is stepping through
        a list of values</td>
      <td style="text-align:left">i in for loop</td>
    </tr>
    <tr>
      <td style="text-align:left">Flag</td>
      <td style="text-align:left">A variable used to indicate that something has happened or is the case</td>
      <td
      style="text-align:left">
        <ul>
          <li>are is_set</li>
          <li>is_available</li>
          <li>is_error</li>
        </ul>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">Walker</td>
      <td style="text-align:left">A walker is a variable that traverses a data structure in a way that is
        unknown before the loop starts.</td>
      <td style="text-align:left">a search index in a binary tree</td>
    </tr>
    <tr>
      <td style="text-align:left">Most-recent holder</td>
      <td style="text-align:left">A variable that holds the latest value encountered in going through a
        series of values.</td>
      <td style="text-align:left">store the latest line read from a file : line = file.readline()</td>
    </tr>
    <tr>
      <td style="text-align:left">Most-wanted holder</td>
      <td style="text-align:left">Often when you are iterating over a list of values, you are doing that
        to search for a certain value. The variable that holds that value, or the
        best value found so far, is what we call a most-wanted holder.</td>
      <td
      style="text-align:left">
        <ul>
          <li>minimum value</li>
          <li>maximum value</li>
          <li>the first value meeting a certain condition</li>
        </ul>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">Gatherer</td>
      <td style="text-align:left">A variable that collects data and aggregates it into one value.</td>
      <td
      style="text-align:left">sum = 0 that uses in a loop</td>
    </tr>
    <tr>
      <td style="text-align:left">Container</td>
      <td style="text-align:left">Any data structure that holds multiple elements that can be added and
        removed.</td>
      <td style="text-align:left">
        <ul>
          <li>lists</li>
          <li>arrays</li>
          <li>trees</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Follower</td>
      <td style="text-align:left">Some algorithms require you to keep track of a previous or subsequent
        value. A variable in this role is called a follower, and <em>is always coupled to another variable</em>.</td>
      <td
      style="text-align:left">A pointer that points to a previous element in a linked list</td>
    </tr>
    <tr>
      <td style="text-align:left">Organizer</td>
      <td style="text-align:left">
        <p>Sometimes a variable has to be transformed in some way for further processing.</p>
        <p>Often, they are temporary variables</p>
      </td>
      <td style="text-align:left">Store a sorted version of a given list</td>
    </tr>
    <tr>
      <td style="text-align:left">Temporary</td>
      <td style="text-align:left">
        <p>Variables that are used only briefly.</p>
        <p>Used to swap data, or to store the result of a computation that is used
          multiple times.</p>
      </td>
      <td style="text-align:left">often called temp or t</td>
    </tr>
  </tbody>
</table>

![Variable roles cheat sheet](../../../.gitbook/assets/image%20%28668%29.png)



For most professional programmers :

* The roles in Sajaniemi’s framework will be somewhat familiar \(maybe by other names\)
* Rather than introducing new concepts, the purpose of this list is to **give you a new vocabulary to use when discussing variables**.

You can create a set of icons corresponding to the 11 roles that a variable can play according to Sajaniemi’s framework, and use them to mark the roles of variables in unfamiliar code.

![Felienne&apos;s variable roles icons](../../../.gitbook/assets/image%20%28674%29.png)

![](../../../.gitbook/assets/image%20%28670%29.png)

#### Gaining a deeper knowledge of programs

* Text knowledge vs plan knowledge
  * _**Text structure knowledge**_ : means knowing the syntactic concepts used in code
  * _**Plan knowledge**_ : means understanding the intentions of the code’s creator
* 4 steps commonly taken when moving from superficial knowledge of a program to deeper understanding are: 
  1. Find a focal point
     * Start your exploration of the code at a certain focal point. 
     * It may be the main\(\) method 
  2. Expand knowledge from the focal point.
     * Look for relationships in the code. 
     * Starting at the focal point, circle all the relevant entities \(variables, methods, and classes\) that play a role 
  3. Understand a concept from a set of related entities. 
     * There are several lessons from the lines highlighted
       * Is there a method that is called in several places within the slice you’ve highlighted? 
       * That method likely plays a large role in the codebase and warrants further investigation 
       * Once you have investigated the important locations further, you can create a list of all related classes 
  4. Understand concepts across multiple entities.
     * Get a high-level understanding of the different concepts in the code 
     * What are you allowed to do, and what is forbidden? 
       * For example, will an error be thrown if you add a third node or is that up to the user?

#### Reading text is similar to reading code

Evidence from fMRI about what code does in the brain

* Siegmund's findings reliably showed that program comprehension activates five Brodmann areas, all located in the left hemisphere of the brain. 
* The regions are BA6, BA21, BA40, BA44, and BA47
  * BA21, BA44, and BA47 are related to natural languages

![](../../../.gitbook/assets/image%20%28665%29.png)

{% hint style="success" %}
There are many similarities between reading code and reading natural language, and your ability to learn a natural language can be a predictor of your ability to learn to program.
{% endhint %}

> If you can learn English, you can learn Clojure !!!

#### Text comprehension strategies applied to code

There has been a lot of research into effective reading strategies and how to learn them. Strategies for reading comprehension can be roughly divided into these seven categories : 

* _**Activating**_—Actively thinking of related things to activate prior knowledge
  * Actively thinking about code elements will help your working memory to find relevant information stored in the LTM
  * That might be helpful in comprehending the code at hand 
* _**Monitoring**_—Keeping track of your understanding of a text
  * When reading code, it is important to keep track of what you are reading and whether or not you understand it

![](../../../.gitbook/assets/image%20%28673%29.png)

* _**Determining importance**_—Deciding what parts of a text are most relevant
  * What matters is that you think about which parts of the code are likely to have the most influence on the program’s execution.
* _**Inferring**_—Filling in facts that are not explicitly given in the text
  * Inferring the meaning of variable names
* _**Visualizing**_—Drawing diagrams of the read text to deepen understanding
  * One technique that can be helpful for very complex code of which a deeper understanding is needed is to list all operations in which variables are involved.
* _**Questioning**_—Asking questions about the text at hand 
  * Asking yourself questions while reading code will help you understand the code’s goals and functionality.
  * Ex : What are the five most central concepts of the code? \(identifier names, themes, classes, or information found in comments\), what strategies did you use to identify the central concepts?
* _**Summarizing**_—Creating a short summary of a text
  * Writing a summary of code in natural language will help you gain a deeper understanding of what’s happening in that code

![](../../../.gitbook/assets/image%20%28664%29.png)

### 6. Getting better at solving programming problems

* Models are simplified representations of reality
  * The main goal = support you in thinking about a problem and ultimately also solving the problem
* How you represent a problem can heavily influence the way you think about it
  * **For example :** thinking of customers as a list versus as a collection can influence how you store and analyze customer objects
* Mental models are mental representations that we form while thinking of problems. 
  * People can hold multiple mental models that can compete with each other. 
* Notional machines are abstract versions of how a real computer functions that are used when explaining programming concepts and reasoning about programming.

### 7. Misconceptions: bugs in thinking

* Sometimes bugs are the result of sloppiness :
  * For example when you forget to close a file or make a typo in a filename.
  * More often though, bugs are the result of a mistake in thinking.

#### Why learning a second programming language is easier than learning the first one

* Keywords and mental models that are stored in your long-term memory can help you comprehend code Sometimes, when you’ve learned something, that knowledge is also useful in another domain. 
  * This is called **transfer**. 
  * Transfer happens when information that you already know helps you to do new things.
* When you activate your working memory by thinking about a new programming concept
  * The LTM is also activated and starts a search for relevant information.

![](../../../.gitbook/assets/image%20%28667%29.png)

_**Transfer of learning**_ happens when you can apply things that you already know in entirely unfamiliar situations. When people are talking about cognitive science and use the term transfer, they almost always mean transfer of learning.

#### Different forms of transfer

* High and Low-road transfer
  * Transfer of automatized skills is called low-road transfer. 
    * In programming, low-road transfer might occur if you use Ctrl-C and Ctrl-V in a new editor without thinking about it. 
  * Transfer of more complex tasks is called high-road transfer. 
    * When high-road transfer occurs, you are often aware that it is happening
    * _**Ex**_ : you might assume that you need to declare a variable in a new programming language because you know that is the case in most languages.
* Near and far transfer :
  * Near transfer happens when knowledge transfers from domains that are seen as close to each other :
    * like calculus and algebra
    * C\# and Java 
  * Far transfer when skills transfer between very different domains
    * like Latin and logic
    * Java and Prolog

> Sometimes existing knowledge helps you learn faster or perform new tasks better. This is called **positive transfer**.

#### Misconceptions: bugs in thinking 

* When existing knowledge prevents you from learning something new, we call this **negative transfer**.
  * Wrong assumptions based on previous leraning
  * _**Ex**_ : Exception in java vs C\#
    * Similar languages but not identical
    * Checked Exceptions in java \(exceptions checked at compile-time\)
      * No try / catch -&gt; will not compile
    * People from C\# won't realize these exceptions from what the are used to
    * Those people have the wrong mental model, but they think they have the right one! 
* You can use positive transfer to learn new things more effectively by **actively searching for related information in your long-term memory** \(for example, by elaboration, as covered earlier in the book\).
* You may hold misconceptions, which occur when you are sure you are right but are actually wrong
* Misconceptions are not always addressed by simply realizing or being told that you are wrong. 
  * For misconceptions to be fixed, you need a new mental model to replace the old, wrong model.
* Even if you have learned a correct model, there is always the risk that you will fall back to using the misconception. 
* Use tests and documentation within a codebase to help prevent misconceptions. 

## Part 3. On writing code better

### 8. How to get better at naming things

* **Good names** help to activate your LTM to find relevant information that you already know about the domain of the code
* **Bad names** can lead you to make assumptions about the code leading to misconceptions.
* 4 main reasons **why** identifier names matter :
  * _Names make up a large part of codebases_
    * Eclipse source code : tokens = 33%, characters = 72%
  * _Names play a role in code reviews_
    * Analyzed over 170 reviews with over 1000 remarks in them
      * **Findings** : 
        * 1 in four code reviews contained remarks related to naming
        * Remarks about identifier names occurred in 9% of all code reviews.
    * cf Miltiadis Allamanis study
  * _Names are the more accessible form of documentation_
    * Serve as an important type of documentation : right inside the codebase
  * _Names can serve as beacons_
    * Help readers make sense of code

