## Enumerate 

* list 의 element를 추출할 때 번호를 붙여서  추출

```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
    #list에 있는 index와 값을 unpacking
    print(i, v)
0 tic
1 tac
2 toe

>>> mylist = ["a", "b", "c", "d"]
>>> list(enumerate(mylist)) 
#list의 index와 값을 unpacking하여 list로 저장 
[(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd')]

{i:j for i,j in enumerate('The quick fox jumps over the lazy dog'.split())}
#문장을 list 로 만들고 list의 index와 value를 unpacking하여 dict로 저장 
{0: 'The',
 1: 'quick',
 2: 'fox',
 3: 'jumps',
 4: 'over',
 5: 'the',
 6: 'lazy',
 7: 'dog'}
```



## Zip 

* 두 개의 list 값을 병렬적으로 추출. 

```python
>>> alist = ['a1', 'a2', 'a3']
>>> blist = ['b1', 'b2', 'b3']
>>> for a, b in zip(alist, blist):
    print(a,b)
a1 b1
a2 b2
a3 b3

>>> a,b,c = zip((1,2,3),(10,20,30),(100,200,300))
# 각 tuple의 같은 index끼리 묶음. 
(1, 10, 100) (2, 20, 200) (3, 30, 300)

>>> [sum(x) for x in zip((1,2,3), (10,20,30),(100,200,300))]
# 각 tuple의 같은 index를 묶어 합을 list로 변환
[111, 222, 333]
```



## Enumerate & Zip 

```python
>>> alist = ['a1', 'a2', 'a3']
>>> blist = ['b1', 'b2', 'b3']

for i, (a,b) in enumerate(zip(alist,blist)):
    print(i, a, b)
0 a1 b1
1 a2 b2
2 a3 b3
```

