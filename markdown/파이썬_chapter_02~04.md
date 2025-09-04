
---

## 🐍 파이썬 문법 모음집 (Chapter 02 ~ 04)

### Chapter 02: 기초 문법

#### 1. 변수와 자료형

##### ◦ 변수명 선언 규칙
변수는 데이터를 저장하기 위한 메모리 공간에 붙이는 이름입니다.
- **알파벳, 숫자, 밑줄(`_`)**로 선언할 수 있습니다.
- 변수명은 **의미 있는 단어**로 표기하는 것이 좋습니다. (예: `user_age` > `a`)
- 변수명은 **대소문자를 구분**합니다. (`name`과 `Name`은 다른 변수입니다.)
- 특별한 의미가 있는 **예약어(keyword)**는 변수명으로 사용할 수 없습니다. (예: `if`, `for`, `class` 등)

```python
# 파일명: variable_declaration.py

# 올바른 변수명 선언 예시
user_name = "홍길동"
age = 30
_private_variable = "비밀"
user_height_cm = 175.5

# 잘못된 변수명 선언 예시 (주석 해제 시 오류 발생)
# 2nd_user = "김유신" # 숫자로 시작할 수 없음
# user-age = 25       # 하이픈(-) 사용 불가
# for = "예약어"       # 예약어 사용 불가

print(f"사용자 이름: {user_name}, 나이: {age}")
```

##### ◦ 기본 자료형
데이터의 종류를 나타내며, 파이썬의 주요 기본 자료형은 다음과 같습니다.
- **정수형 (integer)**: 0, 100, -50 등 소수점이 없는 숫자.
- **실수형 (float)**: 3.14, -0.01 등 소수점이 있는 숫자.
- **문자열형 (string)**: "Hello", '파이썬' 등 따옴표로 묶인 텍스트.
- **불린형 (boolean)**: `True`(참) 또는 `False`(거짓) 두 가지 값만 가집니다.

```python
# 파일명: data_types.py

# 각 자료형의 변수 선언
integer_num = 100
float_num = 3.14
string_val = "Hello, Python!"
boolean_true = True
boolean_false = False

# type() 함수로 각 변수의 자료형 확인
print(f"'{integer_num}'의 자료형: {type(integer_num)}")
print(f"'{float_num}'의 자료형: {type(float_num)}")
print(f"'{string_val}'의 자료형: {type(string_val)}")
print(f"'{boolean_true}'의 자료형: {type(boolean_true)}")
```

##### ◦ 동적 타이핑 (Dynamic Typing)
파이썬은 변수를 선언할 때 자료형을 미리 지정하지 않아도 됩니다. 코드가 실행되는 시점(runtime)에 인터프리터가 할당되는 값에 따라 자동으로 자료형을 결정합니다. 이를 '동적 타이핑'이라고 합니다.

```python
# 파일명: dynamic_typing.py

# 처음에는 정수형으로 자동 결정됨
data = 10
print(f"값: {data}, 자료형: {type(data)}")

# 이후 문자열을 할당하면 문자열형으로 변경됨
data = "파이썬은 유연해요"
print(f"값: {data}, 자료형: {type(data)}")

# 실수형을 할당하면 실수형으로 변경됨
data = 99.9
print(f"값: {data}, 자료형: {type(data)}")
```

##### ◦ 기본 연산

- **사칙연산**: `+`, `-`, `*`, `/`
- **제곱승**: `**`
- **몫과 나머지**: `//` (몫), `%` (나머지)
- **증감 연산**: `+=` (더한 후 할당), `-=` (뺀 후 할당)

```python
# 파일명: basic_operations.py

a = 10
b = 3

# 다양한 연산 수행 및 결과 출력
print(f"{a} + {b} = {a + b}")           # 더하기
print(f"{a} / {b} = {a / b}")           # 나누기 (결과는 실수)
print(f"{a} ** {b} = {a ** b}")         # 제곱 (10의 3승)
print(f"{a} // {b} = {a // b}")         # 몫
print(f"{a} % {b} = {a % b}")           # 나머지

# 증감 연산
x = 5
x += 2  # x = x + 2 와 동일
print(f"증가 연산 후 x: {x}") # 결과: 7

x -= 3 # x = x - 3 과 동일
print(f"감소 연산 후 x: {x}") # 결과: 4
```

##### ◦ 관계, 논리, 비트 연산
- **관계 연산자**: 값들을 비교하여 `True` 또는 `False`를 반환. (`==`, `!=`, `>`, `<`, `>=`, `<=`)
- **논리 연산자**: 여러 조건을 조합할 때 사용. (`and`, `or`, `not`)
- **비트 연산자**: 비트(0과 1) 수준에서 연산. (`&`, `|`, `^`, `~`, `<<`, `>>`)

```python
# 파일명: logical_operations.py

# 관계 연산자
print(f"10 > 5는? {10 > 5}")     # True
print(f"10 == 10은? {10 == 10}") # True

# 논리 연산자
age = 25
is_student = True
print(f"나이가 20 이상이고 학생인가? {age >= 20 and is_student}") # True

# 비트 연산자 (예시)
a = 60  # 60 = 0011 1100
b = 13  # 13 = 0000 1101
print(f"a & b = {a & b}") # 비트 AND 연산: 12 (0000 1100)
```

##### ◦ 자료형 변환 (Type Casting)
필요에 따라 데이터의 자료형을 명시적으로 변환할 수 있습니다.
- `int()`: 정수형으로 변환
- `float()`: 실수형으로 변환
- `str()`: 문자열형으로 변환

