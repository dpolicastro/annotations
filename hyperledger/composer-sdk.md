# Composer SDK
SDK for developing full stack applications  

### Nodejs  

The Nodejs SDK contains for modules that exposes interfaces to interact with the Hyperledger Fabric  

**Client Module** - Depends on card  
Hides protocols level details, makes easy for developers to interact with Fabric.  
  - CRUD operations on assets
  - Submit transactions
  - Event listener

**Admin Module** - Depends on card
Supports automation of administrative tasks, for example:  
  - Deploy/Update BNA
  - Manage Cards
  - Ping the network to check its availability
  
**Commom Module** 
Exposos commom interfaces.  

**Runtime Module**  
Provides the Nodejs container environment for the BNA deployed on HF. The container exposes the interfaces to be invoked by the chain code for the transactions.
  - CRUD operations
  - Business logic
  - Emitting events
  
