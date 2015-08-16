expressed
=========

A boilerplate for quickly building an API on [node.js](https://nodejs.org/) and [Express](http://expressjs.com/). Includes:

- Authentication via [Passport](http://passportjs.org/)
- Automated testing framework with code coverage results
- Automated documentation

---

### Getting up and running

1. Clone this repo from `https://github.com/jakemmarsh/expressed-boilerplate.git`
2. Run `npm install` from the root directory
3. Run `npm start`

Your API will now be served to `localhost:3000` by default.

**Note:** While developing, `npm run dev` can be used in place of `npm start` to use Supervisor, allowing your server to automatically restart any time a file is changed.

---

### Sample .env file

API credentials, secret keys, etc. should all be stored in `process.env.*`. This boilerplate achieves this through the use of a `.env` file along with the [dotenv](https://github.com/bkeepers/dotenv) library. The file is gitignored to avoid checking any credentials into source control. This boilerplate currently only uses one environment variable, and so the `.env` file looks like this:

```

SECRET='abcefgqwerty123'

```

---

### API Architecture


```
/api              (Contains all files relevant to the API and database logic)
  /controllers    (Contains all route controllers, separated by entity type)
    auth.js       (Methods related to user authentication)
    user.js
    index.js      (Exports all controllers to be required in the API)
  /models         (Will contain all database models/schema definitions)
  /utils          (Contains miscellaneous files used within the API)
    passport.js   (Initializes Passport authentication)
  index.js        (Associates endpoints with route controllers)
/__tests__        (Contains tests for the API, organized in the same structure as the /api directory)
  helper.js       (Runs before any of the tests, defining test libraries and starting the server)
/__coverage__     (gitignored, but contains HTML coverage results automatically generated by running the tests)
/docs             (Contains the auto-generated documentation)
server.js         (The Express server which loads and serves the API)
```

**Note:** none of the authorization or database logic has been provided. Any places in which code has been omitted or stubbed are marked with `TODO` comments.

---

### Tests and Coverage

All tests are contained within the `/__tests__` directory, arranged in the same structure as the `/api` directory. The `helper.js` file automatically loads the testing libraries [sinon.js](http://sinonjs.org/) and [should.js](https://shouldjs.github.io/), making them available on the global scope for any of your tests. It also loads and starts the server before running your tests.

Tests are written and run using [mocha](https://mochajs.org/). Code coverage is automatically calculated using [Istanbul](https://github.com/gotwarlost/istanbul), which also generates HTML results pages in the `/__coverage__` directory.

**To run your tests, use the command `npm test`.**

![Image of generated code coverage results](https://raw.githubusercontent.com/jakemmarsh/expressed-boilerplate/master/coverage.png)

---

### Auto-Documentation

Documentation can be auto-generated for your API using [apiDoc](http://apidocjs.com/) if you annotate your controller methods in the correct format. The format and other options can be seen in the apiDocs documentation.

**To generate your docs, use the command `npm run gen-docs`.**

![Image of generated documentation](https://raw.githubusercontent.com/jakemmarsh/expressed-boilerplate/master/docs.png)
