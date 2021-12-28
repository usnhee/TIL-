## Lambda 

* 함수 이름 없이 함수처럼 쓸 수 있음. 

* 수학의 람다대수에서 유래.

* Python3 부터는 권장하지 않으나, 여전히 많이 쓰임. 

* if 넣으려면 else 값도 반드시 넣어줘야 함. 

  ```python
  # 일반적으로 함수 쓰는 법. 
  >>> def f(x,y):
       return x+y
  >>> print(f(1,4))
  ```

  ```python
  # Function using Lambda
  >>> f = lambda x,y: x+y
  >>> print(f(1,4))
  ```

  ```python
  # lambda drill 
  >>> f = lambda x,y: x+y
  >>> print(f(1,4))
  5
  >>> f = lambda x: x**2
  >>> print(f(3))
  9
  >>> f = lambda x: x/2
  >>> print(f(3))
  1.5
  >>> print((lambda x: x+1)(5))
  6
  ```



## Map & Reduce

* Sequence 자료형 각 element 에 동일한 fuction을 적용함. 
* map(function_name, list_data)

```python
>>> ex = [1,2,3,4,5]
>>> f = lambda x: x**2
>>> print(list(map(f,ex)))
[1, 4, 9, 16, 25]
#Simpler code
>>> [value**2 for value in ex]
[1, 4, 9, 16, 25]

#인수 두개
>>> f = lambda x,y: x+y
>>> print(list(map(f, ex,ex)))
[2, 4, 6, 8, 10]

```



### Map function

* 두 개 이상의 list에도 적용 가능 

* if filter도 적용 가능. 

```python
>>> ex = [1,2,3,4,5]
>>> f = lambda x, y: x+y 
>>> print(list(map(f, ex, ex)))
[2, 4, 6, 8, 10]
```

```python
>>> list(
>>> 	map(
>>> 		lambda x: x**2 if x%2 == 0
>>> 	 	else x,
>>> 	ex
>>> 	)
>>> )
[1, 4, 3, 16, 5]

```



* python3은 iteration을 생성 -> list 붙여줘야 list 사용 가능. 
* 실행시점의 값을 생성, 메모리 효율성. 

```python
>>> ex = [1,2,3,4,5]
>>> print(list(map(lambda x: x+x, ex)))
>>> print((map(lambda x: x+x, ex)))
[2, 4, 6, 8, 10]
<map object at 0x0000021CF9B7EAC0>

>>> f = lambda x: x**2
>>> print(map(f, ex))
>>> for i in map(f, ex):
   	 print(i)
1
4
9
16
25

>>> result = map(f, ex)
>>> print(next(result))

```



## Reduce function 

* map function 과 달리 list에 똑같은 함수를 적용해서 통합. 

```python
#reduce 
from functools import reduce
print(reduce(lambda x, y: x+y, [1,2,3,4,5]))
# ((((1+2)+3)+4)+5)
15

```



## Summary 

* lambda, map, reduce는 간단한 코드로 다양한 기능 제공.
* 그러나 코드의 직관성 떨어지기 때문에 lambda나 reduce는 __python3에서는 사용을 권장하지 않음.__
* legacy library나 다양한 머신러닝 코드에서 여전히 사용중. 