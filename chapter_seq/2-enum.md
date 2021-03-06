# Работа с последовательностями как с массивами

## Индекс и значение (номер и число)

Сохраним последовательность целых чисел в памяти, чтобы мы могли перебрать ее много раз. Будем называть такую последовательность массивом.
В питоне нет типа "массив". Но есть тип **list** (список, значения - любые типы) и **str** - строка (значения только символы).

```python
a = list(map(int, input().split()))
```
или зададим ее не с клавиатуры, а определим прямо в программе:
```python
a = [3, 7, -2, 10]
print(a)           # [3, 7, -2, 10]
```

Если последовательность чисел хранится в памяти, мы можем обратиться к любому ее элементу в любом порядке по индексу (номеру элемента в последовательности.

```
     +---+---+---+---+---+---+
  x  | P | y | t | h | o | n |        значение (число), value
     +---+---+---+---+---+---+
  i    0   1   2   3   4   5   6=len  номер (index)
      -6  -5  -4  -3  -2  -1
```

Переберем последовательсть (строку), печатая значения (буквы) и их номера в строке. Используем для этого **enumerate**

**len** - вычислить длину последовательности (функция языка питон).

```python
a = 'python'
for i, x in enumerate(a):
    print(i, x)

print('length =', len(a))    

# Output:
# 0 p
# 1 y
# 2 t
# 3 h
# 4 o
# 5 n
# length = 6
```

## a[i] - доступ к любому элементу массива

**массив[номер]** - обращение к элементу массива. Так можно читать, так можно писать в массив.

```python
a = [3, 5, -2, 10]
print(a)            # [3, 5, -2, 10]
x = a[1]            # x = 5
a[0] = 77
print(a)            # [77, 5, -2, 10]
a[1] = a[2] + a[0]  # a[1] = -2 + 77 
print(a)            # [77, 75, -2, 10]
a[-1] = 8
print(a)            # [77, 75, -2, 8]
```

## Перебираем 

Зададим список `a = [3, 5, -2, 10]` и переберем его всеми известными способами.

### enumerate - номер, значение
```python
for i, x in enumerate(a):
    print(i, x)
# Output:
# 0 3
# 1 5
# 2 -2
# 3 10    
```

### for..in - только значение

Номер не печатаем.

```python
for x in a:
    print(x)
# Output:
# 3
# 5
# -2
# 10    
```

### range(len(a)) - только номера

По номеру `i` можно найти значение `a[i]`.

```python
for i in range(len(a)):
    print(i, a[i])
# Output:
# 0 3
# 1 5
# 2 -2
# 3 10    
```

## Срез (slice) - часть списка 

Можно обратиться к части массива от номера i (включая) до номера j (не включая). Математики запишут это как \[i, j\)
Программисты запишут **срез** (slice) **a[i:j]** и сделают новый список.

```python
>>> a = [3, 5, -2, 10, 8, 1, 17]
>>> a[3]
10
>>> a[1:4]
[5, -2, 10]
>>> a[-5:-2]
[-2, 10, 8]
```

У срезов есть (как у range) третий аргумент - шаг.

**a[i:j:k]** - взять срез списка a от i (включая) до j (НЕ включая) с шагом (прибавить) k.

```python
>>> a = [3, 5, -2, 10, 8, 1, 17]
>>> a[1:6:2]
[5, 10, 1]
>>> a[-2:-5:-1]
[1, 8, 10]
```

Можно не писать номер начала или номер конца среза. Тогда это будет "начало" и "конец" списка.

```python
>>> a = [3, 5, -2, 10, 8, 1, 17]
>>> a[:4]
[3, 5, -2, 10]
>>> a[3:]
[10, 8, 1, 17]
>>> a[:4:2]
[3, -2]
>>> a[3::2]
[10, 1]
>>> a[::2]
[3, -2, 8, 17]
>>> a[::-1]
[17, 1, 8, 10, -2, 5, 3]
```

## Как напечатать список

Дан список `a = [3, 5, -2, 10]`. Надо его напечатать.

Как пишут в программе:
```python
print(a)        # [3, 5, -2, 10]
```

В столбик:
```python
for x in a:
    print(x)
# Output:
# 3
# 5
# -2
# 10
```

В строку, используем аргумент **end** функции print:
```python
for x in a:
    print(x, end=' ')  # печатаем через пробел
print()                # в конце 1 раз - новая строка
```

В строку, используя оператор \* (развернуть список в его элементы):
```python
a = [3, 5, -1, 10]
print(a)              # [3, 5, -1, 10]
print(*a)             # 3 5 -2 10
```

** Внимание! В проверяющей системе, если говорится о последовательности чисел, ее можно печатать или в строку, или в столбец.**