
# React Hooks

Project to study react hoks

useState, useEffect, useMemo, useCallback

## useState

Set the initials state on the component.
```javascript
 const [tech, setTech] = useState([]); // initializing states;
```

## useEffect

Executed when one or more variables changes or when the component is mounted.

```javascript
useEffect(() => {
    const storage = localStorage.getItem('tech');

    if(storage) {
      setTech(JSON.parse(storage));
    }

    return () => {
      console.log('Executed when the component is unmounted');
    };
  },
  [] // when this array is empty, this hook is executed on component is mounted.
);
```

```javascript
 useEffect(() => {
    localStorage.setItem('tech', JSON.stringify(tech));
  },
  [tech] // when this array is populated, this hook is executed when the variable at array changes.
);
```

## useMemo

Executed when you want to change variable based in another changes.

```javascript
const techSize = useMemo(() => tech.length, [tech]);
// ins this case, the variable 'techSize' changes only when the variable 'tech' changes.
```

## useCallback

Is like `useMemo`, but it returns a function and the returned function is remounted only when the variable in array changes.

```javascript
const handleAdd = useCallback(() => {
    setTech([...tech, newTech]);
    setNewTech('');
  }, [newTech, tech]);
  // without hooks, the function handleAdd would be recreated every time that setState was called, but in this way, the function in recreate only when the variables newTech and tech change.
```
