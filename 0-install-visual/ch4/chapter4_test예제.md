
### 📚 파트 4: 자료구조

#### **1. 리스트를 스택처럼 활용하여 문자열 뒤집기**

리스트의 `append()`와 `pop()` 함수를 이용해 스택(LIFO, Last In First Out) 자료구조를 흉내 내어 문자열을 역순으로 출력합니다.

```python
word = input("문자열 입력해주세요: ")
# input()으로 받은 문자열을 list() 함수로 문자 하나하나를 요소로 가지는 리스트로 변환합니다.
word_list = list(word)
print(f"word_list : {word_list}")

result = [] # 스택처럼 사용할 빈 리스트
# 문자열의 길이만큼 반복합니다.
for _ in range(len(word_list)):
  # word_list의 마지막 요소를 꺼내(pop()) result 리스트에 추가(append())합니다.
  result.append(word_list.pop())

# 스택 자료구조를 이용해 역순으로 된 리스트를 확인합니다.
print(f"result 조회 해보기 : {result}")
# 참고: 가장 간단한 문자열 뒤집기 방법은 슬라이싱입니다.
print(f"word 조회 해보기. [::-1] : {word[::-1]}")
```

#### **2. 리스트의 가변성(Mutability)**

리스트는 가변 객체이므로, 특정 인덱스의 값을 변경할 수 있습니다.

```python
a = [1,2,3]
a[0] = 100 # 인덱스 0의 값을 100으로 변경
print(a) # 결과: [100, 2, 3]
```

#### **3. 튜플의 불변성(Immutability)**

튜플은 변경할 수 없는(immutable) 객체이므로, 특정 인덱스의 값을 변경하려고 하면 오류가 발생합니다.

```python
a = (1,2,3)
# a[0] = 100 # TypeError: 'tuple' object does not support item assignment
print(a)
```

#### **4. 자료형 변환 (리스트, 세트, 튜플)**

리스트, 세트, 튜플은 서로 자유롭게 변환할 수 있습니다. 특히 `set()`은 중복된 값을 자동으로 제거합니다.

```python
a = [1,1,2,2,3,3]
b = set(a) # 리스트 a를 세트로 변환, 중복 제거
print(b) # 결과: {1, 2, 3}
print(type(b)) # <class 'set'>

c = list(b) # 세트 b를 다시 리스트로 변환
print(c) # 결과: [1, 2, 3]
print(type(c)) # <class 'list'>

d = tuple(c) # 리스트 c를 튜플로 변환
print(d) # 결과: (1, 2, 3)
print(type(d)) # <class 'tuple'>
```

#### **5. 딕셔너리**

딕셔너리는 키(key)와 값(value)의 쌍으로 데이터를 저장하는 자료구조입니다.

```python
# 딕셔너리 생성, 값은 리스트를 포함할 수 있습니다.
dic1 = {"a" :1, "b":2, "c": [100,200,300]}
print(dic1["a"]) # 키 'a'의 값 출력
print(dic1["b"]) # 키 'b'의 값 출력
print(dic1["c"]) # 키 'c'의 값 출력

dic1["a"] = 100 # 키 'a'의 값 변경
print(dic1["a"])

dic1["d"] = 1000 # 새로운 키-값 쌍 추가
print(dic1["d"])

# 딕셔너리의 키, 값, 아이템(키-값 쌍)을 확인합니다.
print(dic1.keys())
print(dic1.values())
print(dic1.items())

# 반복자 패턴: items()를 사용해 키와 값을 동시에 순회합니다.
for k, v in dic1.items():
    print(f"키 : {k}, 값 : {v}")
```

#### **6. 문자열 관련 연습 예제**

여러 가지 문자열 관련 함수를 사용해봅니다.

