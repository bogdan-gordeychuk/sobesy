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
