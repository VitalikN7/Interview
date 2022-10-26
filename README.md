# Вопросы на собесах JS and React

---

# JavaScript
<details>
<summary>1. Что такое Замыкание?</summary>

##
При создании функции и использования внутри нее переменных, эти переменные доступны только локально внутри функции. Снаружи мы не можем получить к ним доступ. На хранение таких переменных в том числе и аргументов выделяется определенная память и когда функция заканчивает свое выполнение это память очищается. Таким образом эти переменные больше не где не существуют.

Но вот если внутри одной функции создать вторую то вложенная функция получит доступ к переменным которые были объявлены во внешней функции этот механизм
и называется замыканием т е вложенная функция замыкает на себе переменные и аргументы внешней функции.

Таким образом при отработке внешней функции возвращается внутренняя которая замыкается на значения внешней и не дает памяти очистится 

Где используется: если нужно создать приватные переменные внитри другой функции
##
</details>

<details>
<summary>2. Что такое цикл событий (event loop) и как он работает?</summary>

##
Выполнение JS-кода — однопоточное. Это значит, что в конкретный момент времени движок может выполнять не более одной строки кода. То есть вторая строка не будет выполнена, пока не выполнится первая. Такое выполнение кода (строка за строкой) называется синхронным.

- Стек вызовов

При вызове какой-то функции она попадает в так называемый стек вызовов.
Стек — это структура данных, в которой элементы упорядочены так, что последний элемент, который попадает в стек, выходит из него первым

- Цикл событий

Цикл событий отвечает за выполнение кода, сбор и обработку событий и выполнение подзадач из очереди. Очередь — структура данных, в которой элементы упорядочены так, что первый попавший в очередь элемент покидает её первым.

Заметьте, что стек вызовов и очередь задач называются именно стеком и очередью. Потому что вызовы из стека работают по принципу «последний зашёл, первый вышел»
а в очереди — по принципу «первый зашёл, первый вышел»

Это по сути бесконечный цикл, в котором выполняются многочисленные обработчики событий. Если очередь пустая — движок браузера ждет, когда поступит событие. Если непустая — первое в ней событие извлекается и его обработчик начинает выполняться. И так до бесконечности.
##
</details>

<details>
<summary>3. Контекст (this)</summary>

## 
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
##
</details>

<details>
<summary>4. В чем разница между null и undefined?</summary>

##
Оба варианта означают пустое значение. Если мы инициализируем
переменную, но не присваиваем ей значение, туда помещается специальный
«маркер», который отображается при выводе на экран как undefined. Null
присваиваем самостоятельно.

Null - Это просто специальное значение, которое представляет собой «ничего»,
«пусто» или «значение неизвестно». Если необходимо очистить значение
переменной, мы делаем q = null.
undefined означает, что «значение не было присвоено».
##
</details>

<details>
<summary>5. Стрелочные функции и их отличие от функций, объявленных через function</summary>

## 
- Стрелочные функции не имеют argumemts.
- Синтаксис
- У стрелочных функций нет своего this. Если идет обращение к this, то он
берется снаружи.
- Не могут быть функциями – конструкторами. Т.е не могут вызываться с
помощью new
- Cтрелочную функцию можно написать в одну строку без объявления слова return
##
</details>

<details>
<summary>6. Что такое set и map?</summary>

##
Map – это коллекция, структура данных, работающая по принципу
ключ/значение, как и Object. Но основное отличие от объекта в том, что Map
позволяет использовать ключи любого типа.

Объект Set – это особый вид коллекции: «множество» значений (без ключей),
своего рода массив, где каждое значение может появляться только один раз.
##
</details>

<details>
<summary>7. Какие значения являются falsy (ложными) значениями?</summary>

##
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
##
</details>

<details>
<summary>8. Что такое Promise?</summary>

##
Промис (Promise) — специальный объект JavaScript, который используется для написания и обработки асинхронного кода.

Асинхронные функции возвращают объект Promise в качестве значения. Внутри промиса работает асинхронная операция, которая управляет его состоянием.\
Промисы были придуманы для решения проблемы так называемого «ада функций обратного вызова».

