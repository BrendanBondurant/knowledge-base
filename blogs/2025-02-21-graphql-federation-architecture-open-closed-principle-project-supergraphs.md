---
type: blog
title: GraphQL Federation Architecture: Open/Closed Principle & Project-Based SuperGraphs
slug: 2025-02-21-graphql-federation-architecture-open-closed-principle-project-supergraphs
series: WunderGraph Blog
date: 2025-02-21
author: Jens Neuse
speakers: []
episode: null
chunk: null
segment: Full article
topics:
  - GraphQL Federation
  - API Architecture
  - Software Design Principles
  - Team Collaboration
tags:
  - graphql
  - graphql-federation
  - rest
  - architecture
  - microservices
entities:
  - GraphQL Federation
  - Open/Closed Principle
  - SuperGraph
  - REST APIs
  - WunderGraph
summary: |
  GraphQL Federation enables the Open/Closed Principle in API design by allowing new services to extend schemas dynamically without modifying existing subgraphs. This architecture supports project-based SuperGraphs where teams can reuse foundational services and extend them independently, avoiding the breaking changes and versioning issues that plague REST APIs in multi-team environments.
faqs:
  - q: What is the Open/Closed Principle in API design?
    a: The Open/Closed Principle (OCP) means software should be open for extension but closed for modification. In API development, this means you can add new features without changing existing services or code.
  - q: Why do REST APIs violate the Open/Closed Principle?
    a: REST APIs often require modifying existing endpoints to add new fields or features. This can introduce breaking changes, increase maintenance overhead, and usually leads to versioning (e.g., `/v2/users`), which goes against the OCP.
  - q: How does GraphQL Federation support the Open/Closed Principle?
    a: GraphQL Federation allows new services to extend the schema dynamically without modifying existing subgraphs. Existing services remain unchanged, and new functionality is added via composition.
  - q: What is a project-based SuperGraph?
    a: A project-based SuperGraph is a pattern where each project has its own Supergraph that builds on top of shared base subgraphs. Teams can reuse foundational services like a scores API and extend them per project without altering the base implementation.
  - q: Can multiple teams extend the same base subgraph?
    a: Yes. For example, a base `scores` subgraph can be used across projects. One game team might extend it with `currencyEarned`, while another adds a `killDeathRatio`. Each team builds independently on the shared foundation.
  - q: What are the advantages of using GraphQL Federation over REST in multi-team environments?
    a: GraphQL Federation enables independent extensibility, avoids breaking changes, eliminates the need for versioning, and lets teams compose scalable APIs without modifying each other's services. REST requires modifying core services, which can break OCP.
canonical_url: https://wundergraph.com/blog/graphql-federation-architecture-open-closed-principle-project-supergraphs
---

Recently, I discussed with one of our customers from the game development industry how they could leverage GraphQL Federation for their upcoming projects.
We came up with a fundamentally new way to think about GraphQL Federation that's leveraging the Open/Closed Principle (OCP) to create a modular, reusable API architecture for development teams working on multiple similar projects.

I call this approach **Project-based SuperGraphs** with **shared base Subgraphs**.

The Open Closed Principle originates from the SOLID principles of object-oriented design.
It states that a software entity should be open for extension but closed for modification.
In the context of API development,
we're taking a look at how GraphQL Federation supports this principle,
what the benefits are,
and how this differentiates from traditional REST APIs.

{% partial file="blog-callout.md" /%}

## Introduction: What is the Open/Closed Principle?

In software design, the **Open/Closed Principle (OCP)** is one of the five SOLID principles. It states:

> **"Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification."**

This means you should be able to **add new functionality** to a system without modifying its existing code. A classic example in **Object-Oriented Programming** is using **polymorphism** to extend behavior.

### **Classic Example: Open/Closed Principle in OOP**

Let's say we have a `Shape` class, and we want to calculate areas for different shapes. A **bad design** that violates OCP would look like this:

```javascript
class Shape {
  constructor(type, dimensions) {
    this.type = type;
    this.dimensions = dimensions;
  }

  getArea() {
    if (this.type === "circle") {
      return Math.PI * this.dimensions.radius ** 2;
    } else if (this.type === "rectangle") {
      return this.dimensions.width * this.dimensions.height;
    }
    return 0;
  }
}
```

### ❌ **Why is this bad?**

- Adding a new shape (e.g., `Triangle`) requires **modifying the `getArea` method**, which breaks the **closed for modification** rule.
- The code becomes **harder to maintain** over time.

### ✅ **A Better Design (OCP-Friendly)**

Instead of modifying `Shape`, we can **extend** it with new classes:

```javascript
class Shape {
  getArea() {
    throw new Error("Method not implemented");
  }
}

class Circle extends Shape {
  constructor(radius) {
    super();
    this.radius = radius;
  }

  getArea() {
    return Math.PI * this.radius ** 2;
  }
}

class Rectangle extends Shape {
  constructor(width, height) {
    super();
    this.width = width;
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }
}
```

Now, if we need a `Triangle`, we simply **extend** the `Shape` class without modifying existing code.

---

## How OCP Applies to API Development