```python
# 파일명: type_casting.py

# 정수 -> 실수
int_val = 100
float_val = float(int_val)
print(f"정수 {int_val} -> 실수: {float_val}, 타입: {type(float_val)}")

# 실수 -> 정수 (소수점 이하 버림)
float_val_2 = 99.9
int_val_2 = int(float_val_2)
print(f"실수 {float_val_2} -> 정수: {int_val_2}, 타입: {type(int_val_2)}")

# 숫자 -> 문자열
num = 123
str_num = str(num)
print(f"숫자 {num} -> 문자열: '{str_num}', 타입: {type(str_num)}")
# 문자열 덧셈은 숫자 연산이 아닌 '이어붙이기(concatenate)'가 됨
print(f"문자열 덧셈: {str_num + str_num}") # 결과: '123123'

# 문자열 -> 숫자
str_val = "456"
num_val = int(str_val)
print(f"문자열 '{str_val}' -> 숫자: {num_val}, 타입: {type(num_val)}")
# 이제 숫자 연산이 가능
print(f"숫자 덧셈: {num_val + num_val}") # 결과: 912
```

##### ◦ 자동 형 변환
파이썬은 특정 상황에서 자동으로 자료형을 변환합니다.
- **정수와 실수의 연산**: 결과는 더 넓은 범위인 실수형으로 자동 변환됩니다. (`10 / 3`의 결과가 `3.333...`인 이유)
- **불린형과 숫자의 비교**: `True`는 `1`로, `False`는 `0`으로 인식되어 비교됩니다.

```python
# 파일명: auto_type_conversion.py

# 정수와 실수의 연산 결과는 실수
result = 10 / 3
print(f"10 / 3의 결과: {result}, 자료형: {type(result)}")

# 불린형과 숫자의 비교
print(f"1 == True 결과: {1 == True}") # True
print(f"0 == False 결과: {0 == False}") # True

# 내용이 없는 문자열("")이나 숫자 0은 False로 간주됨
print(f"''를 불린형으로 변환: {bool('')}") # False
print(f"0을 불린형으로 변환: {bool(0)}") # False
```

#### 2. 입출력 함수

##### ◦ 출력 함수: `print()`
데이터를 화면(콘솔)에 출력하는 함수입니다.
- 콤마(`,`)를 사용하여 여러 데이터를 한 번에 출력할 수 있으며, 각 데이터는 공백으로 구분됩니다.

```python
# 파일명: print_examples.py

# 다양한 데이터 출력
print("안녕하세요") # 문자열
print(123)       # 정수
print(3.14)      # 실수
print(True)      # 불린

# 변수 내용 출력
a = 10
print(a)

# 여러 데이터 조합하여 출력
age = 20
name = "홍길동"
print("나이 :", age)
print("저는", name, "입니다.")
```

##### ◦ 입력 함수: `input()`
사용자로부터 키보드 입력을 받을 수 있는 함수입니다.
- **주의**: `input()`으로 받은 모든 값은 **문자열(string) 자료형**입니다. 숫자 계산이 필요하면 반드시 `int()`나 `float()`로 형 변환을 해야 합니다.

```python
# 파일명: input_example.py

# 사용자에게 이름을 물어보고 입력받음
name = input("당신의 이름은 무엇인가요? ")
print(f"안녕하세요, {name}님!")

# 나이를 입력받아 정수로 변환 후, 내년 나이 계산
age_str = input("나이를 입력하세요: ")
age_int = int(age_str) # 입력받은 문자열을 정수로 변환
next_year_age = age_int + 1
print(f"내년에는 {next_year_age}살이 되시는군요.")
```

##### ◦ 실습: 화씨 온도 변환기
사용자에게 섭씨 온도를 입력받아 화씨 온도로 변환하여 출력하는 프로그램을 만듭니다.
- **변환 공식**: 화씨 = (섭씨 × 9/5) + 32

```python
# 파일명: fahrenheit_converter.py

# 프로그램 제목 출력
print("--- 화씨 온도 변환기 ---")

# 사용자로부터 섭씨 온도를 문자열로 입력받음
celsius_str = input("섭씨 온도를 입력하세요: ")

# 입력받은 문자열을 계산을 위해 실수형(float)으로 변환
celsius = float(celsius_str)

# 화씨 온도 계산 공식을 적용
fahrenheit = (celsius * 9/5) + 32

# 최종 결과 출력
print(f"섭씨 {celsius}도는 화씨 {fahrenheit:.2f}도 입니다.") # .2f: 소수점 둘째 자리까지 표시
```

#### 3. 리스트 (List)

##### ◦ 리스트의 개념
하나의 변수에 여러 개의 데이터를 순서대로 저장하는 자료형입니다.
- 대괄호 `[]`를 사용하여 생성하고, 각 데이터는 콤마(`,`)로 구분합니다.
- 정수, 실수, 문자열 등 다양한 자료형을 함께 저장할 수 있습니다.

```python
# 파일명: list_basic.py

# 다양한 데이터를 포함하는 리스트 생성
my_list = [10, "hello", 3.14, True]
print(f"나의 리스트: {my_list}")

# 도시 이름을 저장하는 리스트
cities = ["서울", "부산", "인천", "대구", "광주", "대전", "울산", "수원"]
print(f"대한민국 주요 도시: {cities}")
```

##### ◦ 인덱싱 (Indexing)
리스트 내 특정 위치의 데이터에 접근하는 방법입니다. 인덱스는 **0부터 시작**합니다.

```python
# 파일명: list_indexing.py

cities = ["서울", "부산", "인천", "대구"]

# 첫 번째 요소에 접근 (인덱스 0)
first_city = cities[0]
print(f"첫 번째 도시: {first_city}") # 결과: 서울

# 세 번째 요소에 접근 (인덱스 2)
third_city = cities[2]
print(f"세 번째 도시: {third_city}") # 결과: 인천

# 리버스 인덱스: -1은 마지막 요소, -2는 마지막에서 두 번째 요소를 의미
last_city = cities[-1]
print(f"마지막 도시: {last_city}") # 결과: 대구
```

##### ◦ 슬라이싱 (Slicing)
리스트의 일부분을 잘라내어 새로운 리스트를 만드는 방법입니다. `[시작인덱스:끝인덱스]` 형식을 사용하며, **끝 인덱스는 포함되지 않습니다**.

