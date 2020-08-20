---
description: >-
  Read this article if you want to demystify Functional Programming and
  understand why and how to start using FP paradigms in C#.
---

# Functional Programming made easy in C\# with Language-ext

In the title I have written FP and C\# but the question you probably wonder is :

> What the hell should we want to use FP paradigms in an OO language like C\# ?

Here are some arguments to answer this question \(from my POV\) :

{% hint style="success" %}
* Write less code and more meaningful one : improved code clarity
* Avoid side effects by using immutability and pure functions : Easier concurrent programming
* Easier testing : it’s really easy to test functions
* Easier debugging
* Funnier to write
{% endhint %}

![](https://miro.medium.com/max/1440/0*P33ZZhUjLG5IPM6t.png)

## OK but why don’t we use a FP language instead of C\# ?

In companies it’s really hard to change the habits. We don’t all work in the Sillicon Valley and in my reality the latest versions in the production environments are : Java 8, .NET Framework 4, NodeWhat ?, …

In my world organizations are not yet ready to invest in pure FP languages like F\#, Kotlin, Clojure or whatever. They are stuck in legacy code…

To go further on this topic I invite you to watch this video on _**Functional Core, Imperative Shell**_ : [https://discventionstech.wordpress.com/2017/06/30/functional-core-and-imperative-shell/](https://discventionstech.wordpress.com/2017/06/30/functional-core-and-imperative-shell/)

![](../.gitbook/assets/image%20%28363%29.png)

It’s a pattern that could be really useful to every developers on earth I think.

* **Functional core \(declarative\)** composed of pure functions \(in / out\) and easy to test without any mocks.
* **Imperative shell or reactive** container the ****service logic that you can test with integration tests

Now I have proved the interest of FP in OO language let’s go for a quick lesson.

## Let’s demystify Functional Programming \(FP\) <a id="9146"></a>

> “In computer science, **functional programming** is a **programming** paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.” —[ wikipedia](https://en.wikipedia.org/wiki/Functional_programming)

Basically FP is all about **functions and immutability :**

* Pure functions
* Lambda functions \(anonymous\)
* High order functions
* Composition
* Closures
* Currying & partial application
* Recursion

_If you have already looked at it, you have probably read other words like functors, monads and monoïds that can be very scary but in reality concepts are not._

Let’s start by explaining 3 concepts :

### Immutability <a id="662a"></a>

We **never** want to **mutate an object in FP we want to avoid side effects so we prefer** creating a new one. ****If we have mutable objects it could be possible for another function to mutate the object we were working on concurrently.

{% hint style="success" %}
Immutability ensures a function remains pure, it makes concurrency much more easy to handle and makes our dev life easier.
{% endhint %}

### Pure Functions <a id="92b0"></a>

A pure function don’t refer to any global state. The same inputs will always get the same output.![Image for post](https://miro.medium.com/max/1148/1*wr5pNa2qjdVvxrD_wUfBjA.png)

Combined with **immutable data** types mean you can be sure the same inputs will give the same outputs.

### Higher order function <a id="69d2"></a>

A function that does at least one of the following:

* Takes one or more functions as arguments
* Returns a function as its result

A higher order function that takes 2 functions as arguments

![](https://miro.medium.com/max/1674/1*cruiC2X46yWBxq6QyFO_rw.png)

Before demonstrating code I highly recommend you to read this great article about FP concepts \(I won’t do better for sure\) :

[http://adit.io/posts/2013-04-17-functors,\_applicatives,\_and\_monads\_in\_pictures.html\#just-what-is-a-functor,-really?](http://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html)

Now you know the basics behind FP we can start deep diving into Language-ext.

## What is Language-ext ? <a id="2a7c"></a>

According to the creator of the lib [**Paul Louth**](https://twitter.com/paullouth) ****: It’s a library that uses and abuses the features of C\# to provide a functional-programming ‘base class library’ that, if you squint, can look like extensions to the language itself.

His desire here is to make programming in C\# much more reliable and to make the engineer’s inertia flow in the direction of declarative and functional code rather than imperative.

It’s basically “**one lib to rule them all**” : [https://github.com/louthy/language-ext](https://github.com/louthy/language-ext)

![](../.gitbook/assets/image%20%28376%29.png)

### Language-ext vs LinQ <a id="7536"></a>

Yes FP paradigms in C\# exist since the introduction of LinQ. Here is a mapping between some language-ext functionalities and their equivalence in LinQ :

![](../.gitbook/assets/image%20%28356%29.png)

### **Easy immutable record types**

Implementing immutable data structures is a nightmare in OO languages \(Equals, GetHashCode, IEquatable&lt;A&gt;, IComparer&lt;A&gt;, implementing operators: ==, !=, &lt;, &lt;=, &gt;, &gt;=\).

That’s why there is a **Record** class in language-ext :

```csharp
public class User
{
    public readonly Guid Id;
    public readonly string Name;
    public readonly int Age;

    public User(Guid id, string name, int age)
    {
        Id = id;
        Name = name;
        Age = age;
    }
}

public class UserRecord : Record<UserRecord>
{
    public readonly Guid Id;
    public readonly string Name;
    public readonly int Age;

    public UserRecord(Guid id, string name, int age)
    {
        Id = id;
        Name = name;
        Age = age;
    }
}

[Fact]
public void record_types()
{
    var spongeGuid = Guid.NewGuid();

    var spongeBob = new User(spongeGuid, "Spongebob", 40);
    var spongeBob2 = new User(spongeGuid, "Spongebob", 40);

    Assert.False(spongeBob.Equals(spongeBob2));

    // Use immutable records available in Language-ext
    var spongeBobRecord = new UserRecord(spongeGuid, "Spongebob", 40);
    var spongeBobRecord2 = new UserRecord(spongeGuid, "Spongebob", 40);

    Assert.True(spongeBobRecord.Equals(spongeBobRecord2));
}
```

### **No more out parameters**

Yes in C\# we have out parameters on TryParse for example now it’s finished :

![](../.gitbook/assets/image%20%28361%29.png)

### Option <a id="6be8"></a>

Many functional languages disallow null values, as null-references can introduce hard to find bugs. Option is a type safe alternative to null values. \(it also exists in F\#\).

> **Avoid nulls by using an Option**

An Option&lt;T&gt; can be in one of two states :  
**some** =&gt; the presence of a value  
**none** =&gt; lack of a value

```csharp
Option<int> aValue = 2;
aValue.Map(x => x + 3); // Some(5)

Option<int> none = None;
none.Map(x => x + 3); // None

//Left -> Some, Right -> None
aValue.Match(x => x + 3, () => 0); // 5
none.Match(x => x + 3, () => 0); // 0

// Returns the Some case 'as is' -> 2 and 1 in the None case
int value = aValue.IfNone(1);
int noneValue = none.IfNone(42); // 42
```

_**Match**_ : match down to primitive type

_**Map**_ : We can match down to a primitive type, or can stay in the elevated types and do logic using map.

* Lambda inside map won’t be invoked if Option is in None state
* Option is a replacement for if statements ie if obj == null
* Working in elevated context to do logic

### Lists are functors <a id="a157"></a>

We can map them :

```csharp
new int[] { 2, 4, 6 }.Map(x => x + 3); // 5,7,9
new List<int> { 2, 4, 6 }.Map(x => x + 3); // 5,7,9
//Prefer use List (Immutable list)
List(2, 4, 6).Map(x => x + 3); // 5,7,9
```

### Function composition <a id="cf4c"></a>

What happens when you apply a function to another function? When you use **map on a function**, you’re just doing **function composition :**

```csharp
static Func<int, int> Add2 = x => x + 2;
static Func<int, int> Add3 = x => x + 3;

static int Add5(int x) => Add2.Compose(Add3)(x);
```

### Bind <a id="258f"></a>

Monads apply a function that **returns a wrapped value to a wrapped value**. Monads have a function “bind” to do this.

Suppose **half** is a function that only **works on even numbers.**

![](../.gitbook/assets/image%20%28373%29.png)

What if we feed it a wrapped value? This is where **bind** comes in!

![](../.gitbook/assets/image%20%28386%29.png)

```csharp
static Option<double> Half(double x)
    => x % 2 == 0 ? x / 2 : Option<double>.None;

[Fact]
public void bind_monad()
{
    Option<double>.Some(3).Bind(x => Half(x));// None
    Option<double>.Some(4).Bind(x => Half(x));// Some(2)
}

[Fact]
public void chain_bind_monad()
{
    Option<double>.Some(20)
        .Bind(x => Half(x))// Some(10)
        .Bind(x => Half(x))// Some(5)
        .Bind(x => Half(x));// None
}
```

### Try <a id="fab7"></a>

Exception handling made easier the use of try. No more needs of ugly try/catch that pollutes the flow of your code you can describe your pipeline in a really readable way.

```csharp
public void file_monad_example()
{
    GetLine()
        .Bind(ReadFile)
        .Bind(PrintStrln)
        .Match(success => Console.WriteLine("SUCCESS"),
                failure => Console.WriteLine("FAILURE"));
}

static Try<string> GetLine()
{
    Console.Write("File:");
    return Try(() => Console.ReadLine());
}

static Try<string> ReadFile(string filePath) => Try(() => File.ReadAllText(filePath));

static Try<bool> PrintStrln(string line)
{
    Console.WriteLine(line);
    return Try(true);
}
```

Here if something fails, you have the exception in the failure match part. The better part is that **Try** has a brother called **TryAsync** that is demonstrated in the real life example.

### **Memoization** <a id="5cd6"></a>

Memoization is some kind of caching, if you memoize a function, it will be only executed once for a specific input.

```csharp
static Func<string, string> GenerateGuidForUser = user => user + ":" + Guid.NewGuid();
static Func<string, string> GenerateGuidForUserMemoized = memo(GenerateGuidForUser);

[Fact]
public void memoization_example()
{
    GenerateGuidForUserMemoized("spongebob");// spongebob:e431b439-3397-4016-8d2e-e4629e51bf62
    GenerateGuidForUserMemoized("buzz");// buzz:50c4ee49-7d74-472c-acc8-fd0f593fccfe
    GenerateGuidForUserMemoized("spongebob");// spongebob:e431b439-3397-4016-8d2e-e4629e51bf62
}
```

### **Partial application** <a id="8c7d"></a>

Partial application allows you to **create new function from an existing one by setting some arguments.**

```csharp
static Func<int, int, int> Multiply = (a, b) => a * b;
static Func<int, int> TwoTimes = par(Multiply, 2);

[Fact]
public void partial_app_example()
{
    Multiply(3, 4); // 12
    TwoTimes(9); // 18
}
```

### **Either** <a id="9015"></a>

**Either** represents a value of two types, it is either **a left or a right** by convention **left** is the **failure case**, and **right** the **success case.**

```csharp
public static Either<Exception, string> GetHtml(string url)
{
    var httpClient = new HttpClient(new HttpClientHandler());
    try
    {
        var httpResponseMessage = httpClient.GetAsync(url).Result;
        return httpResponseMessage.Content.ReadAsStringAsync().Result;
    }
    catch (Exception ex) { return ex; }
}

[Fact]
public void either_example()
{

    GetHtml("unknown url"); // Left InvalidOperationException
    GetHtml("https://www.google.com"); // Right <!doctype html...

    var result = GetHtml("https://www.google.com");

    result.Match(
            Left: ex => Console.WriteLine("an exception occured" + ex),
            Right: r => Console.WriteLine(r)
        );
}
```

### **Fold vs Reduce \(Aggregate in LinQ\)** <a id="a499"></a>

* **Fold** takes an explicit initial value for the accumulator. The accumulator and result type can differ as the accumulator is provided separately.
* **Reduce** uses the first element of the input list as the initial accumulator value \(just like the Aggregate function\). The accumulator and therefore result type must match the list element type.

![](../.gitbook/assets/image%20%28372%29.png)

```csharp
[Fact]
public void fold_vs_reduce()
{
    //fold takes an explicit initial value for the accumulator
    //Can choose the result type
    var foldResult = List(1, 2, 3, 4, 5)
        .Map(x => x * 10)
        .Fold(0m, (x, s) => s + x); // 150m

    //reduce uses the first element of the input list as the initial accumulator value
    //Result type will be the one of the list
    var reduceResult = List(1, 2, 3, 4, 5)
        .Map(x => x * 10)
        .Reduce((x, s) => s + x); // 150
}
```

### Real life example <a id="2693"></a>

This example demonstrates the kind of usage you could have of language-ext in application services : **chaining operations / pipelining, improve error handling, no more redundant checks, …**

```csharp
using System;
using System.Threading.Tasks;
using LanguageExt;
using static LanguageExt.Prelude;

namespace language_ext.kata.Account
{
    public class AccountService
    {
        private readonly UserService userService;
        private readonly TwitterService twitterService;
        private readonly IBusinessLogger businessLogger;

        public AccountService(UserService userService, TwitterService twitterService, IBusinessLogger businessLogger)
        {
            this.userService = userService;
            this.twitterService = twitterService;
            this.businessLogger = businessLogger;
        }

        private TryAsync<RegistrationContext> CreateContext(Guid userId) =>
            TryAsync(() => userService.FindById(userId)).Map(user => new RegistrationContext(user));

        private TryAsync<RegistrationContext> RegisterOnTwitter(RegistrationContext context) =>
            TryAsync(() => twitterService.Register(context.Email, context.Name)).Map(context.SetAccount);

        private TryAsync<RegistrationContext> AuthenticateOnTwitter(RegistrationContext context) =>
            TryAsync(() => twitterService.Authenticate(context.Email, context.Password)).Map(context.SetToken);

        private TryAsync<RegistrationContext> Tweet(RegistrationContext context) =>
            TryAsync(() => twitterService.Tweet(context.Token, "Hello I am " + context.Name)).Map(context.SetTweetUrl);

        private TryAsync<RegistrationContext> UpdateUser(RegistrationContext context) =>
            TryAsync(async () =>
            {
                await userService.UpdateTwitterAccountId(context.Id, context.AccountId);
                return context;
            });

        public async Task<Option<string>> Register(Guid id)
        {
            return await CreateContext(id)
                    .Bind(RegisterOnTwitter)
                    .Bind(AuthenticateOnTwitter)
                    .Bind(Tweet)
                    .Bind(UpdateUser)
                    .Do(context => businessLogger.LogSuccessRegister(context.Id))
                    .Map(context => context.Url)
                    .IfFail(failure =>
                    {
                        businessLogger.LogFailureRegister(id, failure);
                        return (string)null;
                    });
        }
    }
}
```

## Conclusion <a id="d278"></a>

> Start using language-ext in your projects is a really good idea. This lib can make your life much more easier.
>
> You can see it at your first step to go into the FP world, before one day be able to use a language like Clojure or F\#.

## Resources <a id="4870"></a>

All the source code is available in my github repository : [https://github.com/ythirion/fp-in-csharp-sandbox](https://github.com/ythirion/fp-in-csharp-sandbox).

{% embed url="https://speakerdeck.com/thirion/functional-programming-made-easy-in-c-number-with-language-ext" %}

If you want to go further :

* _FP in pictures_ : [http://adit.io/posts/2013-04-17-functors,\_applicatives,\_and\_monads\_in\_pictures.html\#just-what-is-a-functor,-really?](http://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html)
* _Gitter on language-ext_ : [https://gitter.im/louthy/language-ext](https://gitter.im/louthy/language-ext)
* _Doc and examples_ : [https://github.com/louthy/language-ext/issues](https://github.com/louthy/language-ext/issues)
* _What’s new in C\# 8_ : [https://medium.com/swlh/how-c-8-helps-software-quality-cfa81a18907f](https://medium.com/swlh/how-c-8-helps-software-quality-cfa81a18907f)
* _“functional core, imperative shell” video_ : [https://discventionstech.wordpress.com/2017/06/30/functional-core-and-imperative-shell/](https://discventionstech.wordpress.com/2017/06/30/functional-core-and-imperative-shell/)
* _**Domain modeling made functional book from Scott Wlaschin**_ : [https://www.amazon.com/Domain-Modeling-Made-Functional-Domain-Driven/dp/1680502549/ref=sr\_1\_1?crid=FXE4W7BCGETO&keywords=domain+modeling+f%23&qid=1576686914&sprefix=design+thin%2Caps%2C330&sr=8-1](https://www.amazon.com/Domain-Modeling-Made-Functional-Domain-Driven/dp/1680502549/ref=sr_1_1?crid=FXE4W7BCGETO&keywords=domain+modeling+f%23&qid=1576686914&sprefix=design+thin%2Caps%2C330&sr=8-1)

