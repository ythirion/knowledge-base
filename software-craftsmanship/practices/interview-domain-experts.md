---
description: >-
  This workshop is inspired by Scott Wlaschin's one from Domain Modeling Made
  Functional Workshop
---

# Interview Domain Experts

## Connection - 10'

{% hint style="info" %}
_**Remember a time when you had everything you needed to understand business needs and develop software accordingly.**_
{% endhint %}

* In solo answer to this question :
  * What were the secrets ingredients you had at the time ?
* Share in pair
* Cross-pollination

Or use the Game "[Specifiers and Artists](https://coach-agile.com/serious-game/artists-specifiers/)"

## Concepts - 15'

In Domain Driven Design we talk about Domain Modeling and Ubiquitous Language but how could we do it ?

### Communication issues

* Misunderstanding the requirement
* Acting on the requirement without getting feedback first

#### Café example

* Customer: "Can I have some eggs?"
* Waiter to chef: "Some eggs, please" 
* Russian chef: "Here you go…" 

![](<../../.gitbook/assets/image (525).png>)

* Waiter to chef: "Not fish eggs, chicken eggs " 
* Chef: "Ok, here you go…" 

![](<../../.gitbook/assets/image (526).png>)

* Waiter to chef: " No, cooked chicken eggs" 
* Chef: "Ok, this time I understand…" 

![](<../../.gitbook/assets/image (527).png>)

* Waiter to customer: "Here are your eggs" 
* Customer: "I wanted fried eggs"

![](<../../.gitbook/assets/image (528).png>)

> "_Entre ce que je pense, ce que je veux dire, ce que je crois dire, ce que je dis, ce que vous voulez entendre, ce que vous entendez, ce que vous croyez en comprendre, ce que vous voulez comprendre, et ce que vous comprenez, il y a au moins neuf possibilités de ne pas se comprendre._" - Bernard Werber

#### Huge specifications as a Solution ?

We give a hundred pages to the Chef so he/she know how to make them ?

#### In fact

* We expect the chef to be a subject matter expert – an expert on making breakfast 
* A 200 pages spec should not be needed

#### In real life

Spec for the eggs : **2 fried eggs**

* Shared knowledge of the domain 
  * Everyone is a "breakfast" expert! 
* Shared vocabulary 
  * Everyone knows what "fried eggs" means

![](<../../.gitbook/assets/image (530).png>)

In our day to day job we need to create this Shared Mental Model

#### The importance of feedback

* Fast feedback from the customer is important
  * The customer can be unclear 
  * The waiter can misunderstand 
  * The chef can mess up 

### What's the ideal software development process? 

* Build a shared mental model
  * Means a smaller spec 
  * Less misunderstanding 
* Have frequent feedback 
  * Make sure you are going in the right direction 
  * Do a course correction if goals change 
* Value effectiveness over speed 
  * No point going fast in the wrong direction

#### What we want to avoid

![](<../../.gitbook/assets/image (532).png>)

#### Waterfall

![](<../../.gitbook/assets/image (535).png>)

{% hint style="warning" %}
_**It's the developer's understanding of the domain that gets deployed to production! **_
{% endhint %}

#### Agile

![](<../../.gitbook/assets/image (534).png>)

#### Domain Driven Design

![](<../../.gitbook/assets/image (536).png>)

```
Domain Model == Code == Documentation
```

### Domain Models

#### What non-developers think source code looks like

![](<../../.gitbook/assets/image (537).png>)

####  What DDD source code should look like 

![](<../../.gitbook/assets/image (538).png>)

#### Modeling actions with functions

![](<../../.gitbook/assets/image (539).png>)

{% tabs %}
{% tab title="F#" %}
```fsharp
type Deal = Deck -> (Deck * Card)
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
typealias deal = (Deck) -> Pair<Card?, ShuffledDeck>
```
{% endtab %}

{% tab title="Scala" %}
```scala
type deal = (ShuffledDeck) => (Option[Card], ShuffledDeck)
```
{% endtab %}
{% endtabs %}

![](<../../.gitbook/assets/image (540).png>)

{% tabs %}
{% tab title="F#" %}
```fsharp
type PickupCard = (Hand * Card) –> Hand
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
private typealias pickUpCard = (Card, Hand) -> Hand
```
{% endtab %}

{% tab title="Scala" %}
```scala
type pickUpCard = (Card, Hand) => Hand
```
{% endtab %}
{% endtabs %}

#### Domain Modeling can be an interactive process

* Creating the domain model is an interactive process 
  * Not just for developers
  * Ideally, everyone should participate
* The design process can be done fast

### The Entire Domain Model on 1 page

