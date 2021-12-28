# List Comprehensions 

* 기존 list 사용하여 간단히 다른 list 만드는 기법
* 포괄적인 List, 포함되는 list라는 의미로 사용
* 파이썬에서 가장 많이 사용되는 기법
* 일반적으로 for + append 보다 속도가 빠름



## List Comprehensions (1/4)

``` python
>>> result = []
>>> for i in range(10): 
       result.append(i)
   
>>>result
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```python
>>> result = [i for in range(10)]
>>> result 
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> result = [i for i in range(10) if i%2 == 0]
>>> result 
[0, 2, 4, 6, 8]
```



## List Comprehensions (2/4)

```python
>>> word_1 = "Hello"
>>> word_2 = "World"
>>> result = [i+j for i in word_1 for j in word_2]
#Nested For Loop
>>> result 
['HW',
 'Ho',
 'Hr',
 'Hl',
 'Hd',
 'eW',
 'eo',
 'er',
 'el',
 'ed',
 'lW',
 'lo',
 'lr',
 'll',
 'ld',
 'lW',
 'lo',
 'lr',
 'll',
 'ld',
 'oW',
 'oo',
 'or',
 'ol',
 'od']
```



## List Comprehensions (3/4)

```python
>>> case_1 = ["A", "B", "C"]
>>> case_2 = ["D", "E", "A"]
>>> result = [i+j for i in case_1 for j in case_2]
>>> result 
['AD', 'AE', 'AA', 'BD', 'BE', 'BA', 'CD', 'CE', 'CA']

>>> result = [i+j for i in case_1 for j in case_2 if not(i==j) ]
#Filter : i랑 j랑 같다면 list에 추가하지 않음. 
>>> result 
['AD', 'AE', 'BD', 'BE', 'BA', 'CD', 'CE', 'CA']

>>> result.sort()
>>> result 
['AD', 'AE', 'BA', 'BD', 'BE', 'CA', 'CD', 'CE']
```



## List Comprehension (4/4)

```python
>>> words = 'the quick brown fox jumps over the lazy dog'.split()
#문장을 빈칸 기준으로 나눠 list 변환

>>> print(words)
['the', 'quick', 'brown', 'fox', 'jumps', 'over', 'the', 'lazy', 'dog']

>>> stuff = [[w.upper(), w.lower(), len(w)] for w in words]
# list 의 각 element 들을 대문자, 소문자, 길이로 변환. 2 dimensional list로 변환. 
>>> print(stuff)
[['THE', 'the', 3], ['QUICK', 'quick', 5], ['BROWN', 'brown', 5], ['FOX', 'fox', 3], ['JUMPS', 'jumps', 5], ['OVER', 'over', 4], ['THE', 'the', 3], ['LAZY', 'lazy', 4], ['DOG', 'dog', 3]]
>>> for i in stuff:
    print(i)
    ['THE', 'the', 3]
['QUICK', 'quick', 5]
['BROWN', 'brown', 5]
['FOX', 'fox', 3]
['JUMPS', 'jumps', 5]
['OVER', 'over', 4]
['THE', 'the', 3]
['LAZY', 'lazy', 4]
['DOG', 'dog', 3]
```



## Dimensions... One or Two? 

``` python
>>> case_1 = ["A", "B", "C"]
>>> case_2 = ["D", "E", "A"]
['AD', 'AE', 'AA', 'BD', 'BE', 'BA', 'CD', 'CE', 'CA']

>>> result = [i+j for i in case_1 for j in case_2]
>>> result 
['AD', 'AE', 'AA', 'BD', 'BE', 'BA', 'CD', 'CE', 'CA']

>>> result = [[i+j for i in case_1] for j in case_2]
>>> result 
[['AD', 'BD', 'CD'], ['AE', 'BE', 'CE'], ['AA', 'BA', 'CA']]
```

