## 1)  глубокое копирование через рекурсию

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