```python
practice1 = input("문자열을입력하세요1 :")
text1 = practice1
length1 = len(text1) # len() 함수로 문자열의 길이를 구합니다.
print("입력한 문장의 문자열 갯수는 : " + str(length1) + "개 입니다.")

practice2 = input("문자열을입력하세요2 :")
text2 = practice2
reverse = text2[::-1] # 슬라이싱으로 문자열을 뒤집습니다.
print(reverse)

practice3 = input("문자열을입력하세요3 :")
text3 = practice3
count = text3.count('문') # count() 함수로 특정 문자의 개수를 셉니다.
print("특정한문자('문') 의 갯수는 : " ,count, "개 입니다.")

practice4 = input("문자열을입력하세요4 : ")
text4 = practice4
split = text4.split() # split() 함수로 공백을 기준으로 문자열을 분리해 리스트로 만듭니다.
print("공백을 기준으로 나눈 문장은 : " + str(split) + "입니다.")

practice5 = input("문자열을입력하세요5 : ")
text5 = practice5
swap = text5.swapcase() # swapcase()로 대소문자를 서로 바꿉니다.
print("입력한 문장의 대/소문자를 서로 변경 : " +str(swap))

practice6 = input("문자열을입력하세요6 : ")
text6 = practice6
reverse = text6[::-1]
# 회문: 앞뒤가 동일한 문자열인지 비교합니다.
if text6 == reverse:
    print("입력한 문장은 회문이 맞습니다.")
else:
    print("입력한 문장은 회문이 아닙니다!")
```

#### **7. `deque` (Double-ended Queue)**

`deque`는 양쪽 끝에서 데이터를 빠르고 효율적으로 추가/삭제할 수 있는 자료구조입니다.

```python
from collections import deque

deque_list = deque()

 # 0부터 4까지 5번 반복하며 deque에 요소를 추가합니다.
 # append()는 오른쪽에 추가합니다.
for i in range(5):
  deque_list.append(i)
print(f"deque_list 출력 : {deque_list}")

# pop()은 오른쪽 끝 요소를 삭제하고 반환합니다. (스택처럼 작동)
deque_list.pop() # 4 삭제
print(f"deque_list 출력 : {deque_list}") # 결과: deque([0, 1, 2, 3])

# pop()은 오른쪽 끝 요소를 삭제하고 반환합니다. (스택처럼 작동)
deque_list.pop() # 3 삭제
print(f"deque_list 출력 : {deque_list}") # 결과: deque([0, 1, 2])
```

-----

파이썬의 deque는 'double-ended queue'의 약자로, 리스트(list)와 비슷하지만 양쪽 끝에서 데이터를 빠르고 효율적으로 추가하거나 삭제할 수 있는 자료구조입니다.

일반 리스트는 맨 뒤에 데이터를 추가(`append`)하거나 삭제(`pop`)하는 것은 빠르지만, 맨 앞에 데이터를 추가하거나 삭제하면 모든 기존 데이터의 위치를 한 칸씩 뒤로 밀거나 당겨야 해서 매우 비효율적입니다. deque는 이러한 단점을 보완하기 위해 만들어졌습니다.

**기본 개념 및 특징**
deque는 내부적으로 \*\*이중 연결 리스트(doubly linked list)\*\*로 구현되어 있어 양 끝에서의 데이터 삽입/삭제가 O(1) 시간 복잡도를 가집니다. 이는 데이터의 양에 관계없이 항상 일정한 속도를 보장한다는 의미입니다.

  * **장점**: 양쪽 끝에서의 데이터 처리가 매우 빠르다. 큐(`Queue`)나 스택(`Stack`)을 구현할 때 이상적이다.
  * **단점**: 중간에 있는 데이터에 접근(인덱싱)하는 것은 리스트보다 느리다. (리스트는 O(1), deque는 O(n))

**주요 용도**:

  * **큐(Queue)**: 먼저 들어온 데이터가 먼저 나가는(FIFO) 구조를 구현할 때.
  * **스택(Stack)**: 나중에 들어온 데이터가 먼저 나가는(LIFO) 구조를 구현할 때.
  * **최근 항목 유지**: `maxlen` 옵션을 사용하여 가장 최근의 N개 항목만 저장하는 용도.

-----

