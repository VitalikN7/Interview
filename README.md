# Вопросы на собесах JS and React

# JavaScript
<details>
<summary>1. Что такое Замыкание?</summary>

##

При создании функции и использования внутри нее переменных, эти переменные доступны только локально внутри функции. Снаружи мы не можем получить к ним доступ. На хранение таких переменных в том числе и аргументов выделяется определенная память и когда функция заканчивает свое выполнение это память очищается. Таким образом эти переменные больше не где не существуют.

Но вот если внутри одной функции создать вторую то вложенная функция получит доступ к переменным которые были объявлены во внешней функции этот механизм
и называется замыканием т е вложенная функция замыкает на себе переменные и аргументы внешней функции.

Таким образом при отработке внешней функции возвращается внутренняя которая замыкается на значения внешней и не дает памяти очистится 

Где используется: если нужно создать приватные переменные внитри другой функции
</details>

---

<details>
<summary>2. Что такое цикл событий (event loop) и как он работает?</summary>

## Цикл событий (event loop) и как он работает?

Выполнение JS-кода — однопоточное. Это значит, что в конкретный момент времени движок может выполнять не более одной строки кода. То есть вторая строка не будет выполнена, пока не выполнится первая. Такое выполнение кода (строка за строкой) называется синхронным.

- Стек вызовов

При вызове какой-то функции она попадает в так называемый стек вызовов.
Стек — это структура данных, в которой элементы упорядочены так, что последний элемент, который попадает в стек, выходит из него первым

- Цикл событий

Цикл событий отвечает за выполнение кода, сбор и обработку событий и выполнение подзадач из очереди. Очередь — структура данных, в которой элементы упорядочены так, что первый попавший в очередь элемент покидает её первым.

Заметьте, что стек вызовов и очередь задач называются именно стеком и очередью. Потому что вызовы из стека работают по принципу «последний зашёл, первый вышел»
а в очереди — по принципу «первый зашёл, первый вышел»

Это по сути бесконечный цикл, в котором выполняются многочисленные обработчики событий. Если очередь пустая — движок браузера ждет, когда поступит событие. Если непустая — первое в ней событие извлекается и его обработчик начинает выполняться. И так до бесконечности.
</details>

---

<details>
<summary>Контекст (this)</summary>

## 3. Контекст (this)

this - это специальная переменная, которая ссылается, на тот объект, в котором она на данный момент находится.

```js
let obj = {
   model: "toyota",
   year: 2017,
   show: function() {
   console.log(this.model) // obj.model
   }
 };
obj.show()
```
</details>

---

<details>
<summary>В чем разница между null и undefined?</summary>

## 4. В чем разница между null и undefined?

Оба варианта означают пустое значение. Если мы инициализируем
переменную, но не присваиваем ей значение, туда помещается специальный
«маркер», который отображается при выводе на экран как undefined. Null
присваиваем самостоятельно.

Null - Это просто специальное значение, которое представляет собой «ничего»,
«пусто» или «значение неизвестно». Если необходимо очистить значение
переменной, мы делаем q = null.
undefined означает, что «значение не было присвоено».
</details>

## 5. Стрелочные функции и их отличие от функций, объявленных через function

- Стрелочные функции не имеют argumemts.
- Синтаксис
- У стрелочных функций нет своего this. Если идет обращение к this, то он
берется снаружи.
- Не могут быть функциями – конструкторами. Т.е не могут вызываться с
помощью new
- Cтрелочную функцию можно написать в одну строку без объявления слова return

## 6. Что такое set и map?

Map – это коллекция, структура данных, работающая по принципу
ключ/значение, как и Object. Но основное отличие от объекта в том, что Map
позволяет использовать ключи любого типа.

Объект Set – это особый вид коллекции: «множество» значений (без ключей),
своего рода массив, где каждое значение может появляться только один раз.

## 7. Какие значения являются falsy(ложными) значениями?

Falsy значение – значение, которое при приведении к логическому типу
возвращает false.

```js
console.log(false)
console.log(0)
console.log('')
console.log(undefined)
console.log(null)
console.log(NaN)
console.log(BigInt(0))
```

## 8. Что такое Promise?

Промис (Promise) — специальный объект JavaScript, который используется для написания и обработки асинхронного кода.

Асинхронные функции возвращают объект Promise в качестве значения. Внутри промиса работает асинхронная операция, которая управляет его состоянием.\
Промисы были придуманы для решения проблемы так называемого «ада функций обратного вызова».

Промис может находиться в одном из трёх состояний:

- pending — стартовое состояние, операция стартовала;
- fulfilled — получен результат;
- rejected — ошибка.

Поменять состояние можно только один раз: перейти из pending либо в fulfilled, либо в rejected:

У промиса есть методы then() и catch(), которые позволяют выполнять код при изменении его состояния.

## 9. Что такое async/await?

Async/await — относительно новый способ написания асинхронного (неблокирующего) кода в JS. Им оборачивают промис. Он делает код более читаемым и чистым, чем промисы и функции обратного вызова.\
Функция, обозначенная как async всегда вернет Promise.

Ключевое слово await заставит интерпретатор JavaScript ждать до тех пор, пока
промис справа от await не выполнится. После чего оно вернёт его результат, и
выполнение кода продолжится. await нельзя использовать в обычных функциях

## 10. Для чего нужен оператор spread?

