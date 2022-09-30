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

### Data type with object destructuring

```
const MyComponent = ({ message }: { message: string }) => (
  <div className="msg">{message}</div>
);
```
or
```
type ComponentProps = { message: string }
const MyComponent = ({ message }: ComponentProps) => (
  <div className="msg">{message}</div>
);
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

---

### How to safely declare an optional prop (using the "defaultProps")
```
type  ComponentProps = { name: string; }

const  Component = ({ name }: ComponentProps) => (
  <div>
    {name.toUpperCase()} /* Safe since name is required */
  </div>
);
Component.defaultProps = { name: "John" };

const  Example = () => (<Component />) /* Safe to omit since name has a default value */
```

---

### How to set types with useState hook
a) for simple values type inference works very well
```
const [state, setState] = useState(false);
// 'state' is inferred to be a boolean
// 'setState' only takes booleans
```
b) null-ish default values
* option 1 - explicitly declare the type, and use a union type
```
const [user, setUser] = useState<User | null>(null);

// later...
setUser(newUser);
```

* option 2 - using type assertions if a state is initialized soon after setup and always has a value after
```
const [user, setUser] = useState<User>({} as User);

// later...
setUser(newUser);
```

### How to set redux reducer types
```
import { Reducer } from 'redux';

export function reducer: Reducer<AppState, Action>() {}
```

More examples and explanation [here](https://github.com/typescript-cheatsheets/react#usereducer)

