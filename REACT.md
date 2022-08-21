### How to specify data type for useState hook

#### Without TypeScript

```const [products, setProducts] = useState([])```

#### With TypeScript

```const [products, setProducts] = useState<IProduct[]>([])```