Промис может находиться в одном из трёх состояний:

- pending — стартовое состояние, операция стартовала;
- fulfilled — получен результат;
- rejected — ошибка.

Поменять состояние можно только один раз: перейти из pending либо в fulfilled, либо в rejected:

У промиса есть методы then() и catch(), которые позволяют выполнять код при изменении его состояния.
##
</details>

<details>
<summary>9. Что такое async/await?</summary>

##
Async/await — относительно новый способ написания асинхронного (неблокирующего) кода в JS. Им оборачивают промис. Он делает код более читаемым и чистым, чем промисы и функции обратного вызова.\
Функция, обозначенная как async всегда вернет Promise.

Ключевое слово await заставит интерпретатор JavaScript ждать до тех пор, пока
промис справа от await не выполнится. После чего оно вернёт его результат, и
выполнение кода продолжится. await нельзя использовать в обычных функциях
##
</details>

<details>
<summary>10. Для чего нужен оператор spread?</summary>

##
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
##
</details>

<details>
<summary>11. Поверхностное и глубокое копирование</summary>

##
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
##
</details>

<details>
<summary>12. Что такое деструктуризация?</summary>

##
В JavaScript есть две чаще всего используемые структуры данных – это Object
и Array. Деструктурирующее присваивание – это специальный синтаксис, который
позволяет нам «распаковать» массивы или объекты в кучу переменных, так как
иногда они более удобны.
##
</details>

<details>
<summary>13. Что такое DOM дерево?</summary>

##
DOM (Document Object Model) — это специальная древовидная структура, которая позволяет управлять HTML-разметкой из JavaScript-кода. Управление обычно состоит из добавления и удаления элементов, изменения их стилей и содержимого.

Браузер создаёт DOM при загрузке страницы, складывает его в переменную document и сообщает, что DOM создан, с помощью события DOMContentLoaded. С переменной document начинается любая работа с HTML-разметкой в JavaScript.
##
</details>

<details>
<summary>14. Всплытие и погружение событий</summary>

##
- Всплытие.

Принцип всплытия очень простой. Когда на элементе происходит событие,
обработчики сначала срабатывают на нём, потом на его родителе, затем выше и так
далее, вверх по цепочке предков.

- Погружение

Стандарт DOM Events описывает 3 фазы прохода события:
1. Фаза погружения (capturing phase) – событие сначала идёт сверху вниз.
2. Фаза цели (target phase) – событие достигло целевого(исходного) элемента.
3. Фаза всплытия (bubbling stage) – событие начинает всплывать.
##
</details>

<details>
<summary>15. Для чего нужны полифилы?</summary>

##
«Полифил» – это библиотека, которая добавляет в старые
браузеры поддержку возможностей, которые в современных браузерах являются
встроенными.
##
</details>

<details>
<summary>16. Расскажите о функциях - конструкторах</summary>

## 
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
##
</details>

<details>
<summary>17. Микро и макро таски в JavaScript</summary>

##
В разработке
##
</details>

<details>
<summary>18. Что представляет из себя чистая функция?</summary>

##
Функция должна удовлетворять двум условиям, чтобы считаться «чистой»
- Каждый раз функция возвращает одинаковый результат, когда
вызывается с тем же набором аргументов
- Нет побочных эффектов (например, не изменяет внешние переменные)
##
</details>

<details>
<summary>19. Что представляет из себя функция высшего порядка?</summary>

##
Функция высшего порядка — это функция, которая может принимать другую
функцию в качестве аргумента или возвращать другую функцию в качестве
результата
##
</details>

---

# React

<details>
<summary>1. Что такое VirtualDom</summary>

##
VirtualDOM это копия DOM дерева и вместо того, чтобы взаимодействовать с
DOM напрямую, мы работаем с его легковесной копией. Мы можем вносить
изменения в копию, исходя из наших потребностей, а после этого React применяет
изменения к реальному DOM.

