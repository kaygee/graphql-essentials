# GraphQL Essentials

This is code written while taking a GraphQL tutorial...

h3. Mutation (createProduct)

```json
mutation {
  createProduct(input : {
    name: "Rock"
    description: "For throwing at people"
    price: 6.28
    soldout: SOLD_OUT
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

```json
{
  "data": {
    "createProduct": {
      "id": "562cf1ea2dc9c9363e17",
      "price": 6.28,
      "name": "Rock",
      "inventory": 12,
      "description": "For throwing at people"
    }
  }
}
```

h3. Query (getProduct)

```json
query {
  getProduct(id: "562cf1ea2dc9c9363e17") {
    price
    description
    name
    inventory
    soldout
  }

}
```

h3. Response (getProduct)

```json
{
  "data": {
    "getProduct": {
      "price": 6.28,
      "description": "For throwing at people",
      "name": "Rock",
      "inventory": 12,
      "soldout": "SOLD_OUT"
    }
  }
}
```
