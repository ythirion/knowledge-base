---
description: by Matthew Skelton and Manuel Pais
---

# Team Topologies

## Pitch

Effective software teams are essential for any organization to deliver value continuously and sustainably. 

But how do you build the best team organization for your specific goals, culture, and needs? 

Team Topologies is a practical, step-by-step, adaptive model for organizational design and team interaction based on four fundamental team types and three team interaction patterns. 

It is a model that treats teams as the fundamental means of delivery, where team structures and communication pathways are able to evolve with technological and organizational maturity. 

In Team Topologies, IT consultants Matthew Skelton and Manuel Pais share secrets of successful team patterns and interactions to help readers choose and evolve the right team patterns for their organization, making sure to keep the software healthy and optimize value streams. 

Team Topologies is a major step forward in organizational design for software, presenting a well-defined way for teams to interact and interrelate that helps make the resulting software architecture clearer and more sustainable, turning inter-team problems into valuable signals for the self-steering organization.

![](../../../.gitbook/assets/image%20%28608%29.png)

## Preface

* A functional book
* Part I - explores Conway’s law
  * The way organizational interrelationships constrain the design of systems we build
  * And how we can use this tendency to our advantage
* Part II - set of static team patterns
  * Have been proven in the industry and the implications of choosing one pattern over another 
  * with Conway’s law and organizational context in mind
* Part III - ways to evolve the organization design 
  * To provide powerful capabilities for innovation and rapid delivery i
  * How to use the Team Topologies approach to create a sensing organization that responds to the market and user demands,
  * And accounts for the implications this has for hiring and skills

![](../../../.gitbook/assets/image%20%28610%29.png)

## Part 1 - Team As The Means of Delivery

* The Problem with Org Charts
  * Must shift our thinking from treating teams as collections of interchangeable individuals that will succeed as long as they follow the “right” process and use the “right” tools
  * TO treating people and technology as a single human/computer carbon/silicon sociotechnical ecosystem
  * We need to ensure that teams are intrinsically motivated and are given a real chance of doing their best work within such a system
* Team Topologies focuses on 
  * how to set up dynamic team structures
  * interaction modes that can help teams adapt quickly to new conditions
* Org chart is always out os sync with reality

![](../../../.gitbook/assets/image%20%28612%29.png)

* By empowering teams, and treating them as fundamental building blocks
  * Individuals inside those teams move closer together to act as a team rather than just a group of people
* Explicitly agree on interaction modes with other teams
  * Expectations on behaviors become clearer and inter-team trust grows

{% hint style="info" %}
_**Team structures must match the required software architecture or risk producing unintended software**_
{% endhint %}

### Cognitive Load and Bottlenecks

{% hint style="info" %}
_When cognitive load isn’t considered, teams are spread thin trying to cover an excessive amount of responsibilities and domains. Such a team lacks bandwidth to pursue mastery of their trade and struggles with the costs of switching contexts.”_
{% endhint %}

![](../../../.gitbook/assets/image%20%28609%29.png)

### Conway's law

* An organization that is arranged in functional silos
  * Where teams specialize in a particular function, such as QA, DBA, or security
  * Is unlikely to ever produce software systems that are well-architected for end-to-end flow
* The Reverse Conway Maneuver
  * Accelerate: The Science of Dev Ops 
    * "Our research lends support to what is sometimes called the “inverse Conway maneuver,” which states that organizations should evolve their team and organizational structure to achieve the desired architecture. The goal is for your architecture to support the ability of teams to get their work done—from design through to deployment—without requiring high-bandwidth communication between teams."

> “Team assignments are the first draft of the architecture." - Michael Nygard

* The fundamental _**means of delivery is the team**_
  * The system architecture needs to 
    * Enable 
    * Encourage fast flow within each team
  * In practice, this means that we can follow proven software-architecture good practices:
    * Loose coupling—components do not hold strong dependencies on other components
    * High cohesion—components have clearly bounded responsibilities, and their internal elements are strongly related 
    * _Clear and appropriate version compatibility_
    * Clear and appropriate cross-team testing

### **Organization Design Requires Technical Expertise**

> “if we have managers deciding . . . which services will be built, by which teams, we implicitly have managers deciding on the system architecture.” - Ruth Malan

* How much awareness does the HR department have about software systems? 
* Does the group of department leaders deciding how to allocate budget across teams know of the likely effects of their choices on the viability of the software architecture?

