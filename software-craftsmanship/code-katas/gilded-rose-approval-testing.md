---
description: Learn how Approval testing can help you when dealing with legacy code
---

# Gilded Rose \(Approval Testing\)

## Objectives

* Learn a practice that will help you be quickly productive in an unfamiliar environment
* Use Approval Testing to deal with legacy code

### Before we start

* Clone the repository [here](https://github.com/ythirion/GildedRose-kata)
* Make sure you can build it

## Connection

* On a sticky note, write a question you want answered about Approval Testing

## Concepts

### What is Approval Testing ?

**Approval Tests** are also called **Snapshot Tests** or **Golden Master.** 

{% hint style="success" %}
Approval tests work by creating an output that needs human approval / verification. 
{% endhint %}

Once the initial _**output has been defined and “APPROVED”**_ then as long as the _**test provides consistent output then the test will continue to pass**_. 

Once the test provides output that is _**different to the approved output the test will fail**_. The developer then has two choices:

1. If the change in the output was unintended then fix the bug that’s causing the change in the output.
2. “Approve” the new output as the baseline for future tests.

Output can be anything you want, as long as it can be compared to another copy in a consistent manner.

### The difference with Assert-based tests

Unit testing asserts can be difficult to use. Approval tests simplify this by taking a snapshot of the results, and confirming that they have not changed.

In normal unit testing, you say `assertEquals(5, person.getAge())`. Approval tests allow you to do this when the thing that you want to assert is no longer a primitive but a complex object. For example, you can say, `Approvals.verify(person).`

### Main characteristics

* Test cases check actual program output against a previously approved value, and any difference will fail the test.
* Normally, a human inspects and approves some actual program output when creating a test case.
* Raw program output may be processed into a more convenient format before being used for approval and comparison.
* Design a Printer to display complex objects, instead of many assertions.
* If actual program output is not yet available, the _**approved value may be a manual sketch of the expected output \(usefull when you do TDD\)**_.
* _**Approved values are stored separately from the sourcecode for the test case**_, although in the same VCS repository.
* When a test case fails, you can use a tool to inspect the differences and easily update the approved value.

### How to write Approval Tests ?

When you start working on a new feature :

![](../../.gitbook/assets/image%20%28337%29.png)

![](../../.gitbook/assets/image%20%28335%29.png)

### Tools

There are many tools depending the language you use.

The most common one is [ApprovalTests](https://approvaltests.com/) available on a lot of language \(from js to C\# passing through C++, ...\)

![](../../.gitbook/assets/image%20%28327%29.png)

## Concrete Practice

* Read the specifications in the [Readme](https://github.com/ythirion/GildedRose-kata)
* Look at the [code](https://github.com/ythirion/GildedRose-kata/blob/master/Java/src/main/java/com/gildedrose/GildedRose.java)
* Individually :
  * What do you think about this code ?
  * If you have to add a new type of items what would be your strategy ?
  * Think about testing
    * How many tests would you write before being confident enough to refactor the code ?
    * Which ones ?

### Exercise

We have recently signed a supplier of conjured items. This requires an update to our system:

{% hint style="warning" %}
"Conjured" items degrade in Quality twice as fast as normal items
{% endhint %}

### Draw a diagram representing different paths of the updateQuality

![](../../.gitbook/assets/image%20%28332%29.png)

### Add a first test

Based on the specifications write a first test by using junit 5 \(dependency already in your pom\) :

{% code title="GildedRoseTests.java" %}
```java
package com.gildedrose;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.assertEquals;

public class GildedRoseTests {
    @Test
    public void updateQuality() {
        var items = new Item[]{new Item("a common item", 0, 0)};
        var gildedRose = new GildedRose(items);

        gildedRose.updateQuality();
        assertEquals("a common item", gildedRose.items[0].name);
        assertEquals(-1, gildedRose.items[0].sellIn);
        assertEquals(0, gildedRose.items[0].quality);
    }
}
```
{% endcode %}

### Let's use an approval test

* Add ApprovalTests dependency in your pom.xml :

{% code title="pom.xml" %}
```markup
<dependency>
    <groupId>com.approvaltests</groupId>
    <artifactId>approvaltests</artifactId>
    <version>9.1.0</version>
</dependency>
```
{% endcode %}

* Refactor the existing test using ApprovalTests :

{% code title="GildedRoseTests.java" %}
```java
package com.gildedrose;

import org.approvaltests.Approvals;
import org.junit.jupiter.api.Test;

public class GildedRoseTests {
    @Test
    public void updateQuality() {
        var items = new Item[]{new Item("a common item", 0, 0)};
        var gildedRose = new GildedRose(items);

        gildedRose.updateQuality();
        Approvals.verify(gildedRose.items[0]);
    }
}
```
{% endcode %}

* Run the test 
  * Now it should fail ![](../../.gitbook/assets/image%20%28333%29.png)
* ApprovalTests library compares 2 files :
  * _**GildedRoseTests.updateQuality.received.txt**_ that has been generated based on what is inside the verify method call
  * _**GildedRoseTests.updateQuality.approved.txt**_ a content that has already been approved

![](../../.gitbook/assets/image%20%28334%29.png)

* _In this case we have not approved anything and our approved file is empty._

{% hint style="success" %}
_**The actual implementation is functionally good. So we must approve what is currently generated / calculated by the system.**_
{% endhint %}

* Approve the content of the file : 

```java
mv GildedRoseTests.updateQuality.received.txt GildedRoseTests.updateQuality.approved.txt
```

* If you run the test again, it should be green now

{% hint style="success" %}
_When you work with Approval Tests never commit what you receive from the tests verifications but only the generated files \(Golden Master or Snapshot\)_
{% endhint %}

### What about coverage ?

Before making a refactoring a good practice is to be confident about the tests covering the code you want to refactor. To do so you can run your test with Coverage :

![](../../.gitbook/assets/image%20%28331%29.png)

Because there are plenty of hardcoded strings and paths in the code, we have areas for improvement regarding our code coverage.

#### If you use IntelliJ IDEA

By default test coverage is poor but you can boost it by editing the "Run/Debug" configurations and enabling the Tracing option.

![](../../.gitbook/assets/image%20%28330%29.png)

If you run the test again, you should now have more information and new colors on the screen :

![](../../.gitbook/assets/image%20%28326%29.png)

### Use Code Coverage to increase our confidence

{% hint style="info" %}
What I recommend when you use Code Coverage or design tests is to always have your Subject Under Test in front of you : split your screen vertically.
{% endhint %}

![](../../.gitbook/assets/image%20%28329%29.png)

#### Use CombinationApprovals

_**CombinationApprovals**_ allow to combine a lot of inputs in the same ApprovalTests.

![](../../.gitbook/assets/image%20%28336%29.png)

We need to provide a Function as a first parameter and then the parameters.

* Refactor the test with CombinationApprovals

{% code title="GildedRoseTests.java" %}
```java
package com.gildedrose;

import org.approvaltests.combinations.CombinationApprovals;
import org.junit.jupiter.api.Test;

public class GildedRoseTests {
    @Test
    public void updateQuality() {
        var name = "a common item";
        var sellIn = 0;
        var quality = 0;

        CombinationApprovals.verifyAllCombinations(
                this::callUpdateQuality,
                new String[]{name},
                new Integer[]{sellIn},
                new Integer[]{quality}
        );
    }

    private String callUpdateQuality(String name, int sellIn, int quality) {
        var items = new Item[]{new Item(name, sellIn, quality)};
        var gildedRose = new GildedRose(items);
        gildedRose.updateQuality();

        return gildedRose.items[0].toString();
    }
}
```
{% endcode %}

Note that the received version has changed now because when you use CombinationApprovals it adds a description of the combination for each input :

> \[a common item, 0, 0\] =&gt; a common item, -1, 0

### Cover new lines of codes

By discovering them with the Code Coverage tool :

![](../../.gitbook/assets/image%20%28340%29.png)

At the end you should have a code coverage of 100% with a test looking like this :

{% tabs %}
{% tab title="GildedRoseTests.java" %}
```java
package com.gildedrose;

import org.approvaltests.combinations.CombinationApprovals;
import org.junit.jupiter.api.Test;

public class GildedRoseTests {
    @Test
    public void updateQuality() {
        CombinationApprovals.verifyAllCombinations(
                this::callUpdateQuality,
                new String[]{"a common item",
                        "Aged Brie",
                        "Backstage passes to a TAFKAL80ETC concert",
                        "Sulfuras, Hand of Ragnaros"},
                new Integer[]{-1, 0, 11},
                new Integer[]{0, 1, 49, 50}
        );
    }

    private String callUpdateQuality(String name, int sellIn, int quality) {
        var items = new Item[]{new Item(name, sellIn, quality)};
        var gildedRose = new GildedRose(items);
        gildedRose.updateQuality();

        return gildedRose.items[0].toString();
    }
}
```
{% endtab %}

{% tab title="GildedRoseTests.updateQuality.approved.txt" %}
```
[a common item, -1, 0] => a common item, -2, 0 
[a common item, -1, 1] => a common item, -2, 0 
[a common item, -1, 49] => a common item, -2, 47 
[a common item, -1, 50] => a common item, -2, 48 
[a common item, 0, 0] => a common item, -1, 0 
[a common item, 0, 1] => a common item, -1, 0 
[a common item, 0, 49] => a common item, -1, 47 
[a common item, 0, 50] => a common item, -1, 48 
[a common item, 11, 0] => a common item, 10, 0 
[a common item, 11, 1] => a common item, 10, 0 
[a common item, 11, 49] => a common item, 10, 48 
[a common item, 11, 50] => a common item, 10, 49 
[Aged Brie, -1, 0] => Aged Brie, -2, 2 
[Aged Brie, -1, 1] => Aged Brie, -2, 3 
[Aged Brie, -1, 49] => Aged Brie, -2, 50 
[Aged Brie, -1, 50] => Aged Brie, -2, 50 
[Aged Brie, 0, 0] => Aged Brie, -1, 2 
[Aged Brie, 0, 1] => Aged Brie, -1, 3 
[Aged Brie, 0, 49] => Aged Brie, -1, 50 
[Aged Brie, 0, 50] => Aged Brie, -1, 50 
[Aged Brie, 11, 0] => Aged Brie, 10, 1 
[Aged Brie, 11, 1] => Aged Brie, 10, 2 
[Aged Brie, 11, 49] => Aged Brie, 10, 50 
[Aged Brie, 11, 50] => Aged Brie, 10, 50 
[Backstage passes to a TAFKAL80ETC concert, -1, 0] => Backstage passes to a TAFKAL80ETC concert, -2, 0 
[Backstage passes to a TAFKAL80ETC concert, -1, 1] => Backstage passes to a TAFKAL80ETC concert, -2, 0 
[Backstage passes to a TAFKAL80ETC concert, -1, 49] => Backstage passes to a TAFKAL80ETC concert, -2, 0 
[Backstage passes to a TAFKAL80ETC concert, -1, 50] => Backstage passes to a TAFKAL80ETC concert, -2, 0 
[Backstage passes to a TAFKAL80ETC concert, 0, 0] => Backstage passes to a TAFKAL80ETC concert, -1, 0 
[Backstage passes to a TAFKAL80ETC concert, 0, 1] => Backstage passes to a TAFKAL80ETC concert, -1, 0 
[Backstage passes to a TAFKAL80ETC concert, 0, 49] => Backstage passes to a TAFKAL80ETC concert, -1, 0 
[Backstage passes to a TAFKAL80ETC concert, 0, 50] => Backstage passes to a TAFKAL80ETC concert, -1, 0 
[Backstage passes to a TAFKAL80ETC concert, 11, 0] => Backstage passes to a TAFKAL80ETC concert, 10, 1 
[Backstage passes to a TAFKAL80ETC concert, 11, 1] => Backstage passes to a TAFKAL80ETC concert, 10, 2 
[Backstage passes to a TAFKAL80ETC concert, 11, 49] => Backstage passes to a TAFKAL80ETC concert, 10, 50 
[Backstage passes to a TAFKAL80ETC concert, 11, 50] => Backstage passes to a TAFKAL80ETC concert, 10, 50 
[Sulfuras, Hand of Ragnaros, -1, 0] => Sulfuras, Hand of Ragnaros, -1, 0 
[Sulfuras, Hand of Ragnaros, -1, 1] => Sulfuras, Hand of Ragnaros, -1, 1 
[Sulfuras, Hand of Ragnaros, -1, 49] => Sulfuras, Hand of Ragnaros, -1, 49 
[Sulfuras, Hand of Ragnaros, -1, 50] => Sulfuras, Hand of Ragnaros, -1, 50 
[Sulfuras, Hand of Ragnaros, 0, 0] => Sulfuras, Hand of Ragnaros, 0, 0 
[Sulfuras, Hand of Ragnaros, 0, 1] => Sulfuras, Hand of Ragnaros, 0, 1 
[Sulfuras, Hand of Ragnaros, 0, 49] => Sulfuras, Hand of Ragnaros, 0, 49 
[Sulfuras, Hand of Ragnaros, 0, 50] => Sulfuras, Hand of Ragnaros, 0, 50 
[Sulfuras, Hand of Ragnaros, 11, 0] => Sulfuras, Hand of Ragnaros, 11, 0 
[Sulfuras, Hand of Ragnaros, 11, 1] => Sulfuras, Hand of Ragnaros, 11, 1 
[Sulfuras, Hand of Ragnaros, 11, 49] => Sulfuras, Hand of Ragnaros, 11, 49 
[Sulfuras, Hand of Ragnaros, 11, 50] => Sulfuras, Hand of Ragnaros, 11, 50 

```
{% endtab %}
{% endtabs %}

###  Are we confident enough ?

* Mutate the line 26 manually by 
  * Simply replacing the integer 1 by another random integer
* Run the test again, what happens ?

{% hint style="success" %}
Code coverage is a quantitative metric. To have a quality one we can use Mutation testing.
{% endhint %}

{% page-ref page="../testing/mutation-testing.md" %}

Let's use pitest to discover if we can improve our tests :

{% code title="pom.xml" %}
```java
<plugin>
    <groupId>org.pitest</groupId>
    <artifactId>pitest-maven</artifactId>
    <version>1.5.0</version>
    <dependencies>
        <dependency>
            <groupId>org.pitest</groupId>
            <artifactId>pitest-junit5-plugin</artifactId>
            <version>0.8</version>
        </dependency>
    </dependencies>
</plugin>
```
{% endcode %}

Pitest shows us where mutants survive and guide us to improve our test quality :

![](../../.gitbook/assets/image%20%28353%29.png)

![](../../.gitbook/assets/image%20%28339%29.png)

Based on the report we can add new inputs in our test until it's green :

* _**sellIn**_ between 6 & 11
* _**sellIn**_ lower than 6 and greater than 0

> _**We are now ready to start implementing the new functionality.**_

## Conclusion

Individually note down what has happened today in these categories:

* Liked
* Learned
* Lacked
* Longed for

![](../../.gitbook/assets/image%20%28354%29.png)

## Resources

* [Part 1/3 - Introducing the Gilded Rose kata and writing test cases using Approval Tests, Emily Bache](https://www.youtube.com/watch?v=zyM2Ep28ED8)
* [https://emilybache.github.io/workshops/approvals/](https://emilybache.github.io/workshops/approvals/)
* [https://approvaltests.com/](https://approvaltests.com/)

{% embed url="https://speakerdeck.com/thirion/approval-testing-kata-gilded-rose" caption="Facilitator guide" %}

