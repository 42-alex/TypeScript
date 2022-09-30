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

Uncontrolled
```
function AddTodo() {
  const handleSubmit = (e: React.FormEvent) => {
    const target = e.target as HTMLFormElement;
    const formFields = Object.fromEntries(new FormData(target)) as {[k: string]: string} ;
    const newTodo: TodoToCreate = {
      title: formFields.todoTitle,
      importance: formFields.todoImportance as TodoImportance,
    }
    addTodo(newTodo).then(resetForm);
  }
}
```

---

### Data type for change input handler (React.ChangeEvent<HTMLInputElement>)

```
function AddProduct() {
  const changeHandler = (e: React.ChangeEvent<HTMLInputElement>) => { //... }
  
  return (
    <input type="text" value={productName} onChange={changeHandler}>
    {/*...*/}
  )
}
```

---

### Data type for context 

```
import { createContext } from 'react';

interface IModalContext {
  isModalOpened: boolean
  openModal: () => void
  closeModal: () => void
}

export const ModalContext = createContext<IModalContext>({
  isModalOpened: false,
  openModal: () => {},
  closeModal: () => {},
})
```