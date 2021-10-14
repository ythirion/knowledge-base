---
description: by Felienne Hermans
---

# The Programmer's Brain

## Pitch

**Your brain responds in a predictable way when it encounters new or difficult tasks. This unique book teaches you concrete techniques rooted in cognitive science that will improve the way you learn and think about code.**\
\
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

![](<../../.gitbook/assets/image (655).png>)

## **Infographic**

![Programmer's brain infographic by Yoan Thirion](<../../.gitbook/assets/Programmers brain (1).png>)

{% file src="../../.gitbook/assets/Programmers brain (2).pdf" %}
Programmer's brain infographic (Hi resolution)
{% endfile %}

## **Part 1. On Reading Code Better**

### 1. Decoding your confusion while coding

* Confusion = part of programming.
  * When you learn a new programming language, concept, or framework
    * New ideas might scare you
  * When reading unfamiliar code or code that you wrote a long time ago, you might not understand what the code does or why it was written the way it is
  * Whenever you start to work in a new business domain, new terms and jargon can all bump into each other in your brain
* 3 types of confusion in code
  * Lack of knowledge

![](<../../.gitbook/assets/image (656).png>)

* Lack of easy-to-access information
  * The information about exactly how _toBinaryString()_ works is not readily available
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

![](<../../.gitbook/assets/image (657).png>)

#### Different cognitive processes that affect coding

![](<../../.gitbook/assets/image (658).png>)

An overview of the three cognitive processes that this book covers: STM, LTM, and working memory.

1. Information coming into your brain. 
2. Information that proceeds into your STM
3.  Information traveling from the STM into the working memory, where it’s combined with information from the LTM (arrow 4).

    > _Working memory is where the information is processed while you think about it._

#### Mapping between confusion and cognitive processes

* Lack of knowledge -> Issue in long-term memory 
* Lack of information -> Issue in short-term memory 
* Lack of processing power -> Issue in working memory

#### Cognitive processes and programming

* Long-term memory
  * First cognitive process that is used while programming is long-term memory
  * This can store your memories for a very long time
  * Like the** hard drive** of your brain
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
Research indicates that almost **60% of programmers’ time** is spent understanding code, rather than writing code.\[[1](https://ieeexplore.ieee.org/abstract/document/7997917)] Thus, improving how quickly you can read code, without losing accuracy, **can help you improve your programming skills substantially**.
{% endhint %}

> "Programs must be written for people to read and only incidentally for machines to execute.” - Structure and Interpretation of Computer Programs by Harold Abelson, Gerald Jay Sussman, and Julie Sussman (MIT Press, 1996) 

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
    * Experts grouped info in logical ways -> chunks
    * He considered “Sicilian opening,” for example, as one chunk,
      * Which can fit into one slot in short-term memory. 
  * The theory of chunks also adequately explains why both types of players performed equally in experiment 2 (random setup)

#### Chunking in code

{% hint style="success" %}
The more information you have stored about a specific topic, the easier it is to effectively divide information into chunks.
{% endhint %}

In 1981 [Katherine McKeithen](https://www.researchgate.net/publication/222462455\_Knowledge_Organization_and_Skill_Differences_in_Computer_Programmers), a researcher at Bell Labs, tried to repeat de Groot’s experiments on programmers :

![](<../../.gitbook/assets/image (659).png>)

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
  * Low-level comments such as “increment i (by one)” after a line that reads i++;
    * can create a burden on the chunking process
* **Leave Beacons**
  * Beacons are parts of a program that help a programmer to understand what the code does like a line of code even part of a line of code, that your eye falls on which "Now I see"
  * Provide an important signaling service for programmers during the comprehension process
    * They often act as a trigger for programmers to confirm or refute hypotheses about the source
  * 2 types
    * Simple beacons :
      * Self-explaining syntactic code elements : meaningful variable names, operators such as +, >, and && and structural statements such as if, else, and so on can be considered simple beacons too
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

![example of flashcards on Brainscape](<../../.gitbook/assets/image (660).png>)

_**When to use them ?**_

* Use them often to practice
* Use Apps like [**Brainscape**](https://www.brainscape.com), Anki, Quizlet, that allow you to create your own digital flashcards
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

![Tally on flashcards](<../../.gitbook/assets/image (661).png>)

#### How to not forget things

* The big problem with your **LTM** : _you cannot remember things for a long time without extra practice_
* The decay for LTM is not seconds, like that of the STM
  * But it is still a lot shorter than you might think
  * `After 2 days, just 25% of the knowledge remains in your LTM`

![Forgetting curve](<../../.gitbook/assets/image (662).png>)

#### Why do we forget memories?

* Storage of memories in the brain is not based on zeros and ones
  * BUT it does share a name with how we store information to disk: encoding
* Memories in the brain are organized in a network structure
  * Because facts are connected to large numbers of other facts

![on the left, a hierarchical filesystem; on the right, memories organized as a network](<../../.gitbook/assets/image (663).png>)

* Memories are stored with associations, or relationships to each other

#### Spaced Repetition

* You remember the longest if you study over a longer period of time
  * In contrast with formal education, where we try to cram all the knowledge into one semester
* **Revisiting your set of flashcards once a month** 
  * Will be enough to help your memory in the long run, and it’s also relatively doable!

{% hint style="success" %}
The biggest takeaway from this section is that the best way that science knows to prevent forgetting is to practice regularly._** **_Each repetition strengthens your memory. 

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
      * a name, a song, a phone number, the syntax of the filter() function in JavaScript
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
    * Remember a phone number -> use your STM
    * Add integers -> use your working memory
* What happens in the working memory when you read code?
  * Like the short-term memory, the working memory is only capable of processing between 2 and 6 things at a time
  * In the context of working memory, this capacity is known as the _**cognitive load**_.

Different types of cognitive load :

| Load Type       | Description                                                   |
| --------------- | ------------------------------------------------------------- |
| Intrinsic load  | How complex the problem is in itself                          |
| Extraneous load | What outside distractions add to the problem                  |
| Germane load    | Cognitive load created by having to store your thought to LTM |

#### Intrinsic cognitive load when reading code

Intrinsic cognitive load is cognitive load caused by features of a problem that the problem contains by nature

Example : A geometry problem in which the lengths of two sides of a triangle are given and the third one needs to be calculated. This can be a problem that is hard to solve, depending on your prior knowledge. However, _**the problem itself cannot be made any simpler without changing it. **_

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
**CODE SYNONYMS ARE GREAT ADDITIONS TO A FLASHCARD DECK **

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

![](<../../.gitbook/assets/image (664).png>)

* Link similar variables
  * draw lines between occurrences of the same variable
  * helps you to understand where data is used in the program

![](<../../.gitbook/assets/image (665).png>)

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

![](<../../.gitbook/assets/image (666).png>)

\
Once you’ve prepared the table, work your way through the code and calculate the new value of each variable for each row in the state table. 

> The process of mentally executing code is called _**tracing or cognitive compiling.**_ 

#### Combining state tables and dependency graphs

These techniques focus on different parts of the code :

* Dependency graph draws your attention to how the code is organized
* The state table captures the calculations in the code

## Part 2. On thinking about code

### 5. Reaching a deeper understanding of code

#### Roles of variables (play a central role)

{% hint style="success" %}
Understanding what types of information variables hold is key to being able to reason about and make changes to code.
{% endhint %}

The reason that variables are hard to understand is that most programmers do not have a good schema in their long-term memory to relate variables.

With just **11 roles**, you can describe almost all variables : (distinguished by Sajaniemi)

| Role               | Description                                                                                                                                                                                                     | Examples                                                                                                  |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Fixed value        | Variable whose value does not change after initialization plays the role of a fixed value.                                                                                                                      | <ul><li>pi </li><li>data read from a file</li></ul>                                                       |
| Stepper            | When iterating in a loop : always a variable that is stepping through a list of values                                                                                                                          | i in for loop                                                                                             |
| Flag               | A variable used to indicate that something has happened or is the case                                                                                                                                          | <ul><li>are is_set</li><li>is_available</li><li>is_error</li></ul>                                        |
| Walker             | A walker is a variable that traverses a data structure in a way that is unknown before the loop starts.                                                                                                         | a search index in a binary tree                                                                           |
| Most-recent holder | A variable that holds the latest value encountered in going through a series of values.                                                                                                                         | store the latest line read from a file : line = file.readline()                                           |
| Most-wanted holder | Often when you are iterating over a list of values, you are doing that to search for a certain value. The variable that holds that value, or the best value found so far, is what we call a most-wanted holder. | <ul><li>minimum value</li><li>maximum value</li><li>the first value meeting a certain condition</li></ul> |
| Gatherer           | A variable that collects data and aggregates it into one value.                                                                                                                                                 | sum = 0 that uses in a loop                                                                               |
| Container          | Any data structure that holds multiple elements that can be added and removed.                                                                                                                                  | <ul><li>lists</li><li>arrays</li><li>trees</li></ul>                                                      |
| Follower           | Some algorithms require you to keep track of a previous or subsequent value. A variable in this role is called a follower, and _is always coupled to another variable_.                                         | A pointer that points to a previous element in a linked list                                              |
| Organizer          | <p>Sometimes a variable has to be transformed in some way for further processing. </p><p>Often, they are temporary variables </p>                                                                               | Store a sorted version of a given list                                                                    |
| Temporary          | <p>Variables that are used only briefly. </p><p>Used to swap data, or to store the result of a computation that is used multiple times.</p>                                                                     | often called temp or t                                                                                    |

![Variable roles cheat sheet](<../../.gitbook/assets/image (667).png>)



For most professional programmers :

* The roles in Sajaniemi’s framework will be somewhat familiar (maybe by other names)
* Rather than introducing new concepts, the purpose of this list is to **give you a new vocabulary to use when discussing variables**.

You can create a set of icons corresponding to the 11 roles that a variable can play according to Sajaniemi’s framework, and use them to mark the roles of variables in unfamiliar code.

![Felienne's variable roles icons](<../../.gitbook/assets/image (668).png>)

![](<../../.gitbook/assets/image (669).png>)

#### Gaining a deeper knowledge of programs

* Text knowledge vs plan knowledge
  * _**Text structure knowledge**_ : means knowing the syntactic concepts used in code
  * _**Plan knowledge**_ : means understanding the intentions of the code’s creator
* 4 steps commonly taken when moving from superficial knowledge of a program to deeper understanding are: 
  1. Find a focal point
     * Start your exploration of the code at a certain focal point. 
     * It may be the main() method 
  2. Expand knowledge from the focal point.
     * Look for relationships in the code. 
     * Starting at the focal point, circle all the relevant entities (variables, methods, and classes) that play a role 
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

![](<../../.gitbook/assets/image (671).png>)

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

![](<../../.gitbook/assets/image (672).png>)

* _**Determining importance**_—Deciding what parts of a text are most relevant
  * What matters is that you think about which parts of the code are likely to have the most influence on the program’s execution.
* _**Inferring**_—Filling in facts that are not explicitly given in the text
  * Inferring the meaning of variable names
* _**Visualizing**_—Drawing diagrams of the read text to deepen understanding
  * One technique that can be helpful for very complex code of which a deeper understanding is needed is to list all operations in which variables are involved.
* _**Questioning**_—Asking questions about the text at hand 
  * Asking yourself questions while reading code will help you understand the code’s goals and functionality.
  * Ex : What are the five most central concepts of the code? (identifier names, themes, classes, or information found in comments), what strategies did you use to identify the central concepts?
* _**Summarizing**_—Creating a short summary of a text
  * Writing a summary of code in natural language will help you gain a deeper understanding of what’s happening in that code

![](<../../.gitbook/assets/image (673).png>)

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

![](<../../.gitbook/assets/image (674).png>)

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
    * C# and Java 
  * Far transfer when skills transfer between very different domains
    * like Latin and logic
    * Java and Prolog

> Sometimes existing knowledge helps you learn faster or perform new tasks better. This is called **positive transfer**. 

#### Misconceptions: bugs in thinking 

* When existing knowledge prevents you from learning something new, we call this **negative transfer**.
  * Wrong assumptions based on previous leraning
  * _**Ex**_ : Exception in java vs C#
    * Similar languages but not identical
    * Checked Exceptions in java (exceptions checked at compile-time)
      * No try / catch -> will not compile
    * People from C# won't realize these exceptions from what the are used to
    * Those people have the wrong mental model, but they think they have the right one! 
* You can use positive transfer to learn new things more effectively by **actively searching for related information in your long-term memory** (for example, by elaboration, as covered earlier in the book).
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
* Choosing a good name is important
  * Many different researchers have tried to define what makes a variable name good or bad
  * **Different perspectives **on this question

#### Perspective 1 :  A good name can be defined syntactically

Simon Butler, associate Senior Lecturer at the Open University in the UK, created a list of issues with variable names 

| Name                                      | Description                                                                                                                          | Example of a bad name                                               |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| Capitalization Anomaly                    | Identifiers should use proper capitalization.                                                                                        | page counter                                                        |
| Consecutive underscores                   | Identifiers should not contain multiple consecutive underscores.                                                                     | page\_\_counter                                                     |
| Dictionary words                          | Identifiers should consist of words, and only use abbreviations when they are more commonly used than the full words.                | pag_countr                                                          |
| Number of Words                           | Identifiers should be composed of between two and four words.                                                                        | <p>page_counter_ </p><p>converted_and_ </p><p>normalized_value </p> |
| Excessive words                           | Identifiers should not be composed out of more than four words.                                                                      | <p>page_counter_ </p><p>converted_and_ </p><p>normalized_value </p> |
| Short Identifier Name                     | Identifiers should not consist of fewer than eight characters, except for c, d, e, g, i, in, inOut, j, k, m, n, o, out, t, x, y, z.  | P, page                                                             |
| Enumeration Identifier Declaration Order  | Unless there are clear reasons to do so, enumeration types should be declared in alphabetical order.                                 | CardValue = {ACE, EIGHT, FIVE, FOUR, JACK, KING...}                 |
| External Underscores                      | Identifiers should not begin or end in an underscore.                                                                                | \__page_counter\_                                                   |
| Identifier Encoding                       | Type information should not be encoded in identifier names using Hungarian notation or similar.                                      | int_page_counter                                                    |
| Long Identifier Name                      | Long identifier names should be avoided where possible.                                                                              | <p>page_counter_ </p><p>converted_and_ </p><p>normalized_value </p> |
| Naming Convention Anomaly                 | Identifiers should not combine uppercase and lowercase characters in non-standard ways.                                              | Page_counter                                                        |
| Numeric Identifier Name                   | <p>Identifiers should not be composed entirely of </p><p>numeric words or numbers. </p>                                              | FIFTY                                                               |

#### Perspective 2 :  Names should be consistent in a codebase

* If the same word is used for similar objects across a codebase
* it will be easier for the brain to find relevant related information stored in the LTM
* Proved by Allamanis work on code reviews

#### Formatting names support your STM

It helps make sense of the names you are reading

| Researcher  | Perspective                                   | Fits cognition because                       |
| ----------- | --------------------------------------------- | -------------------------------------------- |
| Allamanis   | Names should be consistent across a codebase  | Supports chunking                            |
| Butler      | Syntactically similar names                   | Lower cognitive load while processing names  |

#### Clear names help your LTM

![](<../../.gitbook/assets/image (675).png>)

* When you read a name, the name firstly will be broken up into separate chunks
* The name is then sent to the working memory
* At the same time, the long-term memory is searched for information related to the different parts of the variable name
* Related information from the long-term memory is also sent to the WM

#### Variable names can contain different types of information to help you understand them

![](<../../.gitbook/assets/image (676).png>)

Names can support your thinking about :

* Domain of the code
  * Word like “customer” will have all sorts of associations in your LTM
  * A customer is probably buying a product, needs a name and an address, and so on
* Programming
  * Concept like a tree will also unlock information from the LTM
  * A tree has a root, can be traversed and flattened, and so on
* Conventions 
  * Contains information about conventions your LTM is aware of
  * For example, a variable named j will remind you of a nested loop

#### To abbreviate or not to abbreviate ?

Hofmeister (researcher at the University of Passau)

* 72 professional C# developers
* Found that participants found on average **19% more defects per minute** when reading programs in which the identifiers were words
  * Compared to letters and abbreviations.

#### Snake case or camel Case ?

Study investigating the differences in comprehension between variables written in camelCase and those written in snake_case : [https://ieeexplore.ieee.org/abstract/document/5090039](https://ieeexplore.ieee.org/abstract/document/5090039) :

* Show that the use of camelCase leads to higher accuracy among both programmers and non-programmers
* There is a 51.5% higher chance of selecting the right option for identifiers written in the camelCase style.

#### Code with bad names has more bugs

Study available here : [http://oro.open.ac.uk/17007/1/butler09wcreshort_latest.pdf](http://oro.open.ac.uk/17007/1/butler09wcreshort_latest.pdf)

#### Feitelson’s three-step model for better variable names

1. Select the concepts to include in the name
   * Domain-specific
   *   Intent of the name : should represent what information the object

       holds and what it is used for
   * When you feel the need to write a comment to explain the name
     * wording from the comment should probably be included in the variable name
2. Choose the words to represent each concept
   * A project lexicon : important definitions are noted and alternatives for synonyms are registered
   * Can help programmers select names consistently
3. Construct a name using these words
   * Constructing a name using the chosen words
   * Comes down to selecting one of the naming molds

### 9. Avoiding bad code and cognitive load

#### Why code with code smells creates a lot of cognitive load

| Code Smell                                     | Explanation                                                                                                                                                                    | Level           |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------- |
| Long method                                    | A method consists of many lines of code, performing different calculations.                                                                                                    | Method level    |
| Long parameter list                            | A method has many parameters                                                                                                                                                   | Method level    |
| Switch statements                              | Code contains large switch statements, while polymorphism could also be used to ease the code                                                                                  | Method level    |
| Alternative classes with different interfaces  | Two different classes seem different at first glance but have similar fields and methods                                                                                       | Class level     |
| Primitive obsession                            | Overuse of primitive types in a class                                                                                                                                          | Class level     |
| Incomplete library class                       | Methods are added to ‘random’ classed instead of to a library class                                                                                                            | Class level     |
| Large class                                    | A class has too many methods and fields, and it is not clear what abstraction the class provides.                                                                              | Class level     |
| Lazy class                                     | A class is doing too little to justify its existence                                                                                                                           | Class level     |
| Data class                                     | Classes should not contain just data, they should contain methods as well                                                                                                      | Class level     |
| Temporary field                                | Classes should not contain unnecessary temporary fields                                                                                                                        | Class level     |
| Data clumps                                    | Data are often used in combination belong together and should be stored together in a class or structure                                                                       | Class level     |
| Divergent change                               | Code changes should in general be local, preferably to one class. If you have to make many different changes in different places, that indicates a poor structure in the code  | Codebase level  |
| Feature Envy                                   | When methods on class A are references a lot from class B, they belong in B and should be moved there.                                                                         | Codebase level  |
| Inappropriate intimacy                         | Classes should not be connected to other classes extensively                                                                                                                   | Codebase level  |
| Duplicated code or code clones                 | The same or very similar code occurs in multiple different places in a codebase                                                                                                | Codebase level  |
| Comments                                       | Comments should describe why the code is there not what it does                                                                                                                | Codebase level  |
| Message chains                                 | Long chains of message calls, where methods call methods call methods, etc                                                                                                     | Codebase level  |
| Middle Man                                     | If a class is delegating too much responsibility, should it exist?                                                                                                             | Codebase level  |
| Parallel inheritance                           | When you make a subclass of one class, you need to make a subclass of another. This indicates that the functionality of both classes might belong in one class.                | Codebase level  |
| Refused bequest                                | When classed inherit behavior that they do not use, the inheritance might not be necessary.                                                                                    | Codebase level  |
| Shotgun surgery                                | Code changes should in general be local to one class. If you have to make many different changes in different places, that indicates a poor structure in the code              | Codebase level  |
| Speculative generality                         | Do not add code to a codebase “just in case”, only add features that are needed.                                                                                               | Codebase level  |

#### How code smells harm cognition

Knowing what we know about the working memory : we can understand why Long parameter list and Complex switch statements are hard to read :

* Both smells are related to an overloaded working memory
* Newer research even suggests that the capacity might be as low as 6
* While reading code, it will be impossible to hold all the parameters in working memory
  * as such, the method will be harder to understand

#### The influence of bad names on cognitive load

{% hint style="warning" %}
Code smells are parts of code that suffer from structural anti-patterns: the code is correct, but not structured in a way that is easy to process.
{% endhint %}

**Arnaoudova’s six categories of linguistic anti-patterns :** 

* Methods that do more than they say 
* Methods that say more than they do 
* Methods that do the opposite than they say 
* Identifiers whose name says that they contain more than what the entity contains
* Identifiers whose name says that they contain less than what the entity contains
* Identifiers whose name says that the opposite than the entity contains

List of Linguistic Anti-patterns available [here](https://veneraarnaoudova.com/linguistic-anti-pattern-detector-lapd/LAs/)

She studied their occurrence in 7 open-source projects :

* 11% of setters also return a value in addition to setting a field
* 2.5% of methods, the method name and the corresponding comment gave opposite descriptions of the working of the method
* 64% of identifiers starting with ‘is’ turned out not to be Boolean

**Measuring Cognitive Load**

* Cognitive load = the overloading of the working memory
* How to measure it ?
  * PAAS scale : participants are asked to self-rate the cognitive load on this nine-point scale ( from "very, very low mental effort" to "very high mental effort")
  * Skin based measurement : skin temperature / sweat
  * Brain based measurement : fMRI scanner
  * Electroencephalogram
  * Functional near infra-read spectroscopy (FNIRS)
* Results from the fNIRS device :
  * Presence of linguistic anti-patterns in the source code significantly increases the average oxygenated blood flow that a participant experiences
  * aka cognitive load that is induced by the snippet is higher

#### Why linguistic anti-patterns cause confusion

* When reading a conflicting name
  * The wrong information will be presented to you
  * Ex : reading a function name retrieveElements() 
    * Think of information on functions returning a list of things
    * Gives you the idea you could sort, filter, or slice the returning element
    * While that is not true for a single element
  * Lead to “mischunking”
    * When you are reading a variable name such as isValid
      * Assume the variable is a Boolean
      * No need for your brain to dig deeper
      * By trying to save energy, your brain has made a wrong assumption

### 10. Getting better at solving complex problems

Problem solving means : 

* Traversing the state space in the optimal way
* Reaching the goal state in as few steps as possible

How to ?

1. Understanding the problem
2. Devising a plan
3. Carrying out the plan

#### Types of memories that play a role in problem solving

* LTM can store different types of memory :
  * **Procedural** (or implicit) memory showcases 
    * **How to do something**
    * **Ex : **How to run a bike
  * **Declarative** (explicit) memory consists of memories we are **explicitly aware of (facts you can remember)**, divided into things :
    * You have experienced and that are stored in **episodic** memory
      * memories of experiences
      * **Ex** :  -> meeting your spouse
    * Facts you know that are stored in **semantic** memory
      * Memory for meanings, concepts, facts
      * **Ex** : 5 x 7 = 35

![](<../../.gitbook/assets/image (677).png>)

#### What types of memories play a role when you solve problems ?

{% hint style="success" %}
Research shows that especially **experts** **heavily rely on episodic memory** when solving problems : instead of finding a new solution, they rely on solutions that have previously worked for similar problems.
{% endhint %}

![](<../../.gitbook/assets/image (678).png>)

* Unlearning :
  * Having a lot of implicit memory can harm your flexibility
    * Ex : once you have learned how to touch type on a Qwerty keyboard, learning to use a Dvorak keyboard will be harder than if you had never learned Qwerty
  * Unlearning implicit memory > learned a second programming language with a syntax quite different from the first programming language that you learned
    * Moving from C# to Java

#### Technique 1 : Automatization (creating implicit memories)

{% hint style="success" %}
Once you have **practiced a skill so many times** that you can do it without thinking about it, like walking, reading, or tying your shoelaces, we say that you have **automatized this skill**.
{% endhint %}

Automatization of programming skills is _**key to being able to solve larger and more complex problems :**_

* The more implicit memories you have for programming
  * The easier it will be to solve larger problems
  * Because you will have more cognitive load to spare to think about the problem
* Implicit memories are formed in 3 different phases :
  * **Cognitive phase** : when you learn something new
    * In this phase : a new piece of information needs to be split explicitly in smaller parts and you have to explicitly think about the task at hand
    * That is why it is called the cognitive phase. 
  * **Associative phase** : you need to actively repeat the new information until patterns of response emerge. 
    * You see an opening bracket and you get nervous if you do not see the closing one 
  * **Autonomous phase **: In the autonomous phase (also called the procedural phase) the skill is perfected. 
    * **Ex** : you have reached the autonomous phase when you index into a list and you always do it correctly, no matter the context, the data type or the operations on the list.
    * Here you have automatized the skill 

![](<../../.gitbook/assets/image (679).png>)

**Automatization will make you program quicker **

* By creating a large repository of techniques (skeptics might call them “tricks”) 
  * we can create an ever-growing toolbox of new techniques 
* Gordon Logan, an American psychologist
  * Automatization is done by retrieving memories _from the episodic part of the long-term memory_
  * When you are confronted with a similar task, rather than reasoning about the task---as someone might do who lacks enough instance memories
    * you can remember how you did it before and apply the same method again
  * According to him
    * automatization is complete when you fully rely on episodic memory and do not use any reasoning at all

#### Improving implicit memories

* Use deliberate practice to improve skills
  * Use very small tasks and execute them repeatedly, until you have reached perfection
* When you are struggling with creating for loops without errors
  * Deliberately typing 100 for loops 
    * Building these small skills will help you to solve larger problems with greater ease
    * It frees up cognitive load for larger problems
  * Just like with flashcards, spaced repetition is key to learning
    * **Set some time aside every day to practice and continue until you can consistently perform the tasks without any effort.**

#### Technique 2 : Learning from code and its explanation

* Deliberately study how others have solved problems
  * Study worked examples
  * Worked examples explain how to solve the problems in detail
* Australian professor John Sweller 
  * Sweller taught children mathematics by having them solve algebra equations
  * Frustrated by how little they were learning from only working on traditional algebra problems 
  * _**Experiment**_ : divided the students into two groups, who were both asked to solve typical algebra equations, like a = 7 – 4a, solve for a.
    * Group 2 : received the algebra equations
      * but also received worked examples of the equations
      * Can think of worked examples are something like a recipe which describes in detail the steps that are needed to solve the equations. 
    * Group 2 solved it 5 times faster
    * Here is the kicker: 
      * Children in Group 2 also performed better on different problems
      * For which calculations rules could be used which were present in the recipe, like subtracting the same value from both sides of an equation or dividing both sides of the equation by the same

![](<../../.gitbook/assets/image (680).png>)

#### Using worked examples in your working life

We have seen that explicitly studying code, plus studying the process of how it was created can help you to strengthen your programming skills :

* Collaborate with a colleague
  * start a “code reading club”
    * can exchange code and its explanation, and learn from each other
* Explore github
  * if you choose a repository of which the domain is at least a bit familiar to you, so there are not too many unfamiliar words and domain concepts causing additional extraneous load and you can focus on the programming itself
* Read books / blog post about source code

## **Part 4. On collaborating on Code**

### 11. The act of writing code

* Different activities while programming :
  * CDN is a framework to evaluate the cognitive impact of a programming language or code base
    * Cognitive Dimensions of Notations
  * CDN describes 5 activities
    * **Searching** : looking through a code base, searching for a specific piece of information
      * Location of a bug
      * Calls of a certain method or the location of something (variables, ...)
      * Mainly hard on your short-term memory
      * _**Best supported by making notes to offload some of the memories to paper, or to a separate document on your code**_
    * **Comprehension **: reading and executing code to gain an understanding of its functionality
      * Running test code as complement
    * **Transcription** : the activity where you are “just coding”. 
      * You have a concrete plan of what you want to add or change to the code base, and you are going to do just that.
    * **Incrementation **: mix of all of the above
      * adding a new feature
        * Likely to include both :
          * searching for the location(s) to add code
          * comprehending the existing code to understand where to add code and how to do that
      * if you know the code base very well, your working memory and short-term memory might not be impacted by searching and comprehending the code
    * **Exploration** : you are in essence sketching with code. 
      * Have a vague idea of where you want to go
      * But by the act of programming you are gaining clarity about the domain of the problem and about the programming constructs that you will need to use

![activities and the memory systems they use most](<../../.gitbook/assets/image (681).png>)

#### Programmer, interrupted

* About 20 percent of a developer’s time is spent on interrupts (Van Solingen study)
* According to [Parnin’s study](ttps://ieeexplore.ieee.org/document/5090030) :
  * The average programmer will have just one uninterrupted two-hour session in a day

#### What happens after an interruption?

{% hint style="danger" %}
It takes about a quarter of an hour to start editing code after an interruption.
{% endhint %}

When interrupted during an edit of a method, only 10% of times programmers could resume their work in less than a minute.

#### How to prepare for interruptions better?

3 techniques :

* **Store your mental model **:
  * Nakagawa’s results showed a warm-up period in comprehension activities :
    * Spent on building a mental model of the code at hand
    * If parts of the model are stored apart from the code, that can help quickly regain your mental model.
  * Comments can be an excellent location to leave notes about your mental model.
* **Help your "Prospective memory"**
  * memory of remembering to do something in the future
    * Related to planning / problem solving
  * TODO comments in the part of the code that they are working on to remind them to complete or improve part of the code
  * Parnin also developed a Visual Studio plugin that allows you to support your prospective memory when you have to stop programming
    * Allows to add TODO items to your code
      * and give the TODOs an expiry date
      * so you do not forget to actually work on tasks
    * [https://marketplace.visualstudio.com/items?itemName=chrisparnin.attachables](https://marketplace.visualstudio.com/items?itemName=chrisparnin.attachables)
* **Label subgoals** 
  * explicitly write down into what small steps a problem can be divided.

![](<../../.gitbook/assets/image (682).png>)

#### When to interrupt a programmer?

Be interrupted at more convenient times with FlowLight :

* a physical light that a developer can place on their desk or on top of their screen
* Based on computer-interactions, like typing speeds and mouse clicks
* Detects whether the programmer is deeply engaged in a task and experiencing high cognitive load

### 12. Designing and improving larger systems

#### Assess and improve the usability of existing large codebases

Cognitive Dimensions of Notations :

| Dimension              | Description                                                                                                                                                                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Error-proneness        | In some programming languages it is easier to make a mistake than in other languages (dynamic languages like JS). inconsistent conventions, a lack of documentation or vague names.                                                |
| Consistency            | Another way to examine how people will interact with a programming language or codebase is consistency: how similar are similar things?                                                                                            |
| Diffuseness            | How much room or space a programming construct takes, not only concern the number of lines of code, you could also consider how many chunks the code consists of                                                                   |
| Hidden dependencies    | <p>indicates to what extent dependencies are visible to the user. </p><p>Ex : HTML page with a button controlled by JavaScript, which is stored in a different file.</p>                                                           |
| Provisionality         | How easy it is to 'think using the tool'                                                                                                                                                                                           |
| Viscosity              | <p>how hard it is to make changes in a certain system. </p><p>Typically, codebases written in dynamically typed languages are a bit easier to change.</p>                                                                          |
| Progressive evaluation | how easy it is in a given system to check or execute partial work.Some programming systems allow programmers to do live programming                                                                                                |
| Role expressiveness    | how easy it is to set the role of different code parts in a program. Brackets at the end of a function are an example of role expressiveness.                                                                                      |
| Closeness of mapping   | how close the programming language or the code is to the domain in which problems are solved                                                                                                                                       |
| Hard mental operations | Some systems require a user to think very hard, to perform hard mental operations, outside of the system. For example, asking users to memorize a large number of parameters to call in the right order is a hard mental operation |
| Secondary notation     | indicates the possibility for the programmer to add extra meaning to code, which is not in the formal specification.                                                                                                               |
| Abstraction            | describes whether a user of your system can create their own abstractions that are as powerful as the build-in abstractions.                                                                                                       |
| Visibility             | <p>how easy it is to see different parts of a system. </p><p>In a codebase, it can be hard to see what classes the codebase consists of, especially if code is divided over different files.</p>                                   |

#### Using CDN to improve your codebase

* The list of Cognitive Dimensions can be used as a sort of a checklist for a codebase. 
* Not all dimensions matter for all codebases
  * Investigating each one and deciding how your codebase is doing regularly will help you maintain the usability

#### Design maneuvers and their trade-offs

Making changes to a codebase to improve a certain dimension in a codebase is called a Design Maneuver.

_**Examples**_ :

* adding types to a codebase is a Design Maneuver that improves error-proneness
* Changing function names to be more in line with the domain of the code is a Design Maneuver that improves Closeness of mapping

#### Dimensions and activities

| Dimension               | Helps                                       | Harms          |
| ----------------------- | ------------------------------------------- | -------------- |
| Error-Proneness         | Incrementation                              |                |
| Consistency             | Searching, Comprehension                    | Transcription  |
| Diffuseness             | Searching                                   |                |
| Hidden Dependencies     | Searching                                   |                |
| Provisionality          | Exploration                                 |                |
| Viscosity               | Transcription, Incrementation               |                |
| Progressive evaluation  | Exploration                                 |                |
| Role expressiveness     | Comprehension                               |                |
| Closeness of mapping    | Incrementation                              |                |
| Hard mental operations  | Transcription, Incrementation, Exploration  |                |
| Secondary Notation      | Searching                                   |                |
| Abstraction             | Comprehension                               | Exploration    |
| Visibility              | Comprehension                               |                |

### 13. How to onboard new developers 

#### Issues in the onboarding process

* A senior developer throws lots of new information at a newcomer
  * The amount of information is too much to process
  * Causing high cognitive load
* After the introduction, the senior developer asks the newcomer a question or gives the newcomer a task.
* The newcomer fails
  * Because of the high cognitive load
  * Caused by a combination of a lack of relevant chunks for the domain and/or the programming language, and a lack of automatized skills relevant

{% hint style="success" %}
One of the reasons that more senior people often struggle with effectively teaching and explaining is the "_**curse of expertise**_." Once you have mastered a certain skill sufficiently, you will inevitably forget how hard it was to learn that skill or knowledge.
{% endhint %}

#### How to improve it ?

**Limit tasks to one programming activity :**

* One of the issues in the onboarding scenario above is that you ask the newcomer to perform at least four different activities: 
  * Searching for the right place to implement the feature or for relevant information
  * Comprehending new source code
  * Exploring the codebase to gain a better understanding
  * Incrementing the codebase with a new feature
* During an onboarding process, it is best to specifically choose activities in each of the five categories, and have newcomers **do them one by one**.

| Activity        | Example use to support onboardees                                                            |
| --------------- | -------------------------------------------------------------------------------------------- |
| Exploration     | Browsing the codebase to get a general sense of the codebase                                 |
| Searching       | Find a class that implements a certain interface                                             |
| Transcription   | Give the newcomer a clear plan to implement a certain method which has to be implemented     |
| Comprehension   | Understand aspects of the code, for example summarize a specific method in natural language  |
| Incrementation  | Add a feature to an existing class, including the creation of the plan for the feature.      |

**Support the memory of the onboardee**

* Support the LTM : explain relevant information
  * Prepare the onboarding process for newcomers by deeply understanding the relevant information that plays a role when working with the codebase
  * Separate domain learning from exploring code

![](<../../.gitbook/assets/image (683).png>)

#### Understanding is a better welcome task than building

If you want a newcomer to understand a certain piece of the code, ask them to understand a piece rather than giving them an implementation task. 

For example, ask them to write a summary of an existing class or write down all classes involved in executing a certain feature. \


#### Support the WTM : draw diagrams

#### Read code together

Another technique you can use to onboard newcomers is to read code as a team collaboratively. In Chapter 5, we proposed seven techniques from natural language to be applied to code reading. 

* **Activating.** Actively thinking of related things to activate prior knowledge. 
* **Determining Importance.** Deciding what parts of text are most relevant. 
* **Inferring.** Filling in facts that are not explicitly given in the text. 
* **Monitoring.** Keeping track of you understanding of a text. 
* **Visualizing.** Drawing diagrams of the read text to deepen understanding. 
* **Questioning.** Asking questions about the text at hand. 
* **Summarizing.** Creating a short summary of text. 
