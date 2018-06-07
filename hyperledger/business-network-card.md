# Business network cards 

### Location:
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


### Roles:
**Peer Administrator**  
-Node Level, created as part of the environment setup

**Network Administrator**  
-Aplication level, created by Peer Administrator  
-Can create participants, or authorize to create other participants  

### Creating and importing a card:

Create a /dist folder inside your project, then cd /dist  
**1. Create archive file (.bna)**  
-n,  Path to package.json  
-t,  Resource type  
```sh
composer archive create -t dir -n ../
```

**2. Install network application to fabric**
```sh
$ composer network install -a test-bna@0.0.1.bna -c PeerAdmin@hlfv1
```

**3. Start BNA on fabric**  
This command deploys a admin network card
```sh
$ composer network start -c PeerAdmin@hlfv1 -n test-bna -V 0.0.1 -A admin -S adminpw
```

**4. Import network admin card**
```sh
$ composer card import -f admin@test-bna.card
```

**5. Check if the card was imported**
```sh
$ composer card list
```
