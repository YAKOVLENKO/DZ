# Домашнее задание: Алгоритмы и структуры данных
## Теоретическая часть
Дерево ван Эмде Боаса (vEB tree) — структура данных, представляющая собой дерево поиска, позволяющее хранить целые неотрицательные числа в интервале [0; U), где U = ![equation](http://latex.codecogs.com/gif.latex?2%5E%7Bk%7D), и осуществлять над ними все соответствующие дереву поиска операции.
### Структура
Дерево ван Эмде Боаса хранит в себе:
+	2 ![equation](http://latex.codecogs.com/gif.latex?2%5E%7Bk/2%7D) штук (k / 2)-дервьев;
+	Вспомогательное (k / 2)-дерево;
+	Максимальный и минимальный элементы, хранящиеся в этом дереве (если оно не является пустым).
