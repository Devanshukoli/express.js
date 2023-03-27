# Express.js Learning

## Installing

- First install _`node.js`_. Then create a Directory `myapp` and go to that directory.

  ```
      $ mkdir myapp
      $ cd myapp

  ```

- Then initiliaze the project with `npm init` command. It will ask you some questions. You can just press enter to accept the default values.

      ```
          $ npm init
      ```

  **OR**

- You can just run `npm init -y` to accept all the default values.

  ```
      $ npm init -y
  ```

- Then install express with `npm install express` command.

  ```
      $ npm install express
  ```

---

## Hello world example

- Create a file `app.js` in the `myapp` directory.

  ```
      $ touch app.js
  ```

- Then open the `app.js` file in your favorite editor and write the following code.

  ````js
    const express = require('express');// for importing express
    const app = express();// for creating an express app

    const PORT = 5000;// for setting the port

    app.listen(PORT, () => {
        console.log(`Server is running on port ${PORT}`);
    });// for listening to the port

    ```
  This will create a server on port 5000 and will print `Server is running on port 5000` in the console.
  ````

Now, When you go to chorme and type `localhost:5000` in the address bar, you will see `Cannot GET /` error.

You think why this happened? Because we have not created any route. So, let's create a route.

- Create a route in the `app.js` file.

  ```js
  app.get("/", (req, res) => {
    res.send("Hello world");
  });
  ```

  This will create a route `/` and will send `Hello world` as a response.
  So, now when you go to chorme and type `localhost:5000` in the address bar, you will see `Hello world` in the browser.

Here, note that any changes you made in the app.js file will not be reflected in the browser. You have to restart the server to see the changes.

And over the time it gets so annyoing to restart the server everytime you make a change. So, we will use `nodemon` to automatically restart the server everytime we make a change.

Now, go to your **terminal** and write the following command.

```
    $ npm install -g nodemon
```

This will install nodeman globally in your system.

---

## Express applicatoin generator

This is one of the easiest way to create an express app. It will create a directory with all the necessary files and folders.

- First install the express generator with the following command.

  ```
      $ npm install -g express-generator
  ```
  This will install the express generator globally in your system.

  - for help

    ```
        $ express --help **OR** $ express -h
    ```
- Now, for creating the express app called `myapp` run the following command in the terminal.
    
      ```
        $ express --view=pug myapp
      ```
    
- After runnig the command, you have to install all the dependinces along the way.
     
        ```
          $ cd myapp
          $ npm install
        ```
- Then run the server with the following command.
    
      ```
        $ npm start
      ```


---

## Basic routing

- ***Routing*** refers to how an application’s endpoints (URIs) respond to client requests.
- Each route can have one ore more handler functions, which are executed when the route is matched.
- Route definition takes the following structure:

  ```js
  app.METHOD(PATH, HANDLER);
  ```

  - `app` is an instance of express.
  - `METHOD` is an HTTP request method, in lowercase.
  - `PATH` is a path on the server.
  - `HANDLER` is the function executed when the route is matched.

  - Here are some examples of that:

    1. `get` method
    
            ```js
            app.get('/', function (req, res) {
                res.send('GET request to the homepage')
            })
            ```
    2. `post` metod

        ```js
        app.post('/', function (req, res) {
            res.send('POST request to the homepage')
        })
        ```

    3. `put` method

        ```js
        app.put('/user', function (req, res) {
            res.send('PUT request to /user')
        })
        ```
    4. `delete` method

        ```js
        app.delete('/user', function (req, res) {
            res.send('DELETE request to /user')
        })
        ```

---

## Serving static files in Express
