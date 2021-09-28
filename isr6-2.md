### Инвариантная самостоятельная работа


```python
#2.1 генератор чисел ряда Фибоначчи
a = int(input('Give amount: '))

def fib(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

print(list(fib(a)))
```


```python
#2.2 Разработать программу, позволяющую генерировать уникальные идентификаторы
import uuid
  
id = uuid.uuid4()
  
# Id generated using uuid4()
print ("The id generated using uuid4() : ",end="")
print (id)
```


```python

```
