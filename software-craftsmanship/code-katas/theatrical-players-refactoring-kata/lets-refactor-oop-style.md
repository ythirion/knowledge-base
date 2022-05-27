---
description: Theatrical players refactoring Kata in Object Oriented Programming
---

# Let's refactor (OOP style)

## Start by establishing our plan

We can use the [mikado method](http://mikadomethod.info/) to do so.

Here is mine :

![](<../../../.gitbook/assets/image (91).png>)

## 1) Extract the amount calculation

#### Create the interface

{% code title="AmountCalculator.java" %}
```java
public interface AmountCalculator {
    Integer compute(Integer audience);
}
```
{% endcode %}

#### Extract the 2 implementations

{% tabs %}
{% tab title="ComedyCalculator.java" %}
```java
public class ComedyCalculator implements AmountCalculator {
    @Override
    public Integer compute(Integer audience) {
        return 30_000 + 300 * audience + (audience > 20 ? 10_000 + 500 * (audience - 20) : 0);
    }
}
```
{% endtab %}

{% tab title="TragedyCalculator.java" %}
```java
public class TragedyCalculator implements AmountCalculator {
    @Override
    public Integer compute(Integer audience) {
        return 40_000 + (audience > 30 ? 1_000 * (audience - 30) : 0);
    }
}
```
{% endtab %}
{% endtabs %}

#### Create a factory to retrieve the implementation based on the type

{% code title="AmountCalculators.java" %}
```java
public class AmountCalculators {
    public static Integer forTypeAndAudience(String type, Integer audience) {
        Map<String, AmountCalculator> types = new HashMap<>();
        types.put("tragedy", new TragedyCalculator());
        types.put("comedy", new ComedyCalculator());

        if (!types.containsKey(type)) {
            throw new Error("Unknown type: " + type);
        } else {
            return types.get(type).compute(audience);
        }
    }
}
```
{% endcode %}

## 2) Extract the credits calculation

```java
private int volumeCredits(Invoice invoice, Map<String, Play> plays) {
    int credits = 0;
    for (Performance perf: invoice.performances) {
        Play play = playForPerformance(perf, plays);
        credits += Math.max(perf.audience - 30, 0);

        if ("comedy".equals(play.type)) {
            credits += perf.audience / 5;
        }
    }

    return credits;
}
```

## 3) Create a specific Printer implementation

#### Create types (simple POJOs) that represents a Statement

{% tabs %}
{% tab title="Statement.java" %}
```java
@Data
public class Statement {
    String customer;
    List<Line> lines = new ArrayList<>();
    Integer totalAmount;
    Integer volumeCredits;

    void addLine(Line line) {
        lines.add(line);
    }
}

```
{% endtab %}

{% tab title="Line.java" %}
```java
@Data
@AllArgsConstructor
public class Line {
    String name;
    Integer amount;
    Integer audience;
}
```
{% endtab %}
{% endtabs %}

#### Create a Printer interface

{% code title="Printer.java" %}
```java
public interface Printer {
    String print(Line line);
    String print(Statement statement);
}
```
{% endcode %}

#### Extract the current print logic in a TextPrinter class

{% code title="TextPrinter.java" %}
```java
public class TextPrinter implements Printer {
    @Override
    public String print(Line line) {
        return String.format("  %s: %s (%s seats)%n",
                line.getName(), Formatter.usd(line.getAmount()), line.getAudience());
    }

    @Override
    public String print(Statement statement) {
        return String.format("Statement for %s%n", statement.getCustomer())
                + statement.getLines().stream().map(this::print).collect(Collectors.joining(""))
                + String.format("Amount owed is %s%n", Formatter.usd(statement.getTotalAmount()))
                + String.format("You earned %s credits", statement.getVolumeCredits());
    }
}

```
{% endcode %}

## 4) Putting whole together

{% code title="StatementPrinter.java" %}
```java
public class StatementPrinter {

    private Play playForPerformance(Performance perf, Map<String, Play> plays) {
        return plays.get(perf.playID);
    }

    private int volumeCredits(Invoice invoice, Map<String, Play> plays) {
        int credits = 0;
        for (Performance perf: invoice.performances) {
            Play play = playForPerformance(perf, plays);
            credits += Math.max(perf.audience - 30, 0);

            if ("comedy".equals(play.type)) {
                credits += perf.audience / 5;
            }
        }

        return credits;
    }

    private int totalAmount(Invoice invoice, Map<String, Play> plays) {
        int amount = 0;
        for (Performance perf: invoice.performances) {
            Play play = playForPerformance(perf, plays);
            amount += AmountCalculators.forTypeAndAudience(play.type, perf.audience);
        }
        return amount;
    }

    public String print(Invoice invoice, 
                        Map<String, Play> plays,
                        Printer printer) {
        Statement statement = new Statement();
        statement.setCustomer(invoice.customer);

        for (Performance perf : invoice.performances) {
            Play play = playForPerformance(perf, plays);
            int amount = AmountCalculators.forTypeAndAudience(play.type, perf.audience);
            statement.addLine(new Line(play.name, amount, perf.audience));
        }

        statement.setTotalAmount(totalAmount(invoice, plays));
        statement.setVolumeCredits(volumeCredits(invoice, plays));

        return printer.print(statement);
    }
}
```
{% endcode %}

Our code is now ready to be extended with the new HTLM printer.
