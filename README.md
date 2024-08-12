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