```python
from collections import deque

deque_list = deque()

# appendleft()를 사용해 0부터 4까지 왼쪽부터 추가합니다.
for i in range(5):
  deque_list.appendleft(i)
# appendleft()는 요소를 왼쪽 끝에 추가합니다.
# [4, 3, 2, 1, 0]
print(f"deque_list 출력 : {deque_list}")

# reversed()를 사용해 deque를 역순으로 정렬합니다.
deque_list_reversed = deque(reversed(deque_list))
print(f"deque_list 출력 : {deque_list_reversed}")
```

#### **8. 일반 딕셔너리의 키 순서**

Python 3.7부터 일반 딕셔너리도 삽입 순서를 유지합니다.

```python
d= {} # 딕셔너리 생성
d["x"] = 1
d["b"] = 2
d["d"] = 4
d["c"] = 3
d["e"] = 5

# Python 3.7 이상에서는 입력된 순서대로 반복문을 순회합니다.
for k,v in d.items():
  print(f"key : {k}, value : {v}")
```

-----

`OrderedDict`는 이름 그대로 \*\*순서가 보장되는 딕셔너리(Dictionary)\*\*입니다. 데이터를 넣은 순서대로 키(key)의 순서가 유지되는 특징을 가집니다.

중요한 점은, Python 3.7 버전부터는 일반 딕셔너리(`dict`)도 입력된 순서를 기억하도록 변경되어 `OrderedDict`의 필요성이 크게 줄었다는 것입니다. 하지만 여전히 순서와 관련된 몇 가지 특별한 기능과 하위 버전 호환성을 위해 사용됩니다.

-----

```python
# 정렬을 위한 헬퍼 함수
def sort_by_key(t):
  return t[0] # 튜플의 첫 번째 요소(키)를 반환하여 정렬 기준으로 삼습니다.

from collections import OrderedDict

d= OrderedDict()
d["x"] = 1
d["b"] = 2
d["d"] = 4
d["c"] = 3
d["e"] = 5

# sorted() 함수로 딕셔너리 아이템(items())을 키를 기준으로 정렬하고,
# 이를 OrderedDict로 다시 변환하여 순서가 유지된 딕셔너리를 만듭니다.
for k,v in OrderedDict(sorted(d.items(), key=sort_by_key)).items():
  print(f"key : {k}, value : {v}")
```

#### **9. `Counter`**

`Counter`는 시퀀스 자료형의 요소 개수를 딕셔너리 형태로 반환하는 클래스입니다.

```python
from collections import Counter
f = open("yesterday.txt","r")
yesterday_lyric = f.readlines()
f.close()

contents = ""
for line in yesterday_lyric:
    contents = contents + line.strip() + "\n"

print(contents)
# 전체 내용을 소문자로 변환하고(lower()), 공백을 기준으로 분리하여(split()) 단어 리스트를 만듭니다.
text = contents.lower().split()
# Counter를 사용해 각 단어의 빈도수를 셉니다.
Counter(text)
```

-----

`Counter`는 이름 그대로 리스트나 문자열과 같은 반복 가능한(`iterable`) 객체 안의 요소들이 몇 번 등장하는지 개수를 세어주는 딕셔너리 형태의 클래스입니다.

데이터의 빈도수를 계산해야 할 때 매우 간결하고 효율적인 코드를 작성할 수 있도록 도와줍니다.

**기본 개념 및 특징**
`Counter`는 파이썬의 기본 `dict`를 상속받아 만들어졌으며, 딕셔너리의 모든 기능을 포함하면서도 개수 세기에 특화된 유용한 기능들을 추가로 제공합니다.

  * **딕셔너리 기반**: `Counter` 객체는 각 요소를 키(key)로, 해당 요소의 등장 횟수(빈도수)를 값(value)으로 가집니다.
  * **자동 개수 세기**: 반복 가능한 데이터를 `Counter`에 전달하면, 내부의 요소들을 알아서 세어 딕셔너리 형태로 정리해 줍니다.
  * **0 반환**: 존재하지 않는 키에 접근해도 에러가 발생하지 않고 0을 반환하여 편리합니다.
  * **산술 연산 지원**: `Counter` 객체끼리 덧셈, 뺄셈 등의 연산이 가능하여 두 데이터 그룹 간의 빈도수를 쉽게 합치거나 뺄 수 있습니다.

