
# Backend Development with Express, Mongoose, and MongoDB

## Table of Contents

1. [Introduction](#introduction)
2. [Express](#express)
3. [MongoDB](#mongodb)
4. [Mongoose](#mongoose)
5. [General Backend Concepts](#general-backend-concepts)
6. [Authentication with bcryptjs](#authentication-with-bcryptjs)
7. [Session Storage](#session-storage)

---

## Introduction
Backend development refers to the server-side development of web applications. It focuses on databases, scripting, and the architecture of websites. The backend is where the functionality of a web application is implemented.

---

## Express

### Definition
A minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

### Key Concepts

- **Middleware**: Functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle.
  
- **Routing**: The way in which an application’s endpoints (URIs) respond to client requests.
  
- **Template Engines**: Allows you to use static template files in your application and replace variables in the template files using values from JavaScript objects.

---

## MongoDB

### Definition
A free and open-source cross-platform document-oriented database program. It is a NoSQL database that uses JSON-like documents with optional schemas.

### Key Concepts

- **Document**: A record in MongoDB, similar to a row in relational databases, but more flexible.
  
- **Collection**: A grouping of MongoDB documents, similar to a table in relational databases.
  
- **BSON**: Binary JSON, a binary-encoded serialization of JSON-like documents.

---

## Mongoose

### Definition
An elegant MongoDB object modeling for Node.js. It provides a straight-forward, schema-based solution to model your application data.

### Key Concepts

- **Schema**: Defines the shape of the documents within a collection.
  
- **Model**: A constructor compiled from a Schema. An instance of a model is a document.
  
- **Query**: Allows for querying the database. Mongoose queries are chainable, and they return promises.

---

## General Backend Concepts

### Key Concepts

- **API**: Application Programming Interface. A set of rules and mechanisms by which one application or component interacts with another.
  
- **CRUD**: Create, Read, Update, Delete. The four basic operations you can perform on data.
  
- **REST**: Representational State Transfer. An architectural style for designing networked applications. It uses a stateless, client-server, cacheable communications protocol.

---

## Authentication with bcryptjs

### Definition
bcryptjs is a library to help you hash passwords.

### Key Concepts

- **Hashing**: The process of converting an input into a fixed-length string of bytes. It ensures that data (like passwords) is stored securely.

- **Salting**: Random data that is used as an additional input to a one-way function that hashes data, a password or passphrase.

---

## Session Storage

### Definition
Session storage is a way to store data on the user's browser for the duration of a session.

### Key Concepts

- **Persistence**: The ability to retain data after the browser is closed.

- **Cookies**: Small pieces of data stored on the user's browser by the web server.

- **Session Management**: The process of keeping track of a user's activity across sessions of interaction with the web application.

---

