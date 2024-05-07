# GraphQL Essentials

This is code written while taking a GraphQL tutorial...

## Fragments

### Query (using a fragment)

```graphql
query {
  allProducts: getAllProducts {
		...productFragment
  }
	specificProduct: getProduct(id: "663941dd64add6906d9cb92a"){
		...productFragment
  }
}

fragment productFragment on Product {
  name
  description
  price
}
```

### Response (using fragment)

```json
{
  "data": {
    "allProducts": [
      {
        "name": "Rock",
        "description": "For throwing at people",
        "price": 6.28
      }
    ],
    "specificProduct": {
      "name": "Rock",
      "description": "For throwing at people",
      "price": 6.28
    }
  }
}
```

## Aliases

### Query (using aliases)

```graphql
query {
  allProducts: getAllProducts {
    id
    name
    price
    inventory
  }
  specificProduct: getProduct(id: "663941dd64add6906d9cb92a"){
    id
    name
    description
  }
}
```

### Response (using aliases)

```json
{
  "data": {
    "allProducts": [
      {
        "id": "663941dd64add6906d9cb92a",
        "name": "Rock",
        "price": 6.28,
        "inventory": 12
      }
    ],
    "specificProduct": {
      "id": "663941dd64add6906d9cb92a",
      "name": "Rock",
      "description": "For throwing at people"
    }
  }
}
```

## createProduct(ProductInput)

### Mutation - createProduct(ProductInput)

```graphql
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

### Response - createProduct(ProductInput)

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

## updateProduct(ProductInput)

### Mutation - updateProduct(ProductInput)

```graphql
mutation {
  updateProduct(input : {
    id: "6639441e8b25572823d219e8"
    name: "Red Brick"
    description: "For throwing at windows"
    price: 1.01
    soldout: ON_SALE
    inventory: 39
    stores: [
      {store: "Savannah"},
      {store: "Helen"}
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

### Response - updateProduct(ProductInput)

```json
{
  "data": {
    "updateProduct": {
      "id": "6639441e8b25572823d219e8",
      "price": 1.01,
      "name": "Red Brick",
      "inventory": 39,
      "description": "For throwing at windows"
    }
  }
}
```

## deleteProduct(id)

### Mutation - deleteProduct(id)

```graphql
mutation {
  deleteProduct(id : "6639441e8b25572823d219e8")
}
```

### Response - deleteProduct(id)

```json
{
  "data": {
    "deleteProduct": "Deleted"
  }
}
```

## getProduct(id)

### Query - getProduct(id)

```graphql
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

### Response - getProduct(id)

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

## getAllProducts()

### Query - getAllProducts()

```graphql
query {
  getAllProducts {
    name
    price
    inventory
  }
}
```

### Response - getAllProducts()

```json
{
  "data": {
    "getAllProducts": [
      {
        "name": "Rock",
        "price": 6.28,
        "inventory": 12
      }
    ]
  }
}
```

## Adding Persistence

Use this link (https://www.mongodb.com/docs/manual/tutorial/install-mongodb-community-with-docker/).

`docker pull mongodb/mongodb-community-server:latest`

`docker run --name mongodb -p 27017:27017 -d mongodb/mongodb-community-server:latest`

h3. Persistence Tool(s)

- Robo 3T (https://robomongo.org/)
