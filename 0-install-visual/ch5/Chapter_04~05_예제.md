
---

## 🐍 파이썬 문법 모음집 (Chapter 04 ~ 05)

### Chapter 04: 자료구조 (Data Structures)

자료구조는 데이터를 효율적으로 저장하고 관리하기 위한 방법입니다. 파이썬은 리스트, 튜플, 세트, 딕셔너리 등 강력하고 사용하기 쉬운 내장 자료구조를 제공합니다.

#### 1. 스택 (Stack)과 큐 (Queue) - 리스트 활용

-   **스택 (Stack)**: LIFO (Last-In, First-Out). 마지막에 들어온 데이터가 가장 먼저 나가는 구조.
-   **큐 (Queue)**: FIFO (First-In, First-Out). 먼저 들어온 데이터가 가장 먼저 나가는 구조.

파이썬의 기본 `list`를 사용하여 스택과 큐의 동작을 흉내 낼 수 있습니다.

```python
# 파일명: stack_with_list.py

# 사용자로부터 문자열을 입력받습니다.
word = input("역순으로 만들 문자열을 입력해주세요: ")

# 입력받은 문자열을 글자 하나하나가 요소인 리스트로 변환합니다.
# 예: "abc" -> ['a', 'b', 'c']
word_list = list(word)
print(f"변환된 리스트: {word_list}")

# 결과를 임시로 저장할 빈 리스트를 생성합니다.
result = []

# word_list의 길이만큼 반복합니다.
for _ in range(len(word_list)):
    # list.pop(): 리스트의 *마지막* 요소를 꺼내고 리스트에서 제거합니다. (스택의 pop 동작)
    # list.pop(0): 리스트의 *첫 번째* 요소를 꺼냅니다. (큐의 dequeue 동작)
    # 여기서는 스택처럼 사용하기 위해 pop()을 사용합니다.
    popped_item = word_list.pop()
    result.append(popped_item)

# pop()을 반복하여 result 리스트에는 원래 리스트의 역순이 담기게 됩니다.
print(f"스택 원리를 이용한 역순 결과: {result}")

# join()을 사용해 리스트를 다시 문자열로 합칩니다.
print(f"역순 문자열: {''.join(result)}")

# [참고] 파이썬 슬라이싱을 이용하면 훨씬 간단하게 문자열을 뒤집을 수 있습니다.
print(f"슬라이싱을 이용한 역순: {word[::-1]}")
```

#### 2. 튜플 (Tuple)

튜플은 리스트와 거의 동일하지만, 한 번 생성되면 그 **값을 변경할 수 없는(immutable)** 특징을 가집니다.

```python
# 파일명: tuple_basics.py

# 리스트는 생성 후에도 요소의 값을 변경할 수 있습니다 (mutable).
mutable_list = [1, 2, 3]
mutable_list[0] = 100
print(f"변경된 리스트: {mutable_list}")

# 튜플은 소괄호 ()를 사용하여 생성합니다.
# 생성된 후에는 요소의 값을 변경하려고 하면 TypeError가 발생합니다.
immutable_tuple = (1, 2, 3)
print(f"원본 튜플: {immutable_tuple}")

try:
    immutable_tuple[0] = 100
except TypeError as e:
    print(f"튜플 변경 시도 시 오류: {e}")
```

#### 3. 세트 (Set)

세트는 **중복을 허용하지 않고**, **순서가 없는** 값들의 모음입니다. 집합 연산에 매우 유용합니다.

```python
# 파일명: set_basics.py

# 1. 중복 제거
# 리스트를 세트로 변환하면 중복된 요소가 자동으로 제거됩니다.
my_list = [1, 1, 2, 2, 3, 3, 4, 5]
my_set = set(my_list)
print(f"리스트: {my_list}")
print(f"세트 (중복 제거됨): {my_set}")
print(f"세트의 타입: {type(my_set)}")

# 2. 자료형 변환
# 세트, 리스트, 튜플은 서로 자유롭게 변환할 수 있습니다.
unique_list = list(my_set)
print(f"세트 -> 리스트: {unique_list}, 타입: {type(unique_list)}")

unique_tuple = tuple(unique_list)
print(f"리스트 -> 튜플: {unique_tuple}, 타입: {type(unique_tuple)}")
```

