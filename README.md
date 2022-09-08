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

### How to restrict object props

Instead of any string as object property we can use a limited set of strings
```
type Genre = 'psychedelic' | 'progressive rock' | 'rock n\'roll' | 'classic rock'

type GenreMap = {
  [genre in Genre]: Band[]
}
```