
## Шпаргалка по JavaScript — основы для быстрого старта

***

### 1. Подключение JS на страницу

- Внутри HTML (скрипты лучше подключать вконце и перед </body>):

```html
<script>
  // JS-код здесь
  console.log('Привет, JS!');
</script>
```

- Из внешнего файла:

```html
<script src="script.js"></script>
```


***

### 2. Объявление переменных

```js
let name = "Вася";    // изменяемая переменная
const pi = 3.1415;    // константа
var oldVar = 10;      // устаревший способ, лучше avoid
```


***

### 3. Типы данных

- Числа: `10`, `3.14`
- Строки: `"привет"`, `'мир'`
- Булевы: `true`, `false`
- Массивы: ``[^1][^2][^3]
- Объекты: `{name: "Вася", age: 30}`
- Null и Undefined
- Symbol, BigInt и др.

***

### 4. Функции

```js
function greet(name) {
  return `Привет, ${name}!`;
}

const greetArrow = name => `Привет, ${name}!`;
```


***

### 5. Условные операторы

```js
if (age >= 18) {
  console.log('Совершеннолетний');
} else if (age > 12) {
  console.log('Подросток');
} else {
  console.log('Ребенок');
}

// Тернарный оператор
const status = age >= 18 ? 'Взрослый' : 'Младший';
```


***

### 6. Циклы

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}

let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

do {
  console.log(i);
  i++;
} while (i < 5);
```


***

### 7. Массивы — основные методы

```js
const nums = [1, 2, 3, 4, 5];

nums.push(6);               // Добавить в конец
nums.pop();                 // Убрать последний

nums.forEach(n => console.log(n));   // Перебор

const doubled = nums.map(n => n * 2);  // Новый массив
const evens = nums.filter(n => n % 2 === 0); // Отбор

const sum = nums.reduce((acc, n) => acc + n, 0);  // Сумма
```


***

### 8. Объекты

```js
const person = {
  name: 'Вася',
  age: 30,
  greet() {
    console.log(`Привет, меня зовут ${this.name}`);
  }
};

person.greet();
console.log(person.name);
```


***

### 9. Основы работы с DOM

```js
const btn = document.getElementById('myBtn');
btn.addEventListener('click', () => alert('Клик!'));

const divs = document.querySelectorAll('.item');
divs.forEach(div => div.style.color = 'red');
```


***

### 10. Асинхронность

```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(err => console.error(err));

// Async/await
async function getData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
getData();
```


***

### 11. ES6+ возможности

- Деструктуризация
- Шаблонные строки
- Спред-оператор `...`
- Стрелочные функции
- Классы и модули

***