#### 4. 딕셔너리 (Dictionary)

딕셔너리는 **키(Key)와 값(Value)**을 한 쌍으로 묶어 저장하는 자료구조입니다. 순서가 없으며, 키를 통해 값을 매우 빠르게 찾을 수 있습니다.

```python
# 파일명: dictionary_basics.py

# 딕셔너리 생성: {키1: 값1, 키2: 값2, ...}
my_dict = {"name": "홍길동", "age": 30, "skills": ["Python", "JavaScript"]}

# 값 접근: 딕셔너리[키]
print(f"이름: {my_dict['name']}")
print(f"기술: {my_dict['skills']}")

# 값 변경 및 추가
my_dict['age'] = 31 # 기존 키의 값 변경
my_dict['city'] = "서울" # 새로운 키-값 쌍 추가
print(f"수정된 딕셔너리: {my_dict}")

# 주요 메서드
print(f"모든 키: {my_dict.keys()}")
print(f"모든 값: {my_dict.values()}")
print(f"모든 (키, 값) 쌍: {my_dict.items()}")

# .items()와 for 루프를 함께 사용 (매우 일반적인 패턴)
print("\n--- 딕셔너리 순회 ---")
for key, value in my_dict.items():
    print(f"키: {key}, 값: {value}")
```

#### 5. `collections` 모듈의 확장 자료구조

파이썬의 기본 자료구조를 더욱 강력하게 만들어주는 `collections` 모듈의 유용한 클래스들입니다.

##### ◦ `deque` (Double-ended Queue)

`deque`는 양쪽 끝(double-ended)에서 데이터를 빠르고 효율적으로 추가하거나 삭제할 수 있는 큐(queue) 자료구조입니다.

-   **장점**: 양쪽 끝에서의 데이터 처리가 매우 빠릅니다. (시간 복잡도 O(1))
-   **단점**: 중간에 있는 데이터에 접근하는 것은 리스트보다 느립니다.
-   **주요 메서드**:
    -   `append(item)`: 오른쪽에 추가
    -   `appendleft(item)`: 왼쪽에 추가
    -   `pop()`: 오른쪽에서 제거
    -   `popleft()`: 왼쪽에서 제거
    -   `rotate(n)`: 요소를 n칸씩 회전

```python
# 파일명: deque_example.py
from collections import deque

# deque 생성
d = deque()

# 0부터 4까지 오른쪽에 추가 (append)
for i in range(5):
    d.append(i)
print(f"append 후: {d}") # deque([0, 1, 2, 3, 4])

# 오른쪽에서 2개 제거 (pop) - 스택처럼 동작
d.pop()
d.pop()
print(f"pop 후: {d}") # deque([0, 1, 2])

# 0부터 4까지 왼쪽에 추가 (appendleft)
d_left = deque()
for i in range(5):
    d_left.appendleft(i)
print(f"appendleft 후: {d_left}") # deque([4, 3, 2, 1, 0])

# 왼쪽에서 2개 제거 (popleft) - 큐처럼 동작
d_left.popleft()
d_left.popleft()
print(f"popleft 후: {d_left}") # deque([2, 1, 0])

# rotate() 기능: 요소를 회전시킴
d.rotate(1) # 오른쪽으로 1칸 회전
print(f"rotate(1) 후: {d}") # deque([2, 0, 1])
d.rotate(-1) # 왼쪽으로 1칸 회전
print(f"rotate(-1) 후: {d}") # deque([0, 1, 2])
```

##### ◦ `OrderedDict`

입력된 순서를 기억하는 딕셔너리입니다. (Python 3.7+부터는 기본 `dict`도 순서를 보장하지만, 하위 버전 호환성이나 순서 관련 명시적 기능이 필요할 때 사용됩니다.)

```python
# 파일명: ordereddict_example.py
from collections import OrderedDict

# 일반 딕셔너리 (Python 3.6 이하에서는 순서가 보장되지 않을 수 있음)
d = {}
d['b'] = 2
d['a'] = 1
d['c'] = 3
print(f"일반 딕셔너리: {d}")

# OrderedDict: 입력된 순서를 기억
od = OrderedDict()
od['b'] = 2
od['a'] = 1
od['c'] = 3
print(f"OrderedDict: {od}")

# 키를 기준으로 정렬하기
# d.items()를 키(t[0]) 기준으로 정렬한 후, 그 순서대로 OrderedDict를 새로 만듭니다.
sorted_od = OrderedDict(sorted(d.items(), key=lambda t: t[0]))
print("\n--- 키 기준 정렬 후 ---")
for k, v in sorted_od.items():
    print(f"키: {k}, 값: {v}")
```

