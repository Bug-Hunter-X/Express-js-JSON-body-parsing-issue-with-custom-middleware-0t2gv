# Express.js JSON Body Parsing Issue

This repository demonstrates a common issue encountered when working with JSON request bodies in Express.js applications.  The problem arises when custom middleware is placed before `express.json()`, preventing the body-parser from correctly interpreting incoming JSON data.  The `bug.js` file showcases this problem, and `bugSolution.js` provides the corrected implementation.

## Problem
The original code attempts to log the request body using `req.body`.  However, due to improper middleware placement, `req.body` remains empty, leading to unexpected behavior or errors. 

## Solution
The solution moves `express.json()` before any custom middleware. This ensures that the body-parser processes the JSON data before other middleware can access it.

## How to Reproduce
1. Clone this repository.
2. Run `npm install express`
3. Run `node bug.js`
4. Send a POST request to `http://localhost:3000/user` with a JSON payload (e.g., using Postman or curl).
5. Observe that `req.body` is empty in the console output.
6. Now, run `node bugSolution.js` and repeat the process.
7. Verify that `req.body` now correctly contains the JSON payload.
