# Вопросы по собеседованию
---
### Вопросы по **html**:

1. Что такое doctype? Зачем он нужен.
   > doctype - используется для указания типа документа. Добавляется первой строкой в любой html документ. Служит для того, чтобы браузер мог понять как ему интерпретировать страницу и с каким стандартом осуществлять парсинг документа. **Из этого он будет определять, какие элементы являются валидными, а какие устаревшими.**

2. Для чего используют data-атрибуты?
   > Следует отметить, что использование data-атрибутов - немного устаревший подход. Они использовались для хранения различной информации, которую в последующем можно было использовать в js для манипуляций. Минус был в безопасности, так как такой атрибут можно легко изменить в консоли разработчика. С появлением js-фреймворков, от такого подхода постепенно отказываются.

3. Разница между <script>, <script async> и <script defer>.
   >  Когда происходит чтение html-документа парсер может наткнуться на тег script. <script> - это тег, предназначенный для исполнения js-кода. Проблема: когда парсер доходит до этого тега, скрипт блокирует дальнейшее чтение документа до момента своего полного исполнения. Извлекается и загружается мгновенно, блокируя дальнейшее чтение html-документа. Поэтому его рекомендуют добавлять в конец html-документа перед <body>. Если тег содержит атрибут async - скрипт извлекается и исполняется параллельно с чтением html-документа. Часто async применяется для скриптов, которые не зависят от других скриптов (аналитика и тп.). Атрибут defer - скрипт будет извлечен при чтении html-страницы, однако его выполнение произойдет после полного парсинга страницы. Если таких скриптов несколько, каждый будет исполняться в том порядке, как он расположен в html. Такое поведение практически идентично обычному тегу скрипт, однако defer гаранитрует что на момент исполнение скрипт-кода DOM-дерево будет полностью готово. Атрибут следует использовать со скриптами, которые взаимодействуют с DOM-элементами.

4. В чем отличие между тэгами strong/em и b/i? Зачем они нужны?
   > Если посмотреть результат в браузере, то теги strong и b делают текст жирным, а теги em и i - делают текст курсивным. Однако теги strong и em предназначены для добавления обернутому элементу логического выделения. К примеру, внутри параграфа обернутое слово будет не только выделено, но и при чтении страницы поисковыми роботами на нем будет сделан акцент, в то время как теги b и i просто изменяют визуальное вид обернутого элемента без добавления семантики или акцента.

5. Что такое canvas и для чего он используется?
   > Canvas - (холст) - это html5 элемент, который можно использовать для вставки изображений, градиентов, сложных анимаций, также он создает область, в которой с помощью js можно рисовать различные объекты, преобразовывать их и взаимодействовать с ними. По сути, это низкоуровневый API, предназначенный для отрисовки графики. Пример использования:

![image](https://user-images.githubusercontent.com/33577099/159160651-a04ce72d-7567-42d1-8d24-b099d0758f6c.png)

---

### Вопросы по **CSS и препроцессорам**:

1. Типы позиционирования в CSS
   
![image](https://user-images.githubusercontent.com/33577099/159160487-ad2b7132-9046-44c5-85da-cef4ffe751de.png)
   
2. Что такое вендорные префиксы и для чего они используются?

   > Вендорный префикс - это приставка к CSS-свойству, которая обеспечивает поддержку данного свойства браузерами, в которых оно не внедрено на постоянной основе. То есть свойство введено в спецификацию CSS, но в конкретном браузере оно находится либо в стадии разработки, либо в стадии тестирования. Причин для их появления несколько: включение в браузер экспериментальных свойств CSS, которые стандартом еще не утверждены и для кроссбраузерности. @@@Спросить где можно узнать про поддержку свойств в разных браузерах@@@ - сервис CanIUse.

3. Порядок наложения элементов в CSS (Stacking Order)?
   > Элементы в html имеют не плоскую, а объемную структуру. Поэтому они способны перекрывать друг друга. Такое поведение регулируется с помощью свойства z-index. Однако при его отсутствии существует свой порядок наложения. Идет он следующим образом, начиная с самого низкого и заканчивая самым верхним: background-border, z-index меньше нуля, элементы pos: static, float элементы, inline-элементы, z-index равным нулю или auto, и в заключении идут элементы с opacity < 1
   
![image](https://user-images.githubusercontent.com/33577099/159161246-8b3adfd1-3251-4511-9056-fe5ae63eccb3.png)

4. Расскажите подробнее про технологии верстки - Flexbox, Grid. В чем разница между этими двумя технологиями? Перечислите основные свойства этих технологий

> Flexbox — это технология для создания сложных гибких макетов за счёт правильного размещения элементов на странице. Flexbox позволяет контролировать размер, порядок и выравнивание элементов по нескольким осям, распределение свободного места между элементами и многое другое. 
> CSS Grid Layout представляет двумерную сетку для CSS. Grid (здесь и далее подразумевается CSS Grid Layout ) можно использовать для размещения основных областей страницы или небольших элементов пользовательского интерфейса. В этой статье описывается компоновка сетки CSS и новая терминология, которая является частью спецификации CSS Grid Layout Level 1. Функции, показанные в этом обзоре, будут более подробно описаны в остальной части данного руководства.
> Главное отличие Flexbox от CSS Grid определяется размерностью. По сути, Flexbox создавался для одноразмерных макетов, а CSS Grid можно было применять к двухмерным макетам. Поэтому CSS Grid может одновременно настраивать и строки, и колонки.

5. Расскажите про препроцессоры. Что это такое? Какими вы пользуетесь? В чем их преимущества? (миксины, расширения/наследования, переменные, примеры использования)

---

### Вопросы по **JS**

1. Что такое чистая функция?
   > Чистая функция - одна из концепций ФП (функционального программирования). Она должна удовлетворять двум условиям: 1) в ней не должно быть побочных эффектов, 2) каждый раз она возвращает одинаковый результат когда вызывается с тем же набором аргументов. К побочным эффектам можно отнести: видоизменение входных парамеров, http-запросы и DOM-запросы, изменение в файловой системе, а также вывод на экран.

2. Как передаются параметры в функцию: по ссылке или по значению? 
   > Параметры, которые передаются в функцию, всегда передаются по значению, однако в переменные, представляющие объекты записаны ссылки на эти объекты. Поэтому когда в функцию передают объект и изменяют свойство этого объекта, это изменение сохраняется в объекте при выходе из функции. Поэтому может возникнуть ощущение того, что параметры в функцию передаются по ссылке. НО если изменить значение переменной, представляющий объект, то это изменение никак не повлияет на объект, находящийся за пределом функции.

![image](https://user-images.githubusercontent.com/33577099/159163989-5496d823-6b9d-4c89-af63-feec099d3538.png)

   > В функцию передаются 3 параметра, внутри функции примитив умножают, св-во первого объекта изменяют, второй объект пытаются переопределить. В результате только второй объект изменился, так как обновление произошло по ссылке

3. Что такое объектная обертка?
   > Это понятие тесно связано со спецификой языка JS. Даже у примитивов есть свои методы. Такое поведение возможно благодаря объектной обертки. Дело в том, что в момент исполнения кода примитив временно преобразуется в объект. Это тоже самое, как если б в момент применения метода использовался конструктор new String('').method() У каждого примитива кроме null и undefined есть такой объект обертка. После работы со свойством или методом временный объект отбрасывается.

4. Что такое цикл event loop. Объясните, как он работает.
   > Javascript является однопоточным языком программирования. Для такого потока выделяется область памяти, которая называется стэк. В стэке хранятся фреймы - локальные переменные и аргументы вызываемых функций. Список событий, которые должны обрабатываться, формируют очередь событий. Когда стэк освобождается, движок может обработать любое событие из этой очереди. Координирование этого процесса и происходит в event loop. По сути это бесконечный цикл, в котором выполняется многочисленные обработчики событий. Если очередь пустая, движок браузера ждет пока поступит новое событие. Если не пустая - первое событие извлекается и обрабботчик начинает его выполнять и так до бесконечности.

![image](https://user-images.githubusercontent.com/33577099/159164877-391970c7-ba88-492c-8e96-c20b1d2b4205.png)

5. This в JS. Расскажите что это. Чем отличаются методы bind, call, apply.
   > This - это контекст вызова или ссылка на значение объекта, который в данный момент выполняет или вызывает функцию. В соответствии с этим this может принимать абсолютно разные значения - это может быть глобальный объект или объект события и тд. This способна меняться в зависимости от контекста выполнения из-за такой неопределенности периодически возникает такая проблема как потеря функцией контекста вызова, и для того, чтобы ее исправить, можно использовать один из трех методов: call, apply или bind. bind - возвращает новую функцию, call принимает вторым аргументом и последующими примитив, а apply один массив.
   
6. Асинхронный JS. Что такое промисы? В чем отличие Promise.all от Promise.race
   > Промисы - один из приемов работы с асинхронным кодом в JS. Промис это объект который может вернуть одно значение в будущем: либо выполненное значение, либо причина, по которой промис не был выполнен - ошибку. Промис может находиться в одном из трех возможных состояний: выполнено (fullfield - успешно), rejected, pending (выполняется). При использовании промисов можно добавлять cb функции для обработки выполненного значения или причиной отказа. Для такого взаимодействия используется chaining - цепочка вызовов.

---
   
### Вопросы по **React**

1. Какие методы жизненного цикла компонента существуют в React?
   > render() — единственный обязательный метод в классовом компоненте.
При вызове он проверяет this.props и this.state и возвращает один из следующих вариантов: Элемент React, Массивы и фрагменты, Порталы, Строки и числа, Booleans или null
   ---
   > constructor() - Конструктор компонента React вызывается до того, как компонент будет примонтирован. В начале конструктора необходимо вызывать super(props). Если это не сделать, this.props не будет определён. Это может привести к багам.
Конструкторы в React обычно используют для двух целей: Инициализация внутреннего состояния через присвоение объекта this.state. Привязка обработчиков событий к экземпляру.
Конструктор — единственное место, где можно напрямую изменять this.state. В остальных методах необходимо использовать this.setState().
   ---
   > componentDidMount() - вызывается сразу после монтирования (то есть, вставки компонента в DOM). В этом методе должны происходить действия, которые требуют наличия DOM-узлов. Это хорошее место для создания сетевых запросов.
Этот метод подходит для настройки подписок. Но не забудьте отписаться от них в componentWillUnmount().
   ---
   > componentDidUpdate(prevProps, prevState, snapshot) - вызывается сразу после обновления. Не вызывается при первом рендере. Метод позволяет работать с DOM при обновлении компонента. Также он подходит для выполнения таких сетевых запросов, которые выполняются на основании результата сравнения текущих пропсов с предыдущими. Если пропсы не изменились, новый запрос может и не требоваться.
   ---
   > componentWillUnmount() - вызывается непосредственно перед размонтированием и удалением компонента. В этом методе выполняется необходимый сброс: отмена таймеров, сетевых запросов и подписок, созданных в componentDidMount().
   ---
   > shouldComponentUpdate(nextProps, nextState) - вызывается перед рендером, когда получает новые пропсы или состояние. Значение по умолчанию равно true. Этот метод нужен только для повышения производительности.. Но не опирайтесь на его возможность «предотвратить» рендер, это может привести к багам. Вместо этого используйте PureComponent, который позволяет не описывать поведение shouldComponentUpdate() вручную. PureComponent поверхностно сравнивает пропсы и состояние и позволяет не пропустить необходимое обновление.
   ---
   > static getDerivedStateFromProps(props, state) - вызывается непосредственно перед вызовом метода render, как при начальном монтировании, так и при последующих обновлениях. Он должен вернуть объект для обновления состояния или null, чтобы ничего не обновлять.
Этот метод существует для редких случаев, когда состояние зависит от изменений в пропсах.
   ---
   > getSnapshotBeforeUpdate(prevProps, prevState) - вызывается прямо перед этапом «фиксирования» (например, перед добавлением в DOM). Он позволяет вашему компоненту брать некоторую информацию из DOM (например, положение прокрутки) перед её возможным изменением. Любое значение, возвращаемое этим методом жизненного цикла, будет передано как параметр componentDidUpdate().
   ---
   > static getDerivedStateFromError(error) - Этот метод жизненного цикла вызывается после возникновения ошибки у компонента-потомка. Он получает ошибку в качестве параметра и возвращает значение для обновления состояния. getDerivedStateFromError() вызывается во время этапа «рендера». Поэтому здесь запрещены любые побочные эффекты, но их можно использовать в componentDidCatch().
   ---
   > componentDidCatch(error, info) - Этот метод жизненного цикла вызывается после возникновения ошибки у компонента-потомка. Он получает два параметра: error — перехваченная ошибка, info — объект с ключом componentStack, содержащий информацию о компоненте, в котором произошла ошибка. Метод можно использовать для логирования ошибок.
   
   ![image](https://user-images.githubusercontent.com/33577099/159166239-550fc9fe-f4d2-484b-a346-c61cf60cae7d.png)

---

2. Что такое Виртуальная DOM? 
   > Виртуальный DOM (VDOM) — это концепция программирования, в которой идеальное или «виртуальное» представление пользовательского интерфейса хранится в памяти и синхронизируется с «настоящим» DOM при помощи библиотеки, такой как ReactDOM. Этот процесс называется согласованием. Поскольку «виртуальный DOM» — это скорее паттерн, чем конкретная технология, этим термином иногда обозначают разные понятия. В мире React «виртуальный DOM» обычно ассоциируется с React-элементами , поскольку они являются объектами, представляющими пользовательский интерфейс. Тем не менее, React также использует внутренние объекты, называемые «волокнами» (fibers), чтобы хранить дополнительную информацию о дереве компонентов. Их также можно считать частью реализации «виртуального DOM» в React.
   
3. Что такое PureComponent?
   > React.PureComponent похож на React.Component. Отличие заключается в том, что React.Component не реализует shouldComponentUpdate(), а React.PureComponent реализует его поверхностным сравнением пропсов и состояния. Если метод render() вашего React-компонента всегда рендерит одинаковый результат при одних и тех же пропсах и состояниях, для повышения производительности в некоторых случаях вы можете использовать React.PureComponent. Метод shouldComponentUpdate() базового класса React.PureComponent делает только поверхностное сравнение объектов. Если они содержат сложные структуры данных, это может привести к неправильной работе для более глубоких различий (то есть, различий, не выраженных на поверхности структуры). Наследуйте класс PureComponent только тогда, когда вы ожидаете использовать простые пропсы и состояние
   
4. Что такое хуки в React?
   > Хуки — нововведение в React 16.8, которое позволяет использовать состояние и другие возможности React без написания классов. Хуки — это функции, с помощью которых вы можете «подцепиться» к состоянию и методам жизненного цикла React из функциональных компонентов. Хуки не работают внутри классов — они дают вам возможность использовать React без классов. Хук состояния - useState:
   ```
     import React, { useState } from 'react';

     function Example() {
       // Объявляем новую переменную состояния "count"
       const [count, setCount] = useState(0);

       return (
         <div>
           <p>You clicked {count} times</p>
           <button onClick={() => setCount(count + 1)}>
             Нажми на меня
           </button>
         </div>
       );
     }
   ```
  
   > Вызов useState возвращает две вещи: текущее значение состояния и функцию для его обновления. Эту функцию можно использовать где угодно, например, в обработчике событий. Она схожа с this.setState в классах, но не сливает новое и старое состояние вместе. Единственный аргумент useState — это начальное состояние. В примере выше — это 0, так как наш счётчик начинается с нуля. Хук эффекта - useEffect
   
   ```
      import React, { useState, useEffect } from 'react';

      function Example() {
        const [count, setCount] = useState(0);

        // По принципу componentDidMount и componentDidUpdate:
        useEffect(() => {
          // Обновляем заголовок документа, используя API браузера
          document.title = `Вы нажали ${count} раз`;
        });

        return (
          <div>
            <p>Вы нажали {count} раз</p>
            <button onClick={() => setCount(count + 1)}>
              Нажми на меня
            </button>
          </div>
        );
      }
   ```
   > Когда вы вызываете useEffect, React получает указание запустить вашу функцию с «эффектом» после того, как он отправил изменения в DOM. Поскольку эффекты объявляются внутри компонента, у них есть доступ к его пропсам и состоянию. По умолчанию, React запускает эффекты после каждого рендера, включая первый рендер.
   
---
   
### Вопросы по тайпскрипту
   
1. Как перезагрузить функцию?
   >  Надо использовать то же имя функции над оригинальной функцией без скобок {} и изменить число и типы аргументов и/или тип возвращаемого значения.
      ```
         function add(x: string, y: string): string;
         function add(x: number, y: number): number {
           return x + y;
         } 
      ```
