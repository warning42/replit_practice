# 자료형
파이썬의 자료형은 기본 자료형뿐만 아니라, 사전 자료형, 집합 자료형 등 다양한 자료형을 기본으로 내장하고 있어서 편리하다.

---
## 수 자료형(Number Datatype)
### 정수형(integer)
- 양의 정수
- 음의 정수
- 0


```python
a = 1000 # 양의 정수
a = -1   # 음의 정수
a = 0    # 0
```

### 실수형(Real Number)
- 소수점 아래의 데이터를 포함하는 수 자료형
- e나 E를 이용해서도 표현 가능
  - 1e9 : 10의 9제곱


```python
a = 157.93  # 양의 실수
a = -157.93 # 음의 실수
a = 5.      # 소수부가 0일 때 0을 생략
a = -.7     # 정수부가 0일 때 0을 생략
a = 1e9     # 10억의 지수 표현 방식
a = 75.25e1 # 752.5
a = 3954e-3 # 3.954
```

컴퓨터 시스템은 실수를 처리할 때 부동 소수점(floating-point) 방식을 이용한다.

실수형에는 4바이트 혹은 8바이트의 고정된 메모리를 할당한다.

또한 2진수로 데이터를 처리하므로 10진수처럼 소수점이 정확히 떨어지지 않고, 0.3 + 0.6이면 0.8999999처럼 저장된다. 이 떄는 round() 함수를 써서 반올림 해주는 것이 좋다.


```python
# round(실수형데이터, 반올림하고자 하는 위치-1)
a = 0.3 + 0.6
print(a)           # 0.899999999
print(round(a,4))  # 0.9 -> 소수점 5번째 자리에서 반올림
```

    0.8999999999999999
    0.9
    

### 수자료형의 연산
- 사칙연산(+, -, /, *)
- 나머지연산자(%), 몫연산자(//)
- 거듭제곱연산자(**)


```python
a, b = 7, 3

a / b     # 2.3333..  (나누기)
a % b     # 1  (나머지)
a // b    # 2  (몫)
a ** b    # 343 (거듭제곱, a^b)

print(a / b)
print(a % b)
print(a // b)
print(a ** b)
```

    2.3333333333333335
    1
    2
    343
    

---

## 리스트 자료형
- 파이썬의 리스트 자료형은 내부적으로 연결 리스트 자료구조를 채택하고 있어서 append(), remove() 등의 메서드를 지원한다.
- 리스트 대신에 배열 혹은 테이블이라고도 부른다.

### 리스트 만들기
- 대괄호 [] 안에 원소를 넣어 초기화하고, 쉼표(,)로 원소를 구분한다.


```python
a = [1, 2, 3, 4, 5]
print(a)      # [1, 2, 3, 4, 5]
print(a[4])   # 5

a = list()  # 빈리스트 선언 1
a = []      # 빈리스트 선언 2
```

    [1, 2, 3, 4, 5]
    5
    

- 크기가 N이고 모든 값이 0인 1차원 리스트는 다음과 같이 초기화한다.


```python
n = 5
a = [0] * n  # [0, 0, 0, 0, 0]
print(a)
```

    [0, 0, 0, 0, 0]
    


### 리스트의 인덱싱과 슬라이싱
- 인덱싱 : 인덱스를 입력하여 특정한 원소에 접근하는 것
- 슬라이싱 : 연속적인 위치를 갖는 원소들을 가져오는 것


```python
a = [1, 2, 3, 4, 5]

# 인덱싱
print(a[1])   # 2
print(a[-1])  # 5

# 슬라이싱
print(a[0:2])  # [1, 2]  슬라이싱의 마지막 숫자는 포함 안함
```

    2
    5
    [1, 2]
    

### 리스트 컴프리헨션
- 리스트를 초기화하는 방법 중 하나
- 대괄호 안에 조건문과 반복문을 넣는 방식으로 리스트를 초기화할 수 있다.


```python
# 0부터 9까지 수 중 홀수만 포함하는 리스트
array = [i for i in range(10) if i % 2 == 1]
print(array)   # [1, 3, 5, 7, 9]

# 1부터 9까지의 수의 제곱 값을 포함하는 리스트
array = [i * i for i in range(1,10)]
print(array)
```

    [1, 3, 5, 7, 9]
    [1, 4, 9, 16, 25, 36, 49, 64, 81]
    

- 컴프리헨션은 2차원 리스트를 초기화할 때 매우 효과적으로 이용된다. N x M 크기의 2차원 리스트를 초기화하는 것은 다음과 같다.


```python
n = 2
m = 3
array = [[0] * m for _ in range(n)]
print(array)  # [[0, 0, 0],[0, 0, 0]]

# 언더바(_)는 반복문에서 대입하여 사용할 인수가 없을 시 사용
```

    [[0, 0, 0], [0, 0, 0]]
    

- 특정 크기의 2차원 리스트를 초기화할 때는 반드시 리스트 컴프리헨션을 이용해야 한다. (각각의 행들이 서로 같은 참조를 하지 않게 하기 위함))

