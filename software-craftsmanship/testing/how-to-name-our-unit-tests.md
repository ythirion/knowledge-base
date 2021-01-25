# How to name our Unit Tests

## Connection - 10'

Imagine we want to test this method :

```java
public static boolean isLeapYear(int year)
```

* Here are the [associated requirements](https://en.wikipedia.org/wiki/Leap_year)

**How would you name your first test ?**

* Ask attendees to note on a Sticky Note what is the name of their first test
* Compare the different styles
* What do they prefer \(Dot voting\)

## Concepts - 10'

#### Tests names v1

```java
yearsNotDivisibleBy4...
yearsDivisibleBy4ButNotBy100...
yearsDivisibleBy100ButNotBy400...
yearsNotDivisibleBy400...
```

* Is it readable ?
* What is the intent ?

#### Tests names v2

```java
years_not_divisible_by_4...
years_divisible_by_4_but_not_by_100...
years_divisible_by_100_but_not_by_400...
years_not_divisible_by_400...
```

* Is it more readable ?
* What is the intent ?

#### Tests names v3

```java
years_not_divisible_by_4_are_not_leap_years
years_divisible_by_4_but_not_by_100_are_leap_years
years_divisible_by_100_but_not_by_400_are_not_leap_years
years_not_divisible_by_400_are_not_leap_years
```

* Intent is more clear, isn’t it ?

#### Tests names v4

```java
public class Leap_year_spec {
    public static class A_year_is_a_leap_year {
        @Test public void if_it_is_divisible_by_4_but_not_by_100()...
        @Test public void if_it_is_divisible_by_400()...
    }
    
    public static class A_year_is_not_a_leap_year {
        @Test public void if_it_is_not_divisible_by_4()...
        @Test public void if_it_is_divisible_by_100_but_not_by_400()...
    }
}
```

* Express what the class should be able to do
* Read it as a full sentence : express a true business specification
* You should avoid technical terms

## Concrete Practice - 30'

* Choose a Kata on [Coding Dojo](https://codingdojo.org/kata/)
* Extract the Test Cases you want to write
  * Define the structure and naming of your tests

## Conclusion - 10'

Imagine you use this naming technique during the next 6 months :

* What has changed ?
* Who else have noticed those changes ?
* What are the impacts on your day to day ?

### Resources

* [https://www.youtube.com/watch?v=azoucC\_fwzw&ab\_channel=BuildStuff](https://www.youtube.com/watch?v=azoucC_fwzw&ab_channel=BuildStuff)



