# Asterisk 

* '*' : 별표

* 단순 곱셈, 제곱 연산, 가변인자 등에 활용
* 함수에서 불특정 여러개의 인자를 받고 싶을 때. 



```python
# *args  arguments(인자)
>>> def asterisk_test(a, *args):
>>>     print(a, args)
>>>     print(type(args))
    
>>> asterisk_test(1,2,3,4,5,6)
1 (2, 3, 4, 5, 6)   # 1 제외 나머지 인자들이 tuple형태로 출력. 
<class 'tuple'>     # 자료형: tuple
```

```python
# **kargs  keyword arguments ('키워드'='특정 값') --> {'키워드':'특정 값'} 딕셔너리로! 
>>> def asterisk_test(a, **kargs):
>>>		print(a, kargs)
>>>		print(type(kargs))

>>> asterisk_test(1, b=2, c=3, d=4, e=5, f=6)
1 {'b': 2, 'c': 3, 'd': 4, 'e': 5, 'f': 6} 
<class 'dict'>

```



## asterisk - unpacking a container

* tuple, dict 등 자료형에 들어가 있는 값을 unpacking

* 함수의 입력값, zip 등에 유용하게 사용가능

  

### unpacking drill 1 

인자로 받기. 

```python
def asterisk_test(a,*args):
    print(a, args)
    print(type(args))
    
asterisk_test(1, (2,3,4,5,6))
1 ((2, 3, 4, 5, 6),)   #2dimensional tuple처럼 출력되었음 
<class 'tuple'>

## tuple 한 개이므로 첫번째(=[0])
def asterisk_test(a,*args):
    print(a, args[0])
    print(type(args))
    
asterisk_test(1, (2,3,4,5,6))

1 (2, 3, 4, 5, 6)
<class 'tuple'>
```



```python
>>> def asterisk_test(a, *args):  #두번째 인자는 *로 받음. 1개의 tuple이 들어감. 
>>>     print(a, args)
>>>     print(type(args))

>>> asterisk_test(1,*(2,3,4,5,6)) # tuple을 unpacking해서 넣어줘
1 (2, 3, 4, 5, 6)
<class 'tuple'>
```

```python
#비교해 보자.. 인자는 args로 print에서 *로! 
>>> def asterisk_test(a,args):  #인자를 일단 받아서
>>>     print(a,*args)   # *로 unpacking해서 보여주자
>>>     print(type(args))
    
>>> asterisk_test(1, (2,3,4,5,6))
1 2 3 4 5 6
<class 'tuple'>
```



### unpacking drill 2 

여러가지 자료형과 zip

```python
>>> a, b, c = ([1,2], [3,4], [5,6])
>>> print(a,b,c)   #[0]이 [1,2], [1]이 [3,4], [2]이 [5,6]
[1, 2] [3, 4] [5, 6]

>>> data = ([1,2], [3,4], [5,6])
>>> print(*data)     #unpacking.
[1, 2] [3, 4] [5, 6]
```

```python
>>> def asterisk_test(a,b,c,d):
>>>     print(a,b,c,d)
>>> data = {"b":1, "c":2, "d":3}
>>> asterisk_test(10, **data)     #키워드아규먼트를 unpacking
10 1 2 3
```

```python
>>> for data in zip(*([1,2],[3,4],[5,6])):
>>>     print(data)
(1, 3, 5)                #첫번째 열끼리 zip
(2, 4, 6)                #두번째 열끼리 zip
```