При этом происходит сравнение DOM-дерева с его виртуальной копией,
определяется разница и запускается перерисовка того, что было изменено.

Такой подход работает быстрее, потому как не включает в себя все
тяжеловесные части реального DOM.
##
</details>

<details>
<summary>2. Разница между контролируемыми и неконтролируемыми компонентами</summary>

##
В HTML элементы формы, **такие как input, textarea и select**, обычно
поддерживают собственное состояние и обновляют его в соответствии с
пользовательскими входными данными. В React изменяемое состояние обычно
хранится в свойстве state компонентов и обновляется только с помощью setState().

Мы можем объединить всё это вместе, сделав состояние React «единственным
источником данных (истины)». Затем компонент React, который отрисовывает
форму, также контролирует, что происходит в этой форме при последующем вводе
данных пользователем. Элемент поля ввода формы, значение которого
контролируется React подобным образом, называется **«контролируемым
компонентом»**.

Вместо того, чтобы писать обработчик события для каждого обновления
состояния, вы можете использовать неуправляемый компонент и читать значения
из DOM через ref

Неуправляемые компоненты опираются на DOM в качестве источника данных и могут быть удобны при интеграции React с кодом, не связанным с React. Количество кода может уменьшиться, правда, за счёт потери в его чистоте. Поэтому в обычных ситуациях мы рекомендуем использовать управляемые компоненты.
##
</details>

<details>
<summary>3. Что такое жизненный цикл компонента React и какие методы знаете?</summary>

##
Каждый компонент React проходит несколько стадий в процессе своей жизни: он создаётся, затем добавляется в DOM, получает пропсы, и, наконец, удаляется из дерева. Этот процесс называют жизненным циклом компонента (Component Lifecycle). React предоставляет набор методов, которые позволяют встроиться в этот процесс.

Существует четыре различных этапа жизненного цикла компонента React:
1. Инициализация: На этом этапе компонент React готовит установку
начального состояния и параметров по умолчанию.
2. Монтирование: Компонент React готов для монтирования в DOM
браузера. Этот этап охватывает методы жизненного цикла
componentWillMount и componentDidMount.
3. Обновление: На этом этапе компонент обновляется двумя способами,
отправляя новые свойства и обновляя состояние. Этот этап охватывает
методы жизненного цикла shouldComponentUpdate, componentWillUpdate
и componentDidUpdate.
4. Размонтирование: На этом последнем этапе компонент не нужен и
отключается из DOM браузера. Этот этап включает метод жизненного
цикла componentWillUnmount.
##
</details>

<details>
<summary>4. Что такое React хуки и какие вы знаете?</summary>

##
Хук — это специальная функция, которая позволяет «подцепиться» к возможностям
React.
Основные React хуки:
- useState;
- useEffect;
- useContext;
- useRef;
- useMemo;
- useCallback;
##
</details>

<details>
<summary>5. useState особенности использования</summary>

##
Хук useState предоставляет функциональным компонентам доступ к состоянию React.

Он возвращает значение с состоянием и функцию для его обновления.
Во время первоначального рендеринга возвращаемое состояние (state)
совпадает со значением, переданным в качестве первого аргумента (initialState).

Функция setState используется для обновления состояния. Она принимает новое
значение состояния и ставит в очередь повторный рендер компонента. Функция
setState может принимать параметром, как и новое значение, так и функцию callback,
которая параметром принимает предыдущее значение.
##
</details>

<details>
<summary>6. useEffect особенности использования</summary>

##
Хук эффекта даёт вам возможность выполнять побочные эффекты в
функциональном компоненте. useEffect - Мутации, подписки, таймеры, логирование
и другие побочные эффекты не допускаются внутри основного тела функционального компонента (называемого этапом рендеринга React). Это приведёт к запутанным
ошибкам и несоответствиям в пользовательском интерфейсе.

Вместо этого рекомендуется использовать useEffect. Функция, переданная в
useEffect, будет запущена после того, как рендер будет зафиксирован на экране или
же если передать вторым параметром массив зависимостей, то функция будет
вызываться каждый раз после изменения одной из зависимостей.
##
</details>

