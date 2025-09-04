
---

### Chapter 05: 파이썬 스타일 코딩 (Pythonic Code)

'파이써닉(Pythonic)'하다는 것은 파이썬 언어의 철학과 고유한 기능들을 잘 활용하여 코드를 간결하고, 가독성 높으며, 효율적으로 작성하는 것을 의미합니다.

#### 1. 문자열의 분리 및 결합

##### ◦ `split()` 함수: 문자열 분리
문자열을 특정 구분자(delimiter)를 기준으로 나누어 **리스트(list)**로 만들어 줍니다.

```python
# 파일명: string_split_join.py

# 공백을 기준으로 문자열을 분리합니다.
# split()에 아무 인자도 주지 않으면 공백, 탭, 줄바꿈 등을 기준으로 분리합니다.
sentence = "zero one two three"
word_list = sentence.split()
print(f"원본 문자열: '{sentence}'")
print(f"분리된 리스트: {word_list}") # ['zero', 'one', 'two', 'three']

# 특정 구분자(',')를 기준으로 분리합니다.
csv_data = "사과,바나나,딸기,오렌지"
fruit_list = csv_data.split(',')
print(f"CSV 데이터: '{csv_data}'")
print(f"분리된 과일 리스트: {fruit_list}")
```

##### ◦ `join()` 함수: 문자열 결합
리스트의 각 문자열 요소들을 하나의 문자열로 합쳐줍니다.

```python
# 파일명: string_split_join.py (이어서)

colors = ["빨강", "주황", "노랑", "초록"]

# 1. 구분자 없이 모든 요소를 합칩니다.
combined_colors_no_space = "".join(colors)
print(f"구분자 없이 합치기: '{combined_colors_no_space}'") # '빨강주황노랑초록'

# 2. 공백(' ')을 구분자로 하여 합칩니다.
combined_colors_with_space = " ".join(colors)
print(f"공백으로 합치기: '{combined_colors_with_space}'") # '빨강 주황 노랑 초록'

# 3. 쉼표와 공백(', ')을 구분자로 하여 합칩니다.
combined_colors_with_csv = ", ".join(colors)
print(f"CSV 형태로 합치기: '{combined_colors_with_csv}'") # '빨강, 주황, 노랑, 초록'

# [Pythonic Code 비교]
# 나쁜 예: for 루프와 + 연산으로 문자열 합치기 (느리고 비효율적)
result_bad = ""
for color in colors:
    result_bad += color + " "

# 좋은 예: join() 사용 (빠르고 간결함)
result_good = " ".join(colors)

print(f"나쁜 예 결과: '{result_bad}'")
print(f"좋은 예 결과: '{result_good}'")
```

#### 2. 리스트 컴프리헨션 (List Comprehension)
기존 리스트나 다른 순회 가능한(iterable) 객체를 기반으로, 간결한 한 줄의 코드로 새로운 리스트를 만드는 매우 파이써닉한 방법입니다.

##### ◦ 기본 용법
```python
# 파일명: list_comprehension.py

# for 루프를 사용한 전통적인 방식
result_loop = []
for i in range(1, 6):
    result_loop.append(i * 2)
print(f"For 루프 결과: {result_loop}")

# 리스트 컴프리헨션을 사용한 방식
# [표현식 for 항목 in 리스트]
result_comp = [i * 2 for i in range(1, 6)]
print(f"리스트 컴프리헨션 결과: {result_comp}")
```

##### ◦ 필터링 (`if` 조건 추가)
조건을 만족하는 항목들만으로 새로운 리스트를 만들 수 있습니다.

```python
# 파일명: list_comprehension.py (이어서)

# 1부터 10까지의 숫자 중 짝수만 포함하는 리스트 생성
# [표현식 for 항목 in 리스트 if 조건문]
even_numbers = [i for i in range(1, 11) if i % 2 == 0]
print(f"짝수 리스트: {even_numbers}")

# if-else를 함께 사용하기
# [참일때_표현식 if 조건문 else 거짓일때_표현식 for 항목 in 리스트]
# 홀수는 그대로, 짝수는 '짝수' 문자열로 변환
odd_even_list = [i if i % 2 != 0 else '짝수' for i in range(1, 11)]
print(f"홀짝 변환 리스트: {odd_even_list}")
```

##### ◦ 중첩 반복문
`for`문을 여러 개 사용하여 복잡한 리스트도 생성할 수 있습니다.

