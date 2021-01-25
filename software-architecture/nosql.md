# NoSQL

### Objectives :

* Understand what does NoSQL mean
* Understand the different kind of databases hidden behind this word

## Connection - 10'

* In pair list every Pros and Cons you have encountered with relational database
* List every relational database you have already used
* Group the answers

## Concepts - 20'

### Relational databases

* Persist data
* Concurrency control
* Manage transactions in an ACID way

### ACID

![](../.gitbook/assets/image%20%28510%29.png)

* Atomicity
  * "all or nothing"
  * One part fails =&gt; the entire transaction fails
* Consistency
  * Bring the database from one valid state to another
  * All defined rules, including constraints, cascades, triggers, and any combination are respected
* Isolation
  * Concurrent execution
    * Would be obtained if transactions were executed sequentially
* Durability
  * Transaction committed : it will remain

### Cons of relational databases

* Impedance mismatch
  * Relational data structures vs In-memory data structures
* Performance
* Distribution
* Cost

### NoSQL

![](../.gitbook/assets/image%20%28519%29.png)

### Different kind of NoSQL Databases

![](../.gitbook/assets/image%20%28511%29.png)

### Why use NoSQL ?

* To improve programmer productivity : better matches an application needs 
* To improve data access performance 
  * Through some combination of handling larger data volumes, reducing latency 
* Large volumes of rapidly changing structured, semi-structured, and unstructured data
* Geographically distributed scale-out architecture 
  * Instead of expensive, monolithic architecture

## Concrete Practice - 20'

Let's play with a GraphDB call Neo4j for the next minutes :

* Connect to the [platform](https://sandbox.neo4j.com/)
* Play with the Cypher queries
* Play with the Graph Visualization

![](../.gitbook/assets/image%20%28512%29.png)

## Conclusion - 10'

{% hint style="success" %}
_**NoSQL does not mean “Death of SQL”**_
{% endhint %}

We can now create polyglot persistence :

* Uses different data storage technologies to handle varying data storage needs
* Can be applied : Anywhere in an organization/in a single application

Use the tool that fits the best your needs.

![](../.gitbook/assets/image%20%28514%29.png)

### Remember the past

Think about the past few years, in which development you have made this kind of database would have been useful ?

* Why ?

### Resources

#### Key Value Stores

* Aerospike
* Apache Cassandra
* Berkeley DB
* Couchbase Server
* Redis
* Riak

#### Document DB

* CouchDB
* Elasticsearch
* MongoDB

#### Graph DB

* Neo4j
* OrientDB
* FlockDB

#### Wide Columns Family Stores

* Cassandra
* HBase



