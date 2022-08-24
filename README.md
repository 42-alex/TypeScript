# TypeScript Notes

---

### How to allow any prop type and props count in object

```
interface User {
    name: string,
    age: number,
    [propName: string]: any
}

const John: User = {
    name: 'John',
    age: 24,
    position: 'driver',
    isMarried: true
}
```
