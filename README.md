
# Домашнее задание: Алгоритмы и структуры данных
## Теоретическая часть

Дерево ван Эмде Боаса (vEB tree) — ассоциативный массив, который позволяет хранить целые числа в диапазоне [0; U), где U = ![equation](http://latex.codecogs.com/gif.latex?2%5E%7Bk%7D), и осуществлять над ними все соответствующие дереву поиска операции.

### Структура

Дерево ван Эмде Боаса хранит в себе:
+ Массив children, состоящий из ![equation](http://latex.codecogs.com/gif.latex?2%5E%7Bk/2%7D) штук (k / 2)-дервьев;
+	Вспомогательное (k / 2)-дерево, aux;
+	Максимальный и минимальный элементы, хранящиеся в этом дереве (если оно не является пустым). В массиве children не хранятся.

### Вспомогательные функции

Для реализации некоторых операций над деревом необходимо ввести вспомогательные функции.
+ *high(x)* — число, соответствующее k/2 старшим битам числа x
+ *low(x)* — число, соответствующее k/2 младшим битам числа x

### Операции над деревом ван Эмде Боаса

**Empty**
Для реализации алгоритма необходимо обозначить условие, по которому значение min пустого дерева является определенным N  ∉  [0; U).

Алгоритм:

+ Сравниваем min с N
+ Если *min* == N - дерево пусто
+ Если *min* != N - дерево не пусто

**Find**

Алгоритм :

-   Если дерево пусто, то число не содержится в нашей структуре.
-   Если число равно полю  _min_  или  _max_, то число в дереве есть.
-   Иначе ищем число _low(x)_  в поддереве _children[high(x)]_.

**Min, Max**

Минимальное и максимальное значения хранятся в дереве отдельно, поэтому данные операции не требуют ничего, кроме вывода значения поля min или max в соответствии с запросом.

**Insert**

Алгоритм:

-   Если дерево пусто или в нем содержится единственный элемент, то присваиваем полям  *min*  и  *max*  соответствующие значения. 
-   Иначе:
    -   Если элемент  *x*  больше  *max*  или меньше  *min*  текущего дерева, то обновляем соответствующее значение минимума или максимума, а старый минимум или максимум добавляем в дерево.
    -   Вставляем во вспомогательное дерево  aux  число  *high(x)*, если соответствующее поддерево  *children[high(x)]*  до этого было пусто.
    -   Вставляем число  low(x) в поддерево  *children[high(x)]*, за исключением ситуации, когда текущее дерево — это 1-дерево, и дальнейшая вставка не требуется.

**Remove**

Алгоритм:

-   Если  *min* = *max* = *x*, значит, в дереве один элемент. Удалим его и отметим, что дерево пусто.
-   Если *x* = *min*, то находим следующий минимальный элемент в этом дереве, присваиваем  *min*  значение второго минимального элемента и удаляем его из того места, где он хранится. Второй минимум — это либо  *max*, либо  *children[aux.min].min*  (для случая  *x* = *max*  действуем аналогично).
-   Если *x* ≠ *min*  и  *x* ≠ *max*, то удаляем  *low(x)*  из поддерева  *children[high(x)]*.

**Next, Prev**

Алгоритм:

-   Если дерево пусто, или максимум этого дерева не превосходит  *x*, то следующего элемента в этом дереве не существует.
-   Если  *x*  меньше поля  *min*, то искомый элемент и есть  *min*.
-   Если дерево содержит не более двух элементов, и  *x* < *max*, то искомый элемент  *max*.
-   Если в дереве более двух элементов:
    -   Если в дереве есть числа больше  *x*, чьи старшие биты равны  *high(x)*,  продолжаем поиск числа, следующего после *low(x)* в поддереве  *children[high(x)]*.
    -   Иначе искомым элементом является либо минимум следующего непустого поддерева, если такое есть, либо максимум текущего дерева в противном случае.
