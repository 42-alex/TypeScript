### We can pass a data type which we expect as response

#### Without TypeScript
```const response = axios.get('https://fakestoreapi.com/products?limit=5')```

#### With TypeScript
```const response = axios.get<IProduct[]>('https://fakestoreapi.com/products?limit=5')```

Explanation: In other words we expect to receive from backend an array of products. Each product
has type of IProduct.

Example of IProduct:
```
export interface IProduct {
  id: number
  title: string
  price: number
  rating: {
    rate: number
    count: number
  }
}
```