
Язык Nix — функциональный ленивый язык с динамической типизацией, который используется для описания пакетов и конфигураций в системе Nix и NixOS:

***

# Шпаргалка по языку Nix

## Основные характеристики

- **Функциональный** — код состоит из функций без побочных эффектов.
- **Ленивый** — вычисления происходят только по необходимости.
- **Динамическая типизация** — типы не объявляются явно.
- **Декларативный** — описываешь, что хочешь получить, а не как это делать.
- **Специализирован для описания программного обеспечения, билдов и конфигураций**.

***

## Синтаксис

### Переменные и выражения

```nix
let
  var = 42;
  greeting = "Hello, Nix!";
in
  greeting
```

- `let ... in` используется для объявления локальных переменных.
- Значение после `in` — результат всего выражения.


### Функции

```nix
add = x: y: x + y;

result = add 2 3;  # result равен 5
```

- Функции — это значения, параметры передаются без скобок через пробел.


### Списки (массивы)

```nix
list = [ 1 2 3 4 ];
first = builtins.head list;  # 1
```


### Атрибуты (объекты)

```nix
person = {
  name = "Alice";
  age = 30;
};

name = person.name;  # "Alice"
```


***

## Основные встроенные функции

- `builtins.head list` — первый элемент списка.
- `builtins.tail list` — список без первого элемента.
- `builtins.map f list` — применение функции ко всем элементам списка.
- `builtins.filter f list` — фильтрация списка по функции-предикату.
- `builtins.concatLists [list1 list2]` — конкатенация списков.

***

## Создание пакетов (дериваций)

Пример простого пакета, который создает скрипт "Hello World":

```nix
{ stdenv, writeShellScript }:

stdenv.mkDerivation {
  name = "hello-script";
  buildCommand = ''
    ${writeShellScript "hello" ''
      echo "Hello, world!"
    ''}
  '';
}
```

- `mkDerivation` — функция создания пакета.
- Аргумент — набор атрибутов (имя, команда сборки и др.)

***

## Управление зависимостями

```nix
{ stdenv, python3 }:

stdenv.mkDerivation {
  name = "mypackage";
  buildInputs = [ python3 ];
  # другие настройки...
}
```

- `buildInputs` — список зависимостей, которые необходимы для сборки пакета.

***

## Полезные конструкции

- **if-конструкция**

```nix
if condition then expr1 else expr2
```

- **Комментарии**

```nix
# Однострочные

/* Многострочные */
```


***

## Работа с атрибутными наборами

```nix
attrs = {
  a = 1;
  b = {
    c = 2;
  };
};

value = attrs.b.c;  # 2
```

Можно использовать оператор `//` для объединения:

```nix
attrs1 = { a = 1; };
attrs2 = { b = 2; };
combined = attrs1 // attrs2;  # { a=1; b=2; }
```


***

## Лучшие практики

- Пиши декларативный чистый код.
- Используй встроенные функции `builtins`.
- Разделяй конфигурации и деривации по файлам.
- Проверяй выражения командой `nix-instantiate`.
- Изучай стандартный репозиторий `nixpkgs` как примеры.

***

## Ресурсы для изучения

- Статья с примерами на Habr: "Nix в пилюлях: Основы языка".
- Документация Nix: nix.dev.
- Примеры на GitHub nixpkgs.

***

[^1]: https://habr.com/ru/articles/806595/

[^2]: https://habr.com/ru/companies/typeable/articles/550860/

[^3]: https://www.reddit.com/r/NixOS/comments/1cp7w20/looking_for_a_proper_guide_on_learning_the_nix/?tl=ru

[^4]: https://edu.cbias.ru/lab-2/Lab-2.html

[^5]: https://apptractor.ru/info/articles/chto-takoe-nix.html

[^6]: https://archercreat.github.io/build-environment-with-nix-shell/

[^7]: https://wiki.nixos.org/wiki/Nix_ecosystem/ru

[^8]: https://pingvinus.ru/note/nixos-configuration

[^9]: https://www.reddit.com/r/NixOS/comments/1iufyul/how_to_actually_learn_nix/?tl=ru

[^10]: https://www.youtube.com/watch?v=0Lhahzs-Wos

