# Why graphql than Rest API :

- avoid overfetching data
- avoid underfetching data

Rest API can send multiple request to a client to display in one view. However Graphql can send one single endpoint

# How he can do it ?

graphql send a post request to the server with a query who describe all the data requirement we need.

# Core Concept of GraphQl

## fundamentanl construct of graphQl

the syntax for writing schemas is called the Schema Definition Language (SDL)

small exemple :

```js
type Person {
  name: String!
  age: Int!
}

type Post {
  title : String
}
```
<!-- the ! at the end is to require the field-->


**to add a relation :**

```
type Person {
  name: String!
  age: Int!
  post: [Post]
}

type Post {
  title : String
  author: Person!
}
```
the bracket express that a person can write multiple post

**Query**
query : information send to a server to express data its needs.

ex :

the request
```
{
  allPersons(last:2) {
    name
    age
  }
}
```
<!-- allPersons is called root field -->

the response
```json
{
  "allPersons": [
    { "name": "Sarah", "age": "20"},
    { "name": "Alice", "age": "20"}
  ]
}
```

**mutation**

Majority of applications need some way of making changes to the data that's curerntly stored in the back-end = we called this mutation.

3 kinds of mutations :

- **Creating** new data
- **Updating** existing data
- **Deleting** existing data

ex :

```
mutation {
  createPerson(name: "bob", age: 36) {
    name
    age
  }
}
```