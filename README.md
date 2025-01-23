# Unhandled Promise Rejection in Node.js HTTP Server

This repository demonstrates a common error in Node.js where unhandled promise rejections in HTTP servers can lead to hanging connections and resource leaks.  The `bug.js` file showcases the problematic code, while `bugSolution.js` provides a corrected version.

## Problem

The issue arises when an asynchronous operation within an HTTP request handler fails, but the error isn't properly caught and handled.  If the connection isn't explicitly closed, it remains open indefinitely, consuming server resources.

## Solution

The solution involves ensuring that all asynchronous operations within the request handler are properly handled using `.catch()` or `try...catch`.  Additionally, the response should always be ended, even in case of errors, to properly close the connection.

## How to Reproduce

1. Clone this repository.
2. Navigate to the directory.
3. Run `node bug.js`.  Make several requests to the server (e.g., using curl).
4. Observe the server's behavior and resource usage.
5. Run `node bugSolution.js`. Repeat the requests. Compare the behavior and resource usage.