```python
# 파일명: list_comprehension.py (이어서)

word_1 = "ABC"
word_2 = "DEF"

# 중첩 for 루프: 앞의 for문(word_1)이 바깥 루프가 됨
# A에 대해 D, E, F를 조합하고, B에 대해 D, E, F를 조합...
nested_list = [i + j for i in word_1 for j in word_2]
print(f"중첩 반복문 결과 (1차원): {nested_list}")
# ['AD', 'AE', 'AF', 'BD', 'BE', 'BF', 'CD', 'CE', 'CF']```

##### ◦ 이차원 리스트 생성
리스트 컴프리헨션을 중첩하여 이차원 리스트를 만들 수 있습니다.

```python
# 파일명: list_comprehension.py (이어서)

# 각 단어의 [대문자, 소문자, 길이]를 요소로 갖는 이차원 리스트 생성
words = ['apple', 'banana', 'cherry']
case_list = [[w.upper(), w.lower(), len(w)] for w in words]
print(f"단어 정보 (2차원): {case_list}")

# [주의] 중첩 for문의 실행 순서에 따른 1차원 vs 2차원 리스트
case_1 = ["A", "B", "C"]
case_2 = ["D", "E"]

# 1차원 리스트: 바깥 for문(j)이 먼저 실행됨
one_dim = [i + j for j in case_2 for i in case_1]
print(f"1차원 중첩: {one_dim}") # ['AD', 'BD', 'CD', 'AE', 'BE', 'CE']

# 2차원 리스트: 대괄호가 하나 더 있으며, 바깥 for문(j)이 고정되고 안쪽 컴프리헨션이 실행됨
two_dim = [[i + j for i in case_1] for j in case_2]
print(f"2차원 중첩: {two_dim}") # [['AD', 'BD', 'CD'], ['AE', 'BE', 'CE']]
```

#### 3. 다양한 방식의 리스트값 출력

##### ◦ `enumerate()` 함수
리스트를 순회할 때 **인덱스(index)와 값(value)**을 동시에 얻고 싶을 때 사용합니다.

```python
# 파일명: enumerate_zip.py

my_list = ['tic', 'tac', 'toe']

# enumerate()를 사용하여 인덱스와 값을 함께 출력
for index, value in enumerate(my_list):
    print(f"인덱스: {index}, 값: {value}")

# enumerate() 결과를 딕셔너리로 변환
# {0: 'tic', 1: 'tac', 2: 'toe'}
my_dict = {i: v for i, v in enumerate(my_list)}
print(f"딕셔너리로 변환: {my_dict}")
```

##### ◦ `zip()` 함수
여러 개의 리스트(또는 iterable)를 병렬적으로 묶어, 같은 인덱스에 있는 요소들끼리 튜플로 묶어줍니다.

```python
# 파일명: enumerate_zip.py (이어서)

alist = ['a1', 'a2', 'a3']
blist = ['b1', 'b2', 'b3']
numbers = [1, 2, 3]

# 두 개의 리스트를 병렬로 묶어 출력
for a, b in zip(alist, blist):
    print(f"{a}, {b}")

# 세 개의 리스트를 묶어 계산
# 각 튜플의 합계를 구함 ('a1b1', 3), ('a2b2', 5) 등은 불가능하므로 문자열과 숫자 분리
for (a, b), num in zip(zip(alist, blist), numbers):
    print(f"{a}와 {b}에 해당하는 숫자는 {num}입니다.")

# 같은 위치의 숫자끼리 더하기
list1 = [1, 2, 3]
list2 = [10, 20, 30]
sums = [x + y for x, y in zip(list1, list2)]
print(f"각 요소의 합: {sums}") # [11, 22, 33]
```

#### 4. 람다(Lambda) 함수
이름이 없는 한 줄짜리 간단한 함수를 만들 때 사용합니다. `def` 키워드 없이 함수를 정의할 수 있어 코드가 간결해집니다.
**`lambda 매개변수: 표현식`**

```python
# 파일명: lambda_function.py

# def를 사용한 일반적인 함수 정의
def add(x, y):
    return x + y

# lambda를 사용한 익명 함수 정의
lambda_add = lambda x, y: x + y

# 두 함수의 사용법과 결과는 동일
print(f"def 함수 결과: {add(3, 5)}")
print(f"lambda 함수 결과: {lambda_add(3, 5)}")

# 람다는 다른 함수의 인자로 전달될 때 유용하게 사용됨
# 예: 리스트 정렬 시 key로 람다 함수 사용
pairs = [(1, 'one'), (3, 'three'), (2, 'two')]
# 각 튜플의 두 번째 요소(문자열)를 기준으로 정렬
pairs.sort(key=lambda pair: pair[1])
print(f"람다로 정렬된 리스트: {pairs}")
```

