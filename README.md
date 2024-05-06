h3. Mutation

```mutation {
  createProduct(input : {
    name: "Brick"
    description: "Yukon Concrete"
    price: 6.28
    soldout: false
    stores: [
      {store: "Dunwoody"},
      {store: "Canton"}
    ]
  }) {
    id
    price
    name
    description
  }
}```

h3. Response
```{
  "data": {
    "createProduct": {
      "id": "c483d1bc4ede946bc4e0",
      "price": 6.28,
      "name": "Brick",
      "description": "Yukon Concrete"
    }
  }
}

h3. Query
```query {
  getProduct(id: "c483d1bc4ede946bc4e0") {
    price
    description
    name
  }

}```

h3. Response
```{
  "data": {
    "getProduct": {
      "price": 6.28,
      "description": "Yukon Concrete",
      "name": "Brick"
    }
  }
}```