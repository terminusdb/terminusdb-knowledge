# terminusdb-knowledge
Terminus DB knowledge Base

A repository for collecting documentation articles about TerminusDB

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

The big advantage is that it is much easier to interpret the model and understand how it maps to real world entities compared to the relational example.  This increased ease is included 

#Query


