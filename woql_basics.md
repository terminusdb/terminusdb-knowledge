# TerminusDB WOQL Basics

WOQL - the Web Object Query Language - is a powerful language for querying the structure of Terminus Data.  WOQL is a very rich 
and expressive language which is highly composable - it allows users to extract or insert pretty much whatever data they want in a single query.  WOQL has many operators and functions for the specification of complex patterns, but at its core it is very simple. 

Under the hood terminusDB uses RDF triples as the basic unit and triple pattern matching is the basis on which WOQL is built.  

# Triples
Triples always take the form
`Object_ID Property_ID Value`

The first two parts of the triple are always IDs, the third part can be either another Object_ID or can be a simple datatype (aka a literal) such as a string, integer, decimal, date or dateTime. 

In WOQL we write a simple triple pattern match as follows: 
`WOQL.triple("doc:john", "mother", "doc:mary")`
This will match a triple where doc:john has a property called mother which points at another object with ID doc:mary

# IDs and Prefixes

In RDF, all IDs are URLs (or to be more accurate, IRIs). This has the advantage of providing us with universal IDs for everything, but the disadvantage is that URLs are long and often hard to remember. In RDF it is common to get around this problem by using prefixed URLs which  

# Variables

# Property Chains