Спред-синтаксис (spread) ... позволяет передавать итерируемые коллекции (например, массивы или строки) как список аргументов функции или добавлять содержащиеся в них элементы в новый массив.

Спред применятся и для объектов, чтобы копировать пары ключ-значение из одного объекта в другой.

- При вызове функции использовать значения из массива как аргументы:
```js
function multiplyThreeNumbers(a, b, c) {
  return a * b * c
}

const nums = [1, 2, 3]

console.log(multiplyThreeNumbers(...nums)) // 6
```

- В массиве скопировать элементы из другого массива в новый:

```js
const donor = ['это', 'старые', 'значения']
const newArray = [...donor, 1, true, 'мама']

console.log(newArray) // ['это', 'старые', 'значения', 1, true, 'мама']
```

- У объекта скопировать свойства из другого объекта в новый:

```js
const persona = { name: 'Иван', lastName: 'Объектов'}
const userData = { ...persona, username: 'killer3000' }

console.log(userData)
// {
//    name: 'Иван',
//    lastName: 'Объектов',
//    username: 'killer3000'
// }
```
Если в массиве будет больше элементов, чем параметров функции, то будут использованы только те элементы, которые идут первыми по порядку:

```js
function multiplyThreeNumbers(a, b, c) {
  return a * b * c
}

const nums = [1, 2, 3, 5, 6]

console.log(multiplyThreeNumbers(...nums)) // 6
```

## 11. Поверхностное и глубокое копирование

При копировании объектов или массивов JavaScript копирует данные только на один уровень вглубь. Этот тип копирования называется поверхностным (shallow).

Если необходимо полностью скопировать сложную структуру данных, например, массив с объектами, то нужно делать глубокое (deep) или полное копирование данных. JavaScript не содержит функций для глубокого копирования, лучший вариант сделать глубокую копию — сериализовать структуру в JSON и тут же распарсить.

- Поверхностное копирование
---
```
const copy = {…obj}
```
- Глубокое копирование
---
1. Воспользоваться костыльным, медленным способом:
const copy = JSON.parse(JSON.stringify(obj))
Такой способ подойдет для объекта без прототипа и без функций.
2. реализовать рекурсивную функцию копирования полей.
3. Воспользоваться библиотекой lodash, функцией deep clone

## 12. Что такое деструктуризация

В JavaScript есть две чаще всего используемые структуры данных – это Object
и Array. Деструктурирующее присваивание – это специальный синтаксис, который
позволяет нам «распаковать» массивы или объекты в кучу переменных, так как
иногда они более удобны.

## 13. Что такое DOM дерево?

DOM (Document Object Model) — это специальная древовидная структура, которая позволяет управлять HTML-разметкой из JavaScript-кода. Управление обычно состоит из добавления и удаления элементов, изменения их стилей и содержимого.

Браузер создаёт DOM при загрузке страницы, складывает его в переменную document и сообщает, что DOM создан, с помощью события DOMContentLoaded. С переменной document начинается любая работа с HTML-разметкой в JavaScript.

## 14. Всплытие и погружение событий

- Всплытие.

Принцип всплытия очень простой. Когда на элементе происходит событие,
обработчики сначала срабатывают на нём, потом на его родителе, затем выше и так
далее, вверх по цепочке предков.

- Погружение

Стандарт DOM Events описывает 3 фазы прохода события:
1. Фаза погружения (capturing phase) – событие сначала идёт сверху вниз.
2. Фаза цели (target phase) – событие достигло целевого(исходного) элемента.
3. Фаза всплытия (bubbling stage) – событие начинает всплывать.

## 15. Для чего нужны полифилы?

«Полифил» – это библиотека, которая добавляет в старые
браузеры поддержку возможностей, которые в современных браузерах являются
встроенными.

## 16. Расскажите о функциях - конструкторах

Функции-конструкторы являются обычными функциями. Но есть два
соглашения:
1. Имя функции-конструктора должно начинаться с большой буквы.
2. Функция-конструктор должна вызываться при помощи оператора "new".
```js
function User() {
  this.name = 'Alex'
}

const firstUser = new User()
firstUser.name === 'Alex' // true
```
Когда функция вызывается как new User(...), происходит следующее:
1. Создаётся новый пустой объект, и он присваивается this.
2. Выполняется код функции. Обычно он модифицирует this, добавляет туда
новые свойства.
3. Возвращается значение this

## 17. Микро и макро таски в JavaScript

## 18. Что представляет из себя чистая функция?

Функция должна удовлетворять двум условиям, чтобы считаться «чистой»
- Каждый раз функция возвращает одинаковый результат, когда
вызывается с тем же набором аргументов
- Нет побочных эффектов (например, не изменяет внешние переменные)

## 19. Что представляет из себя функция высшего порядка?

Функция высшего порядка — это функция, которая может принимать другую
функцию в качестве аргумента или возвращать другую функцию в качестве
результата

# React

## 1. Что такое VirtualDom

VirtualDOM это копия DOM дерева и вместо того, чтобы взаимодействовать с
DOM напрямую, мы работаем с его легковесной копией. Мы можем вносить
изменения в копию, исходя из наших потребностей, а после этого React применяет
изменения к реальному DOM.

При этом происходит сравнение DOM-дерева с его виртуальной копией,
определяется разница и запускается перерисовка того, что было изменено.

Такой подход работает быстрее, потому как не включает в себя все
тяжеловесные части реального DOM.