```python
# 파일명: list_slicing.py

cities = ["서울", "부산", "인천", "대구", "광주", "대전"]

# 인덱스 1부터 3까지 (4-1) 슬라이싱
# ["부산", "인천", "대구"]
some_cities = cities[1:4]
print(f"cities[1:4] 결과: {some_cities}")

# 처음부터 인덱스 2까지 (3-1) 슬라이싱
# ["서울", "부산"]
first_two = cities[:2]
print(f"cities[:2] 결과: {first_two}")

# 인덱스 3부터 끝까지 슬라이싱
# ["대구", "광주", "대전"]
from_daegu = cities[3:]
print(f"cities[3:] 결과: {from_daegu}")

# 전체 리스트 복사
all_cities = cities[:]
print(f"cities[:] 결과: {all_cities}")

# 리버스 인덱스를 이용한 슬라이싱
# 인덱스 -3 (광주) 부터 끝까지
last_three = cities[-3:]
print(f"cities[-3:] 결과: {last_three}")```

##### ◦ 증가값 (Step)
슬라이싱 시 `[시작:끝:증가값]` 형식으로 건너뛸 간격을 지정할 수 있습니다.

```python
# 파일명: list_step.py

numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# 처음부터 끝까지 2칸씩 건너뛰며 슬라이싱 (짝수만 추출)
evens = numbers[::2]
print(f"짝수 리스트: {evens}") # 결과: [0, 2, 4, 6, 8]

# 리스트를 거꾸로 뒤집기
reversed_numbers = numbers[::-1]
print(f"뒤집힌 리스트: {reversed_numbers}") # 결과: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
```

##### ◦ 리스트 연산
- `+` : 두 리스트를 연결합니다.
- `*` : 리스트를 정수만큼 반복합니다.
- `in` : 특정 요소가 리스트에 포함되어 있는지 확인합니다 (`True`/`False`).

```python
# 파일명: list_operations.py

list_a = [1, 2, 3]
list_b = [4, 5, 6]

# 리스트 덧셈
list_sum = list_a + list_b
print(f"{list_a} + {list_b} = {list_sum}") # 결과: [1, 2, 3, 4, 5, 6]

# 리스트 곱셈
list_mul = list_a * 3
print(f"{list_a} * 3 = {list_mul}") # 결과: [1, 2, 3, 1, 2, 3, 1, 2, 3]

# in 연산
is_3_in_list = 3 in list_a
print(f"3이 {list_a}에 있나요? {is_3_in_list}") # 결과: True

is_7_in_list = 7 in list_a
print(f"7이 {list_a}에 있나요? {is_7_in_list}") # 결과: False
```

##### ◦ 리스트 추가 및 삭제
- `append(값)`: 리스트의 맨 끝에 새로운 요소를 추가합니다.
- `extend(리스트)`: 다른 리스트의 모든 요소를 현재 리스트 끝에 추가합니다.
- `insert(인덱스, 값)`: 지정된 인덱스에 새로운 요소를 삽입합니다.
- `remove(값)`: 리스트에서 특정 값을 찾아 첫 번째로 발견된 것만 삭제합니다.
- `del 리스트[인덱스]`: 지정된 인덱스의 요소를 삭제합니다.

```python
# 파일명: list_modify.py

numbers = [1, 2, 3]
print(f"초기 리스트: {numbers}")

# append: 맨 끝에 4 추가
numbers.append(4)
print(f"append(4) 후: {numbers}") # [1, 2, 3, 4]

# extend: 다른 리스트 [5, 6] 추가
numbers.extend([5, 6])
print(f"extend([5, 6]) 후: {numbers}") # [1, 2, 3, 4, 5, 6]

# insert: 인덱스 1에 100 삽입
numbers.insert(1, 100)
print(f"insert(1, 100) 후: {numbers}") # [1, 100, 2, 3, 4, 5, 6]

# remove: 값 3을 찾아서 삭제
numbers.remove(3)
print(f"remove(3) 후: {numbers}") # [1, 100, 2, 4, 5, 6]

# del: 인덱스 0의 요소 삭제
del numbers[0]
print(f"del numbers[0] 후: {numbers}") # [100, 2, 4, 5, 6]
```

##### ◦ 패킹 (Packing)과 언패킹 (Unpacking)
- **패킹**: 하나의 변수에 여러 개의 데이터를 묶어서 할당하는 것 (리스트 생성).
- **언패킹**: 리스트나 튜플의 요소들을 각각의 변수로 풀어 할당하는 것. 언패킹 시 변수의 개수와 요소의 개수가 정확히 일치해야 합니다.

```python
# 파일명: packing_unpacking.py

# 패킹: t 변수에 3개의 값을 묶어서 할당
t = [1, 2, 3]
print(f"패킹된 변수 t: {t}")

# 언패킹: t의 각 요소를 x, y, z 변수에 풀어 할당
x, y, z = t
print(f"언패킹 결과: x={x}, y={y}, z={z}")

# 오류 예시: 변수 개수와 요소 개수가 다르면 에러 발생
# a, b = t # ValueError: too many values to unpack (expected 2)
```

##### ◦ 이차원 리스트
리스트 안에 또 다른 리스트를 포함하는 구조로, 행렬이나 표와 같은 데이터를 표현할 때 유용합니다.

```python
# 파일명: 2d_list.py

# 3x3 크기의 이차원 리스트 생성
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print(f"이차원 리스트: {matrix}")

# 이차원 리스트 인덱싱: matrix[행][열]
# 2행 3열의 값(6)에 접근
element = matrix[1][2]
print(f"matrix[1][2]의 값: {element}") # 결과: 6
```

##### ◦ 리스트의 메모리 저장 방식
파이썬에서 리스트 변수는 데이터 값 자체를 저장하는 것이 아니라, 각 데이터가 저장된 메모리의 **주소(reference)**를 저장합니다.
- `==` 연산자는 **값**을 비교합니다.
- `is` 연산자는 **메모리 주소**를 비교합니다.