{% hint style="info" %}
Allan Kelly’s view of a software architect’s : 

"More than ever I believe that someone who claims to be an **Architect needs both technical and social skills**, they need to understand people and work within the social framework. They also need a remit that is broader than pure technology—they need to **have a say in organizational structures and personnel issues**, i.e. they need to be a **manager too**."
{% endhint %}

* Restrict Unnecessary Communication
  * Not all communication and collaboration is good
  * _**We need focused communication between specific teams**_
* 2 rules
  * The organization’s design limits the number of possible solutions for a given system’s architecture
  * The speed of software delivery is strongly affected by how many team dependencies the organization design instills
* _**Fast flow requires restricting communication between teams**_
  * Team collaboration is important for gray areas of development
  * Where discovery and expertise is needed to make progress

{% hint style="success" %}
“_Disbanding high-performing teams is worse than vandalism: it is corporate psychopathy._" — Allan Kelly, Project Myopia
{% endhint %}

### Team first-thinking

* Research by Google on their own teams 
  * Who is on the team matters less than the team dynamics
  * _**When it comes to measuring performance, teams matter more than individuals**_

### Use Small, Long-Lived Teams as the Standard

* “team” = stable grouping of five to nine people who work toward a shared goal as a unit
* > _An organization should never assign work to individuals; only to teams_
* Allowing teams to grow beyond the _**magic seven-to-nine size**_ imperils the viability of the software being built by that team \(Dunbar’s number\)
  * Trust will begin to break down
  * Unsuitable decisions might ensue
* Organizations need to maximize **trust between people on a team**
  * That means limiting the number of team members

#### Smaller Size Fosters Trust

* Anthropological research shows that the type and depth of relationship we can have with people has clear limits :
  * Around five people—limit of people with whom we can hold close personal relationships and working memory 
  * Around fifteen people—limit of people with whom we can experience deep trust
  * Around fifty people—limit of people with whom we can have mutual trust
  * Around 150 people—limit of people whose capabilities we can remember

### The Team Owns the Software

* With small, long-lived teams in place
  * We can begin to improve the ownership of software
* Team ownership helps to provide the vital “continuity of care”
* The danger of allowing multiple teams to change the same system or subsystem 
  * No one owns the changes made or the resulting mess
* There should be no shared ownership of components, libraries, or code

#### Team Members Need a Team-First Mindset

* Put the needs of the team above their own

#### Embrace Diversity in Teams

* Find Novel and creative ways
* Produce more creative solutions

#### Reward the Whole Team not individuals

### Good Boundaries Minimize Cognitive Load

* Organizations need to _**ensure**_ that the _**cognitive load on a team is not too high**_
* Restrict Team Responsibilities to Match Team Cognitive Load
* **Cognitive load** 
  * Characterized in 1988 
  * By psychologist John Sweller 
  * “_**the total amount of mental effort being used in the working memory.**_”
  * 3 types of cognitive load
    * **Intrinsic** —relates to aspects of the task fundamental to the problem space 
      * What is the structure of a Java class?
      * How do I create a new method?
    * **Extraneous** —relates to the environment in which the task is being done 
      * How do I deploy this component again?
      * How do I configure this service?
    * **Germane** —relates to aspects of the task that need special attention for learning or high performance 
      * How should this service interact with the ABC service?

{% hint style="info" %}
_**With a team-first approach, the team’s responsibilities are matched to the cognitive load that the team can handle**_
{% endhint %}

### Measure the Cognitive Load Using Relative Domain Complexity

* Ask the team : 
  * “Do you feel like you’re effective and able to respond in a timely fashion to the work you are asked to do?”
* Trying to determine the cognitive load of software using simple measures such as lines of code, number of modules, classes, or methods is misguided
* When measuring cognitive load
  * what we really care about = domain complexity
  * how complex is the problem that we’re trying to solve with software? 
  * A domain = a more largely applicable concept than software size

#### 3 heuristics

1. Assign each domain to a single team
   * Instead of splitting responsibilities of a single domain to multiple teams
   * Split the domain into subdomains 
     * Then assign each new subdomain to a single team
2. A single team should be able to accommodate two to three “simple” domains”
3. A team responsible for a complex domain should not have any more domains assigned to them—not even a simple one

#### Design “Team APIs” and Facilitate Team Interactions

