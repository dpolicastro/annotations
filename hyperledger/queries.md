# Queries  
This document describes how to query the ledger using the Hyperledger Composer API

### queries.qry

In this file you can create your queries to perform on the blockchain application, using the following syntax  

```qry  
query getAllCars {  
  description: "Returns all cars in the registry"   
  statement:  
    SELECT org.example.cars.Car
    WHERE (carId == _$car_id)
    LIMIT _$limit   #default 25
    SKIP _$skip
    ORDER BY [carId ASC]
}
```
