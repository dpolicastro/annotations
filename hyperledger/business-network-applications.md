# Business Network Applications 

### Index  
- [Roles](#roles)  
- [Creating BNA](#createbna)  
- [Updating BNA](#updatebna)  
- [Managing Identities](#manageId)  

### Files Path
```
~/.composer  
     ‖----- cards [1]  
          ‖----- PeerAdmin@node-name  
          ‖----- NetworkAdmin@BNA-name  
                  ‖----- metadata.json [2]  
                  ‖----- connection.json [3]  
                  ‖----- credentials  
                        ‖----- certificate  
                        ‖----- privateKey  
     ‖----- client-data (key-files and certificates)  
```
[1] Users may have different cards on their machine to connect to different business networks.  
[1] Roles user has.  
[2] Connection Profile, that contains:  
- Information about how to reach the CA (https://)  
- Information about how to reach the peers and orderers (grpcs://)  

---
### <a name="roles"></a>Roles
**1. Peer Administrator**  
- Node Level, created as part of the environment setup

**2. Network Administrator**  
- Aplication level, created by Peer Administrator  
- Can create participants, or authorize to create other participants  
---
### <a name="createbna"></a>Creating a BNA and importing a network admin card

Considering you created a project using the yo generator cli,, e.g, `yo hyperledger-composer` follow the next steps:  

Create a /dist folder inside your project  
**1. Create archive file (.bna)**  
```sh
$ mkdir dist  
$ composer archive create -a dist/test-bna@0.0.1.bna -t dir -n .  

-a,   .bna file name
-n,   Path to package.json  
-t,   Resource type  
```

**2. Install network application to fabric**
```sh
$ composer network install -a test-bna@0.0.1.bna -c PeerAdmin@hlfv1

-a,   Business Network Archive
-c,   PeerAdmin card
```

**3. Start BNA on fabric**  
This command deploys a network admin card
```sh
$ composer network start -c PeerAdmin@hlfv1 -n test-bna -V 0.0.1 -A admin -S adminpw

-c,   PeerAdmin card
-n,   Business network name
-V,   Business network version
-A,   Admin username
-S,   Admin password
```

**4. Import network admin card**
```sh
$ composer card import -f admin@test-bna.card

-f,   Network Admin Card
```

**5. Check if the card was imported**
```sh
$ composer card list
```

**6. Testing the connection to the network**
```sh
$ composer network ping -c admin@test-bna

-c,   Imported network admin card
```
---
### <a name="updatebna"></a>Updating your BNA

**1. Create a new archive file (.bna)**  
After incrementing the version at package.json
```sh
$ composer archive create -t dir -n ../

-n,   Path to package.json  
-t,   Resource type  
```

**2. Install the new version of the BNA to fabric**  
```sh
$ composer network install -a test-bna@0.0.2.bna -c PeerAdmin@hlfv1

-a,   Business Network Archive
-c,   PeerAdmin card
```

**3. Upgrade the BNA**  
```sh
$ composer network upgrade -c PeerAdmin@hlfv1 -n test-bna -V 0.0.2

-c,   PeerAdmin card
-n,   Business network name
-V,   Business network version
```

**4. Test your network**
```sh
$ composer network ping -c admin@test-bna

-c,   Network Admin Card
```
---
### <a name="manageId"></a>Managing Identities in the Network

- `composer participand add`  
Adds a participant to the BNA  

- `composer identity`  
Can be used for multiple actions, must provide a valid card to execute the commands.  
**Subcommands**
     - `bind` Binds existing Identity(cert) to Participant  
     - `issue` Issue new Identity(card) to Participant  
     - `list` List participants  
     - `request` Request an Identity's certificate and key  
     - `revoke` Revoke an Identity issued to a Participant    
     
