---
description: Hands on Mikado method to refactoring
---

# Mikado kata

This kata is an abstract of the one available here in [java](https://github.com/mikadomethod/kata-java) and [C\#](https://github.com/mikadomethod/kata-dotnet).

### Before we start

Clone the java code from [here](https://github.com/ythirion/kata-java.git)

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

![](../../../.gitbook/assets/image%20%28153%29.png)

###  Find out what we need to do

We analyze the situation to find out what we need to do.

{% hint style="info" %}
We **seek things to try**, where actual consequences of our changes tell us what steps we need to take next. Hence, we strive to make changes that will give us that feedback, as soon as possible.
{% endhint %}

In the Java world, "New deliverables" means we will probably have a separate project source root from which we then create a JAR-file for Stranger Eons Ltd.

{% hint style="success" %}
_**Step**_ : "Create Stranger Eons project" as a prerequisite to our business goal, the root of the Mikado Graph.
{% endhint %}

![](../../../.gitbook/assets/image%20%28158%29.png)

In the naïve spirit, we just create the new project to see what happens. So far so good.

We check in to the main development branch if everything works as it should and the changes make sense : no sense here.

### What next? 

Once again, we want to seek things to try.

* Driving development using Acceptance Tests is something we want to do
* Tests often give us real feedback about the next step

We choose to create a test for Stranger Eons Ltd in the new project, a test which will look much like the one we have already for Gargantua Inc.

{% hint style="success" %}
_**Step**_ : Add a tests case for Stranger Eons
{% endhint %}

## To go further

{% embed url="https://github.com/mikadomethod/kata-java/blob/master/kata.pdf" %}