<details>
<summary>7. useContext для чего нужен и когда использовать?</summary>

##
В типичном React-приложении данные передаются сверху вниз (от родителя к
дочернему компоненту) с помощью пропсов. Однако, подобный способ
использования может быть чересчур громоздким для некоторых типов пропсов
(например, выбранный язык, UI-тема), которые необходимо передавать во многие
компоненты в приложении. Контекст предоставляет способ делиться такими
данными между компонентами без необходимости явно передавать пропсы через
каждый уровень дерева.

Компонент, вызывающий useContext, всегда будет перерендериваться при
изменении значения контекста. Если повторный рендер компонента затратен, вы
можете оптимизировать его с помощью мемоизации.
##
</details>

<details>
<summary>8. useRef для чего нужен и когда использовать?</summary>

##
useRef возвращает изменяемый ref-объект, свойство .current которого
инициализируется переданным аргументом (initialValue). Возвращённый объект будет сохраняться в течение всего времени жизни компонента и не будет изменяться
от рендера к рендеру.

Обычный случай использования — это доступ к потомку в императивном
стиле. Т.е. используя ref, мы можем явно обратиться к DOM элементу.

Пример использования:
```js
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    // `current` указывает на смонтированный элемент `input`
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Установить фокус на поле ввода</button>
    </>
  );
}
```
##
</details>

<details>
<summary>9. useMemo для чего нужен и когда использовать?</summary>

##
useMemo используется для того, чтобы закешировать\замемоизировать результат вычислений.

Пример использования:
```js
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```
Передайте «создающую» функцию и массив зависимостей. useMemo будет
повторно вычислять мемоизированное значение только тогда, когда значение какойлибо из зависимостей изменилось. Эта оптимизация помогает избежать
дорогостоящих вычислений при каждом рендере.

Первым параметром функция принимает callback, в котором проходят вычисления, а
вторым массив зависимостей, функция будет повторно проводить вычисления
только при изменении хотя бы одной из зависимостей
##
</details>

<details>
<summary>10. useCallback для чего нужен и когда использовать?</summary>

##
Хук useCallback вернёт мемоизированную версию колбэка, который
изменяется только, если изменяются значения одной из зависимостей. Это полезно
при передаче колбэков оптимизированным дочерним компонентам, которые
полагаются на равенство ссылок для предотвращения ненужных рендеров
##
</details>

<details>
<summary>11. Что такое JSX?</summary>

##
JSX — расширение синтаксиса JavaScript. Этот синтаксис выглядит как язык шаблонов, но наделён всеми языковыми возможностями JavaScript. В результате компиляции JSX и вызова React.createElement() возникают простые объекты — «React-элементы».

Это некое расширение языка упрощающее восприятие кода и разработку 
##
</details>

<details>
<summary>12. Что такое props?</summary>

##
Props (обьект js) – данные, которые передаются в компонент из родительского. Props
доступны только для чтения и не могут быть изменены.
##
</details>

<details>
<summary>13. React.memo для чего нужен и когда использовать?</summary>

##
React.memo — это компонент высшего порядка.

Если ваш компонент всегда рендерит одно и то же при неменяющихся
пропсах, вы можете обернуть его в вызов React.memo для повышения
производительности в некоторых случаях, мемоизируя тем самым результат. Это
значит, что React будет использовать результат последнего рендера, избегая
повторного рендеринга.

React.memo затрагивает только изменения пропсов. Если функциональный
компонент обёрнут в React.memo и использует useState, useReducer или useContext,
он будет повторно рендериться при изменении состояния или контекста.
##
</details>

<details>
<summary>13. Как работает проп children?</summary>

##
Некоторые компоненты не знают своих потомков заранее. Это особенно характерно для таких компонентов, как Sidebar, которые представляют из себя как бы «коробку», в которую можно что-то положить. Для таких компонентов мы рекомендуем использовать специальный проп children, который передаст дочерние элементы сразу на вывод
##
</details>