##### ◦ `Counter`

반복 가능한(iterable) 객체 안의 요소들이 몇 번 등장하는지 개수를 세어주는 딕셔너리 형태의 클래스입니다.

-   **`most_common(n)`**: 가장 빈도수가 높은 n개의 요소를 `(요소, 횟수)` 튜플 리스트로 반환합니다.

```python
# 파일명: counter_example.py
from collections import Counter

# 1. 문자열 빈도수 세기
sentence = "파이썬 파이썬 정말 정말 정말 재미있다 파이썬 최고"
words = sentence.split() # 문장을 단어 리스트로 분리
word_counts = Counter(words)

print(f"단어 리스트: {words}")
print(f"단어 빈도수: {word_counts}")
# Counter({'정말': 3, '파이썬': 3, '재미있다': 1, '최고': 1})

# 2. 가장 흔한 단어 찾기
top_2_words = word_counts.most_common(2)
print(f"가장 흔한 단어 2개: {top_2_words}")

# 3. Counter 객체 간의 연산
store1_inventory = Counter({'사과': 5, '바나나': 10, '오렌지': 3})
store2_inventory = Counter({'사과': 3, '바나나': 5, '포도': 7})
# 두 매장의 총 재고를 합산합니다.
total_inventory = store1_inventory + store2_inventory
print(f"\n총 재고: {total_inventory}")
# Counter({'바나나': 15, '사과': 8, '포도': 7, '오렌지': 3})
```

##### ◦ `namedtuple`

**이름이 붙은 필드를 갖는 튜플(tuple)**을 만드는 팩토리 함수입니다. 인덱스와 이름으로 모두 접근할 수 있어 코드의 가독성을 크게 향상시킵니다.

```python
# 파일명: namedtuple_example.py
from collections import namedtuple

# 1. namedtuple 타입 생성
# 'Point'라는 새로운 타입을 만들고, 'x'와 'y'라는 필드 이름을 부여합니다.
Point = namedtuple('Point', ['x', 'y'])
# 필드 이름은 공백으로 구분된 문자열로도 전달 가능합니다.
Student = namedtuple('Student', 'id name email')

# 2. 객체(인스턴스) 생성
p1 = Point(10, 20)
s1 = Student(id='s001', name='홍길동', email='gildong@example.com')

# 3. 데이터 접근
# 이름으로 접근 (권장, 가독성이 높음)
print(f"점 p1의 좌표: ({p1.x}, {p1.y})")
print(f"학생 s1의 정보: ID={s1.id}, 이름={s1.name}")

# 인덱스로도 접근 가능 (일반 튜플과 동일)
print(f"점 p1의 y좌표 (인덱스): {p1[1]}")
```
//=====================================================================================

### Chapter 05: 파이썬 스타일 코딩 (Pythonic Code)

'파이써닉(Pythonic)'하다는 것은 파이썬의 철학과 고유한 기능들을 잘 활용하여 코드를 간결하고, 가독성 높으며, 효율적으로 작성하는 것을 의미합니다.

#### 1. 리스트 컴프리헨션 (List Comprehension)

한 줄의 코드로 리스트를 생성하는 매우 파이써닉한 문법입니다. 일반 `for` 루프보다 간결하고 성능도 더 좋습니다.

##### ◦ 기본 용법
```python
# 파일명: list_comprehension_basic.py

# [표현식 for 항목 in 반복_가능한_객체]

# 예시: 1부터 5까지의 숫자를 제곱한 리스트 만들기
# 일반 for문 방식
squares_loop = []
for x in range(1, 6):
    squares_loop.append(x**2)

# 리스트 컴프리헨션 방식 (더 간결하고 빠름)
squares_comp = [x**2 for x in range(1, 6)]

print(f"For 루프 결과: {squares_loop}")
print(f"리스트 컴프리헨션 결과: {squares_comp}")
```