* Team API = an API surrounding each team
* It includes :
  * Code: runtime endpoints, libraries, clients, UI, etc. produced by the team 
  * Versioning: how the team communicates changes to its code and services 
  * Wiki and documentation: especially how-to guides for the software owned by the team 
  * Practices and principles: the team’s preferred ways of working 
  * Communication: the team’s approach to remote communication tools, such as chat tools and video conferencing 
  * Work information: what the team is working on now, what’s coming next, and overall priorities in the short to medium term 
  * Other: anything else that other teams need to use to interact with the team
* Team API should consider usability by other teams

## Part 2 - Team Topologies that Work for Flow

![](../../../.gitbook/assets/image%20%28611%29.png)

### Stream-Aligned teams

* “stream” : the continuous flow of work aligned to a business domain or organizational capability
  * Requires clarity of purpose and responsibility
* Team aligned to a single, valuable stream of work
  * Might be 
    * A single product or service
    * A single set of features
    * A single user journey
    * or a single user persona
* Work on the full spectrum of delivery
* **Primary team type in an organization**

{% hint style="info" %}
_**Purpose of the other fundamental team topologies is to reduce the burden on the stream-aligned teams**_
{% endhint %}

#### **Capabilities**

* Application security
* Commercial and operational viability analysis 
* Design and architecture 
* Development and coding 
* Infrastructure and operability 
* Metrics and monitoring 
* Product management and ownership 
* Testing and quality assurance User experience \(UX\)

> critical not to assume each capability maps to an individual role in the team

* Be able, as a team, to 
  * understand and act upon the above capabilities
* Have a mix of generalists and a few specialists

#### **Expected Behaviors**

* Aims to produce a steady flow of feature delivery
* Correct based on feedback from the latest changes
* Uses an experimental approach to product evolution
  * Expecting to constantly learn and adapt
* Team has minimal \(ideally zero\) hand-offs of work to other teams
* Must have time and space to address code quality changes \(sometimes called “tech debt”\) to ensure that changing the code remains safe and easy to do. 
* Proactively and regularly reaches out to the supporting fundamental-topologies teams \(complicated subsystem, enabling, and platform\)
* Feel they have achieved or are in the path to achieving “autonomy, mastery, and purpose,” the three key components of engaged knowledge workers, according to Daniel Pink

### **Enabling Teams**

* In Accelerate High-performing teams are continuously improving their capabilities in order to stay ahead
  * But how can a stream-aligned team with end-to-end ownership find the space for researching, reading about, learning, and practicing new skills?”
* Enabling team is composed of specialists in a given technical \(or product\) domain
  * They help bridge this capability gap
* Have a strongly collaborative nature
* Avoid becoming “ivory towers” of knowledge
* Increase the autonomy of stream-aligned teams by growing their capabilities 
  * With a focus on their problems first
  * Not the solutions per se
* Should not be a permanent dependency

#### **Expected Behaviors**

{% hint style="info" %}
_The mission of enabling teams is to help stream-aligned teams acquire missing capabilities, usually around a specific technical or product management area_
{% endhint %}

* Seeks to understand the needs of stream-aligned teams
  * Establishing regular checkpoints
  * Jointly agreeing when more collaboration is needed
* Stays ahead of the curve in keeping abreast of new approaches, tooling, and practices in their area of expertise
* Act as a proxy for external \(or internal\) services that are currently too difficult for stream-aligned teams to use directly
* Promotes **learning** not only inside the enabling team but across stream-aligned teams
  * Acting as a curator that facilitates appropriate knowledge sharing inside the organization

{% hint style="info" %}
_**Enabling teams do not exist to fix problems that arise from poor practices, poor prioritization choices, or poor code quality within stream-aligned teams**_
{% endhint %}

### Complicated-Subsystem Teams

* Responsible for building and maintaining
  * a part of the system that depends heavily on specialist knowledge
* GOAL of this team : 
  * Reduce the cognitive load of stream-aligned teams 
    * working on systems that include or use the complicated subsystem
  * Examples : 
    * Video processing codec
    * Mathematical model
    * Real-time trade reconciliation algorithm
    * Transaction reporting system for financial services
    * Face-recognition engine
  * Created only when a subsystem needs mostly specialized knowledge

#### **Expected Behaviors**

* Mindful of the current stage of development of the subsystem / acts accordingly
  * High collaboration with stream-aligned teams during early exploration and development phases
  * Reduced interaction and focus on the subsystem interface and feature evolution and usage during later stages
