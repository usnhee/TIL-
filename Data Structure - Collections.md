# Data Structure - Collections

* list, tuple, dict에 대한 python built-in 자료구조 모듈

* 편의성, 실행 효율성. 

  ` from collections import deque`

  ` from collections import Counter`

  ` from collections import OrderedDict`

  ` from collections import defaultdict`

  `from collections import namedtuple`

  

  ## deque

  - stack과 queue를 지원하는 모듈.

  - list에 비해 효율적인 자료 저장방식을 지원. 

```python
>>> from collections import deque

>>> deque_list = deque()
>>> for i in range(5):           # 0~4까지 
>>>     deque_list.append(i)   
>>> print(deque_list)

>>> deque_list.appendleft(19)   #인자를 왼쪽에 붙여준다.
>>> print(deque_list)
>>> print(type(deque_list))

deque([0, 1, 2, 3, 4])
deque([19, 0, 1, 2, 3, 4])
<class 'collections.deque'>
```

- rotate, reverse 등 linked list의 특성을 지원함. 

- 기존 list 형태의 함수를 모두 지원함. 

  ```python
  # rotate
  >>> deque_list.rotate(2)  
  >>> print(deque_list)
  >>> deque_list.rotate(2)
  >>> print(deque_list)
  deque([3, 4, 19, 0, 1, 2]) 
  deque([1, 2, 3, 4, 19, 0])
  
  # extend / extendleft
  >>> deque_list.extend([5,6,7])
  >>> print(deque_list)
  >>> deque_list.extendleft([5,6,7])
  >>> print(deque_list)
  deque([1, 2, 3, 4, 19, 0, 5, 6, 7])
  deque([7, 6, 5, 1, 2, 3, 4, 19, 0, 5, 6, 7])
  
  # reversed
  >>> print(deque_list)
  >>> print(deque(reversed(deque_list)))
  deque([7, 6, 5, 1, 2, 3, 4, 19, 0, 5, 6, 7])
  deque([7, 6, 5, 0, 19, 4, 3, 2, 1, 5, 6, 7])
  ```

  ```python
  ## deque 로 ! 
  from collections import deque
  import time
  
  start_time = time.process_time()
  deque_list = deque()
  
  for i in range(10000):
      for i in range(10000):
          deque_list.append(i)
          deque_list.pop()
  print(time.process_time() - start_time, "seconds")
  # 13.0 seconds
  
  ## general list 로 ! 
  import time
  
  start_time = time.process_time()
  just_list =[]
  for i in range(10000):
      for i in range(10000):
          just_list.append(i)
          just_list.pop()
  print(time.process_time()-start_time, "seconds")
  # 32.78125 seconds
  ```

  

## Ordered Dict

- dict와 달리 입력한 순서대로 dict를 반환함. 

```python
>>> d = {}
>>> d['x'] = 100 
>>> d['y'] = 200 
>>> d['z'] = 300
>>> d['l'] = 500 

>>> for k, v in d.items():
>>>     print(k,v)
x 100                   
y 200
z 300
l 500
# 강의안에서는 이 경우 l-x-y-z 순서로 나온다고 나왔지만, 실제로는 입력한 순서대로 출력되었다..! 여러번 해봐도 같았다. 

>>> from collections import OrderedDict
>>> d = OrderedDict()
>>> d['x'] = 100
>>> d['y'] = 200
>>> d['z'] = 300
>>> d['l'] = 500

>>> for k,v in d.items():
>>>     print(k,v)
x 100
y 200
z 300
l 500
```

- dict type의 값을 value 나 key 값으로 정렬할 때 사용가능.

```python
for k,v in OrderedDict(sorted(d.items(), key = lambda t: t[0])).items():
	print(k,v)
# 첫번째 값으로 정렬[0]
l 500
x 100
y 200
z 300

for k,v in OrderedDict(sorted(d.items(), key = lambda t: t[1])).items():
	print(k,v)
# 두번째 값으로 정렬[1]
x 100
y 200
z 300
l 500
```



## defaultdict

- dict type의 값에 기본 값을 지정해 신규값 생성시 사용하는 방법

  

![image-20211228173733217](C:\Users\class\AppData\Roaming\Typora\typora-user-images\image-20211228173733217.png)

```python
from collections import defaultdict
d = defaultdict(object)       #default dictionary 생성
d = defaultdict(lambda: 0)    #default 값을 0으로 설정
print(d["first"])
# 0
```