#### 5. 별표(`*`) 활용 (Asterisk)

##### ◦ 함수 정의 시: 가변 인수 (`*args`, `**kwargs`)
- `*args`: 여러 개의 위치 인수를 **튜플**로 받습니다.
- `**kwargs`: 여러 개의 키워드 인수를 **딕셔너리**로 받습니다.

```python
# 파일명: asterisk_usage.py

def variable_args_test(first_arg, *args, **kwargs):
    print(f"첫 번째 인수: {first_arg}")
    print(f"나머지 위치 인수 (튜플): {args}")
    print(f"나머지 키워드 인수 (딕셔너리): {kwargs}")

variable_args_test('hello', 1, 2, 3, name='Python', version=3.9)
```

##### ◦ 함수 호출 시 & 일반 사용: 언패킹 (Unpacking)
리스트, 튜플, 딕셔너리 등의 컬렉션 자료형 앞에 별표를 붙여 그 안의 요소들을 풀어헤치는 기능입니다.

```python
# 파일명: asterisk_usage.py (이어서)

# 1. 리스트/튜플 언패킹 (*)
def print_three_numbers(a, b, c):
    print(a, b, c)

numbers = [10, 20, 30]
# print_three_numbers(numbers) # TypeError 발생
print_three_numbers(*numbers)  # numbers가 언패킹되어 10, 20, 30으로 전달됨

# 2. zip과 함께 사용하여 2차원 리스트의 행과 열을 바꾸기 (Transpose)
scores = [
    (1, 90, 85), # (학생번호, 수학, 영어)
    (2, 95, 88),
    (3, 80, 79)
]
# scores를 언패킹하면 (1, 90, 85), (2, 95, 88), (3, 80, 79) 세 개의 튜플이 zip에 전달됨
# zip은 각 튜플의 0번째, 1번째, 2번째 요소를 묶어줌
unzipped_scores = list(zip(*scores))
print(f"행/열 전환 결과: {unzipped_scores}")
# [(1, 2, 3), (90, 95, 80), (85, 88, 79)]
student_ids, math_scores, english_scores = unzipped_scores
print(f"수학 점수: {math_scores}")

# 3. 딕셔너리 언패킹 (**)
def print_user_info(name, age, city):
    print(f"이름: {name}, 나이: {age}, 도시: {city}")

user_data = {"name": "김철수", "age": 25, "city": "서울"}
# 딕셔너리가 키워드 인수 (name='김철수', age=25, city='서울')로 언패킹됨
print_user_info(**user_data)
```

//=====================================================================================

### Chapter 06: 객체 지향 프로그래밍 (OOP)

객체 지향 프로그래밍은 데이터를 나타내는 **객체(Object)**와 그 객체가 수행할 수 있는 **행동(Method)**을 중심으로 프로그래밍하는 방식입니다.

#### 1. 클래스와 객체

- **클래스(Class)**: 객체를 만들기 위한 '설계도' 또는 '틀'입니다. 객체가 가질 데이터(속성)와 기능(메서드)을 정의합니다.
- **객체(Object) / 인스턴스(Instance)**: 클래스라는 설계도를 바탕으로 실제로 메모리에 생성된 실체입니다.

#### 2. 클래스 구현하기

