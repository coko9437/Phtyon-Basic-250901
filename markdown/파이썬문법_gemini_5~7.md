## 📚 파이썬 학습 노트

### 📚 파트 3: Collections 모듈

#### **1. deque 모듈**

📌 **설명**
`deque` 모듈은 스택(Stack)과 큐(Queue)의 기능을 모두 지원하는 자료구조입니다.
양쪽 끝에서 데이터를 추가하거나 삭제하는 작업에 효율적입니다.

✅ **왜 사용할까?**
일반 리스트는 한쪽 끝에서만 빠르게 데이터를 추가하거나 삭제할 수 있지만, 
`deque`는 양쪽 끝에서 모두 효율적인 작업을 지원합니다.

💡 **주 용도**

  * **스택:** `append()`와 `pop()` 함수를 사용하여 'Last In, First Out(LIFO)' 구조를 구현합니다
  * 
  * **큐:** `appendleft()`와 `pop()` 함수를 사용하여 'First In, First Out(FIFO)' 구조를 구현합니다
  * 
  * **회전 기능:** `rotate()` 함수를 사용하여 요소들의 순서를 회전시킬 수 있습니다.
  * 이는 연결 리스트의 특성을 활용한 기능입니다

🧑‍💻 **예제 코드**

```python
from collections import deque

# deque 객체 생성
dq = deque()

# 스택처럼 사용 (LIFO)
dq.append(1)
dq.append(2)
print(f"현재 deque: {dq}")
print(f"pop 결과: {dq.pop()}")  # 2 출력

# 큐처럼 사용 (FIFO)
dq.appendleft(0)
print(f"현재 deque: {dq}")
print(f"pop 결과: {dq.pop()}")  # 1 출력
```

📝 **심화, 응용 문제**

1.  `deque` 객체를 사용하여 `[1, 2, 3, 4, 5]`를 `[3, 4, 5, 1, 2]`로 회전시키는 코드를 작성하세요.
2.  `deque`의 `extend()`와 `extendleft()` 함수를 사용하여 `[1, 2]`와 `[3, 4]`를 각각 오른쪽에 추가하고 왼쪽에 추가하는 코드를 작성하세요.

<!-- end list -->

  * **사용할 함수 및 방법:**
      * `deque()`: `collections` 모듈에서 가져와 객체를 생성합니다.
      * `append()`: 오른쪽에 요소를 추가합니다.
      * `appendleft()`: 왼쪽에 요소를 추가합니다.
      * `pop()`: 오른쪽에서 요소를 꺼냅니다.
      * `popleft()`: 왼쪽에서 요소를 꺼냅니다.
      * `rotate(n)`: `n`만큼 회전합니다. 양수는 오른쪽, 음수는 왼쪽입니다.
      * `extend()`: iterable 객체를 오른쪽에 추가합니다.
      * `extendleft()`: iterable 객체를 왼쪽에 추가합니다.

-----

#### **2. Counter 모듈**

📌 **설명**
`Counter` 모듈은 시퀀스 자료형(리스트, 문자열 등)의 요소 개수를 세어 딕셔너리 형태로 반환하는 자료구조입니다.

✅ **왜 사용할까?**
 리스트나 문자열에서 특정 요소의 빈도수를 효율적으로 계산할 때 사용합니다.

💡 **주 용도**

  *  **빈도수 계산:** 텍스트에서 각 단어 또는 문자의 빈도수를 쉽게 계산합니다.
  *  **딕셔너리처럼 사용:** 키를 이용해 특정 요소의 개수를 바로 확인할 수 있습니다.

🧑‍💻 **예제 코드**

```python
from collections import Counter

# 리스트의 요소 개수 세기
my_list = ['A', 'B', 'A', 'C', 'B', 'A']
count = Counter(my_list)
print(f"리스트의 빈도수: {count}") # Counter({'A': 3, 'B': 2, 'C': 1})

# 문자열의 요소 개수 세기
my_string = "hello world"
string_count = Counter(my_string)
print(f"문자열의 빈도수: {string_count}") # Counter({'l': 3, 'o': 2, 'h': 1, 'e': 1, ' ': 1, 'w': 1, 'r': 1, 'd': 1})
```

📝 **심화, 응용 문제**

1.  주어진 문장 `'This is a python study guide for python programmers'`에서 가장 많이 등장한 단어 3개를 찾아 출력하세요.
2.  두 개의 `Counter` 객체 `c1 = Counter('apple')`와 `c2 = Counter('banana')`를 합쳐서 총 개수를 구하는 코드를 작성하세요.
3.  딕셔너리 `d = {'a': 10, 'b': 20, 'c': 5}`에서 `Counter` 객체를 생성하고, 가장 적은 값 2개를 출력하는 코드를 작성하세요.

<!-- end list -->

  * **사용할 함수 및 방법:**
      * `Counter()`: `collections` 모듈에서 가져와 객체를 생성합니다.
      * `most_common(n)`: 가장 빈도수가 높은 `n`개의 요소를 반환합니다.
      *  `+` 연산자: 두 `Counter` 객체의 요소를 합칩니다[cite: 86].
      * `-` 연산자: 두 `Counter` 객체의 요소를 뺍니다.
      *  `&` 연산자: 교집합을 구합니다[cite: 86].
      *  `|` 연산자: 합집합을 구합니다[cite: 87].
      *  `Counter()`: 딕셔너리를 입력받아 객체를 생성할 수 있습니다[cite: 82].
      * `most_common(-n)`: 가장 빈도수가 적은 `n`개의 요소를 반환합니다.

-----


### 🐍 파트 4: 객체 지향 프로그래밍

#### **1. 객체와 클래스**

