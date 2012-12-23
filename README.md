Симплекс метод с ипользованием MPI
==================

В данном репозитории находится рабочая версия симплекс метода, написанная с использованием MPI. Текущая реализация не является оптимальной и причина тому не очень правильно составленная перессылка данных. [Изображение](https://github.com/madcat1991/mpi_simplex_method/blob/master/time_to_send.png) отображает временные затраты, на некоторые участки кода, из которых видно, что наибольшее количество времени тратиться на инициализацию данных и конечный сбор результатов. 

Данный косяк можно обойте распаралелив и рассылку. К примеру, в случае с 12 процессами, мастер рассылает по трети данных: себе, четвертому и восьмому процессу. После получения, каждый из них, рассылает данные находящимся выше них(по нумерации) трем процессам. Аналогично и при получение, не все данные тут же шлются мастеру, а схлопываются по чуть-чуть.

Также для ускорения можно воспользоваться MPI структурами.

Алгоритм генерации исходных данных
==================
Генерация исходных данных происходит по хитрому алгоритму, который обеспечивает большое количество итераций при решении симплекс метода. Алгоритм вроде бы построен для размещения точек в пространстве многогранника, расположенного в многомерном пространстве так, чтобы область не была близка к нулевым значениям.

Статья
==================
[Статья](https://github.com/madcat1991/mpi_simplex_method/blob/master/v23-128.pdf), на базе которой была написанна данная реализация, также лежит в репозитории.
