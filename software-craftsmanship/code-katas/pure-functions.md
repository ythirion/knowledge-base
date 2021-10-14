# Pure functions

## Objectives :

Understand what are Pure Functions and the benefits of using them

## Connection - 10'

Categorize these code samples in _**Pure Functions**_ vs _**Impure Functions **_:

```python
import random

def f(x):
    if random.randint(1, 2) == 1:
        return x + 1
    return x + 2
```

```java
public class MathUtility {
    public static int sum(int num1, int num2) {
        return num1 + num2;
    }
}
```

```java
public class Line {
    private int value = 0;

    public int add(int nextValue) {
        this.value += nextValue;
        return this.value;
    }
}
```

```java
public class MathUtility {
    private static int count = 1;
    public static int sum(int num1, int num2) {
        count++;
        multiply(num1,num2);
        return num1 + bnum2;
    }
}
```

```javascript
const double = x => x * 2;
```

Explain your choices.

## Concept - 5'

{% hint style="success" %}
Pure functions don’t refer to any global state. _**Those functions do not produce any side effects (state changes).**_
{% endhint %}

They are _**easier to test because**_ of these properties:

1. You can see all the inputs in the argument list
2. The execution is deterministic (the same inputs will always get the same outputs)
3. You can see all the outputs in the return value

_Code that is harder to test will lack some or all of these properties._

## Concrete Practice - 30'

* Clone the repository [here](https://github.com/ythirion/pure-functions)
* Identify the design problems related to the RentalCalculator
* Refactor this code by using _**Pure Functions**_

{% hint style="success" %}
A step by step solution is provided in the _**solution**_ branch (Look at the commits)
{% endhint %}

![](<../../.gitbook/assets/image (549).png>)

## Conclusion - 10'

* How much of the time do you find yourself writing tests for functions that have all the three properties of pure functions ?
* What do you need to write more Pure Functions ?