{% tabs %}
{% tab title="F#" %}
```fsharp
module CardGame =
    type Suit = Club | Diamond | Spade | Heart
    type Rank = Two | Three | Four | Five | Six | Seven | Eight
                | Nine | Ten | Jack | Queen | King | Ace

    type Card = { Suit : Suit; Rank: Rank}
    type Hand = Card list
    type Deck = Card list
    type Player = { Name : string; Hand : Hand}
    type Game = { Deck : Deck; Players : Player list}

    type ShuffledDeck = ShuffledDeck of Card list
    type Deal = ShuffledDeck -> Card option * ShuffledDeck
    type PickUp = Card * Hand -> Hand
    type Shuffle  = Deck -> ShuffledDeck
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
private enum class Suit { Club, Diamond, Spade, Heart }
private enum class Rank { Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten, Jack, Queen, King, Ace }
private data class Card(val suit: Suit, val rank: Rank)

private typealias Hand = List<Card>
private typealias Deck = List<Card>
private typealias ShuffledDeck = List<Card>

private data class Player(val name: String, val hand: Hand)
private data class Game(val deck: Deck, val players: List<Player>)

private typealias Deal = (ShuffledDeck) -> Pair<Card?, ShuffledDeck>
private typealias PickUpCard = (Card, Hand) -> Hand
private typealias Shuffle = (Deck) -> ShuffledDeck
```
{% endtab %}

{% tab title="Scala" %}
```scala
enum Suit:
  case Club, Diamond, Spade, Heart
enum Rank:
  case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten, Jack, Queen, King, Ace

class Card(val suit: Suit, val rank: Rank)

type Hand = List[Card]
type Deck = List[Card]
type ShuffledDeck = List[Card]

class Player(val name: String, val hand: Hand)
class Game(val deck: Deck, val players: List[Player])

type Deal = (ShuffledDeck) => (Option[Card], ShuffledDeck)
type PickUpCard = (Card, Hand) => Hand
type Shuffle = (Deck) => ShuffledDeck
```
{% endtab %}
{% endtabs %}

#### Questions ?

* What do you think about this code ?
  * Non programmer can understand it ?
  * Can spot mistakes from it (check Card Game picture)
    * Leads to instant feedback
* Domain Driven Design
  * No infrastructure / Database related stuff / No PK or FK
  * Not OO driven : no Base clases, Managers, Handlers, ...

### Structuring the domain model with events and workflows

#### Data Transformation

* A business transforms data somehow
  * The value of the business is created in this process of transformation 
* Data that is sitting there unused is not contributing anything 

![](<../../.gitbook/assets/image (541).png>)

#### Events

* What causes an employee or process to start working with that data and adding value? 
  * An **event**! 
* Examples of events: 
  * New information arrived
  * Context changed
  * A customer request has been received

![](<../../.gitbook/assets/image (542).png>)

#### Workflow

![](<../../.gitbook/assets/image (543).png>)

* In functional programming, workflows are the "unit of development" for modeling, coding, and delivery
* _**Workflows are modeled as functions**_

![](<../../.gitbook/assets/image (544).png>)

```fsharp
type MyWorkflow = EventData * OtherData * State ->
                        OutputEvents * OtherOutputs * State
```

## Concrete Practice - 30'

* In groups of 4
* Pick a domain to model 
* Model it as a group
* Remember
  * It is not : Database or OO modeling
  * If you have a "base", "factory", "manager", or "helper" class then you're doing it wrong

### How to model a domain ?

* Pick one workflow to focus on 
* Learn about that workflow by interviewing domain expert(s) 
* Document your knowledge with a textual domain model

### How to interview ?

* Listen to and learn from the experts 
  * Don't impose your own ideas 
  * Avoid yes/no questions 
  * If you hear "it depends", drill deeper 
* Disagreement between experts is OK 
  * The design process is about getting everyone on the same page, and using the same language
* Everyone must be in the room 
  * Otherwise they miss being part of the process.
  * It's not just about the results

### How to model a workflow

* What is needed for the workflow input?
  * What data is from the triggering event itself
  * What data is from the current state of the system? E.g. loaded from storage?
  * What other data is needed?
* What is the output of the workflow?
  * What events are needed for broadcast to downstream systems?
  * What data should be saved to storage?
* How does the state of the system change?
  * Does data need to be loaded, changed, and resaved?
* What are the side effects? (Things that must be done but are internal to the domain)

### Guidelines

Each team picks a domain and then collaborate on building a shared mental model and documenting the domain.

* One person takes the role of **domain expert**
* One person takes the role of **main interviewer** (although everyone can ask questions)
* One person **documents the domain** (although everyone can contribute)

![](<../../.gitbook/assets/image (545).png>)

_**The interviewer(s) will ask the domain expert questions in order to understand the domain and become domain experts themselves.**_

**The goal is to:**

* Document the domain using AND and OR, etc
* And at the same time, develop a shared mental model and shared language among the group

Possible domains to use:

* ATM/Cash Machine
* Microwave oven
* Self-service espresso/cappuccino machine
* Delivery tracking service (e.g Fedex/DHL)
* Your own domain that you are an expert in