`most_common(n)`: 가장 빈도수가 높은 n개의 요소를 `(요소, 개수)` 형태의 튜플 리스트로 반환합니다.
`elements()`: `Counter`에 저장된 모든 요소를 개수만큼 반복해서 돌려주는 반복자(`iterator`)를 반환합니다.
`update(iterable)`: 기존 `Counter`에 다른 `iterable` 객체의 요소 개수를 더합니다.
`subtract(iterable)`: 기존 `Counter`에서 다른 `iterable` 객체의 요소 개수를 뺍니다.

-----

```python
from collections import Counter

sentence = "파이썬 파이썬 정말 정말 정말 재미있다 파이썬 최고"
words = sentence.split() # 문장을 공백을 기준으로 단어 리스트로 분리
print(words)

word_counts = Counter(words) # 단어 리스트의 빈도수를 계산

# most_common(3)를 사용해 가장 많이 등장하는 단어 3개를 찾습니다.
top_3_words = word_counts.most_common(3)
print(top_3_words)
```

-----

```python
from collections import Counter

# 각 매장의 재고 정보를 Counter 객체로 만듭니다.
store1_inventory = Counter({'사과': 5, '바나나': 10, '오렌지': 3})
store2_inventory = Counter({'사과': 3, '바나나': 5, '포도': 7})

# 두 Counter 객체를 덧셈 연산자로 합산합니다.
total_inventory = store1_inventory + store2_inventory

print(total_inventory)
```

-----

`namedtuple`은 \*\*이름이 붙은 필드를 갖는 튜플(tuple)\*\*을 만드는 팩토리 함수입니다. 일반 튜플처럼 인덱스(`[0]`, `[1]`)로 접근할 수도 있고, 마치 객체처럼 이름(`point.x`, `point.y`)으로도 각 요소에 접근할 수 있어 코드의 가독성을 크게 향상시킵니다.

튜플의 특성인 \*\*불변성(immutable)\*\*과 \*\*가벼움(lightweight)\*\*은 그대로 유지하면서, 각 데이터가 무엇을 의미하는지 명확하게 표현하고 싶을 때 사용합니다.

**기본 개념 및 특징**
일반 튜플은 데이터에 접근할 때 인덱스만 사용해야 해서, 코드를 읽는 사람이 각 인덱스가 무엇을 의미하는지 기억하고 있어야 합니다. `namedtuple`은 이 문제를 해결합니다. 각 위치에 이름을 부여하여 코드를 훨씬 명확하고 읽기 쉽게 만듭니다.

**주요 장점**:

  * **가독성**: `student[1]` 대신 `student.name`처럼 의미 있는 이름으로 데이터에 접근합니다.
  * **튜플의 특성 유지**: 생성된 후에는 값을 변경할 수 없고(불변성), 메모리를 적게 사용하며, 딕셔너리의 키로도 사용할 수 있습니다.
  * **언패킹(Unpacking)**: `x, y = p`와 같이 일반 튜플처럼 값을 여러 변수에 나누어 할당할 수 있습니다.

-----

```python
from collections import namedtuple

# 1. namedtuple 타입 선언
# 'Point'라는 이름의 namedtuple을 정의하고, 'x', 'y' 두 개의 필드를 가집니다.
Point = namedtuple('Point', ['x', 'y'])
# 'Student'라는 namedtuple을 정의하고, 필드 이름을 문자열로 지정합니다.
Student = namedtuple('Student', 'id name email')

# 2. 객체 생성
# 위치 인자(positional arguments)로 객체를 생성합니다.
p1 = Point(10, 20)
# 키워드 인자(keyword arguments)로 객체를 생성합니다.
s1 = Student(id='s001', name='홍길동', email='gildong@example.com')

# 3. 데이터 접근
# 이름으로 접근 (권장)
print(p1.x, p1.y)

# 인덱스로 접근 (일반 튜플과 동일)
print(s1[0], s1[1])
print(s1.id, s1.name, s1.email)
```
