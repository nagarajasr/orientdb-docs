# Multi-Model

The OrientDB engine supports **Graph**, **Document**, **Key/Value**, and **Object** models, so you can use OrientDB as a replacement for a product in any of these categories. However the main reason why users choose OrientDB is its ability to act as a true **Multi-Model** DBMS by combining all the features of the four models into one. These are not just interfaces to the database engine, but the engine, itself, was built to support all four models. This is also the main difference with other DBMSs that claim to be Multi-Model since they just implement an additional layer with an API that mimics additional models, but under the hood they're truly one model therefore limiting speed and scalability.


## Document Model

The data in this model is stored inside documents. A document is a set of key/value pairs (also referred to as fields or properties) where a key allows access to its value. Values can hold primitive data types, embedded documents, or arrays of other values. Documents are not typically forced to have a schema which can be a benefit because they remain flexible and easy to modify. Documents are stored in collections enabling developers to group data as they decide. OrientDB uses the concepts of "[classes](Concepts.md#class)" and "[clusters](Clusters.md)" instead of "collections" for grouping documents. This provides several benefits that we will discuss in further sections of the documentation. OrientDB's Document model adds the concept of a "[LINK](Concepts.md#relationships)" as a relationship between documents. With OrientDB you can decide whether to embed documents or link to them directly. When you fetch the document all the links are automatically resolved by OrientDB. This is the most important difference with any other Document Database like MongoDB.

The table below illustrates the comparison between the relational model, the document model, and the OrientDB document model:

| Relational Model | Document Model   | OrientDB Document Model |
|------------------|------------------|-------------------------|
| Table            | Collection       | [Class](Concepts.md#class) or [Cluster](Clusters.md) |
| Row              | Document         | [Document](Concepts.md#document) |
| Column           | Key/value pair   | Document field          |
| Relationship     | not available    | [Link](Concepts.md#relationships)                    |


## Graph Model

A graph represents a network-like structure consisting of Vertices (also known as Nodes) interconnected by Edges (also known as Arcs). OrientDB's graph model is represented by the concept of a property graph, which defines the following:

 - **Vertex** - an entity that can be linked with other Vertices and has the following mandatory properties:

   - unique identifier
   - set of incoming Edges
   - set of outgoing Edges
   
 - **Edge** - an entity that links two Vertices and has the following mandatory properties:
   
   - unique identifier
   - link to incoming Vertex (also known as head)
   - link to outgoing Vertex (also known as tail)
   - label that defines the type of connection/relationship between head and tail vertex

In addition to mandatory properties, each vertex or edge can also hold a set of custom properties. These properties can be defined by users, which can make vertices and edges appear similar to documents. In the table below, you can find a comparison between the graph model, the relational data model, and the OrientDB graph model:

| Relational Model | Graph Model            | OrientDB Graph Model                     |
|------------------|------------------------|------------------------------------------|
| Table            | Vertex and Edge Class  | [Class](Concepts.md#class) that extends "V" (for Vertex) and "E" (for Edges)|
| Row              | Vertex                 | Vertex                                   |
| Column          | Vertex and Edge property | Vertex and Edge property              |
| Relationship     | Edge                   | Edge                                     |


## Key/Value Model

This is the simplest model of the three. Everything in the database can be reached by a key, where the values can be simple and complex types. OrientDB supports Documents and Graph Elements as values allowing a richer model than the classic Key/Value one. The Key/Value model provides "buckets" to group key/value pairs in different containers. The most classic use cases with Key/Value Model are:

- POST the value as payload of the HTTP call -> `/<bucket>/<key>`
- GET the value as payload from the HTTP call -> `/<bucket>/<key>`
- DELETE the value by Key, by calling the HTTP call -> `/<bucket>/<key>`

The table below illustrates the comparison between the relational model, the Key/Value model, and the OrientDB Key/Value model:

| Relational Model | Key/Value Model   | OrientDB Key/Value Model |
|------------------|------------------|-------------------------|
| Table            | Bucket           | [Class](Concepts.md#class) or [Cluster](Clusters.md) |
| Row              | Key/Value pair   | [Document](Concepts.md#document) |
| Column           | not available    | Document field or Vertex/Edge property          |
| Relationship     | not available    | [Link](Concepts.md#relationships)                    |


## Object Model

This model has been inherited by [Object Oriented programming](http://en.wikipedia.org/wiki/Object-oriented_programming) and supports **Inheritance** between types (sub-types extends the super-types), **Polymorphism** when you refer to a base class, and **Direct binding** from/to Objects used in programming languages.

The table below illustrates the comparison between the relational model, the Object model, and the OrientDB Object model:

| Relational Model | Object Model | OrientDB Object Model |
|------------------|------------------|-------------------------|
| Table            | Class           | [Class](Concepts.md#class) or [Cluster](Clusters.md) |
| Row              | Object   | [Document](Concepts.md#document) or Vertex |
| Column           | Object property    | Document field or Vertex/Edge property          |
| Relationship     | Pointer    | [Link](Concepts.md#relationships)                    |