```python
# 파일명: oop_soccer_player.py

# '축구선수'에 대한 설계도(클래스)를 만듭니다.
# 클래스 이름은 보통 대문자로 시작합니다 (CamelCase).
class SoccerPlayer:
    # 생성자(constructor) 메서드: 객체가 생성될 때 자동으로 호출됩니다.
    # self는 생성되는 객체(인스턴스) 자기 자신을 가리킵니다.
    # __init__ 메서드는 객체의 속성(attribute)을 초기화하는 역할을 합니다.
    def __init__(self, name, position, back_number):
        print(f"'{name}' 선수 객체가 생성되었습니다.")
        self.name = name          # self.name은 이 객체의 '이름' 속성
        self.position = position  # self.position은 이 객체의 '포지션' 속성
        self.back_number = back_number # self.back_number는 이 객체의 '등번호' 속성

    # 등번호를 변경하는 메서드(기능)입니다.
    # 클래스 내의 모든 메서드는 첫 번째 매개변수로 self를 가져야 합니다.
    def change_back_number(self, new_number):
        print(f"{self.name} 선수의 등번호를 {self.back_number}에서 {new_number}로 변경합니다.")
        self.back_number = new_number

    # __str__ 메서드: 객체를 print() 함수로 출력할 때 표시될 문자열을 정의합니다.
    def __str__(self):
        return f"Hello, 제 이름은 {self.name}이고, 포지션은 {self.position}입니다."

# --- 인스턴스 사용하기 ---

# SoccerPlayer 클래스를 이용해 첫 번째 객체 'jinhyun'을 생성합니다.
# 이 때 __init__ 메서드가 자동으로 호출됩니다.
jinhyun = SoccerPlayer("김진현", "MF", 10)

# 두 번째 객체 'heungmin'을 생성합니다.
heungmin = SoccerPlayer("손흥민", "FW", 7)

# 각 객체의 속성에 직접 접근할 수 있습니다.
print(f"첫 번째 선수의 이름은 {jinhyun.name}이고, 등번호는 {jinhyun.back_number}번 입니다.")
print(f"두 번째 선수의 이름은 {heungmin.name}이고, 등번호는 {heungmin.back_number}번 입니다.")

# 객체의 메서드를 호출합니다.
heungmin.change_back_number(17)
print(f"손흥민 선수의 변경된 등번호: {heungmin.back_number}")

# __str__ 메서드 호출 예시
# print(인스턴스)를 실행하면 __str__ 메서드가 반환하는 문자열이 출력됩니다.
print(jinhyun)
print(heungmin)
```

#### 3. 객체 지향 프로그래밍의 특징

##### ◦ 상속 (Inheritance)
부모 클래스의 모든 속성과 메서드를 자식 클래스가 물려받아 사용할 수 있는 기능입니다. 코드 재사용성을 높여줍니다.

```python
# 파일명: oop_inheritance.py

# 부모 클래스: Person
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def about_me(self):
        print(f"제 이름은 {self.name}이고, {self.age}살 입니다.")

# 자식 클래스: Employee가 Person을 상속받음
# class 자식클래스(부모클래스):
class Employee(Person):
    # 메서드 오버라이딩(Method Overriding)
    # 부모의 메서드를 자식 클래스에서 재정의하는 것
    def __init__(self, name, age, salary):
        # super()를 사용하여 부모 클래스의 __init__을 호출
        super().__init__(name, age)
        self.salary = salary

    def about_me(self):
        # 부모의 about_me 메서드를 먼저 호출
        super().about_me()
        print(f"제 연봉은 {self.salary}원 입니다.")

# Person 클래스의 인스턴스 생성
p1 = Person("김사람", 40)
p1.about_me()

print("-" * 20)

# Employee 클래스의 인스턴스 생성
# Employee는 Person의 속성(name, age)과 메서드(about_me)를 물려받음
e1 = Employee("박직원", 30, 5000)
e1.about_me() # 재정의된 about_me가 호출됨
```

##### ◦ 다형성 (Polymorphism)
같은 이름의 메서드라도, 서로 다른 클래스의 객체에서 호출될 때 각 객체의 특성에 맞게 다르게 동작하는 것을 의미합니다.

```python
# 파일명: oop_polymorphism.py

class Animal:
    def talk(self):
        # 이 메서드는 자식 클래스에서 반드시 구현해야 함을 명시
        raise NotImplementedError("Subclass must implement abstract method")

class Cat(Animal):
    def talk(self):
        return "야옹!"

class Dog(Animal):
    def talk(self):
        return "멍멍!"

# Animal 리스트에 Cat과 Dog 객체를 함께 담음
animals = [Cat(), Dog(), Cat()]

# 같은 animal.talk() 호출이지만, 객체의 실제 타입(Cat 또는 Dog)에 따라
# 다른 결과가 출력됨 -> 이것이 다형성
for animal in animals:
    print(animal.talk())
```

##### ◦ 캡슐화와 가시성 (Encapsulation & Visibility)
- **캡슐화**: 데이터(속성)와 그 데이터를 처리하는 코드(메서드)를 하나의 객체로 묶는 것.
- **정보 은닉 (가시성)**: 객체 내부의 중요한 데이터에 외부에서 직접 접근하지 못하도록 막는 것.
  - 파이썬에서는 변수나 메서드 이름 앞에 밑줄(`_`, `__`)을 붙여 접근 수준을 제어합니다.
    - `_variable`: 내부적으로만 사용하라는 '관례적인' 약속 (문법적으로 막히진 않음)
    - `__variable`: 클래스 외부에서 직접 접근하기 어렵게 만드는 '네임 맹글링(name mangling)'이 적용됨 (강한 private)

