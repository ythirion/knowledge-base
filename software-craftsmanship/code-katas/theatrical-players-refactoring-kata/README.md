---
description: Kata based on the work from Emily Bache.
---

# Theatrical players refactoring Kata

### Objectives

* Learn how to refactor “legacy” code
* Practice OOP Design Patterns
* Practice FP concepts

### How to

Clone this repository : [https://github.com/ythirion/Theatrical-Players-Refactoring-Kata](https://github.com/ythirion/Theatrical-Players-Refactoring-Kata)

### Exercise

Add an HTML output with the same information

## Facilitation

### What do you think about this code ?

{% code title="StatementPrinter.java" %}
```java
import java.text.NumberFormat;
import java.util.Locale;
import java.util.Map;

public class StatementPrinter {

    public String print(Invoice invoice, Map<String, Play> plays) {
        var totalAmount = 0;
        var volumeCredits = 0;
        var result = String.format("Statement for %s\n", invoice.customer);

        NumberFormat frmt = NumberFormat.getCurrencyInstance(Locale.US);

        for (var perf : invoice.performances) {
            var play = plays.get(perf.playID);
            var thisAmount = 0;

            switch (play.type) {
                case "tragedy":
                    thisAmount = 40000;
                    if (perf.audience > 30) {
                        thisAmount += 1000 * (perf.audience - 30);
                    }
                    break;
                case "comedy":
                    thisAmount = 30000;
                    if (perf.audience > 20) {
                        thisAmount += 10000 + 500 * (perf.audience - 20);
                    }
                    thisAmount += 300 * perf.audience;
                    break;
                default:
                    throw new Error("unknown type: ${play.type}");
            }

            // add volume credits
            volumeCredits += Math.max(perf.audience - 30, 0);
            // add extra credit for every ten comedy attendees
            if ("comedy".equals(play.type)) volumeCredits += Math.floor(perf.audience / 5);

            // print line for this order
            result += String.format("  %s: %s (%s seats)\n", play.name, frmt.format(thisAmount / 100), perf.audience);
            totalAmount += thisAmount;
        }
        result += String.format("Amount owed is %s\n", frmt.format(totalAmount / 100));
        result += String.format("You earned %s credits\n", volumeCredits);
        return result;
    }

}
```
{% endcode %}

* Will it be easy to do the exercise ?
* Why ?

![](../../../.gitbook/assets/image%20%2824%29.png)

### Identify code smells

![](../../../.gitbook/assets/image%20%2889%29.png)

![](../../../.gitbook/assets/image%20%2881%29.png)

### Does it break any S.O.L.I.D principles ?

![](../../../.gitbook/assets/image%20%2870%29.png)

## How to start ?

{% hint style="info" %}
_"Before you start refactoring, make sure you have a solid suite of tests. Theses tests must be self-checking."_ - Martin Fowler
{% endhint %}

### Which kind of tests can we do ?

The code already exists and works :

* Easiest way to add a regression test is to find some test data, exercise the code, and approve the result
* Add [approval tests](https://approvaltests.com/) / [snapshot tests](https://jestjs.io/docs/en/snapshot-testing) / [Golden master](https://codurance.com/2012/11/11/testing-legacy-code-with-golden-master/)

### Approval tests : generate output / create your golden master

![](../../../.gitbook/assets/image%20%288%29.png)

We store this golden master in a file :

{% code title="StatementPrinterTests.exampleStatement.approved.txt" %}
```text
Statement for BigCo
  Hamlet: $650.00 (55 seats)
  As You Like It: $580.00 (35 seats)
  Othello: $500.00 (40 seats)
Amount owed is $1,730.00
You earned 47 credits
```
{% endcode %}

### Approval tests : create a test

To do so we can use the library "[approvaltests](https://approvaltests.com/)".

The verify is an approvaltests method that will compare the result returned by the print method and our Golden master.

{% code title="StatementPrinterTests.java" %}
```java
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.Test;

import java.util.List;
import java.util.Map;

import static org.approvaltests.Approvals.verify;

public class StatementPrinterTests {

    @Test
    void exampleStatement() {
        Map<String, Play> plays = Map.of(
                "hamlet",  new Play("Hamlet", "tragedy"),
                "as-like", new Play("As You Like It", "comedy"),
                "othello", new Play("Othello", "tragedy"));

        Invoice invoice = new Invoice("BigCo", List.of(
                new Performance("hamlet", 55),
                new Performance("as-like", 35),
                new Performance("othello", 40)));

        StatementPrinter statementPrinter = new StatementPrinter();
        var result = statementPrinter.print(invoice, plays);

        verify(result);
    }
```
{% endcode %}

### Have we missed something ?

We should ask ourselves if we have covered every piece of code with our test. 

To do so we have a tool : _**code coverage**_.

![](../../../.gitbook/assets/image%20%2878%29.png)

The Code Coverage \(from IntelliJ here\) shows us that the default case is not covered at the moment.

![Code coverage](../../../.gitbook/assets/image%20%28119%29.png)

So let's add a new test :

{% code title="StatementPrinterTests.java" %}
```java
        @Test
        void statementWithNewPlayTypes() {
            Map<String, Play> plays = Map.of(
                    "henry-v",  new Play("Henry V", "history"),
                    "as-like", new Play("As You Like It", "pastoral"));
        
            Invoice invoice = new Invoice("BigCo", List.of(
                    new Performance("henry-v", 53),
                    new Performance("as-like", 55)));
        
            StatementPrinter statementPrinter = new StatementPrinter();
            Assertions.assertThrows(Error.class, () -> {
                statementPrinter.print(invoice, plays);
            });
        }
```
{% endcode %}

### Are we confident enough in our tests ?

To check this we can check the quality of our tests by using a concept called mutation testing.

{% page-ref page="../../testing/mutation-testing.md" %}

![](../../../.gitbook/assets/image%20%28111%29.png)

You can use tools like pitest \(for Java\) or stryker \(for C\#, Javascript, Scala\).

Now we are confident enough, let's do the exercise.

## 2 ways of refactoring

![](../../../.gitbook/assets/image%20%2859%29.png)

{% page-ref page="lets-refactor-oop-style.md" %}

{% page-ref page="lets-refactor-fp-style.md" %}

## To go further

* Base artcile from Emily Bache : [https://www.praqma.com/stories/refactoring-kata/  ](https://www.praqma.com/stories/refactoring-kata/
  )
* Approval Tests : [https://approvaltests.com/  ](https://approvaltests.com/
  )
* Strategy pattern : [https://refactoring.guru/design-patterns/strategy  ](https://refactoring.guru/design-patterns/strategy
  )
* Facilitator slide deck :

{% embed url="https://speakerdeck.com/thirion/theatrical-players-refactoring-kata" %}