<details>
<summary>14. Что такое PureComponent?</summary>

##
**PureComponent** при грамотном использовании может значительно повысить производительность ваших приложений, а в противном случае неслабо так навредить.

При работе с обычным компонентом, вы меняете его состояние, а соответственно вызываете ре-рендер, использую встроенную функцию setState. При этом, повторная отрисовка происходит в любом случае. Для, того, что бы это контролировать, вы можете использовать **shouldComponentUpdate**, и прописать там свою логику обработки нового state и новых props.

- shouldComponentUpdate()

Используйте shouldComponentUpdate(), чтобы указать необходимость следующего рендера на основе изменений состояния и пропсов. По умолчанию происходит повторный рендер при любом изменении состояния. В большинстве случаев вы должны полагаться на это поведение.
shouldComponentUpdate() вызывается перед рендером, когда получает новые пропсы или состояние. Значение по умолчанию равно true. Этот метод не вызывается при первом рендере или когда используется forceUpdate().

Этот метод принимает два аргумента (**shouldComponentUpdate**): nextProps и nextState, которые вы можете сравнить с актуальными пропсами и стейтом, и описать логику, в каком случае нужно вызывать обновление компонента, а каком нет.

В **React.Component** данный метод всегда возвращает true, если только вы сами, в ручную, не опишите необходимые проверки. Из-за этого, любой вызов setState, или получение новых props, будут вызывать ре-рендер.

При работе с **React.PureComponent** ситуация другая. Он выполняет “неглубокую” проверку в shouldComponentUpdate (это уже реализовано “из коробки”), и, если данные были изменены, то только тогда срабатывает обновление.

Поскольку проверка “поверхностная”, то и полного сравнения объектов не происходит, сравниваются лишь ссылки на них. Это значит, что если вы, например, не передадите новые пропсы, а просто измените старые “напрямую”, то PureComponent выдаст false в shouldComponentUpdate, и никакого обновления не произойдёт.

Ещё одна проблема с PureComponent заключается в том, что он может блокировать обновления и всех потомков, если shouldComponentUpdate вернул false.

Если метод render() вашего React-компонента всегда рендерит одинаковый результат при одних и тех же пропсах и состояниях, для повышения производительности в некоторых случаях вы можете использовать React.PureComponent.
##
</details>

<details>
<summary>15. Что такое порталы в React?</summary>

##
Порталы позволяют рендерить дочерние элементы в DOM-узел, который находится вне DOM-иерархии родительского компонента.

```js
ReactDOM.createPortal(child, container)
```

Первый аргумент (child) — это любой React-компонент, который может быть отрендерен, такой как элемент, строка или фрагмент. Следующий аргумент (container) — это DOM-элемент.

Типовой случай применения порталов — когда в родительском компоненте заданы стили overflow: hidden или z-index, но вам нужно чтобы дочерний элемент визуально выходил за рамки своего контейнера. Например, диалоги, всплывающие карточки и всплывающие подсказки.
##
</details>

<details>
<summary>16. Для чего нужен атрибут key при рендере списков?</summary>

##
Ключи (keys) помогают React определять, какие элементы были изменены, добавлены или удалены. Их необходимо указывать, чтобы React мог сопоставлять элементы массива с течением времени.

Лучший способ выбрать ключ — это использовать строку, которая будет явно отличать элемент списка от его соседей. Чаще всего вы будете использовать ID из ваших данных как ключи. Когда у вас нет заданных ID для списка, то в крайнем случае можно использовать индекс элемента как ключ.
##
</details>

<details>
<summary>17. Почему react не реактивен?</summary>

##
React назван так потому, что реагирует на изменения состояния компонентов. Все же он делает это не реактивно, а, скорее, по графику.

Помните, что входными данными для render() являются свойства (props) и внутреннее состояние, которое может быть обновлено в любое время.

Когда для render меняются входные данные, меняется и результат ее выполнения.

React.js ведет запись жизненного цикла компонента. Когда React.js видит, что один рендер отличается от другого, он переводит разницу между своим виртуальным представлением в операции с DOM API, которые будут отрисованы в документе.

