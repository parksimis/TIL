# Numpy

> Numpy는 Numerical Python의 줄임말로 고성능의 과학계산 컴퓨팅과 데이터 분석에 필요한 기본 패키지이다. 제공되는 기능은 다음과 같다.
>
> * 빠르고 메모리를 효율적으로 사용하며, 벡터 산술연산과 관련된 브로드캐스팅 기능을 제공하는 다차원 배열인 ndarray
> * 반복문을 작성할 필요없이, 전체 데이터 배열에 대해 빠른 연산을 제공하는 표준 수학함수
> * 배열 데이터를 디스크에 쓰거나 읽을 수 있는 도구와 메모리에 올려진 파일을 사용하는 도구
> * 선형대수, 난수 발생기, 푸리에 변환 기능 제공



* Numpy를 사용하기 위해서는 먼저 `numpy` 패키지를 import 한다.

  ```python
  import numpy as np
  ```



## 다차원 배열 (Arrays)

> Numpy가 제공하는 ndarray(n-dimensional array)은 같은 종류의 데이터를 담을 수 있는 다차원 배열이며, 모든 원소는 같은 자료형이어야 한다. 
>
> 모든 배열은 각 차원의 크기를 알려주는 shape라는 튜플과 배열에 저장된 자료형을 알려주는 type이라는 객체를 가진다. ndarray의 차원(dimension)은 rank라고 부른다.



```python
>>> a = [1, 2, 3, 4, 5, 6] # ndarray를 사용 전, 리스트를 먼저 활용
>>> print(a)
>>> b = [[1, 2, 3], [4, 5, 6]] # 리스트로 2차원 행렬을 표현
>>> print(b)
>>> c = [1, 'a', 3.5] # 리스트는 서로 다른 type의 데이터 저장이 가능하다.
>>> print(c)

[1, 2, 3, 4, 5, 6]
[[1, 2, 3], [4, 5, 6]]
[1, 'a', 3.5]
```

* ndarray는 array 함수와 중첩된 리스트(list)를 이용하여 생성할 수 있으며, [ ]를 이용하여 indexing 한다.

  ```python
  >>> a = np.array([1, 2, 3])  # 1차원 배열 생성
  >>> print(type(a), a.shape, a[0], a[1], a[2])
  >>> a[0] = 5                 # 배열의 한 원소를 변경
  >>> print(a)
  <class 'numpy.ndarray'> (3,) 1 2 3
  [5 2 3]
  
  >>> b = np.array([[1,2,3],[4,5,6]])   # 2차원 배열 생성
  >>> print(b) #2차원 배열의 모양을 확인
  [[1 2 3]
   [4 5 6]]
  
  >>> print(b.shape) #배열의 각 차원의 크기
  >>> print(b[0, 0], b[0, 1], b[1, 0]) #인덱싱 예제
  (2, 3)
  1 2 4
  ```

* Numpy는 array 함수 외에도 배열을 생성하기 위한 다양한 방법을 제공한다.

  * `np.zero`
    * [documentation](https://numpy.org/doc/stable/reference/generated/numpy.zeros.html)
  * 값이 모두 0인 배열을 생성하고, 매개변수는 원하는 shape를 입력
  
  ```python
  >>> a = np.zeros((2, 3)) 
  >>> print(a)
  [[0. 0. 0.]
   [0. 0. 0.]]
  ```
  
    * `np.ones`
    * [documentation](https://numpy.org/doc/stable/reference/generated/numpy.ones.html)
      * 값이 모두 1인 배열을 생성하고, 매개변수는 원하는 shape를 입력
  
  ```python
  >>> b = np.ones((3, 4))
  >>> print(b)
  [[1. 1. 1. 1.]
  [1. 1. 1. 1.]
  [1. 1. 1. 1.]]
  ```
  * `np.full`
  * [documentation](https://numpy.org/doc/stable/reference/generated/numpy.full.html)
    * 모든 원소가 원하는 값으로 초기화된 배열을 생성한다.
    * parameter : shape, fill_value

  ```python
  >>> c = np.full((2, 4), 7)
  >>> print(c)
[[7 7 7 7]
   [7 7 7 7]]
  ```

  * `np.eye`
    * [documentation](https://numpy.org/doc/stable/reference/generated/numpy.eye.html)
    * 단위행렬(identity matrix)를 생성

  ```python
  # 4*4 단위행렬 생성
  >>> d = np.eye(4)
  >>> print(d)
  [[1. 0. 0. 0.]
 [0. 1. 0. 0.]
   [0. 0. 1. 0.]
   [0. 0. 0. 1.]]
  ```

  * `np.random`
    * [documentation](https://numpy.org/doc/stable/reference/random/index.html)
    * 무작위로 이루어진 배열 생성

  ```python
  # 2*4 shape의 무작위값으로 이루어진 배열을 생성
>>> e = np.random.random((2,4)) 
  >>> print(e)
  [[0.47499658 0.85360648 0.20457603 0.04586848]
   [0.69493161 0.12224876 0.51118801 0.07780861]]
  ```

  