\====================

### "Place order" Example

```fsharp
Workflow: "Place order"
triggered by:
  OrderReceived event
input:
  Order (from the triggering event)
  ProductCatalog  (to lookup prices)
output:
  OrderPlaced event (to be sent to downstream systems)
  The final PlacedOrder (to store in the database)
  An OrderAcknowledgment (to be sent to the customer)
```

#### Document the data with "AND"

![](<../../.gitbook/assets/image (546).png>)

```fsharp
data Order =
  CustomerInfo
  AND ShippingAddress
  AND BillingAddress
  AND list of OrderLines
  AND AmountToBill

data OrderLine =
  Product
  AND OrderQuantity
  AND Price

data CustomerInfo = CustomerName AND ContactInfo
data CustomerName = FirstName AND LastName

data BillingAddress = ??? // don't know yet
```

#### Document choices with OR

```fsharp
data OrderQuantity =
  UnitQuantity
  OR KilogramQuantity

data ContactInfo =
  EmailAddress
  OR PhoneNumber
```

#### Document simple/constrained types

```fsharp
data UnitQuantity = integer between 1 and ?
data KilogramQuantity = decimal between ? and ?

data EmailAddress = non empty string containing an @ symbol
data PhoneNumber = non empty string containing only digits, hyphens, and spaces
```

## Conclusion - 5'

* Reflect on what happened during this session
  * Building a shared model 
    * Did it work? Are you using the same vocabulary? 
  * Fast feedback on the design 
    * A few weeks of coding can save hours of talking! 
  * What this practice could bring on your current development ?
* Bonus : Write a feedforward for yourself :
  * Formulate requests or propose future-oriented options or solutions

_**Example**_ : _**For your next**_ report, I suggest that you divide the summary of your activities by date or by function (budget, planning, operations management, ...). _**So that**_ it will be easier to read it, to find the information I need and to refer to it later.

### Cheat sheet

* _**Domain Model**_ :
  * "A set of simplifications that represent those aspects of a domain that are relevant to a particular problem"
  * The domain model is part of the software design 
  * A good domain model reduces "garbage in" 
  * A good domain model represents shared knowledge 
* _**The Everywhere ("Ubiquitous") Language **_
  * Concepts and vocabulary associated with the domain 
  * Shared by both the team members and the source code
* _**Domain Event**_
  * A record of something that happened in the system 
  * An event often triggers activity such as workflows 
* _**Workflow**_ 
  * A business process, a story, a use-case, etc. 
  * Modeled as a function with inputs and outputs 

### Resources

* [Domain Modeling Made Functional book by Scott Wlaschin](https://pragprog.com/titles/swdddf/domain-modeling-made-functional/)
* [Domain Modeling Made Functional Video](https://www.youtube.com/watch?v=2JB1\_e5wZmU\&ab_channel=KanDDDinsky)

![](<../../.gitbook/assets/image (547).png>)

#### Implementation of the Domain Model

{% tabs %}
{% tab title="F#" %}
```fsharp
module CardGameImplementation =
    open CardGame

    let pickup : PickUp =
        fun (card,hand) ->
            // the "::" operator prepends the card to the hand
            let newHand = card::hand
            newHand

    let deal : Deal =
        fun (ShuffledDeck deck) ->
            // the "::" pattern deconstructs a non-empty list into head/tail
            match deck with
            | first::rest -> Some first, ShuffledDeck rest
            | [] -> None, ShuffledDeck []

    let shuffle : Shuffle =
        fun deck ->
            // don't worry about how to do proper shuffling
            let random = System.Random()

            deck
            |> List.map (fun card -> random.Next(), card )  // add a random to each card
            |> List.sortBy (fun (rand,card) -> rand)       // sort
            |> List.map (fun (rand,card) -> card)          // remove the random number
            |> ShuffledDeck
```
{% endtab %}

{% tab title="Kotlin" %}
```kotlin
private val pickUp : PickUpCard = { card, hand -> hand + card }
private val dealer : Deal = { shuffledDeck ->
    when {
        shuffledDeck.isEmpty() -> Pair(null, ArrayList())
        else -> Pair(shuffledDeck.first(), shuffledDeck.drop(1))
    }
}
private val shuffle : Shuffle = { deck -> deck.shuffled() }
```
{% endtab %}

{% tab title="Scala" %}
```scala
import scala.util.Random

val pickUp: PickUpCard =  (card, hand) => card :: hand
val dealer: Deal = (shuffledDeck) => shuffledDeck match {
  case Nil => (None, Nil)
  case head :: tail => (Some(head), tail)
}
extension(deck: Deck)
  def shuffled: ShuffledDeck = Random.shuffle(deck)

val shuffle: Shuffle = deck => deck.shuffled
```
{% endtab %}
{% endtabs %}
