# Pythonic Code - Split & Join 

## split 함수 

- string type 의 값을 나눠서 List 형태로 저장

  ```python
  >>> items = 'zero one two three'.split() #빈칸 기준으로 문자열 나누기
  >>> print(items)
  ['zero', 'one', 'two', 'three']
  
  >>> example = 'python, jquery, javascript'
  >>> example.split(",") #","을 기준으로 문자열 나누기 
  ['python', 'jquery', 'javascript']
  
  >>>a, b, c = example.split(",")
  #리스트에 있는 각 값을 a,b,c 변수로 unpacking
  
  >>> example = 'Scranton.PA.USA'
  >>> city, state, nation = example.split(".")
  #"."을 기준으로 문자열 나누기. ->unpacking
  ```



## Join 함수 

* string list를 합쳐 하나의 string 으로 반환할 때 사용

  ```python
  >>> colors = ['red', 'blue', 'green', 'yellow']
  >>> result = ''.join(colors)
  >>> result
  'redbluegreenyellow'
  
  >>> result = ' '.join(colors) #연결시 빈칸 1칸으로 연결
  >>> result 
  'red blue green yellow'
  
  >>> result = ', '.join(colors) #연결 시 ", "으로 연결
  >>> result 
  'red, blue, green, yellow'
  
  >>> result = '-'.join(colors) #연결시 "-"으로 연결
  >>> result 
  'red-blue-green-yellow'
  ```

  