```python
# 파일명: oop_visibility.py

class Inventory:
    def __init__(self):
        # __items: 외부에서 직접 접근을 막고 싶은 private 변수
        self.__items = []

    def add_item(self, item):
        print(f"'{item}'을 추가합니다.")
        self.__items.append(item)

    def get_item_count(self):
        return len(self.__items)

    # @property: 메서드를 속성처럼 호출할 수 있게 해주는 데코레이터 (getter)
    # 이를 통해 private 변수를 안전하게 외부로 노출(읽기 전용)할 수 있음
    @property
    def items(self):
        print("모든 아이템을 조회합니다.")
        return self.__items

# 인스턴스 생성
my_inventory = Inventory()
my_inventory.add_item("노트북")
my_inventory.add_item("마우스")

# private 변수에는 직접 접근이 어려움
# print(my_inventory.__items) # AttributeError: 'Inventory' object has no attribute '__items'

# public 메서드를 통해 내부 데이터에 접근
print(f"총 아이템 개수: {my_inventory.get_item_count()}")

# @property로 정의된 items는 괄호 없이 속성처럼 접근
print(f"현재 인벤토리: {my_inventory.items}")
```

### Chapter 07: 데이터 분석 라이브러리 (NumPy, Pandas, Matplotlib)

#### 1. NumPy (Numerical Python)
- 대규모 다차원 배열과 행렬 연산에 필요한 다양한 함수를 제공하는 라이브러리. 데이터 분석 및 과학 계산의 핵심입니다.

```python
# 파일명: numpy_basic.py
import numpy as np

# 1. 파이썬 리스트를 NumPy 배열로 변환
py_list = [1, 2, 3, 4, 5]
np_array = np.array(py_list)

print(f"파이썬 리스트: {py_list}")
print(f"NumPy 배열: {np_array}")

# 2. NumPy 배열의 연산 (Vectorization)
# 배열의 각 요소에 대해 한 번에 연산이 수행됨
print(f"배열 + 2: {np_array + 2}")
print(f"배열 * 3: {np_array * 3}")

# 3. 다양한 배열 생성
zeros_array = np.zeros((2, 3)) # 2x3 크기의 0으로 채워진 배열
print(f"0으로 채워진 배열:\n{zeros_array}")

ones_array = np.ones(5) # 1로 채워진 1차원 배열 (5개 요소)
print(f"1로 채워진 배열: {ones_array}")

# 4. 배열 슬라이싱
arr = np.array([10, 20, 30, 40, 50])
print(f"슬라이싱 (1~3): {arr[1:4]}") # [20 30 40]

# 5. Boolean 인덱싱
# 조건에 맞는 요소만 추출
bool_arr = arr > 25
print(f"25보다 큰 요소만 추출: {arr[bool_arr]}") # [30 40 50]
```

#### 2. Pandas (Python Data Analysis Library)
- 행과 열로 이루어진 2차원 테이블 형태의 데이터를 다루는 데 최적화된 라이브러리. `Series`(1차원)와 `DataFrame`(2차원)이라는 핵심 자료구조를 제공합니다.

```python
# 파일명: pandas_basic.py
import pandas as pd

# 1. DataFrame 생성
data = {
    'names': ['민준', '현우', '서연', '동현'],
    'years': [2013, 2014, 2015, 2016],
    'points': [1.5, 1.7, 3.6, 2.4]
}
df = pd.DataFrame(data)
print("--- DataFrame ---")
print(df)

# 2. 데이터 확인
print("\n--- 데이터 미리보기 (head) ---")
print(df.head(2)) # 상위 2개 행

print("\n--- 기본 통계 정보 (describe) ---")
print(df.describe())

# 3. 열(Column) 선택 및 조작
names_col = df['names'] # 'names' 열 선택 (결과는 Series)
print(f"\nNames 열:\n{names_col}")

# 새로운 열 추가
df['penalty'] = [0.1, 0.2, 0.3, 0.4]
print("\n--- 'penalty' 열 추가 후 ---")
print(df)

# 4. 행(Row) 선택
# loc: 레이블(이름) 기반 인덱싱
row_1 = df.loc[1]
print(f"\n인덱스 1의 행 (loc):\n{row_1}")

# Boolean 인덱싱으로 조건에 맞는 행 선택
high_points_df = df[df['points'] > 2.0]
print("\n--- points가 2.0보다 큰 행 ---")
print(high_points_df)
```

