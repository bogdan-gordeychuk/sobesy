# Задачи с собесов

## 1) Найти самый часто встречающийся элемент в массиве

Функция `getMaxValue` принимает массив и возвращает элемент, который встречается чаще всего, и количество его вхождений.

```javascript
function getMaxValue(arr) {
  const duplicates = new Map();
  let maxEntry = [null, 0];

  for (const item of arr) {
    const count = (duplicates.get(item) || 0) + 1;
    duplicates.set(item, count);

    if (count > maxEntry[1]) {
      maxEntry = [item, count];
    }
  }

  return maxEntry;
}
```

## 2) Найти индексы элементов, сумма которых равна target

```javascript
function twoSum(nums, target) => {
    const newMap = new Map();

    for (let i = 0; i < nums.length; i++) {
        const difference = target - nums[i];
    
        if (newMap.has(difference)) return [newMap.get(difference), i];

        newMap.set(nums[i], i);
    }
};
```

## 3) Найти самую длинную подстроку в строке

```javascript
function lengthOfLongestSubstring(s) {
    let set = new Set();
    let left = 0;
    let maxSize = 0;

    if (s.length < 2) return s.length;

    for (let i = 0; i < s.length; i++) {

        while (set.has(s[i])) {
            set.delete(s[left])
            left++;
        }
        set.add(s[i]);
        maxSize = Math.max(maxSize, set.size)
    }
    return maxSize;
}
```

## 4) Создание комплексного объекта

При наличии объекта или массива obj вернуть компактный объект.
Компактный объект — это то же самое, что и исходный объект, за исключением удаленных ключей, содержащих ложные значения. Эта операция применяется к объекту и любым вложенным объектам. Массивы считаются объектами, где индексы являются ключами. Значение считается ложным, когда Boolean(value) возвращает false.

```javascript
function compactObject(obj) {
    if (obj === null) return null
    if (Array.isArray(obj)) return obj.filter(Boolean).map(compactObject)
    if (typeof obj !== 'object') return obj;

    const compacted = {};
    for (const key in obj) {
        let value = compactObject(obj[key]);
        if (value) compacted[key] = value;
    }

    return compacted;
};
```
## 5) Нахождение повторяющихся чисел в массиве
Задача на хэшмапу - 

```javascript
hasDuplicate(nums) {
        const duplicates = new Map();
        for (let i = 0; i < nums.length; i++) {
            if (duplicates.has(nums[i])) return true
            else duplicates.set(nums[i], i)
        }
        return false
    }
```
## 6) Являются ли 2 строки анаграммами

```javascript
isAnagram(s, t) {
        if (s.length !== t.length) {
            return false;
        }

        const charCount = {};

        for (let i = 0; i < s.length; i++) {
            charCount[s[i]] = (charCount[s[i]] || 0) + 1;
            charCount[t[i]] = (charCount[t[i]] || 0) - 1;
        }

        for (let count of Object.values(charCount)) {
            if (count !== 0) {
                return false;
            }
        }

        return true;
    }
```


## 7) Мерж массивов

```javascript
var join = function(arr1, arr2) {
    const combined = [...arr1, ...arr2];
    const merged = {};
    combined.forEach((obj) => {
        const id = obj.id;
        if (!merged[id]) {
            merged[id] = {...obj};
        } else {
            merged[id] = {...merged[id], ...obj}
        }
    })
    return Object.values(merged)
```
