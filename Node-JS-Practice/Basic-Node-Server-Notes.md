# A BASIC Node Server
```javascript
// Require the 'http' module from Node.js, which allows us to create an HTTP server
const http = require("http");

// Create a server using the createServer method from the 'http' module
const server = http.createServer(function(req, res) {
  // Set the response headers to specify that the response will be in JSON format and allow cross-origin requests e.g., any browser, any domain, it doesn't matter what the original was allow the data to go there.
  res.setHeader("Content-type", "application/json");
  res.setHeader("Access-Control-Allow-Origin", "*");
  // Set the status code of the response to HTTP 200 (OK)
  res.writeHead(200);

  // Create an object containing sample data
  let dataObj = { id: 123, name: "Bob", email: "bob@work.org" };
  // Convert the data object to a JSON string
  let data = JSON.stringify(dataObj);
  // Send the JSON data as the response to the client
  res.end(data);
});

// Make the server listen on port 1234, and when it starts listening, log a message to the console
server.listen(1234, function() {
  console.log("Listening on port 1234");
});
```

## Testing out the server

- Open the terminal and type: node [file name].js
  - Look for a response that says, "Listening on port 1234" in the console 
  - The port number is listed in the code on line 23 and the message logged to the console is on line 24.
- Open up a browser tab and type: http://localhost:1234/
  - This is the place that I am sending the request to
- There should be a response of an object displayed on the browser page
  - This object is listed in the code on line 15.
- Open the developer tools, click on the network tab, and refresh the page 
  - There should be a display of the request that I made, along with the headers, with a status code of 200, Access-Control-Allow-Origin, and Content-type are all displayed. 
  - Click on preview to see the data of the json object I got back. 

## Here's how it works:

1. **Require HTTP Module**: The code begins by requiring the built-in 'http' module in Node.js. This module provides functionality to create HTTP servers.

2. **Create Server**: Using the `createServer` method of the 'http' module, a server is created. This method takes a callback function that is executed whenever a request is made to the server. Inside this callback function, the server handles the incoming request and prepares the response.

3. **Set Response Headers**: Within the request callback function, the code sets the response headers. It specifies that the response will be in JSON format and allows cross-origin requests by setting the appropriate headers.

4. **Set Status Code**: The code sets the status code of the response to HTTP 200 (OK) using the `writeHead` method.

5. **Prepare Response Data**: Sample data is created in the form of a JavaScript object (`dataObj`). This object is then converted to a JSON string using `JSON.stringify` to prepare it for sending as the response.

6. **Send Response**: The prepared JSON data is sent as the response to the client using the `res.end` method.

7. **Start Server Listening**: Finally, the server is instructed to listen on port 1234 using the `listen` method. When the server starts listening, a message is logged to the console indicating that it's running.

#### In summary, this code sets up a basic Node.js server that responds to incoming requests with a JSON object containing sample data. It demonstrates the fundamental steps involved in creating a simple server-side application using Node.js.