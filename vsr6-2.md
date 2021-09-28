### Вариантная самостоятельная работа


```python
#2.1 генератор чисел ряда Фибоначчи
def countinfile(filename):
    d = {}
    with open(filename, "r") as fin:
        for line in fin:
            words = line.strip().split()
            for word in words:
                try:
                    d[word] += 1
                except KeyError:
                    d[word] = 1
    return d
```