이러한 특징 때문에 하나의 리스트를 다른 변수에 할당하면, 두 변수는 같은 메모리 주소를 가리키게 되어 하나의 변수를 수정하면 다른 변수도 함께 변경되는 현상이 발생합니다.

```python
# 파일명: list_memory.py

# a 리스트 생성
a = [1, 2, 3]
# b에 a를 할당 (메모리 주소 복사)
b = a

print(f"초기 a: {a}")
print(f"초기 b: {b}")
print(f"a is b ? {a is b}") # True: a와 b는 같은 메모리 주소를 가리킴

# a 리스트의 첫 번째 요소를 변경
a[0] = 99

# a를 변경했지만 b도 함께 변경됨
print(f"a 변경 후 a: {a}")
print(f"a 변경 후 b: {b}") # 결과: [99, 2, 3]

# 값을 복사하여 독립적인 리스트를 만들려면 슬라이싱(:)이나 copy() 메소드를 사용
c = a[:] # 또는 c = a.copy()
print(f"a is c ? {a is c}") # False: c는 새로운 메모리 공간에 값을 복사함

# 이제 a를 변경해도 c는 영향을 받지 않음
a[0] = 1
print(f"a 재변경 후 a: {a}")
print(f"a 재변경 후 c: {c}")
```

#### 4. 조건문

##### ◦ 조건문의 개념
주어진 조건이 참(True)인지 거짓(False)인지에 따라 다른 코드를 실행하도록 흐름을 제어하는 구문입니다.
- **`if`**: 조건이 참일 때 실행됩니다.
- **`else`**: `if` 조건이 거짓일 때 실행됩니다. (선택 사항)
- **`elif`**: 여러 조건을 순차적으로 검사할 때 사용합니다. (else if의 축약)

##### ◦ `if-else` 문
```python
# 파일명: if_else_statement.py

age = 15

# if-else문의 기본 구조
if age >= 20:
    # 조건이 참일 때 실행될 코드 블록 (들여쓰기 필수)
    print("성인입니다.")
else:
    # 조건이 거짓일 때 실행될 코드 블록
    print("미성년자입니다.")
```

##### ◦ `if-elif-else` 문
여러 조건을 순서대로 검사할 때 사용합니다. 위에서부터 하나씩 검사하며, 참인 조건을 만나면 해당 블록을 실행하고 전체 조건문을 빠져나옵니다.

```python
# 파일명: if_elif_else_statement.py

score = 85

if score >= 90:
    print("A 등급입니다.")
elif score >= 80: # 첫 번째 if가 거짓이고, 이 조건이 참일 때 실행
    print("B 등급입니다.")
elif score >= 70:
    print("C 등급입니다.")
else: # 위의 모든 조건이 거짓일 때 실행
    print("D 등급입니다.")```
> 실행 결과: B 등급입니다.

##### ◦ 조건의 판단: 비교 연산자와 논리 연산자
- **비교 연산자**: `==` (같다), `!=` (다르다), `>` (크다), `<` (작다), `>=` (크거나 같다), `<=` (작거나 같다)
- **논리 연산자**:
    - `and`: 양쪽 조건이 모두 참일 때만 `True`
    - `or`: 둘 중 하나라도 참이면 `True`
    - `not`: 조건의 결과를 반대로 뒤집음 (`True` -> `False`)

```python
# 파일명: conditions.py

money = 5000
time = 14

# and: 돈이 4000원 이상 '그리고' 시간이 12시 이후인가?
if money >= 4000 and time >= 12:
    print("점심으로 맛있는 것을 먹자!")

# or: 주말이거나 공휴일인가?
is_weekend = True
is_holiday = False
if is_weekend or is_holiday:
    print("쉬는 날입니다.")
```

#### 5. 반복문

##### ◦ `for` 문
지정된 횟수만큼 또는 시퀀스(리스트, 문자열 등)의 각 요소를 순회하면서 코드를 반복 실행합니다.

- **`range(stop)`**: 0부터 `stop-1`까지의 숫자를 생성합니다.
- **`range(start, stop)`**: `start`부터 `stop-1`까지의 숫자를 생성합니다.
- **`range(start, stop, step)`**: `start`부터 `stop-1`까지 `step` 간격으로 숫자를 생성합니다.

```python
# 파일명: for_loop.py

# 1. 리스트를 이용한 반복
fruits = ["사과", "바나나", "딸기"]
for fruit in fruits:
    print(f"내가 좋아하는 과일: {fruit}")

# 2. range()를 이용한 반복
# 0부터 4까지 5번 반복
for i in range(5):
    print(f"반복 {i}")

# 1부터 9까지 2씩 증가
for num in range(1, 10, 2):
    print(num, end=" ") # 1 3 5 7 9
print() # 줄바꿈

# 3. 문자열을 이용한 반복
for char in "hello":
    print(char)
```

##### ◦ `while` 문
주어진 조건이 참(`True`)인 동안 코드를 계속해서 반복 실행합니다. 조건이 거짓(`False`)이 되면 반복을 멈춥니다.

```python
# 파일명: while_loop.py

# 1부터 5까지 출력
count = 1
while count <= 5:
    print(f"현재 숫자: {count}")
    count += 1 # 이 부분이 없으면 무한 루프에 빠짐

print("반복문 종료")
```

##### ◦ 반복문 제어
- **`break`**: 현재 실행 중인 반복문을 즉시 탈출합니다.
- **`continue`**: 현재 반복을 중단하고, 다음 반복으로 건너뜁니다.
- **`else`**: 반복문이 `break` 없이 정상적으로 모두 완료되었을 때 실행됩니다.

