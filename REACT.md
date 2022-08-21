### How to specify data type for useState hook

#### Without TypeScript

```const [products, setProducts] = useState([])```

#### With TypeScript

```const [products, setProducts] = useState<IProduct[]>([])```

---

### Data type for children prop in a component

```
interface ModalProps {
  children: React.ReactNode
}

function Modal({ children }: ModalProps) {
  //...
}
```