In API development, the Open/Closed Principle means **we should be able to add new fields and functionalities without modifying existing endpoints**.
As we'll find out, traditional REST APIs often struggle with this, while **GraphQL Federation** is designed to support it seamlessly.

### **Why REST APIs Are Not OCP-Friendly**
Let's look at an example.

### **Step 1: A Simple REST API (Before the Change)**

A basic REST API serving user data:

```javascript
const express = require("express");
const app = express();

const users = [
  { id: 1, name: "Alice", email: "alice@example.com" },
  { id: 2, name: "Bob", email: "bob@example.com" }
];

app.get("/users", (req, res) => {
  res.json(users);
});

app.listen(3000, () => {
  console.log("🚀 User API running on http://localhost:3000");
});
```

### **Step 2: Adding an Address Field (Violating OCP)**

Now, we need to add an `address` field to user data:

```javascript
const users = [
  { id: 1, name: "Alice", email: "alice@example.com", address: "123 Main St" },
  { id: 2, name: "Bob", email: "bob@example.com", address: "456 Elm St" }
];

app.get("/users", (req, res) => {
  res.json(users);
});
```

### ❌ **Why This Violates OCP?**

- **Modifies existing code**, risking breaking clients.
- **Grows in complexity** when new fields (e.g., `phoneNumber`) are added.
- REST APIs often resort to **versioning (`/v2/users`)**, which increases **maintenance costs**.

---

## How GraphQL Federation Follows the Open/Closed Principle

Unlike REST, **GraphQL Federation** allows **extending APIs dynamically** without modifying existing services.

### User Service (Closed for Modification)**

A microservice providing basic user data:

```javascript
const { gql, ApolloServer } = require("apollo-server");

const typeDefs = gql`
  type User @key(fields: "id") {
    id: ID!
    name: String!
    email: String!
  }

  type Query {
    users: [User]
  }
`;

const resolvers = {
  Query: {
    users: () => [
      { id: "1", name: "Alice", email: "alice@example.com" },
      { id: "2", name: "Bob", email: "bob@example.com" }
    ]
  }
};

const server = new ApolloServer({ typeDefs, resolvers });

server.listen({ port: 4001 }).then(({ url }) => {
  console.log(`🚀 User Service running at ${url}`);
});
```

✅ **This service remains unchanged when we add new functionality.**

---

## REST vs. GraphQL Federation in OCP Compliance

| Feature            | REST API (Traditional) | GraphQL Federation (OCP-Friendly) |
|-------------------|----------------------|--------------------------------|
| **Adding New Fields**  | Requires modifying API | New services extend schema dynamically |
| **Breaking Changes**   | Possible (clients expect fixed structure) | Minimal risk (queries fetch only required fields) |
| **Versioning Required?** | Yes (`/v2/users`) | No, Federation auto-merges schemas |
| **Independent Extensibility** | Harder (all logic in one service) | Easy (new microservices can extend the schema) |

---

### **Real-World Example: Multi-Tenant Game Development Services**

A game development company can create a **multi-tenant** score service that provides the base functionality for "game scores" as a **subgraph**.
Other teams can then use this service as a foundation and extend it for their specific games.

- **Base `scores` subgraph**: Provides a standard `Score` entity with fields like `playerId` and `points`.
- **Game-specific extensions**:
  - A game with a **virtual currency** can extend the `Score` entity to include `currencyEarned`.
  - A **shooter game** can extend `Score` to include a `killDeathRatio` field.

This can be facilitated by having the scores subgraph **provide the base entities**,
which the individual game subgraphs then **extend** with their additional functionality.

What's amazing about this approach is that the **base `scores` subgraph** can be operated independently by the team owning it.
Individual game teams can then add this **base service** to their Supergraph and **extend** it with game-specific Subgraphs.

---

## REST vs. GraphQL Federation in OCP Compliance

| Feature            | REST API (Traditional) | GraphQL Federation (OCP-Friendly) |
|-------------------|----------------------|--------------------------------|
| **Adding New Fields**  | Requires modifying API | New services extend schema dynamically |
| **Breaking Changes**   | Possible (clients expect fixed structure) | Minimal risk (queries fetch only required fields) |
| **Versioning Required?** | Yes (`/v2/users`) | No, Federation auto-merges schemas |
| **Independent Extensibility** | Harder (all logic in one service) | Easy (new microservices can extend the schema) |

## Conclusion

- 🚀 **GraphQL Federation fully supports the Open/Closed Principle**, allowing APIs to evolve **without modifying existing services**.
- ❌ **REST APIs struggle with OCP**, requiring constant modifications and versioning.
- ✅ **SuperGraph & GraphQL Federation** make **modular, scalable API development possible**.

In summary, this blog post shows that **GraphQL Federation** can be used in more than just one way.
Traditionally, you'd have a single Supergraph that combines all your services into one.
However, for **project-based development** like for example in games,
you can create one Supergraph per project,
which builds on top of shared base Subgraphs.

With **REST APIs**, you'd have to modify core services to add new functionality.
Either you'd have to deploy a version of the core services for each project,
or you have to extend the core services with project-specific versions.

---

{% faq /%}

---