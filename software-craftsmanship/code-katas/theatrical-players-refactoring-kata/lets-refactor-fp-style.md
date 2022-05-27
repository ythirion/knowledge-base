---
description: Theatrical players refactoring Kata in a Functional Programming style
---

# Let's refactor (FP style)

## Start by establishing our plan

We can use the [mikado method](http://mikadomethod.info/) to do so.

Here is mine :

![](<../../../.gitbook/assets/image (92).png>)

We will use [vavr](https://www.vavr.io/) to refactor this code in java.

## 1) Extract the amount calculation

{% code title="PlayAmounts.java" %}
```java
@UtilityClass
class PlayAmounts {
    private static final NumberFormat FORMAT = NumberFormat.getCurrencyInstance(Locale.US);

    private static final IntUnaryOperator TRAGEDY =
            audience -> 40_000 + (audience > 30 ? 1_000 * (audience - 30) : 0);
    private static final IntUnaryOperator COMEDY =
            audience -> 30_000 + 300 * audience + (audience > 20 ? 10_000 + 500 * (audience - 20) : 0);

    private static final Map<String, IntUnaryOperator> TYPES =
            HashMap.of("tragedy", TRAGEDY, "comedy", COMEDY);

    static Integer forTypeAndAudience(String type, Integer audience) {
        return TYPES.get(type).map(f -> f.applyAsInt(audience))
                .getOrElseThrow(() -> new Error("Unknown type: " + type));
    }

    static String format(Integer amount) {
        return FORMAT.format(amount / 100);
    }
}
```
{% endcode %}

## 2) Build a statement

```java
private String formatLine(String name, Integer amount, Integer audience) {
    return String.format("  %s: %s (%s seats)%n", name, format(amount), audience);
}

private String formatStatement(Invoice invoice, Statement pc) {
    return String.format("Statement for %s%n%sAmount owed is %s%nYou earned %s credits",
            invoice.customer, pc.line, format(pc.amount), pc.credits);
}

private Statement makeStatement(Performance perf, Play play) {
    int amount = PlayAmounts.forTypeAndAudience(play.type, perf.audience);
    int volumeCredits = computeCredits(play.type, perf.audience);
    String line = formatLine(play.name, amount, perf.audience);
    
    return new Statement(line, amount, volumeCredits);
}
```

## 3) Run the pipeline

```java
public String print(Invoice invoice, java.util.Map<String, Play> plays) {
    return Vector.ofAll(invoice.performances)
            // for each performance make a statement
            .map(perf -> makeStatement(perf, plays.get(perf.playID)))
            // compute total amount and credit
            .reduceOption(Statement::add)
            // make the final statement to be printed
            .map(p -> formatStatement(invoice, p))
            .getOrElse("");
}
```

## 4) Putting whole together

{% code title="StatementPrinter.java" %}
```java
public class StatementPrinter implements StatementPrinter {
    private String formatLine(String name, Integer amount, Integer audience) {
        return String.format("  %s: %s (%s seats)%n", name, format(amount), audience);
    }

    private String formatStatement(Invoice invoice, Statement pc) {
        return String.format("Statement for %s%n%sAmount owed is %s%nYou earned %s credits",
                invoice.customer, pc.line, format(pc.amount), pc.credits);
    }

    private Statement makeStatement(Performance perf, Play play) {
        int amount = PlayAmounts.forTypeAndAudience(play.type, perf.audience);
        int volumeCredits = computeCredits(play.type, perf.audience);
        String line = formatLine(play.name, amount, perf.audience);

        return new Statement(line, amount, volumeCredits);
    }

    private int computeCredits(String type, Integer audience) {
        return Math.max(audience - 30, 0)
                + ("comedy".equals(type) ? (audience / 5) : 0);
    }


    public String print(Invoice invoice, java.util.Map<String, Play> plays) {
        return Vector.ofAll(invoice.performances)
                // for each performance make a statement
                .map(perf -> makeStatement(perf, plays.get(perf.playID)))
                // compute total amount and credit
                .reduceOption(Statement::add)
                // make the final statement to be printed
                .map(p -> formatStatement(invoice, p))
                .getOrElse("");
    }
}
```
{% endcode %}

Our code is now ready to be extended with the new HTLM printer.
