# *Как красиво и правильно писать на JavaScript* #

1. ### Избегайте глобальных переменных #
  Минимизируйте использование глобальных переменных.

  Это включает в себя все типы данных, объекты и функции.

  Глобальные переменные и функции могут быть перезаписаны другими скриптами.

  Вместо этого используйте локальные переменные и научитесь использовать замыкания.
 
2. ### Всегда объявляйте локальные переменные #
  Все переменные, используемые в функции, должны быть объявлены как локальные переменные.

  Локальные переменные должны быть объявлены с ключевым словом let (или const), в противном случае они станут глобальными переменными.
  
3. ### Имена переменных и функций  # 
  Названия функций и переменных могут содержать латинские буквы, цифры и знак $, но имена должны начинаться с латинской буквы. 
  
  В имени переменной или функции должно отображаться её содержание. 
  
  Если название переменной или функции состоит из нескольких слов, то каждое последующее слово пишется с заглавной буквы( js чувствителен к регистру).
  
  Как не стоит называть переменные или функции: 
    
 ``` 
    let a = Kate;
    const 5m = 25 ;
    function abc();
    function startplay();
 ```
 
   Хорошие примеры для названия переменных и функций: 
   
 ``` 
   let name = Kate;
   const number = 25;
   function startPlay();
   function read45Page();
 ```
   
4. ### Объявления сверху #
 Хорошей практикой написания кода является размещение всех объявлений в начале каждого скрипта или функции.

  Это:
  - Сделает чище код
  - Предоставит единственное место для поиска локальных переменных
  - Позволит избегать нежелательных (подразумеваемых) глобальных переменных
  - Уменьшит возможность нежелательных повторных объявлений<br />
   ```
   // Объявите в начале
var firstName, lastName, price, discount, fullPrice;

// Используйте после
firstName = "John";
lastName = "Doe";

price = 19.90;
discount = 0.10;

fullPrice = price * 100 / discount;
   ```

5. ###  Переменные #
  Из возможных переменных var, const и let необходимо правильно выбирать нужную по ситуации. Переменная Var устарела, и ее рекомендуют не использовать. Const - постоянная, константа значение которой не меняется. let - переменная, значение которой можно изменить.
  плохая практика:  <br />
  ```
  const num = 2;  
  const num = 3;
  let hoursPerDay = 24; 
  var name = Kate;
  ```
   хорошая практика:  <br />
  ```
  let num = 2; 
  let num = 3; 
  const hoursPerDay = 24;
  let name = Kate;
  ```
  
  Хорошей практикой кодирования является инициализация переменных при их объявлении.

  Это:
  - Сделает код чище
  - Предоставит единственное место для инициализации переменных
  - Позволит избежать неопределенных значений
  
```
// Объявите и инициализируйте в начале
var firstName = "",
lastName = "",
price = 0,
discount = 0,
fullPrice = 0,
myArray = [],
myObject = {};
```
  
6. ### Oбъекты #
  Никогда не объявляйте числовые (number), строковые (string) или логические (boolean) объекты
  Всегда обрабатывайте числа, строки или логические значения как примитивные значения. Но не как объекты.

  Объявление этих типов как объектов замедляет скорость выполнения и вызывает неприятные побочные эффекты: 
```
var x = "John";             
var y = new String("John");
(x === y) // является false, потому что x является строкой и y является объектом.
```
  Или еще хуже:
```
var x = new String("John");             
var y = new String("John");
(x == y) // является false, потому что вы не можете сравнивать объекты.
```
 
7. ### Автоматическое преобразование типов #
  Остерегайтесь автоматических преобразований типов
  Помните, что числа могут быть случайно преобразованы в строки или `NaN` (Not a Number / Не число).

  JavaScript слабо типизирован. Переменная может содержать разные типы данных, а переменная может изменять свой тип данных:
```
var x = "Hello";     // по типу x является строкой
x = 5;               // изменение типа x на число
```
  При выполнении математических операций JavaScript может преобразовывать числа в строки:
```
var x = 5 + 7;       // x.valueOf() является 12,  тип x является числом
var x = 5 + "7";     // x.valueOf() является 57,  тип x является строкой
var x = "5" + 7;     // x.valueOf() является 57,  тип x является строкой
var x = 5 - 7;       // x.valueOf() является -2,  тип x является числом
var x = 5 - "7";     // x.valueOf() является -2,  тип x является числом
var x = "5" - 7;     // x.valueOf() является -2,  тип x является числом
var x = 5 - "x";     // x.valueOf() является NaN, тип x является числом
```
  Вычитание строки из строки не генерирует ошибку, но возвращает `NaN` (Not a Number):
```
"Hello" - "Dolly"    // возвращает NaN
```
  
8. ### Создание объектов и массивов #
  Для создания массивов и объектов лучше использовать специальные символы (скобки)

Плохо:
``` 
    let numbers = new Array();
    let user = new Object();
```

Хорошо:
```
    let numbers = [];
    let user = {};
```

9. ### Сравнение #
  Оператор сравнения == всегда преобразует (в соответствующие типы) перед сравнением.

  Оператор === вызывает сравнение значений и типа:
```
0 == "";        // true
1 == "1";       // true
1 == true;      // true

0 === "";       // false
1 === "1";      // false
1 === true;     // false
```

10. ### Параметры по умолчанию #

    Использование параметров по умолчанию
  Если функция вызывается с отсутствующим аргументом, значение отсутствующего аргумента устанавливается в `undefined` (не определено).

  Неопределенные значения могут нарушить ваш код. Это хорошая привычка назначать значения по умолчанию для аргументов.
```
function myFunction(x, y) {
  if (y === undefined) {
    y = 0;
  }
}
```
