# Ways to make Http Requests in Node js
Making HTTP request is a core functionality for modern languages.
when it comes to the Node js we have multiple ways to achieve that.


## Request Module

Which is the third party NPM module to make the HTTP requests from the node.
This library is much more user friendly than the default http module and has been considered a go-to for the community for several years.
###
Run the following in your terminal from the directory you want your code to live in:
```
npm install request
You’ll see that you need much less code to accomplish the same task that we did above:
```
```
const request = require('request');
```
      request('https://reqres.in/api/users', { json: true }, (err, res, body) => {
        if (err) { return console.log(err); }
        console.log(body.url);
        console.log(body.explanation);
      });

For more Info https://www.npmjs.com/package/request

## Got module 
Which is the third party NPM module to make the HTTP requests from the node.
Light weight of this library is much more user friendly than the default http module.

###
Run the following in your terminal from the directory you want your code to live in:
```

npm install got
Similarly to Axios, Got works with Promises as well. The following code will work as the rest of the examples do:
```

```
const got = require('got');
```

      got('https://reqres.in/api/users', { json: true }).then(response => {
        console.log(response.body.url);
        console.log(response.body.explanation);
      }).catch(error => {
        console.log(error.response.body);
      });

For more Info https://www.npmjs.com/package/got

## SuperAgent Module

Similarly to Axios, SuperAgent is another popular library primarily used for making AJAX requests in the browser but works in Node.js as well. Install SuperAgent with the following command:

```
npm install superagent
```
What is cool about SuperAgent is that you have other useful functions that you can chain onto requests such as query() to add parameters to the request.

```
const superagent = require('superagent');
```
      superagent.get('https://reqres.in/api/users')
      .query({ api_key: 'DEMO_KEY', date: '2017-08-02' })
      .end((err, res) => {
        if (err) { return console.log(err); }
        console.log(res.body.url);
        console.log(res.body.explanation);
      });

For more Info https://www.npmjs.com/package/superagent

## Axios Module

Axios is a Promise based HTTP client for the browser as well as node.js. Using Promises is a great advantage when dealing with code that requires a more complicated chain of events.
Writing asynchronous code can get confusing, and Promises are one of several solutions to this problem.

To install Axios from npm, enter the following command in your terminal:

```
npm install axios
```

The following code will accomplish the same task of logging the URL to and of explaining the astronomy picture of the day.

```
const axios = require('axios');
```

      axios.get('https://reqres.in/api/users')
        .then(response => {
          console.log(response.data.url);
          console.log(response.data.explanation);
        })
        .catch(error => {
          console.log(error);
        });

Axios even parses JSON responses by default. Pretty convenient! You can also see that error handling is done with .catch() since we are using promises now.

You can even make multiple concurrent requests with axios.all if you wanted to do something like get the astronomy picture of two different days at once:

```
const axios = require('axios');
```

    axios.all([
     axios.get('https://reqres.in/api/users'),
     axio.get('https://reqres.in/api/users/2')
    ]).then(axios.spread((response1, response2) => {
     console.log(response1.data.url);
     console.log(response2.data.url);
    })).catch(error => {
     console.log(error);
    });

For more Info https://www.npmjs.com/package/axios
