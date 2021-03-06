
Алгоритм выглядит просто:
1. Назначаем обработчики `onmouseover/out` на элементе. Также можно было бы использовать `onmouseenter/leave`, но они менее универсальны и не сработают с делегированием.
2. Когда курсор переходит на элемент, начинаем измерять скорость его движения, используя `mousemove`.
3. Если скорость низкая, то вызываем `over`.
4. Позже, если мы уже не на элементе и `over` отработал, вызываем `out`.

Вопрос: "Как измерить скорость?"

Первая приходящая в голову идея: запускать нашу функцию каждые `100ms` и находить разницу между прежними и текущими координатами курсора. Если она мала, то значит и скорость низкая.

К сожалению, в JavaScript нет возможности получать текущие координаты мыши. Не существует функции типа `getCurrentMouseCoordinates()`.

Единственный путь - это подписаться и слушать события мыши, например `mousemove`.

Таким образом, мы определяем обработчик на событие `mousemove`, чтобы отслеживать координаты и запоминать их. Затем мы можем сравнивать результаты каждые `100ms`.

P.S. Обратите внимание: тесты для решения этой задачи используют `dispatchEvent`, чтобы проверить, что подсказка работает корректно.