```python
# 파일명: loop_control.py

# break 예제: 5를 만나면 반복 중단
for i in range(1, 11):
    if i == 5:
        print("5를 찾았으므로 중단합니다.")
        break
    print(i, end=" ") # 결과: 1 2 3 4
print("\n")

# continue 예제: 짝수만 건너뛰고 홀수만 출력
for i in range(1, 11):
    if i % 2 == 0: # 짝수이면
        continue   # 현재 반복을 건너뛰고 다음 반복으로 넘어감
    print(i, end=" ") # 결과: 1 3 5 7 9
print("\n")

# else 예제: 반복문이 정상 종료되었을 때 실행
for i in range(1, 6):
    print(i, end=" ")
else:
    print("\n반복문이 성공적으로 완료되었습니다.")
```

#### 6. 조건문과 반복문 실습

##### ◦ 실습 1: 구구단 계산기
사용자에게 숫자를 입력받아 해당 숫자의 구구단을 출력합니다.

```python
# 파일명: gugudan_calculator.py

dan = int(input("출력할 구구단 숫자를 입력하세요: "))

print(f"--- {dan}단 ---")
for i in range(1, 10):
    print(f"{dan} x {i} = {dan * i}")
```

##### ◦ 실습 2: 문자열 역순 출력
입력된 문자열을 거꾸로 출력합니다.

```python
# 파일명: reverse_string.py

sentence = input("역순으로 출력할 문자열을 입력하세요: ")
reverse_sentence = ""

# 문자열의 마지막 글자부터 첫 글자까지 역순으로 반복
for i in range(len(sentence) - 1, -1, -1):
    reverse_sentence += sentence[i]

print(f"역순 출력: {reverse_sentence}")

# 더 쉬운 방법: 슬라이싱 이용
print(f"슬라이싱을 이용한 역순 출력: {sentence[::-1]}")
```

##### ◦ 실습 3: 십진수를 이진수로 변환
사용자에게 십진수 숫자를 입력받아 이진수로 변환하여 출력합니다.
- **로직**: 숫자를 2로 계속 나누면서 나머지를 역순으로 취합니다.

```python
# 파일명: decimal_to_binary.py

decimal_num = int(input("이진수로 변환할 십진수를 입력하세요: "))
binary_result = ""
temp_num = decimal_num

if temp_num == 0:
    binary_result = "0"
else:
    # temp_num이 0이 될 때까지 반복
    while temp_num > 0:
        # 2로 나눈 나머지를 구함
        remainder = temp_num % 2
        # 나머지를 결과 문자열의 앞쪽에 추가
        binary_result = str(remainder) + binary_result
        # 몫을 다음 나눗셈을 위해 저장
        temp_num = temp_num // 2

print(f"십진수 {decimal_num}는 이진수 {binary_result}입니다.")
```
//=====================================================================================

### Chapter 03: 함수, 문자열

#### 1. 함수 기초

##### ◦ 함수의 개념과 장점
- **함수(Function)**: 특정 작업을 수행하는 코드의 묶음(덩어리).
- **장점**:
    1.  **재사용성**: 필요할 때마다 이름으로 호출하여 재사용할 수 있습니다.
    2.  **모듈화**: 코드를 논리적인 단위로 나누어 관리하기 용이합니다.
    3.  **캡슐화**: 함수 내부의 동작을 숨기고, 입력과 결과에만 집중할 수 있어 코드의 복잡도가 낮아집니다.

##### ◦ 함수의 선언과 호출
- `def` 키워드로 함수를 정의(선언)합니다.
- `함수이름()` 형태로 함수를 실행(호출)합니다.

```python
# 파일명: function_basic.py

# 1. 함수 선언 (정의)
# def 함수이름(매개변수1, 매개변수2, ...):
#     <수행할 코드 블록>
#     return 결과값

def add(a, b):
    """두 수를 더한 결과를 반환하는 함수""" # Docstring: 함수에 대한 설명
    result = a + b
    return result

# 2. 함수 호출 (실행)
sum_result = add(5, 3) # a=5, b=3이 전달됨
print(f"5 + 3의 결과: {sum_result}")

# 반환값이 없는 함수
def print_hello(name):
    print(f"안녕하세요, {name}님!")

print_hello("홍길동")
```

##### ◦ 함수의 실행 순서
1.  파이썬 인터프리터가 `def` 키워드를 만나 함수를 메모리에 등록합니다.
2.  프로그램 흐름에 따라 진행되다가 `함수이름()` 호출 코드를 만납니다.
3.  프로그램 흐름이 함수 내부로 점프합니다.
4.  함수 내부의 코드를 위에서부터 순서대로 실행합니다.
5.  `return`을 만나거나 함수 코드의 끝에 도달하면 함수를 호출했던 위치로 돌아옵니다.

#### 2. 함수 심화

##### ◦ 변수의 사용 범위 (Scoping Rule)
- **지역 변수 (Local Variable)**: 함수 **안에서** 선언된 변수. 함수가 종료되면 사라지며, 함수 밖에서는 접근할 수 없습니다.
- **전역 변수 (Global Variable)**: 함수 **밖에서** 선언된 변수. 프로그램 전체에서 접근할 수 있습니다.

```python
# 파일명: variable_scope.py

global_var = 100 # 전역 변수

def my_function():
    local_var = 10 # 지역 변수
    print(f"함수 안에서 출력: global_var={global_var}, local_var={local_var}")

my_function()
print(f"함수 밖에서 출력: global_var={global_var}")
# print(f"함수 밖에서 local_var 접근: {local_var}") # NameError: name 'local_var' is not defined

# 함수 내에서 전역 변수 값을 변경하려면 'global' 키워드 사용
def modify_global():
    global global_var # 이 함수 안에서 global_var는 전역 변수를 가리킴
    global_var = 200

print(f"변경 전 전역 변수: {global_var}")
modify_global()
print(f"변경 후 전역 변수: {global_var}") # 결과: 200
```

##### ◦ 재귀 함수 (Recursive Function)
함수가 자기 자신을 다시 호출하는 함수입니다. 반복적인 작업을 수행할 때 사용되며, 반드시 종료 조건이 있어야 무한 루프에 빠지지 않습니다. 대표적인 예로 팩토리얼(factorial) 계산이 있습니다.

