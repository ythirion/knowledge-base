# Stack kata

### Objective

* Create production code from test
* Start from assertions

![](../../../.gitbook/assets/image%20%28485%29.png)

## Connection - 10'

What are the key principles to write good unit tests ?

## Concepts - 10'

{% hint style="info" %}
Tip for deciding the first test to write: The simplest possible.
{% endhint %}

* Red, Green, Refactor
  * Add a test
  * Run all tests and see if the new one fails - Red
  * Write the minimum amount of code to pass the failing test - 
  * Run tests - Green
  * Refactor code - Blue 
  * **Repeat**
* TDD Golden Rule
  * **Do not write any production code until you have a failing test that requires it**
* Arrange, Act, Assert
  * Arrange :
    * Setup everything needed for the testing code
    * Data initialization / mocks
  * Act :
    * Invoke the code under test / behavior
  * Assert :
    * Specify the pass criteria for the test

Define a test checklist for your team :

![](../../../.gitbook/assets/image%20%28503%29.png)

## Concrete Practice - 25'

* In pair, implement a Stack class with the following public methods by  using TDD :

```text
void push(Object object)
Object pop()
```

* Stack should throw an exception if popped when empty
* Start by writing your assertions

#### When you use TDD :

* Split your screen
  * Your tests at the left
  * Your production code at the right

![](../../../.gitbook/assets/image%20%28506%29.png)

#### Questions to ask :

* _**What is the value to test the push ?**_
  * Do not change your production code encapsulation for testing purpose
* Often developers want to inherit from ArrayList or another types of collection
  * Ask them Why
  * Remind them that the purpose of TDD is also to avoid writing unnecessary code
    * In the exercise, is it required to have a Count function on the Stack for example ?

After 20' of coding ask them to demonstrate what has been written

Here is a solution : [https://github.com/ythirion/stack-kata](https://github.com/ythirion/stack-kata)

{% tabs %}
{% tab title="stack\_should" %}
```java
import org.junit.jupiter.api.Assertions;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;

import java.util.EmptyStackException;

public class stack_should {
    private final Object object1 = new Object();
    private final Object object2 = new Object();

    private Stack stack;

    @BeforeEach
    public void init() {
        stack = new Stack();
    }

    @Test
    public void raise_an_exception_when_popped_and_empty() {
        Stack emptyStack = new Stack();
        Assertions.assertThrows(EmptyStackException.class, emptyStack::pop);
    }

    @Test
    public void pop_the_last_object_pushed() {
        stack.push(object1);
        Assertions.assertEquals(object1, stack.pop());
    }

    @Test
    public void pop_objects_in_the_reverse_order_they_were_pushed()
    {
        stack.push(object1);
        stack.push(object2);

        Assertions.assertEquals(object2, stack.pop());
        Assertions.assertEquals(object1, stack.pop());
    }
}

```

 Ask to the participants what do they think about the naming of the tests.
{% endtab %}

{% tab title="Stack" %}
```java
import java.util.ArrayList;
import java.util.EmptyStackException;

public class Stack {
    private final ArrayList<Object> stack;

    public Stack() {
        stack = new ArrayList<>();
    }

    public Object pop() {
        if(stack.isEmpty()) {
            throw new EmptyStackException();
        }
        var lastElement = stack.get(stack.size() - 1);
        stack.remove(lastElement);

        return lastElement;
    }

    public void push(Object element) {
        stack.add(element);
    }
}
```
{% endtab %}
{% endtabs %}

## Conclusion - 5'

Note the main thing you want to remember about this session on a Sticky Note

### Resources

* [Programming with GUTs by Kevlin Henney](https://www.youtube.com/watch?v=azoucC_fwzw&ab_channel=BuildStuff)
* [Test Driving Algorithms by Sandro Mancuso](https://codurance.com/videos/2014-12-05-test-driving-algorithms/)

![](../../../.gitbook/assets/image%20%28489%29.png)

