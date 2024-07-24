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