- `n! = n * (n-1) * (n-2) * ... * 1`
- `n! = n * (n-1)!` (점화식)

```python
# 파일명: recursive_function.py

def factorial(n):
    # 종료 조건: n이 1이면 1을 반환하고 재귀 호출을 멈춤
    if n == 1:
        return 1
    # 재귀 호출: n과 n-1의 팩토리얼 결과를 곱함
    else:
        return n * factorial(n - 1)

# 5! = 5 * 4 * 3 * 2 * 1 = 120
result = factorial(5)
print(f"5!의 결과: {result}")
```

#### 3. 함수의 인수 (Arguments)

##### ◦ 키워드 인수 (Keyword Arguments)
함수를 호출할 때 `매개변수이름=값` 형태로 직접 값을 전달하는 방식입니다. 인수의 순서가 헷갈리지 않고 코드의 가독성을 높여줍니다.

```python
# 파일명: keyword_arguments.py

def print_user_info(name, age, city):
    print(f"이름: {name}, 나이: {age}, 거주지: {city}")

# 위치 인수로 호출 (순서가 중요)
print_user_info("홍길동", 30, "서울")

# 키워드 인수로 호출 (순서가 바뀌어도 상관없음)
print_user_info(age=25, city="부산", name="이순신")
```

##### ◦ 디폴트 인수 (Default Arguments)
함수의 매개변수에 기본값을 미리 지정하는 방식입니다. 함수 호출 시 해당 인수를 생략하면 기본값이 사용됩니다.
- **주의**: 디폴트 인수는 항상 일반 매개변수 **뒤에** 위치해야 합니다.

```python
# 파일명: default_arguments.py

# country 매개변수에 '한국'이라는 기본값을 지정
def print_user_info(name, age, country="한국"):
    print(f"이름: {name}, 나이: {age}, 국가: {country}")

# country 인수를 생략하면 기본값 '한국'이 사용됨
print_user_info("홍길동", 30)

# country 인수에 다른 값을 전달하면 그 값이 사용됨
print_user_info("John", 28, country="USA")
```

##### ◦ 가변 인수 (Variable-length Arguments)
함수에 전달되는 인수의 개수가 정해져 있지 않을 때 사용합니다.
- `*args`: 여러 개의 인수를 **튜플(tuple)** 형태로 받습니다.
- `**kwargs`: 여러 개의 키워드 인수를 **딕셔셔너리(dictionary)** 형태로 받습니다.

```python
# 파일명: variable_arguments.py

# 1. *args: 여러 위치 인수를 튜플로 받음
def add_all(*args):
    print(f"받은 인수 (튜플): {args}")
    total = 0
    for num in args:
        total += num
    return total

print(f"결과: {add_all(1, 2, 3)}")
print(f"결과: {add_all(10, 20, 30, 40, 50)}")


# 2. **kwargs: 여러 키워드 인수를 딕셔너리로 받음
def print_info(**kwargs):
    print(f"받은 인수 (딕셔너리): {kwargs}")
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="제임스", job="개발자", city="런던")


# 3. 모든 인수 형태를 사용하는 함수의 매개변수 순서
# 일반 매개변수 -> 디폴트 매개변수 -> *args -> **kwargs
def complex_function(a, b, c="default", *args, **kwargs):
    print(f"a: {a}")
    print(f"b: {b}")
    print(f"c: {c}")
    print(f"args: {args}")
    print(f"kwargs: {kwargs}")

complex_function(1, 2, "C", 10, 20, 30, key1="value1", key2="value2")
```

#### 4. 문자열의 이해

##### ◦ 문자열의 특징
문자열은 여러 문자가 순서대로 나열된 **시퀀스(Sequence) 자료형**입니다. 따라서 리스트처럼 인덱싱, 슬라이싱, `len()` 함수 등을 사용할 수 있습니다.
- **불변성(Immutable)**: 한 번 생성된 문자열의 내용은 직접 수정할 수 없습니다. (`'hello'[0] = 'H'` 와 같은 시도는 오류 발생)

```python
# 파일명: string_features.py

s = "Hello, Python!"

# 인덱싱
print(f"첫 번째 글자: {s[0]}") # H
# 슬라이싱
print(f"7번째부터 12번째까지: {s[7:13]}") # Python
# 길이 확인
print(f"문자열의 길이: {len(s)}")

# 문자열은 불변(immutable)하므로 직접 수정 불가
# s[0] = 'h' # TypeError: 'str' object does not support item assignment
```

##### ◦ 문자열 연산
- `+`: 두 문자열을 이어붙입니다.
- `*`: 문자열을 정수만큼 반복합니다.

```python
# 파일명: string_operations.py

s1 = "안녕"
s2 = "하세요"

# 덧셈 연산
greeting = s1 + s2
print(greeting) # 안녕하세요

# 곱셈 연산
laugh = "하" * 5
print(laugh) # 하하하하하
```

##### ◦ 유용한 문자열 함수 (메서드)
문자열 변수 뒤에 점(`.`)을 찍어 다양한 기능을 사용할 수 있습니다.
- `upper()` / `lower()`: 대/소문자로 변환
- `title()` / `capitalize()`: 각 단어의 첫 글자만 대문자로 / 문장의 첫 글자만 대문자로
- `count('찾을문자')`: 특정 문자의 개수 반환
- `startswith('시작문자')` / `endswith('끝문자')`: 특정 문자열로 시작/끝나는지 확인 (`True`/`False`)
- `strip()` / `lstrip()` / `rstrip()`: 양쪽/왼쪽/오른쪽 공백 제거
- `replace('바꿀문자', '새문자')`: 특정 문자열을 찾아 다른 문자열로 변경
- `split('구분자')`: 문자열을 구분자 기준으로 나누어 리스트로 반환
- `join(리스트)`: 리스트의 각 요소를 문자열로 연결