Не отслеживает в реальном времени изменения переменных.
##
</details>

<details>
<summary>18. Что такое компонент React?</summary>

##
- Компонент React – это класс, который наследуется от класса React.Component 
- Функция render возвращает HTML разметку, то что будет отрисовано в браузере. Класс-компонент без функции render существовать не может, это его интерфейс.
##
</details>

---

# Redux

<details>
<summary>1. В каких случаях можно использовать локальное состояние, а в каких
лучше использовать глобальный State?</summary>

##
Локальное состояние рекомендуется использовать в тех случаях, когда оно
используется только в рамках 1го компонента и не планируется передавать его в
других компоненты. Также локальное состояние используется в компоненте какогото отдельного элемента списка. Если же декомпозиция на компоненты предполагает
вложенность с передачей данных по иерархии, то лучше использовать global state
##
</details>

<details>
<summary>2. Что такое редьюсер и какие параметры он принимает?</summary>

##
Reducer это чистая функция, которая принимает параметрами state и action.
Внутри редюсера мы отслеживаем тип полученного actions и в зависимости от него
мы изменяем состояние и возвращаем новый объект состояния.
##
</details>

<details>
<summary>3. Что такое экшен и как изменить состояние?</summary>

##
Action - это простой js объект, у которого обязательно должно быть поле с типом.
```js
{type: “SET_PAGE”}
```
Также опционально можно добавить какие-то данные. Для того что бы
изменить состояние необходимо вызвать функцию dispatch, в которую передаем
action.
##
</details>

<details>
<summary>4. Асинхронные actions в redux с помощью thunk?</summary>

##
Для того, чтобы использовать redux thunk необходимо подключить его как
middleware. Action creators должны возвращать не просто объект, а функцию, которая
параметром принимает dispatch.
##
</details>

<details>
<summary>5. Что такое Flux - архитектура? Какие сущности она имеет?</summary>

##
Flux-архитектура — архитектурный подход или набор шаблонов программирования для построения пользовательского интерфейса веб-приложений, сочетающийся с реактивным программированием и построенный на однонаправленных потоках данных.

Основной отличительной особенностью Flux является односторонняя направленность передачи данных между компонентами Flux-архитектуры. Архитектура накладывает ограничения на поток данных, в частности, исключая возможность обновления состояния компонентов самими собой. Такой подход делает поток данных предсказуемым и позволяет легче проследить причины возможных ошибок в программном обеспечении.

В минимальном варианте Flux-архитектура может содержать три слоя, взаимодействующие по порядку:

- Действия (англ. actions) — выражение событий (часто для действий используются просто имена — строки, содержащие некоторый «глагол»). Диспетчеры передают действия нижележащим компонентам (хранилищам) по одному. Новое действие не передаётся пока предыдущее полностью не обработано компонентами. Действия из-за работы источника действия, например, пользователя, поступают асинхронно, но их диспетчеризация явлется синхронным процессом. Кроме имени (англ. name), действия могут иметь полезную нагрузку (англ. payload), содержащую относящиеся к действию данные.
- Диспетчер/Диспатчер (англ. dispatcher) предназначен для передачи действий хранилищам. В упрощённом варианте диспетчер может вообще не выделяться, как единственный на всё приложение. В диспетчере хранилища регистрируют свои функции обратного вызова (callback) и зависимости между хранилищами.
- Хранилище (англ. store) является местом, где сосредоточено состояние (англ. state) приложения. Остальные компоненты, согласно Flux, не имеют значимого (с точки зрения архитектуры) состояния. Изменение состояния хранилища происходит строго на основе данных действия и старого состояния хранилища при помощи чистых функций.
- Представление (англ. view) — компонент, обычно отвечающий за выдачу информации пользователю. Во Flux-архитектуре, которая может технически не касаться внутреннего устройства представлений вообще, это — конечная точка потоков данных. Для информационной архитектуры важно только, что данные попадают в систему (то есть, обратно в хранилища) только через действия.
##
</details>

