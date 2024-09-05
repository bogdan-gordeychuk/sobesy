## 1)  глубокое копирование через рекурсию (копирует функции)

```javascript
function deepCopy(val) {
    // Если val не является объектом (или null), просто возвращаем его
    if (val === null || typeof val !== 'object') {
        return val;
    }

    // Если это массив, создаем новый массив и копируем в него элементы
    if (Array.isArray(val)) {
        return val.map(item => deepCopy(item));
    }

    // Иначе создаем новый объект
    let newVal = {};
    for (let key in val) {
        if (val.hasOwnProperty(key)) {
            newVal[key] = deepCopy(val[key]);
        }
    }

    return newVal;
}
```


## Другие виды копирования - 
### JSON.stringify(JSON.parse(obj)) - неглубокое копирование, игнорирует циклические ссылки, Map, Set, функции
### structuredClone(obj) - глубокое копирование, игнорирует функции
### Object.create(Object.getPrototypeOf(клонируемый_объект), Object.getOwnPropertyDescriptors(клонируемый_объект)) - глубокое копирование, поддерживает функции