```python
# 파일명: string_methods.py

text = "  hello world, welcome to python world!  "

print(f"원본: '{text}'")
print(f"대문자로: '{text.upper()}'")
print(f"첫 글자만 대문자로: '{text.strip().capitalize()}'") # strip()으로 공백 제거 후 capitalize() 적용
print(f"'world' 개수: {text.count('world')}")
print(f"'hello'로 시작하는가? {text.strip().startswith('hello')}")
print(f"공백 제거: '{text.strip()}'")
print(f"'world'를 'galaxy'로 변경: '{text.replace('world', 'galaxy')}'")
print(f"공백 기준으로 나누기: {text.strip().split(' ')}")

words = ['파이썬', '정말', '재밌다']
sentence = " ".join(words)
print(f"리스트를 문장으로 합치기: '{sentence}'")
```

##### ◦ 실습: 단어 카운팅
비틀즈의 노래 <Yesterday> 가사에서 'yesterday'라는 단어가 몇 번 나오는지 세어봅니다.

```python
# 파일명: word_counting.py

lyric = """
Yesterday all my troubles seemed so far away
Now it looks as though they're here to stay
Oh, I believe in yesterday
Suddenly I'm not half the man I used to be
There's a shadow hanging over me
Oh, yesterday came suddenly
Why she had to go, I don't know, she wouldn't say
I said something wrong, now I long for yesterday
Yesterday love was such an easy game to play
Now I need a place to hide away
Oh, I believe in yesterday
"""

# 1. 모든 문자를 소문자로 변환 (대소문자 구분 없이 세기 위해)
lower_lyric = lyric.lower()

# 2. 'yesterday' 단어의 개수를 센다
count = lower_lyric.count('yesterday')

print(f"가사에서 'yesterday'는 총 {count}번 나옵니다.")
```

#### 5. 문자열 서식 지정 (Formatting)

##### ◦ `%` 서식 (Old style)
- `%s`: 문자열 (string)
- `%d`: 정수 (decimal)
- `%f`: 실수 (float)

```python
# 파일명: percent_formatting.py

name = "홍길동"
age = 30
height = 175.5

# % 서식을 이용한 출력
print("이름: %s, 나이: %d세" % (name, age))

# 패딩: %10s -> 10칸을 확보하고 우측 정렬
# 패딩: %-10s -> 10칸을 확보하고 좌측 정렬
# 소수점: %.2f -> 소수점 둘째 자리까지 표시
print("키: %.2fcm" % height)
```

##### ◦ `format()` 함수 (New style)
- `{}` 플레이스홀더를 사용하며, 인덱스나 이름으로 값을 지정할 수 있습니다.

```python
# 파일명: format_method.py

name = "이순신"
temperature = 25.845

# 인덱스 기반 포매팅
print("이름: {0}, 현재 기온: {1}".format(name, temperature))

# 이름 기반 포매팅 (가독성이 좋음)
print("이름: {n}, 현재 기온: {t}".format(n=name, t=temperature))

# 서식 지정 (패딩 및 소수점)
# :<10 -> 10칸 확보, 좌측 정렬
# :.2f -> 소수점 둘째 자리까지
print("기온 정보: {0:.2f}도".format(temperature))
```

##### ◦ `f-string` (Python 3.6+ 권장)
- 문자열 앞에 `f`를 붙이고, `{}` 안에 변수나 표현식을 직접 넣습니다. 가장 직관적이고 편리합니다.

```python
# 파일명: f_string.py

name = "강감찬"
pi = 3.141592

# f-string을 이용한 출력
print(f"장군님의 이름은 {name}입니다.")

# f-string 안에서 연산도 가능
x = 10
y = 20
print(f"{x} + {y} = {x + y}")

# 서식 지정도 동일하게 가능
print(f"원주율 (소수점 셋째 자리): {pi:.3f}")
print(f"이름(10칸, 좌측 정렬): '{name:<10}'")
```

//=====================================================================================


### Chapter 04: 자료구조

#### 1. 자료구조의 이해
- **자료구조(Data Structure)**: 데이터를 효율적으로 저장하고 관리하기 위한 방법. 파이썬은 리스트, 튜플, 세트, 딕셔너리 등 강력한 내장 자료구조를 제공합니다.

#### 2. 스택과 큐

##### ◦ 스택 (Stack): LIFO (Last-In, First-Out)
- 마지막에 들어온 데이터가 가장 먼저 나가는 구조. (예: 접시 쌓기)
- 파이썬 리스트의 `append()`(push)와 `pop()`(pop)을 이용해 쉽게 구현할 수 있습니다.

```python
# 파일명: stack_example.py

# 스택으로 사용할 빈 리스트 생성
stack = []

# Push: 데이터 삽입
stack.append(1)
stack.append(2)
stack.append(3)
print(f"스택 상태: {stack}") # [1, 2, 3]

# Pop: 마지막 데이터 추출
last_item = stack.pop()
print(f"Pop된 항목: {last_item}") # 3
print(f"스택 상태: {stack}") # [1, 2]

last_item = stack.pop()
print(f"Pop된 항목: {last_item}") # 2
print(f"스택 상태: {stack}") # [1]```

##### ◦ 큐 (Queue): FIFO (First-In, First-Out)
- 먼저 들어온 데이터가 가장 먼저 나가는 구조. (예: 은행 대기 줄)
- 리스트의 `append()`(enqueue)와 `pop(0)`(dequeue)으로 구현할 수 있지만, `pop(0)`는 비효율적입니다.
- **`collections.deque`**를 사용하는 것이 훨씬 효율적입니다.

```python
# 파일명: queue_example.py
from collections import deque

# 큐로 사용할 deque 객체 생성
queue = deque()

# Enqueue: 데이터 삽입
queue.append(1)
queue.append(2)
queue.append(3)
print(f"큐 상태: {queue}") # deque([1, 2, 3])

# Dequeue: 첫 번째 데이터 추출 (popleft 사용)
first_item = queue.popleft()
print(f"Dequeue된 항목: {first_item}") # 1
print(f"큐 상태: {queue}") # deque([2, 3])

first_item = queue.popleft()
print(f"Dequeue된 항목: {first_item}") # 2
print(f"큐 상태: {queue}") # deque([3])
```

