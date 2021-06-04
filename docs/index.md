```
{
 // Require the Fastify framework and instantiate it
const fastify = require("fastify")();
// Handle GET verb for / route using Fastify
// Note use of "chain" dot notation syntax
fastify.get("/", (request, reply) => {
  reply
    .code(200)
    .header("Content-Type", "text/html; charset=utf-8")
    .send("<h1>Hello from Lab 4!</h1>");
});

//Name route
fastify.get("/name", (request, reply) => {
    //Getting information from the request
   const {first, last} = request.query;
   //Processing the information from the request on the server
   const name = first && last ? `${first} ${last}` : `Guest`;
   //Returning the results of the processing to the user
    reply
      .code(200)
      .header("Content-Type", "text/html; charset=utf-8")
      .send(`<h1>Hello, ${name}</h1>`);
  });
// Start server and listen to requests using Fastify
const listenIP = "localhost";
const listenPort = 8080;
fastify.listen(listenPort, listenIP, (err, address) => {
  if (err) {
    console.log(err);
    process.exit(1);
  }
  console.log(`Server listening on ${address}`);
}); 
}
```

```
{
  {
  "name": "lab-04",
  "version": "1.0.0",
  "description": "",
  "main": "lab-04.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "fastify": "^3.15.0"
  }
}

}
```

