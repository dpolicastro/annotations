# Rest Server Tool
Standalone Nodejs process that exposes the business network resources as REST API  

1. To start the API execute (You need to supply the network admin card)  
```sh
$ Composer-rest-server
```
2. Go to http://localhost:3000/explorer

**Pros**
- The rest server can be used to explore the data, CRUD operations and submit transactions  
- Applications can interact with fabric consuming the REST API  

**Cons** 
- A single network card can deploy the rest-server and execute ALL the transactions
---