* Delivery speed and quality for the subsystem is clearly higher than if/when the subsystem was being developed by a stream-aligned team
* Prioritizes and delivers upcoming work 
  * Respecting the needs of the stream-aligned teams that use the complicated subsystem

### Platform Teams

* Purpose : enable stream-aligned teams to deliver work with substantial autonomy
* Provides internal services to reduce the cognitive load that would be required from stream-aligned teams to develop these underlying services

{% hint style="info" %}
_A digital platform is a foundation of self-service APIs, tools, services, knowledge and support which are arranged as a compelling internal product._ 
{% endhint %}

* Treat the services they offer as products
  * reliable
  * usable
  * fit for purpose
* A thick platform might consist of the combination of several inner platform teams
  * Providing a myriad of services
* A thin platform 
  * could simply be a layer on top of a vendor-provided solution
* Examples :
  * From provisioning a new server instance 
  * To providing tools for access management and security enforcement

#### **Expected Behaviors**

* Uses strong collaboration with stream-aligned teams to understand their needs
* Relies on fast prototyping techniques
  * Involves stream-aligned team members for fast feedback 
* Has a strong focus on 
  * Usability and reliability for their services
    * Treating the platform as a product
    * Regularly assesses if the services are still fit for purpose and usable
* Leads by example
  * Using the services they provide internally \(when applicable\)
  * Partnering with stream-aligned teams and enabling teams
  * Consuming lower level platforms \(owned by other platform teams\) whenever possible
* Understands that adoption of internal new services, like new technologies, is not immediate, but instead evolves along an adoption curve

#### A Good Platform Is “Just Big Enough”

* A good platform provides 
  * standards
  * templates
  * APIs
  * well-proven best practices for Dev teams to use to innovate rapidly and effectively
* Thinnest Viable Platform
  * A list on a wiki page of underlying components or services used by consuming software

### Convert Common Team Types to the Fundamental Team Topologies

{% hint style="info" %}
_"Most organizations would see major gains in effectiveness by mapping each of their teams to one of the four fundamental topologies; that is, identify which of the four fundamental topologies would represent the best way of working for each team, and then change that team’s remit to adopt the purpose and behavior patterns of that topology.”_
{% endhint %}

* Infrastructure Teams to Platform Teams 
  * Platform is managed as a product using proven software development techniques
    * May be quite unfamiliar to infrastructure people
* Component teams to Platform or Other Team Types
  * DBA teams -&gt; enabling teams
    * Focus on spreading awareness of DB Perf, monitoring, ...
* Tooling Teams to Enabling Teams or Part of the Platform
* Converting Architecture and Architects
  * Most effective pattern : a part-time enabling team
  * Emphasizes that many decisions should be taken by implementing teams rather than left to the architecture team

### Software Boundaries or “Fracture Planes

{% hint style="info" %}
_A fracture plane is a natural seam in the software system that allows the system to be split easily into two or more parts_
{% endhint %}

* Look for similar fracture planes in software 
  * To find the natural split points that lead to software boundaries
* **Fracture Plane: Business Domain Bounded Context**
  * A bounded context :
    * A unit for partitioning a larger domain \(or system\) model into smaller parts
    * Each of which represents an internally consistent business domain area
  * Identifying bounded contexts :
    * Requires a fair amount of business knowledge and technical expertise
  * Aligns technology with business
    * Reduces mismatches in terminology and “lost in translation” issues, improving the flow of changes and reducing rework
* **Fracture Plane: Regulatory Compliance**
* **Fracture Plane: Change Cadence**
  * With a monolith, every piece moves at the speed of the slowest part
  * Splitting off the parts of the system that typically change at different speeds allows them to change more quickly
* **Fracture Plane: Team Location**
  * Working across different time zones aggravates communication delays and introduces bottlenecks
* **Fracture Plane: Risk**
  * Splitting off subsystems with clearly different risk profiles allows mapping the technology changes to business appetite or regulatory
* **Fracture Plane: Performance Isolation**
  * In particular types of systems, differentiating levels of performance might be beneficial
  * Splitting off such a subsystem based on particular performance demands helps to ensure
    * it can scale autonomously
    * increasing performance and reducing cost
* **Fracture Plane: Technology**
* **Fracture Plane: User Personas**

## Part 3 - Evolving Team Interactions for Innovation and Rapid Delivery

### Team Interaction Modes

