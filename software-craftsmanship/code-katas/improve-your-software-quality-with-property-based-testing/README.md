---
description: Write bulletproof code with Property-Based Testing (PBT)
---

# Improve your software quality with Property-Based Testing

Before talking about PBT, let’s talk about the different test technics we use to test the correctness of our code. Those technics are represented on 2 axis :

* Input scope covered: Do we cover the full scope of possible inputs ?
* Feature compliance: Does the developed feature is compliant with what is expected ?

![](https://miro.medium.com/max/270/1\*9v9aKPnhlNU0rUJiimv6NQ.png)

When we write Unit tests, we often focus on examples especially when using approaches like Specification by examples.&#x20;

Examples are really good to understand requirements :

```groovy
Given (x, y, ...)
When I [call the subject under test] with (x, y, ...)
Then I expect this (output)
```

The limitation of this approach is that we will only focus on the input scope we identified. It is where PBT comes at our rescue.

Imagine an approach as powerful as Example based testing in terms of feature compliance checking but covering also a much more important numbers of inputs. That’s the promise of PBT.

## What is Property-based testing (PBT) ? <a href="#364c" id="364c"></a>

Property-based testing is generative testing. You do not supply specific example inputs with expected outputs.

{% hint style="info" %}
Instead, you define properties about your feature requirements and use a generative-testing engine to create randomized inputs to ensure the defined properties are correct.
{% endhint %}

Property-based tests are designed to test the aspects of a property that should always be true. They allow for a range of inputs to be programmed and tested within a single test, rather than having to write a different test for every value that you want to test.

A property looks like this :

```groovy
for all (x, y, ...)
such that property (x, y, ...)
is satisfied
```

It’s used a lot in the functional world where we favor the writing of pure functions (same output for a given output without side effects).

### Let’s take an example <a href="#5ac5" id="5ac5"></a>

Imagine we write an addition function that add 2 integers together.&#x20;

With Example-Based Testing we would write tests like this :

```groovy
Given (2, 2)
When I add them
Then I expect 4
```

![](https://miro.medium.com/max/1654/1\*1eCbpT78yrAfKMkxacVMyw.png)

With this test we cover 100% of the code but what about edge cases ? Add negative numbers together for example.

With PBT we would identify the properties of the addition operation :

* **Commutativity** : the parameter order does not matter

```groovy
for all (int x, int y)
such that (add(x, y) equals add(y, x)) is satisfied
```

* **Associativity** : “add 1” twice is the same as doing “add 2”

```groovy
for all (int x)
such that (add(add(x, 1), 1) equals add(x, 2)) is satisfied
```

* **Identity** : add 0 does nothing

```groovy
for all (int x)
such that (add(x, 0) equals x) is satisfied
```

If we check those properties to all inputs we are confident the implementation is correct. We do not check specific values in output anymore we check the properties.

## A word on QuickCheck <a href="#b63c" id="b63c"></a>

The first tool used to do PBT was QuickCheck (in Haskell) and in this hands-on I will talk only for the behavior of QuickCheck. How does a PBT tool work ?

* You define a Property : a function that returns a boolean
* You pass it to a checker that will generate random inputs (through the generator in QuickCheck)
* A shrinker will attempt to shrink the input sequence to the smallest possible that will reproduce the error. The smaller the input, the easier it is to reproduce and fix.
* The Runner will use the whole to run your predicate (Property) with the generated

![](https://miro.medium.com/max/554/1\*zV-jkgfTSJk1SubHLFVhrQ.png)

{% hint style="success" %}
_As soon as there is one value which yields false, the property is said to be falsified, and checking is aborted._
{% endhint %}

## How to implement PBT in Java ? <a href="#a664" id="a664"></a>

An implementation of QuickCheck is available for Java : [junit-quickcheck](https://pholser.github.io/junit-quickcheck/site/0.9.1/)

* Add the dependency to your pom :

{% code title="pom.xml" %}
```markup
<properties>
    <junit-quickcheck.version>0.9.1</junit-quickcheck.version>
</properties>

<dependency>
    <groupId>com.pholser</groupId>
    <artifactId>junit-quickcheck-core</artifactId>
    <version>${junit-quickcheck.version}</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>com.pholser</groupId>
    <artifactId>junit-quickcheck-generators</artifactId>
    <version>${junit-quickcheck.version}</version>
    <scope>test</scope>
</dependency>
```
{% endcode %}

* Define your properties

{% code title="Addition_properties.java " %}
```java
import com.pholser.junit.quickcheck.Property;
import com.pholser.junit.quickcheck.runner.JUnitQuickcheck;
import org.junit.Assert;
import org.junit.runner.RunWith;

@RunWith(JUnitQuickcheck.class)
public class Addition_properties {
    @Property
    public void commutative(int randomX, int randomY) {
        int result1 = Calculator.add(randomX, randomY);
        int result2 = Calculator.add(randomY, randomX);

        Assert.assertEquals(result1, result2);
    }

    @Property
    public void associative(int randomX) {
        int result1 = Calculator.add(randomX, 1);
        result1 = Calculator.add(result1, 1);
        int result2 = Calculator.add(randomX, 2);

        Assert.assertEquals(result1, result2);
    }

    @Property
    public void identity(int randomX) {
        int result1 = Calculator.add(randomX, 0);

        Assert.assertEquals(result1, randomX);
    }
}
```
{% endcode %}

* On top of your PBT test classes you need to specify the Runner to be used : JUnitQuickCheck.class
* On each Property, add the annotation @Property

Here it is we just have created our first PBT class to test our Calculator.add function.

## Junit-quickcheck <a href="#0559" id="0559"></a>

It supports a lot of types by default :

![](https://miro.medium.com/max/2119/1\*oPmm5N0SBvjyyex-1Sn7WQ.png)

### Configure generator <a href="#7fc1" id="7fc1"></a>

You can specify ranges for your inputs with @Range :

![](https://miro.medium.com/max/2119/1\*ZYlNrZlaw6PR75nBMN9uww.png)

Or you can use assumptions to restrain those values :

![](https://miro.medium.com/max/1100/1\*3GbPwLoU7IH8GIkkQTRYUA.png)

### Generate complex inputs : <a href="#a378" id="a378"></a>

To instantiate complex objects in input of your functions, you can simply create custom Generators :![](https://miro.medium.com/max/27/1\*Vf-otIfhTa9\_4JNQKhkNZA.png?q=20)

![](https://miro.medium.com/max/2131/1\*Vf-otIfhTa9\_4JNQKhkNZA.png)

### Default behaviors : <a href="#45f0" id="45f0"></a>

By default it will verify a property in “sampling” mode, it generates 100 tuples of random values for the parameter list of a property, and verifies the property against each of the tuples.

To change the number of generated values, use the trials attribute of the @Property annotation.

## PBT in real life <a href="#602c" id="602c"></a>

Imagine we have an Account class which defines the behavior of a withdraw.

{% code title="Account.java" %}
```java
import io.vavr.control.Try;
import lombok.AllArgsConstructor;
import lombok.Getter;
import lombok.NoArgsConstructor;

@AllArgsConstructor
@Getter
public class Account {
    private final double balance;
    private final boolean isOverdraftAuthorized;
    private final double maxWithdrawal;

    public Try<Account> withdraw(Withdraw command) {
        return Try.of(() -> {
            checkMaxWithdrawal(command);
            checkBalance(command);

            return new Account(balance - command.getAmount(),
                    this.isOverdraftAuthorized,
                    this.maxWithdrawal);
        });
    }

    private void checkMaxWithdrawal(Withdraw command) {
        if(command.getAmount() > maxWithdrawal) {
            throw new IllegalArgumentException("Amount exceeding your limit of " + maxWithdrawal);
        }
    }

    private void checkBalance(Withdraw command) {
        if(command.getAmount() > balance && !isOverdraftAuthorized()) {
            throw new IllegalArgumentException("Insufficient balance to withdraw : " + command.getAmount());
        }
    }
}
```
{% endcode %}

We would like to test the feature compliance. To do so we identify the properties :

* The account balance should be decremented of the withdrawal amount when _the account balance is sufficient or the overdraft is authorized_
* The client must not be allowed to withdraw when _the withdraw amount is over the max withdrawal amount of the account OR the account balance is insufficient and overdraft is not authorized for the account_

### Create custom generators <a href="#f11c" id="f11c"></a>

To write PBTs we need to be able to generate random Inputs (withdraw) and random accounts for a given property. To do so we simply create 2 generators :

{% code title="Generators.java" %}
```java
public class WithdrawGenerator extends Generator<Withdraw> {

    public WithdrawGenerator() {
        super(Withdraw.class);
    }

    @Override
    public Withdraw generate(SourceOfRandomness sourceOfRandomness, GenerationStatus generationStatus) {
        return new Withdraw(sourceOfRandomness.nextDouble(), new Date());
    }
}

public class AccountGenerator extends Generator<Account> {
    public AccountGenerator() {
        super(Account.class);
    }

    @Override
    public Account generate(SourceOfRandomness sourceOfRandomness, GenerationStatus generationStatus) {
        return new Account(sourceOfRandomness.nextDouble(),
                sourceOfRandomness.nextBoolean(),
                sourceOfRandomness.nextDouble());
    }
}
```
{% endcode %}

Those generators are really dumb, we just want them to generate complex data structure by using random values in the constructors.

### Use the generators and assumptions <a href="#8f4d" id="8f4d"></a>

{% code title="account_properties.java" %}
```java
@RunWith(JUnitQuickcheck.class)
public class Account_properties {
    @Property
    public void balance_should_be_decremented_of_the_amount(
            @From(AccountGenerator.class) Account account,
            @From(WithdrawGenerator.class) Withdraw withdraw) {

        withEnoughMoney(account, withdraw);
        withoutReachingMaxWithdrawal(account, withdraw);

        Try<Account> debitedAccount = account.withdraw(withdraw);

        Assert.assertEquals(
                account.getBalance() - withdraw.getAmount(),
                debitedAccount.get().getBalance(), 0);
    }

    @Property
    public void balance_should_be_decremented_even_when_insufficient_balance_because_overdraft_is_authorized(
            @From(AccountGenerator.class) Account account,
            @From(WithdrawGenerator.class) Withdraw withdraw) {

        withInsufficientBalance(account, withdraw);
        withoutReachingMaxWithdrawal(account, withdraw);
        withOverdraftAuthorized(account);

        Try<Account> debitedAccount = account.withdraw(withdraw);

        Assert.assertEquals(
                account.getBalance() - withdraw.getAmount(),
                debitedAccount.get().getBalance(), 0);
    }

    @Property
    public void withdraw_should_not_be_allowed_when_withdraw_over_maxWithdrawal_requested(
            @From(AccountGenerator.class) Account account,
            @From(WithdrawGenerator.class) Withdraw withdraw) {

        assumeThat(account.getMaxWithdrawal(), lessThan(withdraw.getAmount()));

        Throwable failure = account.withdraw(withdraw).getCause();

        Assert.assertTrue(failure instanceof IllegalArgumentException);
        Assert.assertTrue(failure.getMessage().startsWith("Amount exceeding your limit of"));
    }

    @Property
    public void withdraw_should_not_be_allowed_when_no_money_and_no_overdraft(
            @From(AccountGenerator.class) Account account,
            @From(WithdrawGenerator.class) Withdraw withdraw) {

        withInsufficientBalance(account, withdraw);
        withoutReachingMaxWithdrawal(account, withdraw);
        withoutOverdraftAuthorized(account);

        Throwable failure = account.withdraw(withdraw).getCause();

        Assert.assertTrue(failure instanceof IllegalArgumentException);
        Assert.assertTrue(failure.getMessage().startsWith("Insufficient balance to withdraw"));
    }

    private void withoutOverdraftAuthorized(Account account) {
        assumeThat(account.isOverdraftAuthorized(), is(false));
    }

    private void withEnoughMoney(Account account, Withdraw withdraw) {
        assumeThat(account.getBalance(), greaterThan(withdraw.getAmount()));
    }

    private void withoutReachingMaxWithdrawal(Account account, Withdraw withdraw) {
        assumeThat(account.getMaxWithdrawal(), greaterThan(withdraw.getAmount()));
    }

    private void withInsufficientBalance(Account account, Withdraw withdraw) {
        assumeThat(account.getBalance(), lessThan(withdraw.getAmount()));
    }

    private void withOverdraftAuthorized(Account account) {
        assumeThat(account.isOverdraftAuthorized(), is(true));
    }
}
```
{% endcode %}

To use a custom generator you can pass it through the @From annotation. We need to use assumptions to declare the conditions under the properties hold.

I encapsulate those assumptions in small functions to understand quickly what are the conditions for the properties.

## Another lib — vavr-test <a href="#c019" id="c019"></a>

You can use another java lib to write PBTs : [vavr-test](https://github.com/vavr-io/vavr-test)

It allows you to write PBT in more functional way. If we write the same properties for the addition it would look like this :

{% code title="Addition_properties_with_vavr_test.java" %}
```java
public class Addition_properties_with_vavr_test {

    private final int size = 10_000, tries = 100;

    @Test
    public void commutative() {
        Property.def("Addition is commutative")
                .forAll(Arbitrary.integer(), Arbitrary.integer())
                .suchThat((x, y) -> Calculator.add(x, y) == Calculator.add(y, x))
                .check(size, tries)
                .assertIsSatisfied();
    }

    @Test
    public void associative() {
        Property.def("Addition is associative")
                .forAll(Arbitrary.integer())
                .suchThat(x -> Calculator.add(Calculator.add(x, 1), 1) == Calculator.add(x, 2))
                .check(size, tries)
                .assertIsSatisfied();
    }

    @Test
    public void identity() {
        Property.def("0 is the identity")
                .forAll(Arbitrary.integer())
                .suchThat((x) -> Calculator.add(x, 0) == x)
                .check(size, tries)
                .assertIsSatisfied();
    }
}
```
{% endcode %}

With vavr-test you don’t need to specify a given Runner nor Property annotation. You specify Property in your test.

## Quickcheck in your favorite language <a href="#0194" id="0194"></a>

![](https://miro.medium.com/max/1240/1\*Ff\_2n41L0uSrVWw3gbgMQQ.png)

Source : [https://hypothesis.works/articles/quickcheck-in-every-language/](https://hypothesis.works/articles/quickcheck-in-every-language/)

## Benefits of PBT <a href="#c7ad" id="c7ad"></a>

![](https://miro.medium.com/max/2068/1\*gBIuM0W6rSnspKdSJvE76g.png)

* PBTs are **more general than Example based testing :** 1 PBT can replace many example-based tests
* PBTs can **reveal edge cases** : through the usage of random values (Nulls, negative numbers, weird strings,…)
* PBTs **ensures deep understanding** of the business : to be able to identify properties we must deeply understand business invariants

## Resources <a href="#ba0f" id="ba0f"></a>

If you want to go further I highly recommend you to read and watch those resources :

* [An introduction to property based testing ](https://fr.slideshare.net/ScottWlaschin/an-introduction-to-property-based-testing)_— Scott Wlaschin_
* [Property-Based Testing for everyone ](https://www.youtube.com/watch?v=5pwv3cuo3Qk)_— Romeu Moura (Video)_
* __[Property-based testing in Java with JUnit-Quickcheck](https://baasie.com/2017/05/03/property-based-testing-in-java-with-junit-quickcheck-part-1-the-basics/) _— Kenny Baas-Schwegler_
* __[Property Testing with vavr](https://www.baeldung.com/vavr-property-testing)
* [junit-quickcheck documentation](https://github.com/pholser/junit-quickcheck)
* [https://johanneslink.net/how-to-specify-it/](https://johanneslink.net/how-to-specify-it/)

The source code used in this article is available on github [here](https://github.com/ythirion/pbt-kata).