#### 3. Matplotlib
- 데이터를 시각화하여 그래프로 나타내는 라이브러리. 선 그래프, 막대 그래프, 산점도, 히스토그램 등 다양한 형태의 그래프를 그릴 수 있습니다.

```python
# 파일명: matplotlib_basic.py
import matplotlib.pyplot as plt
import numpy as np

# 한글 폰트 설정 (Windows 예시)
from matplotlib import font_manager, rc
font_path = "c:/Windows/Fonts/malgun.ttf"
font = font_manager.FontProperties(fname=font_path).get_name()
rc('font', family=font)

# 1. 선 그래프 (plot)
x_values = [1, 2, 3, 4, 5]
y_values = [1, 4, 9, 16, 25]

plt.figure(figsize=(8, 5)) # 그래프 크기 설정
plt.plot(x_values, y_values, marker='o') # 마커 추가

# 그래프 꾸미기
plt.title("간단한 선 그래프")
plt.xlabel("X 축")
plt.ylabel("Y 축 (X^2)")
plt.grid(True) # 그리드 표시
plt.show()

# 2. 막대 그래프 (bar)
customers = ['A', 'B', 'C', 'D', 'E']
sale_amounts = [127, 90, 201, 111, 232]

plt.figure(figsize=(8, 5))
plt.bar(customers, sale_amounts, color='skyblue')

plt.title("고객별 판매 금액")
plt.xlabel("고객명")
plt.ylabel("판매 금액")
plt.show()

# 3. 산점도 (scatter)
np.random.seed(0) # 재현 가능성을 위해 시드 설정
x_data = np.random.rand(50) * 100
y_data = np.random.rand(50) * 100

plt.figure(figsize=(8, 5))
plt.scatter(x_data, y_data, c='coral')

plt.title("X와 Y의 관계 (산점도)")
plt.xlabel("X 데이터")
plt.ylabel("Y 데이터")
plt.show()
```

//=====================================================================================

### Chapter 08: 데이터베이스 연동

파이썬은 다양한 데이터베이스 시스템(SQLite, Oracle, MySQL 등)과 연동할 수 있는 라이브러리를 제공합니다.

#### 1. SQLite
- 별도의 서버 설치 없이 파일 기반으로 동작하는 가벼운 데이터베이스입니다. 파이썬에 기본 내장되어 있습니다.

```python
# 파일명: sqlite_example.py
import sqlite3

# 1. DB 연결 및 테이블 생성
conn = sqlite3.connect('my_books.db') # DB 파일에 연결 (없으면 자동 생성)
cursor = conn.cursor() # SQL을 실행하기 위한 커서 생성

# 테이블이 없으면 생성
cursor.execute('''
CREATE TABLE IF NOT EXISTS books (
    title TEXT,
    published_date TEXT,
    publisher TEXT,
    pages INTEGER,
    recommend INTEGER
)
''')
conn.commit() # 변경사항 저장
conn.close() # 연결 종료

# 2. 데이터 삽입
def insert_book(data):
    conn = sqlite3.connect('my_books.db')
    cursor = conn.cursor()
    # SQL 쿼리의 ?는 플레이스홀더로, 보안상 안전함 (SQL Injection 방지)
    sql = 'INSERT INTO books (title, published_date, publisher, pages, recommend) VALUES (?, ?, ?, ?, ?)'
    cursor.execute(sql, data)
    conn.commit()
    conn.close()
    print(f"'{data[0]}' 데이터가 삽입되었습니다.")

# 3. 데이터 조회
def select_all_books():
    conn = sqlite3.connect('my_books.db')
    cursor = conn.cursor()
    cursor.execute("SELECT * FROM books")
    
    # fetchall()은 모든 결과를 리스트 형태로 가져옴
    books = cursor.fetchall()
    
    print("\n--- 모든 책 목록 ---")
    for book in books:
        print(book)
    
    conn.close()

# --- 실행 ---
# 데이터가 중복 삽입되지 않도록 초기화 (실습용)
conn = sqlite3.connect('my_books.db'); conn.execute("DELETE FROM books"); conn.commit(); conn.close()

insert_book(('Python', '2020-01-01', '한빛', 584, 20))
insert_book(('Java', '2019-05-20', '길벗', 500, 10))
select_all_books()
```