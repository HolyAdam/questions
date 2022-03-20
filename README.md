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
 