* Team topologies used should adapt and evolve to meet emerging challenges
* 3 core team interaction modes that **simplify and clarify the essential interactions needed between teams building software systems**
  * **Collaboration** : two teams work together on a shared goal, particularly during discovery of new technology or approaches.
    * The overhead is valuable due to the rapid pace of learning
  * **X-as-a-Service** : one team consumes something provided by another team \(such as an API, a tool, or a full software product\). 
    * Collaboration is minimal
  * **Facilitating** : one team \(usually an enabling team\) facilitates another team in learning or adopting a new approach.

#### Well-Defined Interactions Are Key to Effective Teams

{% hint style="info" %}
“poorly defined team interactions and responsibilities are a source of friction and ineffectiveness"
{% endhint %}

![](../../../.gitbook/assets/image%20%28614%29.png)

* Teams should ask: 
  * What kind of interaction should we have with this other team? 
  * Should we be collaborating closely with the other team? 
  * Should we be expecting or providing a service? 
  * Or should we be expecting or providing facilitation?

![](../../../.gitbook/assets/image%20%28616%29.png)

* The team on the right is providing something “as a service” to the team on the left \(perhaps an API, some developer tooling, or even an entire platform\).

### Choose suitable Team interaction modes

![](../../../.gitbook/assets/image%20%28617%29.png)

|  | Collaboration | X-as-a-Service | Facilitating |
| :--- | :--- | :--- | :--- |
| **Stream-aligned** | Typical | Typical | Occasional |
| **Enabling** | Occasional |  | Typical |
| **Complicated-subsystem** | Occasional | Typical |  |
| **Platform** | Occasional | Typical |  |

### Constant Evolution of Team Topologies

![](../../../.gitbook/assets/image%20%28613%29.png)

### Triggers for Evolution of Team Topologies

{% hint style="success" %}
_it's often difficult to have the required organizational self-awareness to detect when it’s time to evolve the team structure_
{% endhint %}

* **Trigger: Software Has Grown Too Large for One Team**
  * Symptoms :
    * A startup company grows beyond fifteen people \(Dunbar’s number\)
    * Other teams spend lots of time waiting on a single team 
    * Changes to certain components or workflows in the system routinely get assigned to the same people, even when they’re already busy or away
    * Team members complain about lack of system documentation
* **Trigger: Delivery Cadence Is Becoming Slower**
  * Team members qualitatively feel it takes longer to release changes
  * Team velocity or throughput metrics show a clear downward variation compared to one year ago
  * Team members complain that the delivery process used to be simpler, with fewer steps. 
  * Work in progress keeps increasing

### Conclusion

Team Topologies alone will not produce an effective software-delivery and operations organization. Beyond the structures and dynamics suggested in this book, important additional ingredients of success include :

* **A healthy organizational culture** : 
  * an environment that supports the professional development of individuals and teams
  * which people feel empowered
    * Safe to speak 
    * The organization expects to learn continuously
* **Good engineering practices** : 
  * Test-first design and development of all aspects of the systems
  * a focus on continuous delivery and operability practices
  * pairing and mobbing for code review
  * avoiding the search for a single “root cause” for incidents
  * designing for testability, and so on
* **Healthy funding and financial practices** :
  * Avoiding the pernicious effects of a CapEx/OpEx 
  * Avoiding project-driven deadlines and large-batch budgeting wherever possible
  * Allocating training budgets to teams or groups rather than individuals
* **Clarity of business vision** : 
  * Executive or leadership provides a clear vision and direction
    * with horizons at human-relevant timescales
    * clear reasoning behind the priorities
      * So people in the organization can understand how and why these were chosen.

### How to get started ?

1. **Start with the Team**
   * What does the team need in order to :
     * Act and operate as an effective team? 
     * Own part of the software effectively? 
     * Reduce unnecessary cognitive load? 
     * Consume and provide software and information to other teams?
2. **Identify Suitable Streams of Change**
3. **Identify a Thinnest Viable Platform \(TVP\)**
   * Identify the services needed to support a reliable, swift flow of change in those streams
4. **Identify Capability Gaps** in Team Coaching, Mentoring, Service Management, and Documentation
   * Ensure that your teams are populated not just with technologists 
     * BUT also with people who have other skills
     * Examples : Team coaching, Mentoring, Well written documentation
5. **Share and Practice Different Interaction Modes and Explain Principles behind New Ways of Working**

