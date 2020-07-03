---
description: Hands on Mikado method to refactoring
---

# Mikado kata

## Facilitation notes

This kata is an abstract of the one available here in [java](https://github.com/mikadomethod/kata-java) and [C\#](https://github.com/mikadomethod/kata-dotnet).

### Before we start

Clone the java code from [here](https://github.com/ythirion/kata-java.git)

### Connection

* What was your last refactoring ?
* How was it ?
* What was your goal / plan ?

### Concepts : Mikado method explained

{% page-ref page="./" %}

### Concrete practice

* Open existing code
* Draw class diagram
  * What does the code smell ?
  * Does it break any SOLID principle ?

#### Baby steps

* Together :
  * Create the project
  * Create the test
* Then ask question :
  * What is the next step ?
  * Do it : extract common dependencies
    * Naive way : just take the UI
  * Roll back
  * Update the graph

### **Conclusion**

* What do you think about this method ?
* How can it be useful ?
* Use it on your next refactoring
  * What is your feedback ?

## Context

Pasta Software is a small family-owned company. By good luck and coincidence, their pride and joy MasterCrüpt \(TM\), has been sold to a new customer. 

But now, problems arise. 

The very, very secret obfuscation algorithm in the application cannot be exposed between the old customer Gargantua Inc and the new customer, Stranger Eons Ltd.

Without really knowing it, Pasta Software has just **put themselves into technical debt by changing their business model,** i.e getting a customer with slightly different needs. They did not see this coming and the code isn’t flexible enough to offer an easy way out. 

The design has to change so that confidential information doesn’t leak between their customers.

{% hint style="info" %}
_It is virtually impossible to tell how a system will evolve in advance. Trying to anticipate all future changes to a system and make the code flexible enough to handle them only makes the codebase bloated. In fact, that kind of over-design makes the code more complex and will likely become a problem in itself._
{% endhint %}

#### Ubiquitous language

* _**Leetspeak**_ : the way hackers and crackers avoided text filters on Bulletin Board Systems \(BBS\) in the eighties by re-placing alphabetic characters with non-alphabetic, but resembling, characters. 
  * For instance, in one leet dialect ’leet’ is translated to ’l33t’, where ’3’ is the mirrored capital ’E’.

### Existing code

Here is the entire code of the system :

{% tabs %}
{% tab title="AcceptanceTest.java" %}
```java
package mastercrupt;

import static org.junit.Assert.assertEquals;
import mastercrupt.UI;

import org.junit.Test;
public class AcceptanceTest {
    @Test
    public void testLeeting() throws Exception {
        UI ui = new UI();
        assertEquals("Leeted: S3cr3t", ui.leetMessage("Secret"));
    }
}
```
{% endtab %}

{% tab title="UI.java" %}
```java
package mastercrupt;

public class UI {
    private Application application = new Application();
    private String leeted;
    
    public String leetMessage(String unLeeted) {
        application.leet(unLeeted, this);
        return "Leeted: " + leeted;
    }

    public void setLeeted(String leeted) {
        this.leeted = leeted;
    }
}
```
{% endtab %}

{% tab title="Application.java" %}
```java
package mastercrupt;

public class Application {
    public void leet(String string, UI ui) {
        ui.setLeeted(Leeter.leet(string));
    }
    public static void main(String[] args) {
        UI ui = new UI();
        System.out.println(ui.leetMessage(args[0]));
    }
}
```
{% endtab %}

{% tab title="Leeter.java" %}
```java
package mastercrupt;

public class Leeter {
	public static String leet(String message) { 
		return message.replace('e', '3');
	}
}
```
{% endtab %}
{% endtabs %}

## Baby steps

We will run this kata in baby steps_**.**_ 

{% hint style="warning" %}
_The code is really easy and could be rewritten in only a few minutes but the whole exercise has been created to practice Mikado method and to do so the creator proposes to follow those steps **:**_
{% endhint %}

![](../../../.gitbook/assets/image%20%28152%29.png)

### Draw the class diagram of the system

![Class diagram](../../../.gitbook/assets/image%20%28154%29.png)

#### How does it work ?

* The _**UI**_ class creates an _**Application**_ instance.
* The _**Application**_ instance is called with the string to leet and a reference to this UI class. 
* The _**Application**_ instance call back _**UI**_ to set the leeted String value.
* The _**Application**_ class uses the _**Leeter**_ class, to leet the given string and calls back to the provided UI instance with the leeted value. 
* The _**Application**_ class also contains the main method for the application.
* The _**Leeter**_ simply performs the leeting of the incoming message by substituting the character ’e’ with the character ’3’.

{% hint style="info" %}
**It only takes a few classes to create a mess.** For instance there’s a circular dependency between UI and Application, not to mention the mysterious callbacks.
{% endhint %}

_**In reality, codebases are a lot bigger and more complex by nature, so the ways of creating a mess are almost unlimited.**_ 

{% hint style="success" %}
Mikado Method can be applied no matter how big or small the codebase is. The method serves as a guide and helps to identify the critical change path in order to be able to deliver. 
{% endhint %}

### Before touching the code

Before making any changes to the code, we make sure that everything works. We check that :

* The code compiles
* All the existing tests run 
* There are no checked out files nor uncommitted changes

We start from a clean state.

### Define our goal

Now, our goal is to create a system that can be delivered to Stranger Eons Ltd.

{% hint style="success" %}
_**Mikado Goal**_ : new deliverable for Stranger Eons Ltd
{% endhint %}

![](../../../.gitbook/assets/image%20%28162%29.png)

###  Find out what we need to do

We analyze the situation to find out what we need to do.

{% hint style="info" %}
We **seek things to try**, where actual consequences of our changes tell us what steps we need to take next. Hence, we strive to make changes that will give us that feedback, as soon as possible.
{% endhint %}

In the Java world, "New deliverables" means we will probably have a separate project source root from which we then create a JAR-file for Stranger Eons Ltd.

{% hint style="success" %}
_**Step**_ : "Create Stranger Eons project" as a prerequisite to our business goal, the root of the Mikado Graph.
{% endhint %}

![](../../../.gitbook/assets/image%20%28157%29.png)

In the naïve spirit, we just create the new project to see what happens. So far so good.

We check in to the main development branch if everything works as it should and the changes make sense : no sense here.

{% code title="pom.xml" %}
```markup
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>mastercrupt.strangereons</groupId>
    <artifactId>strangereons</artifactId>
    <version>1.0-SNAPSHOT</version>
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```
{% endcode %}

### What next? 

Once again, we want to seek things to try.

* Driving development using Acceptance Tests is something we want to do
* Tests often give us real feedback about the next step

We choose to create a test for Stranger Eons Ltd in the new project, a test which will look much like the one we have already for Gargantua Inc.

{% hint style="success" %}
_**Step**_ : Add a tests case for Stranger Eons
{% endhint %}

![](../../../.gitbook/assets/image%20%28175%29.png)

```java
package mastercrupt.strangereons;

import mastercrupt.UI;
import org.junit.Test;

public class AcceptanceTest {
    @Test
    public void testLeeting() throws Exception {
        UI ui = new UI();
        assertEquals("Leeted:5ecret ", ui.leetMessage("Secret"));
    }
}
```

Can not compile : the UI class is in the mastercrupt project and we must avoid a dependency to that project, since it still contains code that can’t be shared

![](../../../.gitbook/assets/image%20%28181%29.png)

![](../../../.gitbook/assets/image%20%28161%29.png)

  
To resolve the compilation problems, one option is to duplicate the entire project. We won’t do that because we think duplication is bad, as described in detail in Don’t Repeat Yourself - DRY.

So, _**we need to change the chain of dependencies in order to allow us to add the test case to the project without any compilation errors**_.

![](../../../.gitbook/assets/image%20%28180%29.png)

### Extract common dependencies

* What to do about the dependency problems ?
* UI has some common logic which we want to use in both projects
* Choose to create a new project for the UI code and this project will be used as a common dependency : `mastercrupt.shared` for example

![](../../../.gitbook/assets/image%20%28185%29.png)

* We can't compile because of the circular dependency

#### Rollback time

Now it’s time for a non-intuitive step, but an important part of the method: Back out broken code.

{% hint style="warning" %}
_**Step**_ **:** Roll back to the tag "Before new client".
{% endhint %}

The `strangereons` project has compilation problems and we don’t want to do anything there, nor any place else. So, we roll back to the very beginning.

We update our Mikado graph

![](../../../.gitbook/assets/image%20%28177%29.png)

![](../../../.gitbook/assets/image%20%28179%29.png)

{% hint style="success" %}
_**Decision**_ : Break dependency between UI and Application.
{% endhint %}

### Break circular dependency

We often add decisions, like breaking dependencies, to the Mikado Graph even before we know exactly how to resolve them. Such items serve as a decision node, and they help us defer commitment until the last responsible moment.

![](../../../.gitbook/assets/image%20%28166%29.png)

#### Dependency Inversion Principle

A common way to break circular dependencies is to introduce an interface for one of the classes involved in order to change the direction of the dependency. 

We choose to introduce an interface for the `Application` class, the `ApplicationInterface`.

{% hint style="success" %}
_**Step**_ : Extract ApplicationInterface, including method leet\(...\)
{% endhint %}

![](../../../.gitbook/assets/image%20%28159%29.png)

```java
public interface ApplicationInterface {
    void leet(String string, UI ui);
}
```

{% hint style="success" %}
_**Step**_ : Inject ApplicationInterface instance into the UI constructor
{% endhint %}

![](../../../.gitbook/assets/image%20%28183%29.png)

{% tabs %}
{% tab title="ApplicationInterface.java" %}
```java
package mastercrupt;

public interface ApplicationInterface {
    void leet(String string, UI ui);
}
```
{% endtab %}

{% tab title="Application.java" %}
```java
package mastercrupt;

public class Application implements ApplicationInterface {
    @Override
    public void leet(String string, UI ui) {
        ui.setLeeted(Leeter.leet(string));
    }

    public static void main(String[] args) {
        UI ui = new UI(new Application());
        System.out.println(ui.leetMessage(args[0]));
    }
}
```
{% endtab %}

{% tab title="AcceptanceTest.java" %}
```java
package mastercrupt;

import org.junit.Test;

import static org.junit.Assert.assertEquals;
public class AcceptanceTest {
    @Test
    public void testLeeting() throws Exception {
        UI ui = new UI(new Application());
        assertEquals("Leeted: S3cr3t", ui.leetMessage("Secret"));
    }
}
```
{% endtab %}
{% endtabs %}

By doing this we have solved the circular dependency problem

![](../../../.gitbook/assets/image%20%28171%29.png)

{% hint style="success" %}
_**Commit**_ : Broke circular dependency between UI and Application
{% endhint %}

![](../../../.gitbook/assets/image%20%28173%29.png)

We can now tick the 3 leafs : \(here in green on the graph\)

* Extract Application interface
* Inject instance of ApplicationInterface
* Break circular dependency

### Move the code to new project

{% hint style="success" %}
We perfectly now what are our next steps : go through our graph to our goal

* Create UI project
* Move UI code to UI project
{% endhint %}

![](../../../.gitbook/assets/image%20%28184%29.png)

{% hint style="success" %}
_**Commit :**_ UI-code in separate project
{% endhint %}

![](../../../.gitbook/assets/image%20%28160%29.png)

### Create the Stranger Eons project

{% tabs %}
{% tab title="AcceptanceTest.java" %}
```java
@Test
public void testLeeting()throws Exception {
​	UI ui = new UI(new StrangerEonsApplication()) ;
​	assertEquals("Leeted : 5ecret ", ui.leetMessage("Secret"));
}
```
{% endtab %}

{% tab title="StrangerEonsApplication.java" %}
```java
public class StrangerEonsApplication implements ApplicationInterface {
    @Override
    public void leet( String string, UI ui) {
    }
}
```
{% endtab %}
{% endtabs %}

![](../../../.gitbook/assets/image%20%28174%29.png)

![](../../../.gitbook/assets/image%20%28172%29.png)

We have reached our goal and can stop here.

### Conclusion

We’ve managed to morph the code from one state that didn’t allow us to do what we wanted, to one that actually does what we want. 

We did this by using the Mikado Method to 

* Write down the goals
* Seek things to try
* Back out broken code
* Fix the leaves first

### What do you think about this method ?

* How can it be useful ?
* Use it on your next refactoring
  * What is your feedback ?

## To go further

{% embed url="https://github.com/mikadomethod/kata-java/blob/master/kata.pdf" %}