#### 3. 튜플과 세트

##### ◦ 튜플 (Tuple)
- 리스트와 거의 동일하지만, 한 번 생성되면 그 **값을 변경할 수 없는(immutable)** 자료형입니다.
- 소괄호 `()`를 사용하여 선언합니다.
- 함수의 반환값처럼 변경되면 안 되는 데이터를 다룰 때 유용합니다.

```python
# 파일명: tuple_example.py

# 튜플 생성
my_tuple = (1, 2, "hello")
print(f"튜플: {my_tuple}")

# 인덱싱과 슬라이싱은 리스트와 동일
print(f"첫 번째 요소: {my_tuple[0]}")

# 값 변경 시도 시 오류 발생
# my_tuple[0] = 100 # TypeError: 'tuple' object does not support item assignment
```

##### ◦ 세트 (Set)
- **중복을 허용하지 않고**, **순서가 없는** 값들의 모음입니다.
- 중괄호 `{}` 또는 `set()` 함수로 생성합니다.
- 합집합, 교집합, 차집합 등 집합 연산에 유용합니다.

```python
# 파일명: set_example.py

# 중복된 요소를 포함한 리스트
my_list = [1, 2, 2, 3, 4, 4, 4]

# 리스트를 세트로 변환하여 중복 제거
my_set = set(my_list)
print(f"세트 (중복 제거됨): {my_set}") # {1, 2, 3, 4}

# 세트 연산
set_a = {1, 2, 3, 4}
set_b = {3, 4, 5, 6}

# 합집합 (|)
print(f"합집합: {set_a | set_b}") # {1, 2, 3, 4, 5, 6}

# 교집합 (&)
print(f"교집합: {set_a & set_b}") # {3, 4}

# 차집합 (-)
print(f"차집합 (A-B): {set_a - set_b}") # {1, 2}
```

#### 4. 딕셔너리 (Dictionary)

##### ◦ 딕셔너리의 개념
- **키(Key)와 값(Value)**을 한 쌍으로 묶어 저장하는 자료구조입니다.
- 순서가 없으며, 키를 통해 값을 빠르게 찾을 수 있습니다. (Key는 중복될 수 없습니다)
- 중괄호 `{}`를 사용하며, `{키1: 값1, 키2: 값2, ...}` 형태로 선언합니다.

```python
# 파일명: dictionary_example.py

# 딕셔너리 생성
student_info = {
    "name": "홍길동",
    "student_id": 2024001,
    "major": "컴퓨터공학",
    "credits": [3.5, 4.0, 4.5]
}
print(f"학생 정보: {student_info}")

# 값 접근: 딕셔너리[키]
print(f"이름: {student_info['name']}")
print(f"전공: {student_info['major']}")

# 값 추가 및 변경
student_info['age'] = 20 # 새로운 키-값 쌍 추가
student_info['major'] = "인공지능" # 기존 키의 값 변경
print(f"수정된 정보: {student_info}")
```

##### ◦ 딕셔너리 함수 (메서드)
- `keys()`: 모든 키를 모아 `dict_keys` 객체로 반환
- `values()`: 모든 값을 모아 `dict_values` 객체로 반환
- `items()`: 모든 (키, 값) 쌍을 모아 `dict_items` 객체로 반환

```python
# 파일명: dictionary_methods.py

country_codes = {"한국": 82, "미국": 1, "일본": 81}

# keys()
print(f"모든 키: {country_codes.keys()}")

# values()
print(f"모든 값: {country_codes.values()}")

# items()와 for문을 함께 사용
for country, code in country_codes.items():
    print(f"{country}의 국가 번호는 +{code}입니다.")

# 'in'을 사용하여 키 존재 여부 확인
print(f"'한국' 키가 딕셔너리에 있나요? {'한국' in country_codes}") # True
```

#### 5. `collections` 모듈
기본 자료구조를 더욱 확장한 유용한 자료구조들을 제공하는 내장 모듈입니다.

- **`deque`**: 양방향 큐. 스택과 큐의 기능을 모두 가지며, 양쪽 끝에서의 추가/삭제가 매우 빠릅니다.
- **`OrderedDict`**: 입력된 순서를 기억하는 딕셔너리. (Python 3.7+부터는 기본 딕셔너리도 순서를 기억하지만, 명시적으로 순서가 중요할 때 사용)
- **`defaultdict`**: 존재하지 않는 키를 조회할 때, 지정된 기본값을 자동으로 생성해주는 딕셔너리. `KeyError`를 방지할 수 있습니다.
- **`Counter`**: 시퀀스 자료형의 요소 개수를 세어 딕셔너리 형태로 반환합니다.
- **`namedtuple`**: 이름으로 각 요소에 접근할 수 있는 튜플을 만듭니다.

```python
# 파일명: collections_module.py

from collections import defaultdict, Counter

# 1. defaultdict 예제
# 'int'를 기본값 팩토리로 지정하면, 존재하지 않는 키 조회 시 0을 기본값으로 생성
word_count = defaultdict(int)
text = "apple banana apple orange banana apple"
for word in text.split():
    word_count[word] += 1

print(f"단어 개수 (defaultdict): {word_count}")


# 2. Counter 예제
# 동일한 작업을 Counter로 훨씬 간단하게 수행 가능
word_count_counter = Counter(text.split())
print(f"단어 개수 (Counter): {word_count_counter}")

# 가장 많이 등장한 단어 2개 찾기
print(f"가장 흔한 단어 2개: {word_count_counter.most_common(2)}")
```

---

`Chapter 05`부터 `Chapter 08`까지의 내용도 준비가 되면 보여주세요. 이어서 멋진 문법 모음집을 만들어 드리겠습니다.