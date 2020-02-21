#TerminusDB Graph Basics

TerminusDB organises data in a very simple structure to make it easy and natural to model the real world. 

Whereas traditional relational databases divide data into tables, columns and rows, 
in terminusDB everything is an object - objects can have properties and some of these properties may link to other objects. 
The network of interlinked forms a graph structure (in the mathematical sense - nodes and edges). 

This is the basic idea of the graph database - using data structures that are things rather than cells allows users to create models 
that are much closer to the real world things that they want to model - because people perceive the world as things, not cells.  

To explain with a very simple example - if we were building a database to hold a family tree and we want to record the parents and grand-parents of an individual. 
In a relationsal database, we might record this in a simple table


Person_ID | Name | DOB | mother | father
--- | --- | --- | --- | ---
1 | John | 1/10/79 | 2 | 3
2 | Mary | 4/2/56 | 4 | 5
3 | John snr | 28/11/52 | 6 | 7
4 | Patricia | 17/4/22 | null | null
5 | Michael | 1/9/09 | null | null
6 | Sally | 17/4/23 | null | null
7 | Robert | 3/10/13 | null | null

In a graph database, this would look like the following

![Family Tree Graph](https://terminusdb.github.io/terminusdb-knowledge/images/family-tree.png "Family Tree")

The big advantage is that it is much easier to interpret the model and understand how it maps to real world entities compared to the relational example.  This increased ease also extends to querying the database. 

#Query
For example, if we wanted to fetch the name of john's mother and grandmother from the database, if we were using a relational database, we could use the following two SQL queries to get the name of the mother and grandmother respectively: 

```
SELECT Name from TABLE where Person_ID = (SELECT mother from TABLE where Name="John")
SELECT Name from TABLE where Person_ID = (SELECT mother from TABLE WHERE Person_ID = (SELECT mother from TABLE where Name="John"))
```

In a graph database this is much simpler: we can use a triple pattern such as the following to get both names in the same query - we do not have to explicitly join the records together, the joins are implicit - we use the same ID in different parts of the query: 

```
WOQL.and(
   WOQL.triple("v:Person", "mother", "v:MotherID"),
   WOQL.triple("v:MotherID", "name", "v:MotherName"),
   WOQL.triple("v:MotherID", "mother", "v:GrandmotherID"),
   WOQL.triple("v:GrandmotherID", "name", "v:GrandmotherName"),
)
```

By using "v:MotherID" multiple times in the query, we create a chain: v:Person =mother=> v:Mother =mother=> v:Grandmother

This makes our queries much easier to understand - we can follow them naturally across multiple patterns. 