📌 **설명**
\*\*객체 지향 프로그래밍(OOP)\*\*은 실생활의 사물을 본떠 코드를 작성하는 프로그래밍 기법입니다.  
객체는 실제 존재하는 사물이나 개념을 뜻하며, **클래스**는 이 객체를 만들기 위한 설계도입니다.
클래스로부터 만들어진 객체를 **인스턴스**라고 부릅니다.

💡 **주 용도**

  * **재사용성 증가:** 한 번 만든 클래스를 여러 곳에서 재사용할 수 있어 코드의 효율을 높입니다.
  * **모듈화:** 코드를 기능별로 분리하여 유지보수 및 관리가 용이합니다.
  *  **데이터와 기능 결합:** 객체의 \*\*속성(attribute)\*\*과 \*\*행동(method)\*\*을 한데 묶어 관리합니다

🧑‍💻 **예제 코드**

```python
# 클래스 선언 템플릿
class SoccerPlayer(object):
    pass
```

**✅ 클래스 구현하기: 속성**
 객체의 속성을 정의하기 위해 `__init__()` 함수를 사용합니다. 이 함수의 첫 번째 매개변수로는 반드시 **self**를 사용해야 하며, `self`는 생성된 인스턴스에 접근하는 예약어입니다.

```python
# SoccerPlayer 클래스에 속성 정의
class SoccerPlayer:
    def __init__(self, name, position, back_number):
        self.name = name
        self.position = position
        self.back_number = back_number

# 인스턴스 생성
jinhyun = SoccerPlayer("Jinhyun", "MF", 10)
print(f"선수 이름: {jinhyun.name}")
print(f"등번호: {jinhyun.back_number}")
```

**✅ 클래스 구현하기: 함수(메서드)**
 클래스 내부에 정의된 함수를 \*\*메서드(method)\*\*라고 합니다
메서드도 `self`를 첫 번째 매개변수로 받아야 인스턴스가 사용할 수 있습니다.

```python
# change_back_number 메서드 추가
class SoccerPlayer:
    def __init__(self, name, position, back_number):
        self.name = name
        self.position = position
        self.back_number = back_number

    def change_back_number(self, new_number):
        print(f"선수의 등번호를 {self.back_number}에서 {new_number}로 변경합니다.")
        self.back_number = new_number

# 인스턴스 사용
jinhyun.change_back_number(5)
print(f"변경 후 등번호: {jinhyun.back_number}")
```

-----

#### **2. 상속**

📌 **설명**
 \*\*상속(Inheritance)\*\*은 부모 클래스의 속성과 메서드를 자식 클래스가 물려받아 사용하는 개념입니다.
부모 클래스에는 일반적인 기능을, 자식 클래스에는 더 상세하고 구체적인 기능을 구현하여 코드의 재사용성을 높일 수 있습니다


✅ **부모 클래스 메서드 재정의**
 부모 클래스의 메서드를 자식 클래스에서 필요에 맞게 다시 정의하는 것을 \*\*오버라이딩(overriding)\*\*이라고 합니다

-----

### 📚 파트 5: 파이썬 데이터 분석 라이브러리

#### **1. 개요: NumPy, Pandas, Matplotlib**

📌 **설명**
파이썬의 주요 데이터 분석 라이브러리는 다음과 같습니다.

  *  **넘파이(NumPy):** 벡터 및 행렬 연산에 특화된 라이브러리입니다
  * 
  *  **판다스(Pandas):** `Series`와 `DataFrame` 자료구조를 활용해 대량의 데이터를 빠르고 효율적으로 처리합니다
  * 
  *  **맷플롯립(Matplotlib):** 데이터 분석 결과를 시각화하는 데 사용됩니다

-----

#### **2. NumPy**

📌 **설명**
 NumPy는 다차원 배열인 \*\*`array`\*\*를 사용하여 수치 계산을 효율적으로 처리합니다.
리스트보다 빠르고 메모리 사용이 적다는 장점이 있습니다.

🧑‍💻 **예제 코드: NumPy 배열 생성**

```python
import numpy as np

# 1차원 배열 생성
data_1d = np.array([1, 2, 3, 4])
print(f"1차원 배열: {data_1d}")

# 2차원 배열 생성 (리스트의 리스트로 만듦)
data_2d = np.array([[1, 2], [3, 4]])
print(f"2차원 배열:\n{data_2d}")
```

**✅ 배열 슬라이싱 및 연산**
 NumPy 배열은 리스트와 유사하게 슬라이싱을 지원하며, 
배열 전체에 대한 사칙연산, 평균, 합계 등의 다양한 연산을 제공합니다

```python
# 슬라이싱 예제
arr = np.array([[1, 2, 3], [4, 5, 6]])
print(f"두 번째 열 전체: {arr[:, 1]}")

# 연산 예제
arr2 = np.array([1, 2, 3, 4, 5, 6])
print(f"배열의 평균: {arr2.mean()}")
print(f"배열의 합계: {arr2.sum()}")
```

-----

#### **3. Pandas**

📌 **설명**
 Pandas는 \*\*`Series`\*\*와 \*\*`DataFrame`\*\*이라는 두 가지 핵심 자료구조를 제공합니다

  *  **`Series`:** 1차원 배열로, 하나의 열과 인덱스로 구성됩니다
  *  **`DataFrame`:** 2차원 배열로, 여러 개의 행과 열로 구성된 표 형태의 데이터입니다

🧑‍💻 **예제 코드**

```python
import pandas as pd
import numpy as np

# Series 생성
data = np.random.rand(5)
seri = pd.Series(data)
print(f"Series 객체:\n{seri}")

# DataFrame 생성
data_set = np.random.rand(5, 3)
df = pd.DataFrame(data_set, columns=["A", "B", "C"])
print(f"DataFrame 객체:\n{df}")
```