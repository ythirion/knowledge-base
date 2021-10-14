# Mocking

### Objectives

* Understand what is a mock
* Practice mocking on a code example

## Connection - 10'

In groups of 3 answer to this question : in which cases do you use a Mock ?

![](<../../.gitbook/assets/image (521).png>)

## Concepts - 5'

### What is a Mock ?

* Mock objects allow you to simulate the behavior of classes and interfaces
  * Letting the code in the test interact with them as if they were real
* Mocks are used to test behavior of other objects, reals, but link to another object not available in test context or not implemented yet

### In which cases do we use them ?

Be able to execute tests in isolation

* Replaces dependency from other object
* Set expectations on calls to the dependent object
* Set the exact return values it should give you to perform the test you want

When using mocks you need to always ask yourselves what are your test boundaries.

### Examples of situation

* The system needs a DB access
* The system call services that are not available
* The system call APIs developed by other teams which are not implemented yet

### How does it work ?

![](<../../.gitbook/assets/image (523).png>)

## Concrete Practice - 45'

We would like to test a system which convert an amount in a specific currency to another one. The converter method call a service to retrieve the change rate between the two currencies.

_**Some rules are checked during treatment :**_

```
- The amount must be equal or greater than zero
- Service checks if currencies exist
- The service could throw other types of exception following the context
- The return rate must be equal or greater than zero
- The result must be between 0 and the maximum value
```

In our Unit Tests methods the service is not accessible -> we need to “mock” it

### How to ?

* Open the source code [here](https://github.com/ythirion/mock-kata)
* Demonstrate how to add Mockito to our tests

{% code title="pom.xml" %}
```markup
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>3.3.3</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-junit-jupiter</artifactId>
    <version>3.3.3</version>
    <scope>test</scope>
</dependency>
```
{% endcode %}

* This annotation allows us to use the @Mock annotation (inject Mocks)
  * Learn more about it [here](https://www.baeldung.com/mockito-junit-5-extension)

```java
@ExtendWith(MockitoExtension.class)
@Mock private ChangeRateService changeRateService;
```

### Implement tests - 35'

* The production code is implemented as expected
* Please add the tests to check it

When working with existing code and adding test on it : _**use your Code Coverage**_

![](<../../.gitbook/assets/image (524).png>)

### Debrief the exercise - 10'

* Group sharing
* Demo the solution in the dedicated branch

## Conclusion - 10'

* Think about what we did today. 
  * If you had to explain the main idea of mocking to someone else, what would you say?
* Write your explanation in a sentence or two on a post-it