##### ◦ 조건문(`if`) 포함
```python
# 파일명: list_comprehension_if.py

# [표현식 for 항목 in 반복_가능한_객체 if 조건문]

# 예시: 1부터 10까지의 숫자 중 짝수의 제곱만 포함하는 리스트 만들기
even_squares = [x*x for x in range(1, 11) if x % 2 == 0]

print(f"짝수의 제곱 리스트: {even_squares}")
```

##### ◦ 중첩 `for`문
```python
# 파일명: list_comprehension_nested.py

# [표현식 for 바깥항목 in 바깥리스트 for 안쪽항목 in 안쪽리스트]

# 예시: 두 리스트의 모든 조합 만들기
colors = ['빨강', '파랑']
sizes = ['S', 'M', 'L']

combinations = [(color, size) for color in colors for size in sizes]
print(f"모든 조합: {combinations}")

# 2차원 리스트를 1차원으로 펼치기 (Flattening)
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened_list = [element for row in matrix for element in row]
print(f"펼쳐진 리스트: {flattened_list}")
```

#### 2. `enumerate()`와 `zip()`

##### ◦ `enumerate()`
반복 가능한 객체를 순회할 때 **인덱스와 값**을 동시에 가져올 수 있게 해주는 내장 함수입니다.

```python
# 파일명: enumerate_zip_example.py

fruits = ["사과", "바나나", "체리"]

# 인덱스 번호와 함께 과일 이름을 출력
for index, fruit in enumerate(fruits):
    print(f"인덱스 {index}: {fruit}")

# 시작 인덱스를 1로 지정할 수도 있습니다.
for index, fruit in enumerate(fruits, start=1):
    print(f"번호 {index}: {fruit}")
```

##### ◦ `zip()`
여러 개의 반복 가능한 객체들을 받아, 각 객체의 동일한 인덱스에 있는 요소들을 하나의 튜플로 묶어줍니다.

```python
# 파일명: enumerate_zip_example.py (이어서)

names = ["철수", "영희", "민수"]
scores = [85, 90, 78]

# 이름과 점수를 짝지어 출력
for name, score in zip(names, scores):
    print(f"{name}의 점수: {score}점")

# 길이가 다를 경우, 가장 짧은 리스트를 기준으로 묶임
ids = ['id1', 'id2']
ages = [25, 30, 35]
zipped_info = list(zip(ids, ages)) # 2개의 쌍만 생성됨
print(f"길이가 다른 리스트 zip 결과: {zipped_info}")

# 묶인 데이터 다시 풀기 (Unzipping)
student_scores = [('철수', 88), ('영희', 92)]
# zip과 별표(*)를 함께 사용하면 압축을 풀 수 있습니다.
students, scores_unzipped = zip(*student_scores)
print(f"Unzip된 학생들: {students}")
print(f"Unzip된 점수들: {scores_unzipped}")
```

#### 3. 람다 (Lambda) 함수

이름이 없는 작은 **익명 함수(anonymous function)**를 만드는 방법입니다. `def`를 사용하는 일반 함수보다 간결하게 표현할 수 있어, 다른 함수의 인자로 함수를 전달할 때 유용하게 사용됩니다.

-   **문법**: `lambda 인자1, 인자2, ... : 표현식`

```python
# 파일명: lambda_example.py

# 일반 함수
def add(x, y):
    return x + y

# 람다 함수 (위 함수와 기능적으로 동일)
add_lambda = lambda x, y: x + y
print(f"일반 함수 결과: {add(3, 5)}")
print(f"람다 함수 결과: {add_lambda(3, 5)}")


# 람다 함수의 주요 활용처

# 1. map(): 리스트의 각 요소에 함수를 적용
numbers = [1, 2, 3, 4, 5]
squared_numbers = list(map(lambda x: x * x, numbers))
print(f"map과 lambda 활용: {squared_numbers}")

# 2. filter(): 조건에 맞는 요소만 걸러냄
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(f"filter와 lambda 활용: {even_numbers}")

# 3. sorted(): 정렬 기준(key)을 지정
students = [('철수', 88), ('민준', 95), ('영희', 76)]
# 점수(튜플의 두 번째 요소)를 기준으로 내림차순 정렬
sorted_by_score = sorted(students, key=lambda student: student[1], reverse=True)
print(f"sorted와 lambda 활용: {sorted_by_score}")
```