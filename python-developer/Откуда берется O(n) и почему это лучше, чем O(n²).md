### Шанс вопроса: 3%

О(n) означает линейное время выполнения алгоритма, что означает, что время работы программы прямо пропорционально количеству входных данных. В отличие от квадратичного времени O(n²), которое растет экспоненциально с увеличением размера входных данных, линейное время означает, что удвоение входного объема данных приводит к примерному удвоению времени выполнения.

Например, рассмотрим простой поиск элемента в списке:
```python
def find_element(elements, target):
    for element in elements:
        if element == target:
            return True
    return False
```
В этом примере время выполнения функции зависит от количества элементов в списке `elements`. Если в списке 100 элементов, функция проверит их все; если 200 элементов, то будет выполнено два раза больше проверок. Это линейная зависимость от количества данных, что и обозначается как O(n).

С другой стороны, алгоритм с квадратичным временем O(n²) означает, что для каждого элемента в списке выполняется проверка всех остальных элементов. Например:
```python
def bubble_sort(elements):
    n = len(elements)
    for i in range(n):
        for j in range(n - 1):
            if elements[j] > elements[j + 1]:
                elements[j], elements[j + 1] = elements[j + 1], elements[j]
```
Здесь внутренний цикл выполняется для каждого элемента списка, что приводит к O(n²) времени работы. Если размер списка увеличивается вдвое, время выполнения такого алгоритма возрастет в четыре раза (2^2 = 4).

Таким образом, линейное время O(n) является более предпочтительным, так как его производительность не зависит от размера данных в той же степени, что и алгоритмы с квадратичным временем.