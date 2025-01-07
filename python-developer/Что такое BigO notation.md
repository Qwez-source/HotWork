### Шанс вопроса: 10%

Big O Notation — это способ представления сложности алгоритма в зависимости от размера входных данных. Он описывает, как время выполнения или пространство, используемое алгоритмом, увеличивается с ростом размера входных данных. Big O Notation позволяет сравнить эффективность различных алгоритмов и оценить производительность кода.

Вот основные компоненты Big O Notation:
- **O(1)**: Алгоритм работает за постоянное время, не зависящее от размера входных данных. Пример: доступ к элементу массива по индексу.
  ```python
  def get_first_element(arr):
      return arr[0]
  ```
- **O(n)**: Время выполнения алгоритма линейно зависит от размера входных данных. Пример: поиск элемента в массиве.
  ```python
  def find_element(arr, target):
      for element in arr:
          if element == target:
              return True
      return False
  ```
- **O(n²)**: Время выполнения алгоритма квадратично зависит от размера входных данных. Пример: сортировка пузырьком.
  ```python
  def bubble_sort(arr):
      n = len(arr)
      for i in range(n):
          for j in range(0, n-i-1):
              if arr[j] > arr[j+1]:
                  arr[j], arr[j+1] = arr[j+1], arr[j]
  ```
- **O(log n)**: Время выполнения алгоритма логарифмически зависит от размера входных данных. Пример: бинарный поиск.
  ```python
  def binary_search(arr, target):
      left, right = 0, len(arr) - 1
      while left <= right:
          mid = (left + right) // 2
          if arr[mid] == target:
              return True
          elif arr[mid] < target:
              left = mid + 1
          else:
              right = mid - 1
      return False
  ```
- **O(n log n)**: Время выполнения алгоритма линейно-логарифмически зависит от размера входных данных. Пример: быстрая сортировка.
  ```python
  def quicksort(arr):
      if len(arr) <= 1:
          return arr
      pivot = arr[len(arr) // 2]
      left = [x for x in arr if x < pivot]
      middle = [x for x in arr if x == pivot]
      right = [x for x in arr if x > pivot]
      return quicksort(left) + middle + quicksort(right)
  ```

Big O Notation помогает оценить, как быстро или медленно будет работать алгоритм при увеличении объема данных и выбирать наиболее эффективные решения для конкретных задач.