### 리스트 관련 기타 메서드
- 변수명.append() : 리스트 맨 끝에 원소 삽입, 시간 복잡도 O(1)
- 변수명.sort(), 변수명.sort(reverse=True) : 오름차순, 내림차순(reverse=True)로 정렬, 시간 복잡도 O(NlogN)
- 변수명.reverse() : 원소의 순서를 뒤집음, 시간 복잡도 O(N)
- 변수명.insert(삽입할 위치 인덱스, 삽입할 값) : 특정 인덱스에 값 삽입(기존에 있던 값은 뒤로 밀림), 시간 복잡도 O(N)
  - insert()는 원소 삽입뿐 아니라 원소 위치 조정도 해야해서 append()에 비해 시간복잡도가 append()에 비해 크다. 따라서 남발하면 시간 초과가 될 수 있다.

- 변수명.count(특정값) : 특정값을 갖는 원소 개수 카운트, 시간 복잡도 O(N)
- 변수명.remove(특정값) : 특정값을 갖는 원소 중 1개를 제거, 시간 복잡도 O(N)
  - 파이썬은 remove() 외에 특정값을 가지는 모든 원소를 제거하기 위한 함수가 없으므로 다음과 같이 작성해야 한다.



```python
a = [1, 2, 3, 4]
remove_set = [2, 3]

# remove_set에 포함되지 않은 값만 저장 (a의 원소를 하나씩 확인)
result = [i for i in a if i not in remove_set]
print(result)   # [1, 4]
```

    [1, 4]
    

----

## 문자열 자료형

