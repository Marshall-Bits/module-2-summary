# Module 2 review
### FROM SCRATCH Initialize a new project with packages 

- Create a new project folder
- Open the folder in VS Code
- Use `npm init -y` to initialize a new project with packages
- Now you can install packages with `npm install <package-name>`
To install more than one package at a time, use `npm install <package-name> <package-name> <package-name>`

Example: `npm install express mongoose bcryptjs`

- Check that you have all the new dependencies in your package.json file. 
package.json:
```js
{
  "dependencies": {
    "bcryptjs": "^2.4.3",
    "express": "^4.17.1",
    "mongoose": "^5.9.7"
  }
}
```
- Check that you also have a node_modules folder.

- Make sure you create a `.env` file and add there all the environment variables you need for your project. For example, you need to add your `MONGODB_URI` variable.


You are done with the initialization. Now you can start coding!

#### Now I want to link my project to GitHub

- Create a new repository on GitHub
- Follow the instructions on GitHub to link your project to the new repository
- Before pushing your code, make sure you have a `.gitignore` file and add there all the files and folders you don't want to push to GitHub. For example, you don't want to push your `node_modules` folder.

Example of a `.gitignore` file:
```
node_modules
package-lock.json
.env
```

- Now you can push your code to GitHub
---

### NOT FROM SCRATCH: Cloned project with packages

Whenever we clone a project from GitHub, we need to install the packages. 
We'll see that we don't have any `node_modules` folder. We should have a `package.json` file, though.

- Open the project folder in VS Code
- Run `npm install` to install all the packages listed in the `package.json`
- Check that you have a `node_modules` folder now
- Make sure you create a `.env` file and add there all the environment variables you need for your project. For example, you need to add your `MONGODB_URI` variable.

Example of a `.env` file:
```
PORT=3000
MONGODB_URI="mongodb://yourMongoURLWithUserAndPassword/your-db-name"
```

You are done with the initialization. Now you can start coding!

## Server setup

When we create a server, we have a lot of things to do. We need to create the server, connect to the database, create the routes, etc.

### Create the server
Server will be created normally in the `server.js` file.
In our projects, we have a few files to help us with the server setup. 
Check the portal lesson for more details: [Ironlauncher setup](https://my.ironhack.com/lms/courses/course-v1:IRONHACK+WDFT+202307_BCN/modules/ironhack-course-chapter_6/units/ironhack-course-chapter_6-sequential_1-vertical_1)

### Connect to the database
We need to connect to the database in order to be able to use it.
The default setup for ironlauncher is to have the database connection in `db/index.js` file.

Notice this file is trying to connect to the database using the `MONGODB_URI` environment variable.
```js

const MONGO_URI =
  process.env.MONGODB_URI || "mongodb://127.0.0.1:27017/name-of-your-db";

```
If you don't provide a `MONGODB_URI` environment variable, it will use the default value after the `||` operator. To avoid confusion, you can delete the default value and just use the environment variable in the `db/index.js` file.

```js
const MONGO_URI = process.env.MONGODB_URI;
```

Notice the name of the environment variable and the name of the variable in the `db/index.js` file are not the same. Be careful with that when you add the variable to the .env file.

### Create the routes
One of the most important things we need to do is to create the routes.

It is a good practice to divede the routes in different files. For example, we can have a `routes/auth.routes.js` file to handle all the routes related to authentication and some book routes in a `routes/books.routes.js` file.

Every time we create a new route file, we need to import it in the `app.js` file and use it as a middleware.

In the previous example, we would add something like this in the `app.js` file:
```js
const authRoutes = require("./routes/auth.routes");
app.use("/", authRoutes);
```

#### Different types of routes
We can use routes to display information in the browser, to create new information in the database, to update information in the database, to delete information from the database, etc.

To have in mind which type of route we are creating, we can use the following convention:

| HTTP Method | Path | Description |
| ----------- | ---- | ----------- |
| GET | /books | Get all the books |
| POST | /books | Create a new book |
| POST | /books/delete/:id | delete a specific book |
| POST | /books/edit/:id | update a specific book |
| GET | /books/:id | Get a specific book |

Try to create a table with the different routes you need for your project. 
While working on it you can rely on the table. You may need to add more routes or change the ones you have. That's fine. The table is just a guide to help you. Try to update it as you go.

Notice in the example we add the books/:id route at the end. This is because the order matters. If we go to the route books/delete the server will try to find a book with the id "delete". We need to make sure we have the most specific routes at the top and the most generic ones at the bottom if they can cause conflict.

Once we have the table with the routes we need, we can start creating them in the routes folder.

#### Display information in the browser

Every time you want to display information in the browser, you need to create a GET route.

This get route is going to RENDER a view. To render a view, we need to use the `res.render()` method.
Inside the parenthesis we add the location of the file we want to render. For example, if we want to render the `views/index.hbs` file, we need to add `res.render("index")`. It's not necessary to add the extension of the file because our project has already been configured to use `.hbs` files.

Example of a GET route that renders a view:
```js
router.get("/", (req, res) => {
  res.render("index");
});
```

#### Create new information in the database

Every time you want to create new information in the database, you need to create a POST route.
To collect the information of a form with a POST route, we need to use the `req.body` object.

Example of a POST route that creates a new book in the database:
```js
router.post("/books", (req, res) => {
  const { title, author, description, rating } = req.body;
  Book.create({ title, author, description, rating })
    .then((book) => {
      res.redirect("/books");
    })
    .catch((err) => {
      console.log(err);
    });
});
```

Our hbs form should look something like this:
```html
<form action="/books" method="POST">
  <label for="title">Title</label>
  <input type="text" name="title" id="title" />
  <label for="author">Author</label>
  <input type="text" name="author" id="author" />
  <label for="description">Description</label>
  <textarea name="description" id="description" cols="30" rows="10"></textarea>
  <label for="rating">Rating</label>
  <input type="number" name="rating" id="rating" />
  <button type="submit">Create book</button>
</form>
```
Remember to add a name to every input in the form. The name will be the key of the object we will collect in the `req.body` object.

