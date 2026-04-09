# Short Response Questions

Answer each question below in your own words. Aim for 3–5 sentences per answer. Be specific — use the exact terms and concepts from the lesson.

Your responses will each be evaluated out of 6 points. You can earn 3 points for writing quality and 3 points for the accuracy and precision of the technical content per question.

---

## Question 1: Express vs `node:http`

Express is described as a framework that "wraps" `node:http`. What does that mean? Compare how you would handle a `GET /api/users` request in `node:http` versus in Express. What does Express do for you automatically that you had to write manually with `node:http`?

**Your answer here**:
Express is described as wrapping `node:http` because Express is built on top of `node:http` and provides simpler request, response, and routing without writing everything manually. 

With `node:http`, handling a `GET /api/users`request requires you to manually check the URL and method, and then send a response. For example, you need to write `req.url === "/api/users"` and `req.method === "GET" before returning the data. 

In Express, it is much simpler because you can directly define a route like `app.get('/api/users', ...)` and Express handles matching the route, method, sending responses, and parsing requests.

---

## Question 2: Endpoints, Controllers, and Middleware

What are **controllers** and **middleware** in Express? What are each responsible for and how do they work together to handle incoming requests?

**Your answer here**:
**Controllers** are responsible for handling the main logic of a request and sending back a response. It takes the processed data and determines what to send back to the client. 

**Middleware** runs before the controllers and helps process incoming HTTP requests. It can also perform server-side actions such as parsing the request, modifying the response, or executing additional logic before passing it onto the next middleware or controller.

They work together because **middleware** prepares and processes the request, and then the **controllers** handle the final logic and sends back a response to the client.

---

## Question 3: Query Strings and Route Parameters

How are **query strings** and **route parameters** similar? How are they different? In your answer, provide an example of when you would use each.

**Your answer here**:
Both **query strings** and **route parameters** are similar in the sense that they both send a request to the server. The difference is where the data is placed in the URL and how it’s used.

Route parameters are part of the URL path. For example, `GET /api/users/5`. 5 is the user's ID, and in Express, you can access it using `req.params.id`. You would use route parameters when you need a specific item. 

Query strings are added at the end of a URL. For example, `GET /api/users?id=5`. 5 is a query string, and you can access it using `req.params.id`. You would use query strings when you want to filter or modify the results.

---

## Question 4: Same-Origin Requests

For API fetch calls from a client-side application, explain the difference between fetching from endpoints with relative paths like `/api/quotes` and fetching from endpoints with a full URL like `https://dog.ceo/api/breeds/image/random`. Why do we not send a fetch using a url like `http://localhost:8080/api/quotes`?

**Your answer here**:
Fetching from `/api/quotes` uses a relative path, which means the request is sent to the same server the app is running on. A full URL like `https://dog.ceo/api/breeds/image/random` sends a request to an external server. 

We don't use `http://localhost:8080/api/quotes` because `localhost` only works on my own computer/machine. Using a relative path allows the app to work both locally and when deployed. 