### 문자열 초기화
- 문자열 변수 초기화는 큰따옴표("), 작은따옴표(')를 이용.
- 큰따옴표 안에 작은따옴표, 작은따옴표 안에 큰따옴표, 백슬래시(\)를 사용하면 따옴표 내부에 다른 따옴표를 표시할 수 있다.

### 문자열 연산
- 파이썬은 문자열에 대한 연산도 지원한다.


```python
a = "Hello"
b = "World"
print(a + " " + b)  # Hello World

print(a * 3)  # HelloHelloHello

print(a[1:4])  # ell
```

    Hello World
    HelloHelloHello
    ell
    

----

## 튜플 자료형
- 튜플은 값 변경이 불가능하다.
- () 소괄호로 정의한다.
- 값 변경이 불가능한 특성을 그래프 알고리즘을 구현할 때 자주 사용한다.
  - 다익스트라 최단 경로 알고리즘 등에서 우선순위 큐를 이용할 때 튜플을 쓰면 큐에 들어간 값을 변하지 않게 할 수 있다.
  - 다익스트라에서는 '비용'과 '노드 번호'라는 다른 특성의 데이터를 구분하기 위해 (비용, 노드 번호)의 형태로 함께 튜플로 묶어서 주로 관리한다.
  - 또는 일부러 튜플을 사용하여 변경하면 안되는 값이 변경되는 것을 막을 수 있다.


## 사전 자료형(Dictionary Datatype)
- 키(key)와 값(value)의 쌍을 데이터로 가지는 자료형
- 변경 불가능한 데이터를 키로 사용할 수 있다. (수 자료형, 문자열 자료형, 튜플 자료형)
- 파이썬의 사전 자료형은 내부적으로 '해시 테이블'을 이용하므로 기본적으로 데이터의 검색 및 수정에 있어서 O(1)의 시간에 처리할 수 있다. 리스트보다 훨씬 빠르게 동작한다는 점을 알아두자.


```python
data = dict()
data['사과'] = 'Apple'
data['바나나'] = 'Banana'
data['코코넛'] = 'Coconut'

print(data)
```

    {'사과': 'Apple', '바나나': 'Banana', '코코넛': 'Coconut'}
    

- in 연산자를 이용하여(iterable 자료형에 사용 가능), 사전 안의 특정 원소를 찾을 수 있다.
- iterable 자료형이란 리스트, 튜플 같이 순차적인 정보를 담고 있는 자료형을 말한다.



```python
# '원소 in 사전' 형태로 특정 원소를 찾을 수 있음
if '사과' in data:
  print("True")  # True - 사과가 dict 안에 있음
else:
  print("False")  # False - 사과가 dict 안에 없음
```

    True
    

- 사전의 키와 값을 별도로 뽑기 위한 함수가 존재한다.
- keys() 함수 : 키 데이터만 뽑아 리스트로 이용
- values() 함수 : 값 데이터만 뽑아 리스트로 이용


```python
key_list = data.keys()
value_list = data.values()

print(key_list) # dict_key(['사과', '바나나', '코코넛'])
print(value_list) # dict_values(['Apple', 'Banana', 'Coconut'])

for key in key_list:
  print(data[key])
```

    dict_keys(['사과', '바나나', '코코넛'])
    dict_values(['Apple', 'Banana', 'Coconut'])
    Apple
    Banana
    Coconut
    

----

## 집합자료형

### 집합 자료형 소개
- 파이썬에서는 집합(set)을 처리하기 위한 집합 자료형을 제공한다.
- 집합은 기본적으로 리스트 혹은 문자열을 이용해서 만들고 다음의 특징을 가진다.
 - 중복을 허용하지 않는다.
 - 순서가 없다.
- 사전 자료형과 마찬가지로 집합 자료형 또한 순서가 없어서 인덱싱, 슬라이싱은 사용 불가능하다.
- 집합 자료형은 키도 존재하지 않으며, 단순히 값 데이터만 담는다. 특정 원소가 존재하는지를 검사하는 연산의 시간 복잡도는 사전 자료형과 마찬가지로 O(1)이다.
- '특정한 데이터가 이미 등장한 적이 있는지 여부'를 체크할 때 매우 효과적이다.
- 집합 자료형을 초기화할 때 set() 함수를 쓰거나, 중괄호({}) 안에 각 원소를 콤마(,)를 기준으로 구분해서 넣으면 된다.


```python
# 집합 자료형 초기화 방법 1
data = set([1, 1, 2, 3, 4])
print(data)

# 초기화 방법 2
data = {1, 1, 2, 3, 4}
print(data)
```

    {1, 2, 3, 4}
    {1, 2, 3, 4}
    

### 집합 자료형 연산
- 기본적인 집합 연산으로는 합집합, 교집합, 차집합 연산이 있다.
- 합집합 : ('|')
- 교집합 : ('&')
- 차집합 : ('-')


```python
a = {1, 2, 3, 4, 5}
b = {1, 3, 5, 7, 9}

print(a | b) # 합집합
print(a & b) # 교집합
print(a - b) # 차집합
```

    {1, 2, 3, 4, 5, 7, 9}
    {1, 3, 5}
    {2, 4}
    

### 집합 자료형 관련 함수
- add() : 하나의 집합 데이터에 값을 추가할 때
- update() : 여러 개의 값을 한꺼번에 추가하고자할 때
- remove() : 특정한 값을 제거할 때
- add(), remove() 함수는 모두 시간 복잡도가 O(1)이다.


```python
data = {1, 2, 3}
print(data)

# 원소 추가
data.add(4)
print(data)

# 원소 여러 개 추가
data.update([5,6])
print(data)

# 특정 원소 삭제
data.remove(3)
print(data)
```

    {1, 2, 3}
    {1, 2, 3, 4}
    {1, 2, 3, 4, 5, 6}
    {1, 2, 4, 5, 6}
    
