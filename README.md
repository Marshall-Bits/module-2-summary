
# Backend Development with Express, Mongoose, and MongoDB
Hello Ironhacker! We are going to review a few concepts that we have learned in module 2.

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

- **Middleware**: Imagine there is a guardian at the door of each part of your application. Middleware is the one that is going to check, for example, if you are allowed to enter or not. It is a function that has access to the request and response objects. It can execute any code, transform the request, and decide whether to pass the request to another middleware or to send a response to the client.
It uses req, res, and next as parameters. THe next() function is a callback that tells Express that the middleware has finished and it can move on to the next middleware in the chain (it can be a route handler or another middleware).
  
- **URI**: Uniform Resource Identifier. It is a string of characters that identifies a particular resource. The difference between URI and URL is that a URI is a simpler way of identifying, while a URL gives you more specific information about how to locate something.

- **Endpoint**: A URI (Uniform Resource Identifier) that a client can request. It can be a route handler or a middleware function. For example, if you want to access the profile page of a user, you need to send a GET request to the `/profile` endpoint. The server will respond with the profile page of the user. But the actual URL of the profile page could be `https://www.myapp.com/users/12345/profile`.

- **Routing**: The way in which an application’s endpoints (URIs) respond to client requests. For example, if you want to access the profile page of a user, you need to send a GET request to the `/profile` endpoint. The server will respond with the profile page of the user.

  
- **Template Engines**: Allows you to use static template files in your application and replace variables in the template files using values from JavaScript objects. HBS is a popular template engine for Express.

---

## MongoDB

### Definition
A free and open-source cross-platform document-oriented database program. It is a NoSQL database that uses JSON-like documents with optional schemas.

### Key Concepts

- **Document**: A record in MongoDB, similar to a row in relational databases or excel sheets.
  
- **Collection**: A grouping of MongoDB documents. For example, a collection of users, a collection of products, etc.
  
- **BSON**: Binary JSON, a binary-encoded serialization of JSON-like documents. MongoDB uses BSON to represent documents in the database. It extends the JSON model to provide additional data types and to be efficient for encoding and decoding within different languages.

---

## Mongoose

### Definition
An elegant MongoDB object modeling for Node.js. It provides a straight-forward, schema-based solution to model your application data. We need to install it as a dependency in our project. It's a library that allows us to interact with our MongoDB.

### Key Concepts

- **Schema**: Defines the shape of the documents within a collection.
  
- **Model**: A constructor compiled from a Schema. An instance of a model is a document.
  
- **Query**: Allows for querying the database. Mongoose queries are chainable, and they return promises.

---

## General Backend Concepts

### Key Concepts

- **API**: Application Programming Interface. A set of rules and mechanisms by which one application or component interacts with another.
  
- **CRUD**: Create, Read, Update, Delete. The four basic operations you can perform on data.
  
- **REST**: Representational State Transfer. An architectural style for designing networked applications. It uses a stateless, client-server, cacheable communications protocol. RESTful is typically used to refer to web services implementing such an architecture.

---

## Authentication with bcryptjs

### Definition
bcryptjs is a library to help you hash passwords.

### Key Concepts

- **Hashing**: The process of converting an input into a fixed-length string of bytes. It ensures that data (like passwords) is stored securely.

- **Salting**: Random data that is used as an additional input to a one-way function that hashes data, a password or passphrase.

- **One way function**: A function that is easy to compute on every input, but hard to invert given the image of a random input. It is easy to compute a hash from a password, but it is hard to find a password that hashes to a given value.
---

## Session Storage

### Definition
Session storage is a way to store data on the user's browser for the duration of a session. We can create a session by using cookies. In express, we need to install the `express-session` package in order to create a session. Once the session is created, we can store data in it. 

### Key Concepts

- **Persistence**: The ability to retain data after the browser is closed. The cookie is stored on the user's browser, so it is persistent. We can set an expiration date for the cookie, so it can be persistent for a certain amount of time.

- **Cookies**: Small pieces of data stored on the user's browser by the web server.

- **Session Management**: The process of keeping track of a user's activity across sessions of interaction with the web application.

---

