### Лабораторная работа square_seq_digit
Написать функцию squareSequenceDigit(), где решалась бы следующая задача. Найти n-ю цифру последовательности из квадратов целых чисел: 149162536496481100121144...


```python
def squareDigitsSequence(a0):
    used_elements = [a0]

    while True:
        temp_val = value(used_elements[-1])

        if temp_val in used_elements:
            return len(used_elements)
        else:
            used_elements.append(temp_val)

def value(b):
    sum = 0

    for char in str(b):
        sum += int(char) ** 2

    return sum
```


```python

```
