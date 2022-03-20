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
   
6. Асинхронный JS. 
