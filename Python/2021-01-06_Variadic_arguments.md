# 가변 인수

### 가변길이 인수(Variadic Arguments)

* 함수 호출 시 함수 정의문의 형식 인수 개수만큼 실인수를 전달해야 함. 

* 예를 들어, 두 변수를 더하는 `add(x, y)`라는 함수가 있을 때 이는 두 개의 인수를 요구하므로 두 인수 모두 넘겨야 한다.

* 하나만 전달하거나 세 개를 전달하면 에러 처리된다.

  ```python
  >>> def add(x, y):
  >>>     return x+y
  # 인수 2개를 넘겨야 함.
  >>> print(add(2, 3))
  5
  # 인수를 1개만 넘긴 경우
  >>> add(1)
  Traceback (most recent call last):
    File "<input>", line 1, in <module>
  TypeError: add() missing 1 required positional argument: 'y'
  ```

  * 이처럼 `add()` 함수는 인수 2개를 모두 전달해야 제대로 동작함.
  * 일반적인 함수는 정의문에 필요한 인수의 개수가 명시되어 있고, 호출할 때 이 개수에 맞게 실인수를 넘겨야 함.
  * 하지만, **가변인수**는 임의 개수의 인수를 받음. 인수 이름 앞에 **\***기호를 붙이면 이 자리에 여러 개의 인수가 올 수 있다.

#### 가변 인수

* arguments의 약자로 인수 값을 받는다.

* `*args`대신에 다른 이름 사용이 가능함.

  ```python
  >>> def test_args(*args):
  >>>     print(type(args))
  >>> test_args(1, 2, 3, 4, 5)
  <class 'tuple'>
  ```

  * 파이썬은 호출문에 나타난 실인수를 튜플로 묶어 전달한다. 얼마든지 많은 정수가 튜플로 포장되어 `args`에 전달되고, 함수는 튜플의 요소를 꺼내 작업을 수행한다.
  * 가변 인수는 이후의 모든 인수를 다 포함하기 때문에, **인수 목록의 마지막에 와야 한다.** 가변 인수 앞에는 일반 인수가 올 수 있지만, 뒤쪽에는 올 수 없다. 가변 인수 뒤에 일반 인수가 더 있으면, 어디까지가 가변 인수인지 잘 구분되지 않기 때문이다.

  ```python
  >>> def order_coffee(coffee, *options):
  >>>     print(coffee + ', 옵션 : ', end=' ')
  >>>     for opt in options:
  >>>         print(opt, end=' ')
  >>>     print()
  
  # 가변 인수를 앞에 작성하는 경우
  >>> order_coffee('Tall', coffee='아메리카노')
  Traceback (most recent call last):
    File "<input>", line 1, in <module>
  TypeError: order_coffee() got multiple values for argument 'coffee'
      
  # 가변 인수를 생략한 경우    
  >>> order_coffee('아메리카노')
  아메리카노, 옵션 :  
      
  # 가변 인수에 두 개의 인수를 넣은 경우
  >>> order_coffee('아메리카노', 'Tall', 'Ice')
  아메리카노, 옵션 :  Tall Ice 
  ```

* **위치 인수(Positional Argument)**
  * 순서대로 인수를 전달하는 방식으로, 호출문이 짧고 간단하지만 인수의 수가 많아지면 헷갈리게 된다.(등장 순서대로 형식 인수와 대응되며, 정확하게 호출하려면 순서와 의미를 숙지해야 하기 때문에)

* **키워드 인수(Keyword Argument)**
  * 순서와 무관하게 인수를 전달할 수 있도록 인수의 이름을 지정하여 대입 형식으로 전달하는 방식으로, 이름으로 인수를 구분 가능하기 때문에 순서가 바뀌어도 상관 없다.

#### 키워드 가변 인수

* 키워드 인수를 가변 개수로 전달할 때는 인수 목록에 `**` 기호를 붙인다. 호출원에서 여러 개의 키워드 인수를 전달하면, 인수의 이름과 값의 쌍을 사전으로 만들어 전달한다. 함수 내부에서는 사전을 읽듯이 인수값을 꺼내 사용한다.

  ```python
  >>> def show_keywords(**kwargs):
  >>>     print('-----------------')
  >>>     for key in kwargs.keys():
  >>>         print(key, end=' ')
  >>>     print('\n')
  >>> 
  >>>     for value in kwargs.values():
  >>>         print(value, end=' ')
  >>>     print('\n')
  >>> 
  >>>     for item in kwargs.items():
  >>>         print(item, end=' ')
  
  # key=value로 전달
  >>> show_keywords(id='sun',
  >>>               name='kim',
  >>>               phone='010-1234-1234')
  
  -----------------
  id name phone 
  sun kim 010-1234-1234 
  ('id', 'sun') ('name', 'kim') ('phone', '010-1234-1234') 
  ```

  * 키워드 인수만 받겠다고 선언되어 있는 경우(`show_keywords`와 같은 함수) 키워드 인수만 넘겨야 한다. 예를 들어 `show_keywords(3, 2, 5)`와 같이 위치 인수를 넘기면 에러 처리된다.
  * 또한 keyword로 숫자는 불가능 하다.

  ```python
  # 위치 인수를 넘기는 경우
  >>> show_keywords(3, 2, 5)
  Traceback (most recent call last):
    File "<input>", line 1, in <module>
  TypeError: show_keywords() takes 0 positional arguments but 3 were given
      
  # keywords로 숫자를 작성한 경우
  >>> show_keywards(1=2, 2=3, 3=4)
    File "<input>", line 1
  SyntaxError: expression cannot contain assignment, perhaps you meant "=="?
  ```

  