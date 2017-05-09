# Getting Started with Neo4j

+ Author: Arjun Rajeev Nedungadi (@arjuntherajeev)
+ Field: Graph Databases 
+ Topic: Installing & Performing CRUD (Create-Read-Update-Delete) operations on Neo4j - a Graph Database 

## Why are we doing this?

Typically, when we talk about databases (or persistant storage), the first thing that pops in my head is MySQL - the infamous RDBMS. However, the dynamic is changing and for certain problems, it is much easier and intuitive to represent data using __graphs__.
Neo4j is a Graph Database which helps us represent and visualize data intuitively. It uses a query language called __Cypher__. In this lesson, we will learn how to represent our data and use Cypher. By the end of this lesson, we will be able to comfortably use Neo4j and perform CRUD (Create-Read-Update-Delete) operations on our data. 

## Getting Set Up 

The first we need to do is to [download Neo4j](https://neo4j.com/download/community-edition/). Run the executable and install it on your machine. A restart might be required. 

After installation, there should be a __Neo4j__ shortcut on the Desktop/Start Menu. Run it!

## 1. Starting Neo4j

Firstly, we see a pop-up window saying __Neo4j Community Edition__ and the Status saying __Choose a graph database directory, then start the sever__. 
The most important thing here is to select a __Database Location__ for our Neo4j files. Let us create a new folder on the Desktop called `lessongraph`. Now, click on the __Choose...__ button and select this folder. 

For example, my __Database Location__ is `C:\Users\Arjun\Desktop\lessongraph`. Next, click __Start__!

## 2. Web Interface 

After Neo4j is ready, the Status will say __Neo4j is ready. Browse to http://localhost:7474/__. This means that Neo4j has been _started_ and its Web Interface can be accessed on `localhost` or `127.0.0.1` on port `7474`. 
We are going to be greeted with a __Log in__ screen. Log in with username `neo4j` and password `neo4j`. We will now be prompted to enter a _new_ password. Let us change the password! 

The Web Interface has a friendly menu on the left which contains database information, favorites and documentation amongst other items.
Here, the `Database Information` tab is crucial for us where we can see: 
+ Node labels 
+ Relationship types
+ Property keys 

## 3. Graph Databases 

Before we start writing Cypher code, we need to understand the _parts_ of a Graph. 
A Graph in Neo4j has __Nodes__, __Relationships__ and __Properties__. 
To understand these terms, let us take an example: 

"_Thomas likes rock music_"

+ _Thomas_ is the __name__ of a __Person__
+ _rock_ is the __genre__ of __music__
+ _likes_ is the __relationship__ between _Thomas_ and _rock music_

To make it clearer, 

+ __Person__ is a Node with the Property __name__
+ __music__ is a Node with the Property __genre__
+ __likes__ is a Relationship between Nodes - __Person__ and __music__

## 4. Cypher

Great! We've reached this far! Now, all we need to do is learn __Cypher__ - the Query language of Neo4j. 
Cypher is pretty straightforward and with a little practice, we can easily master it! 

On the Neo4j Web Interface, there is an empty input field on the top of the screen. This is where we need to type in our Cypher queries. 

#### Tip: Type in the Cypher query and press `[ENTER]` instead of clicking on the `Submit` button all the time!

A typical Cypher query looks like: 

`MATCH (p:Person {name:"Thomas"}) RETURN (p)`

+ `MATCH` is a keyword indicating that we want to search (similar to __SELECT__ in SQL).
+ `(p:Person)` means that we want a Node __p__ with __Person__ Label.
+ `{name:"Thomas"}` means that we are _checking_ if the property __name__ is __"Thomas"__.
+ `RETURN (p)` means that we want to _return_ the __entire__ Node (including its properties). __RETURN__ is a keyword!

## 5. CREATE Operation 

Sweet! Now that we have learnt about Graph Databases and Cypher, let's get started with the __CREATE__ operation! 

We are trying to replicate the sentence - "_Thomas likes rock music_" on Neo4j using Cypher.

| Nodes        | Properties           | 
| ------------- |:-------------:|
| Person      | name : **Thomas**|
| music      | genre : **rock**    |

| Relationships        | Properties           | 
| ------------- |:-------------:|
| Person __likes__ music      | _None_|

In Cypher, to understand the _flow_ of Relationships, we use __Arrows__. The above Relationship is represented as: 
`(Person)-[likes]->(music)` with the Arrow indicating that a __Person__ likes __music__ and NOT vice versa!

#### Tip: Like Nodes, even Relationships can have Properties! 
#### For example, a Property for _likes_ could be _since_ (the year which Thomas began liking rock music) 

To construct this Query using Cypher, we need to use the `CREATE` keyword. 
Using the concepts mentioned above, the Query will look like: 

`CREATE (p:Person {name:"Thomas"})-[r:likes]->(m:Music {genre:"Rock"})`

Type or Copy-Paste this Query to the input field on the Neo4j Web Interface and hit `[ENTER]`! If the query successfully executed, we should see that 2 __Node labels__ and 1 __Relationship type__ have been created in the database. Verify this by opening the `Database Information` tab on the Side Menu of the Web Interface!

#### Tip: Sometimes, it's nice to get a holistic view of the Graph. Type `MATCH (n) RETURN (n)` to view the whole Graph! 

## 6. READ Operation

