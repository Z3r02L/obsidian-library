

Alpine.js — это легковесный JS-фреймворк для добавления реактивности на страницы, похожий на Vue, но проще и мельче. Если ты знаком с Vue или хочешь быстро оживить HTML, Alpine идеально подойдёт для "живых" элементов и не требует сборщиков вроде Webpack.

***

### 1. Подключение

```html
<script src="https://unpkg.com/alpinejs" defer></script>
```


***

### 2. Основы

- Всё работает через x-data (аналог data() во Vue)
- Директивы начинаются с `x-`

```html
<div x-data="{ open: false }">
  <button @click="open = !open">Тоггл</button>
  <div x-show="open">Контент</div>
</div>
```


***

### 3. Часто используемые директивы

| Директива | Назначение | Пример |
| :-- | :-- | :-- |
| x-data | Инициализация состояния | `<div x-data="{ count: 0 }">` |
| x-show | Показ/скрытие по условию | `<div x-show="open">...</div>` |
| x-bind | Динамическое связывание атрибута | `<input x-bind:disabled="isLoading">` |
| x-model | Двухстороннее связывание | `<input x-model="name">` |
| x-on или `@` | Обработчик событий | `<button @click="count++">+</button>` |
| x-for | Циклы по массиву | `<template x-for="item in items">...</template>` |
| x-effect | Реакция на изменение переменной | `<div x-effect="console.log(val)">` |


***

### 4. Примеры

#### Счётчик

```html
<div x-data="{ count: 0 }">
  <button @click="count--">-</button>
  <span x-text="count"></span>
  <button @click="count++">+</button>
</div>
```


#### Тоггл модального окна

```html
<div x-data="{ open: false }">
  <button @click="open = true">Открыть</button>
  <div x-show="open" @click.away="open = false">
    <p>Модалка</p>
    <button @click="open = false">Закрыть</button>
  </div>
</div>
```


***

### 5. События и модификаторы

- `.prevent`, `.stop`, `.once` работают аналогично Vue

```html
<button @click.prevent="submit()">Отправить</button>
```


***

### 6. x-init — запуск кода при инициализации

```html
<div x-data="{ loaded: false }" x-init="loaded = true">
  <span x-show="loaded">Готово!</span>
</div>
```


***

### 7. Магические переменные

- `$el` — текущий элемент
- `$refs` — доступ к refs
- `$nextTick` — дождаться обновления DOM
- `$watch` — отслеживание значения

```html
<div x-data="{ name: '' }" x-init="$watch('name', val => console.log(val))">
  <input x-model="name">
</div>
```


***

### 8. Хелперы

- `x-ref="имя"` — ссылка на элемент (как ref во Vue)
- Можно использовать с `$refs.имя`

***

### 9. Установка (NPM)

```bash
npm install alpinejs
```

```js
import Alpine from 'alpinejs'
window.Alpine = Alpine
Alpine.start()
```


***

### 10. Лучшие практики

- Используй Alpine для простых "живых" виджетов, не для SPA
- Держи x-data максимально локально
- Для сложной логики — вынеси функции в отдельные JS-модули и цепляй через x-init
- Легко сочетается с TailwindCSS

***

### 📌 Альтернативы AlpineJS: VueJS, Stimulus, React (для SPA/сложных интерфейсов).

> Alpine — “jQuery новой эпохи”: минимализм, реактивность, лаконичный синтаксис.

***

https://alpinejs.dev/