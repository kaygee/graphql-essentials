# GraphQL Essentials

This is code written while taking a GraphQL tutorial...

h3. Mutation (createProduct)

```mutation {
  createProduct(input : {
    name: "Brick"
    description: "Yukon Concrete"
    price: 6.28
    soldout: false
    inventory: 12
    stores: [
      {store: "Dunwoody"},
      {store: "Canton"}
    ]
  }) {
    id
    price
    name
    inventory
    description
  }
}
```

h3. Response (createProduct)

```{
  "data": {
    "getProduct": {
      "price": 6.28,
      "description": "Yukon Concrete",
      "name": "Brick",
      "inventory": 12
    }
  }
}
```

h3. Query (getProduct)

```query {
  getProduct(id: "c483d1bc4ede946bc4e0") {
    price
    description
    name
  }

}
```

h3. Response (getProduct)

```{
  "data": {
    "getProduct": {
      "price": 6.28,
      "description": "Yukon Concrete",
      "name": "Brick"
    }
  }
}
```