- 하나의 지문에 각 단어들이 몇 개나 있는지 세고 싶을 경우
- text-mining 접근법 - Vector Space Model

```python
text = """A press release is the quickest and easiest way to get free publicity. If well written, a press release can result in multiple published articles about your firm and its products. And that can mean new prospects contacting you asking you to sell them.""".lower().split()

print(text)
# ['a', 'press', 'release', 'is', 'the', 'quickest', 'and', 'easiest', 'way', 'to', 'get', 'free', 'publicity.', 'if', 'well', 'written,', 'a', 'press', 'release', 'can', 'result', 'in', 'multiple', 'published', 'articles', 'about', 'your', 'firm', 'and', 'its', 'products.', 'and', 'that', 'can', 'mean', 'new', 'prospects', 'contacting', 'you', 'asking', 'you', 'to', 'sell', 'them.']
```

``` python
from collections import OrderedDict
word_count = defaultdict(object)   #default dict 생성
word_count = defaultdict(lambda: 0)   #default 값 0 설정

for word in text: 
    word_count[word] += 1
for i, v in OrderedDict(sorted(word_count.items(), key=lambda t: t[1], reverse=True)).items():
	print(i,v)

##
and 3
a 2
press 2
release 2
to 2
can 2
you 2
is 1
the 1
quickest 1
easiest 1
way 1
get 1
free 1
publicity. 1
if 1
well 1
written, 1
result 1
in 1
multiple 1
published 1
articles 1
about 1
your 1
firm 1
its 1
products. 1
that 1
mean 1
new 1
prospects 1
contacting 1
asking 1
sell 1
them. 1
```



## Counter 

- sequence type의 element 갯수를 dict 형태로 반환. 

```python
from collections import Counter

c = Counter()             # a new, empty counter
c = Counter('gallahad')   # a new counter from an iterable
print(c)
#
Counter({'a': 3, 'l': 2, 'g': 1, 'h': 1, 'd': 1})
```

- dict type, keyword parameter 모두 처리 가능. 

```python
c = Counter({'red': 4, 'blue': 2}) 
# a new counter from a mapping
print(c)
print(list(c.elements()))
#
Counter({'red': 4, 'blue': 2})
['red', 'red', 'red', 'red', 'blue', 'blue']
```

```python
c = Counter(cats=4, dogs=8)
# a new counter from keyword args
print(c)
print(list(c.elements()))
#
Counter({'dogs': 8, 'cats': 4})
['cats', 'cats', 'cats', 'cats', 'dogs', 'dogs', 'dogs', 'dogs', 'dogs', 'dogs', 'dogs', 'dogs']
```

- set의 연산도 지원. 

```python
c = Counter(a=4, b=2, c=0, d=-2)
d = Counter(a=1, b=2, c=3, d=4)
c.subtract(d)  # c-d
print(c)
#
Counter({'a': 3, 'b': 0, 'c': -3, 'd': -6})
```

- word counter의 기능도 가능. 

```python
text = """A press release is the quickest and easiest way to get free
publicity. If well written, a press release can result in multiple
published articles about your firm and its products. And that can mean
new prospects contacting you asking you to sell to them.
….""".lower().split()
print(Counter(text))
print(Counter(text)["a"])
#
Counter({'and': 3, 'to': 3, 'a': 2, 'press': 2, 'release': 2, 'can': 2, 'you': 2, 'is': 1, 'the': 1, 'quickest': 1, 'easiest': 1, 'way': 1, 'get': 1, 'free': 1, 'publicity.': 1, 'if': 1, 'well': 1, 'written,': 1, 'result': 1, 'in': 1, 'multiple': 1, 'published': 1, 'articles': 1, 'about': 1, 'your': 1, 'firm': 1, 'its': 1, 'products.': 1, 'that': 1, 'mean': 1, 'new': 1, 'prospects': 1, 'contacting': 1, 'asking': 1, 'sell': 1, 'them.': 1, '….': 1})
2

```



## named tuple

- tuple 형태로 data 구조체를 저장하는 방법
- 저장되는 data의 variable을 사전에 지정해서 저장. 

```python
from collections import namedtuple
Point = namedtuple('Point', ['x','y'])
p = Point(11,y=22)
print(p[0] + p[1])

x,y = p
print(x,y)
print(p.x + p.y)
print(Point(x=11,y=22))
#
33
11 22
33
Point(x=11, y=22)
```

