### How to specify data type for useState hook

#### Without TypeScript

```const [products, setProducts] = useState([])```

#### With TypeScript

```const [products, setProducts] = useState<IProduct[]>([])```

---

### Data type for children prop in a component (React.ReactNode)

```
interface ModalProps {
  children: React.ReactNode
}

function Modal({ children }: ModalProps) {
  //...
}
```

---

### Data type for submit form handler (React.FormEvent)

```
function AddProduct() {
  const handleSubmit = (e: React.FormEvent) => { //... }
  
  return (
    <form onSubmit={handleSubmit}>
    {/*...*/}
  )
}
```