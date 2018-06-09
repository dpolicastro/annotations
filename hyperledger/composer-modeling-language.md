# Composer Modeling Language (.cto)  

The .cto files specify the business domain  

### Object Orientation

- `abstract`  
Supports resources abstract classes  

- `extends`  
Supports inheritance  

- `concept`  
Represents a generic class, group fields  

- `import`  
Used to import resources from another namespace  

### Relationship  

- `-->`  
This syntax is used to represent a relationship between resources in the .cto file  

To assign value to a resource, you need to need to pass the fully qualified resource name and identity  
```js
"car": "org.example.cars.Car#CAR001"
```  
