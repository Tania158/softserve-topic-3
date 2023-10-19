# Loops-Functions

1. Написати функцію `compact()` яка має приймати на вхід масив, а на вихід має повертати значення нового масиву без повторень.

```js
const arr = [5, 3, 4, 5, 6, 7, 3];

function compact(arr) {
  const uniqueArr = [];

  for (const item of arr) {
    if (!uniqueArr.includes(item)) {
      uniqueArr.push(item);
    }
  }

  return uniqueArr;
}

const arr2 = compact(arr);
console.log(arr2); // [5,3,4,6,7]
```

2. Написати функцію `createArray(start, end)`, яка приймає на вхід 2 параметри: **початкове значення** та **кінцеве значення**, а на виході отримує масив із діапазоном цих значень (реалізувати достатньо лише із числовими значеннями).

```js
function createArray(start, end) {
  let newArr = [];

  for (let i = start; i <= end; i++) {
    newArr.push(i);
  }

  return newArr;
}
let arr = createArray(2, 9);
console.log(arr); // [2,3,4,5,6,7,8,9]
```

3. Задані цілі числа **a** і **b** (**a < b**). Виведіть усі цілі числа від **a** до **b** включно, при цьому a виводится один раз, число **а+1** - два рази і т.д.

```js
const a = 2;
const b = 6;
let arrNumbers = [];

for (let i = a; i <= b; i++) {
  for (let j = 0; j <= i - a; j++) {
    arrNumbers.push(i);
  }
}

console.log(...arrNumbers);
```

4. Напишіть функцію `randArray(k)`, яка заповнюватиме масив `k` випадковими цілими числами. Випадкові числа генеруються із діапазону **1-500**.

```js
function randArray(k) {
  let resultArr = [];

  for (let i = 1; i <= k; i++) {
    const randomNum = Math.floor(Math.random() * 500) + 1;
    resultArr.push(randomNum);
  }

  return resultArr;
}

randArray(5); // [399,310,232,379,40]
```

5. Є масив `arr`, який може містити підмасиви, написати функцію `showByTypes` яка виведе у консоль масиви які складаються із примітивних даних початкового масиву і усіх вкладених масивів, але одного типу даних (не приводити тип **String** в **Number** навіть, якщо там лише число).

```js
function showByTypes(arr) {
  const result = arr.reduce((obj, item) => {
    if (Array.isArray(item)) {
      item.forEach((subItem) => {
        const typeItem = typeof subItem;
        obj[typeItem] = obj[typeItem] || [];
        obj[typeItem].push(subItem);
      });
    } else {
      const typeItem = typeof item;
      obj[typeItem] = obj[typeItem] || [];
      obj[typeItem].push(item);
    }
    return obj;
  }, {});

  for (let key in result) {
    console.log(result[key]);
  }
}

let arr = [
  5,
  "Limit",
  12,
  "a",
  "3",
  99,
  2,
  [2, 4, 3, "33", "a", "text"],
  "strong",
  "broun",
];
showByTypes(arr);
/*
[5, 12, 99, 2, 2, 4, 3]
["Limit", "a", "3", "33", "a", "text", "strong", "broun"]
*/
```

6. Напишіть функцію `calc(a, b, op)`, яка виконує над числами `a` і `b` одну із арифметичних операцій та повертає її результат. Вид операції визначається цілим числом `op`:
   **1** – _віднімання_,
   **2** – _добуток_,
   **3** – _ділення_,
   **інші значення** – _додавання_.

```js
function calc(a, b, op) {
  switch (op) {
    case 1:
      return a - b;
    case 2:
      return a * b;
    case 3:
      if (b === 0) {
        return "Division by zero is impossible";
      }
      return a / b;
    default:
      return a + b;
  }
}

console.log(calc(5, 2, 2)); //10
```

7. Напишіть функцію `findUnique(arr)`, яка приймає масив `arr` і перевіряє на унікальність його елементи. Якщо всі елементи масиву унікальні (не мають дублів), то функція поверне **true**, інакше - **false**.

```js
function findUnique(arr) {
  const uniqueArr = [];

  for (const item of arr) {
    if (!uniqueArr.includes(item)) {
      uniqueArr.push(item);
    } else {
      return false;
    }
  }

  return true;
}

findUnique([1, 2, 3, 5, 3]); // => false
findUnique([1, 2, 3, 5, 11]); // => true
```

⭐⭐⭐

(Ускладнене. Задача не оцінюється. Для тих, кому хочеться поробити ще щось)

Створити функцію `create()`, яка приймає один аргумент у вигляді рядка. Ця функція повертає анонімну функцію, яка перевіряє чи переданий в неї аргумент збігається з аргументом зовнішньої функції.

```js
function create(string) {
  return (comparedStr) => string === comparedStr;
}
const tom = create("pass_for_Tom");
tom("pass_for_Tom"); //повертає true
tom("pass_for_tom"); //повертає false
```
