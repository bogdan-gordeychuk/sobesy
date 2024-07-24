Задачи
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
