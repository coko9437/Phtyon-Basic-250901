
---

## 🐍 파이썬 문법 모음집 (Chapter 06 ~ 07)

### Chapter 06: 객체 지향 프로그래밍 (OOP)

객체 지향 프로그래밍(Object-Oriented Programming)은 데이터를 나타내는 **객체(Object)**와 그 객체가 수행할 수 있는 **행동(Method)**을 중심으로 프로그래밍하는 패러다임입니다. 코드의 재사용성을 높이고, 유지보수를 용이하게 만듭니다.

#### 1. 클래스와 객체 (Class & Object)

-   **클래스(Class)**: 객체를 만들기 위한 '설계도' 또는 '틀'입니다. 객체가 가질 데이터(**속성**)와 기능(**메서드**)을 정의합니다.
-   **객체(Object) / 인스턴스(Instance)**: 클래스라는 설계도를 바탕으로 실제 메모리에 생성된 실체입니다.
-   **속성(Attribute)**: 객체의 상태나 데이터를 나타내는 변수입니다. (예: 사람의 이름, 나이)
-   **메서드(Method)**: 객체가 수행할 수 있는 동작을 나타내는 클래스 내의 함수입니다. (예: 사람이 걷다, 말하다)

```python
# 파일명: oop_basic_syntax.py

# 클래스의 기본 문법 구조
class ClassName:
    # 생성자 메서드(initializer): 객체가 생성될 때 자동으로 호출되어 속성을 초기화합니다.
    def __init__(self, param1, param2):
        # self는 생성되는 객체(인스턴스) 자기 자신을 가리킵니다.
        # self.attribute_name 형태로 객체의 속성을 정의하고 값을 할당합니다.
        self.attribute1 = param1
        self.attribute2 = param2

    # 일반 메서드(기능): 객체가 수행할 동작을 정의합니다.
    # 첫 번째 매개변수는 반드시 self여야 합니다.
    def method_name(self, extra_param):
        # self.attribute1 과 같이 자신의 속성에 접근할 수 있습니다.
        print(f"속성1: {self.attribute1}, 추가 매개변수: {extra_param}")
```

#### 2. 클래스 실제 구현 예제

`Person`이라는 클래스를 통해 실제 객체를 어떻게 만들고 사용하는지 알아봅니다.

```python
# 파일명: person_class_example.py

# '사람'에 대한 설계도(클래스)를 만듭니다.
class Person:
    # 클래스 변수: 이 클래스로부터 생성된 모든 객체(인스턴스)가 공유하는 변수입니다.
    # '빵틀' 자체에 붙어있는 라벨과 같습니다.
    species = "Homo sapiens"

    # 생성자 메서드: 객체가 생성될 때 이름과 나이를 받아 초기화합니다.
    def __init__(self, name, age):
        # 인스턴스 변수: 각 객체(인스턴스)마다 독립적으로 가지는 변수입니다.
        # '빵'마다 다른 토핑과 같습니다.
        self.name = name
        self.age = age
        print(f"'{self.name}' 객체가 생성되었습니다. (생성자 호출)")

    # 인스턴스 메서드: 객체의 속성을 사용하여 동작을 수행합니다.
    def introduce(self):
        print(f"안녕하세요, 제 이름은 {self.name}이고, 나이는 {self.age}살입니다.")

    # 특수 메서드(__str__): print(객체)를 호출할 때 표시될 문자열을 정의합니다.
    # Java의 toString() 오버라이딩과 유사합니다.
    def __str__(self):
        return f"[Person 객체: 이름={self.name}, 나이={self.age}]"

    # 클래스 메서드: @classmethod 데코레이터를 사용합니다.
    # 객체를 생성하지 않고 '클래스' 자체로 호출할 수 있는 메서드입니다.
    # 첫 인자로 클래스 자신(cls)을 받습니다.
    @classmethod
    def get_species(cls):
        return cls.species

# --- 클래스 사용하기 ---

# Person 클래스를 이용해 첫 번째 사람(객체) 'p1'을 생성합니다.
p1 = Person("홍길동", 30)
# Person 클래스를 이용해 두 번째 사람(객체) 'p2'를 생성합니다.
p2 = Person("이순신", 45)

# 각 객체의 인스턴스 메서드를 호출합니다.
print("\n--- 자기소개 시작 ---")
p1.introduce()
p2.introduce()

# 객체의 속성에 직접 접근합니다.
print(f"\n첫 번째 사람의 이름: {p1.name}")

# 클래스 변수는 객체를 통해서도, 클래스 이름을 통해서도 접근 가능합니다.
print(f"\np1의 종: {p1.species}")
print(f"p2의 종: {p2.species}")
print(f"Person 클래스의 종: {Person.species}")

# 클래스 메서드는 클래스 이름으로 직접 호출하는 것이 일반적입니다.
print(f"Person의 종(클래스 메서드 호출): {Person.get_species()}")

# __str__ 메서드 확인: print() 함수에 객체를 넣으면 __str__이 반환하는 문자열이 출력됩니다.
print(f"\np1 객체 정보 출력: {p1}")
```

#### 3. 상속 (Inheritance)

상속은 부모 클래스의 모든 속성과 메서드를 자식 클래스가 물려받아, 기능을 확장하거나 변경하여 사용하는 OOP의 핵심 기능입니다. 코드의 재사용성을 극대화합니다.

```python
# 파일명: inheritance_example.py

# 부모 클래스: 모든 '탈것'의 공통적인 특징을 정의합니다.
class Vehicle:
    def __init__(self, speed):
        self.speed = speed
        print(f"부모 클래스(Vehicle) 생성자 호출: 시속 {self.speed}km로 생성되었습니다.")

    def drive(self):
        print(f"탈것이 시속 {self.speed}km로 달립니다.")

# 자식 클래스: Vehicle을 상속받아 '자동차'를 정의합니다.
# class 자식클래스(부모클래스):
class Car(Vehicle):
    # 자식 클래스에만 있는 고유한 메서드를 추가합니다.
    def honk(self):
        print("빵빵! 자동차가 경적을 울립니다.")

# --- 상속 사용하기 ---
# '자동차' 객체를 생성합니다. Car 클래스에는 __init__이 없지만,
# 부모인 Vehicle의 __init__이 자동으로 호출됩니다.
my_car = Car(100)

# 부모(Vehicle)로부터 물려받은 메서드를 사용합니다.
my_car.drive()

# 자신(Car)에게만 있는 고유한 메서드를 사용합니다.
my_car.honk()

# 부모(Vehicle)로부터 물려받은 속성에도 접근 가능합니다.
print(f"이 자동차의 현재 속도는 {my_car.speed}km/h 입니다.")
```

#### 4. 다형성 (Polymorphism)

다형성은 '여러 형태를 가진다'는 뜻으로, 같은 이름의 메서드를 호출하더라도 객체의 실제 타입에 따라 서로 다른 동작을 하는 특징을 말합니다.

```python
# 파일명: polymorphism_example.py

# 부모 클래스
class Animal:
    def speak(self):
        # 자식 클래스에서 이 메서드를 반드시 재정의(override)하도록 유도
        raise NotImplementedError("자식 클래스에서 speak 메서드를 구현해야 합니다.")

# 자식 클래스 1
class Dog(Animal):
    def speak(self):
        return "멍멍!"

# 자식 클래스 2
class Cat(Animal):
    def speak(self):
        return "야옹~"

# --- 다형성 실행 ---
# 리스트에는 Animal의 자식 클래스인 Dog와 Cat 객체가 함께 담겨 있습니다.
animals = [Dog(), Cat(), Dog()]

# 반복문을 통해 각 동물의 소리를 들어봅니다.
for animal in animals:
    # 똑같이 animal.speak()를 호출했지만,
    # animal 변수에 할당된 실제 객체가 Dog냐 Cat이냐에 따라
    # 다른 결과가 출력됩니다. 이것이 다형성입니다.
    print(f"이 동물의 소리는? {animal.speak()}")
```

#### 5. 가시성 (Visibility) - 정보 은닉

객체 내부의 중요한 데이터에 외부에서 직접 접근하는 것을 막고, 허용된 메서드를 통해서만 접근하도록 제어하는 기능입니다. 데이터의 무결성을 지키는 데 중요합니다.

-   **Public (공개)**: `name` - 어디서든 자유롭게 접근 가능.
-   **Protected (보호)**: `_age` - 클래스 자신과 자식 클래스에서만 사용하자는 '관례적 약속'. (문법적으로 강제되지는 않음)
-   **Private (비공개)**: `__balance` - 클래스 내부에서만 사용 가능. 외부에서 직접 접근 시 `Name Mangling` 기술로 이름이 바뀌어 접근이 어려워짐.

```python
# 파일명: visibility_example.py

# 1. Public 멤버: 직접 접근의 문제점
class PersonDirect:
    def __init__(self, name, age):
        self.name = name
        self.age = age # 나이에 누구나 직접 접근 가능

p1 = PersonDirect("홍길동", 30)
p1.age = -100 # 논리적으로 잘못된 값을 막을 방법이 없음
print(f"직접 접근으로 변경된 나이: {p1.age}")


# 2. @property를 이용한 접근 제어 (Pythonic한 방법)
class PersonProperty:
    def __init__(self, name, age):
        self.name = name
        self._age = age  # 실제 데이터는 보호 멤버(_age)에 저장

    # getter: 'age' 속성을 읽으려고 할 때 호출됨
    @property
    def age(self):
        print(">> getter가 호출되었습니다.")
        return self._age

    # setter: 'age' 속성에 값을 할당하려고 할 때 호출됨
    @age.setter
    def age(self, value):
        print(">> setter가 호출되었습니다.")
        # 값의 유효성을 검사하는 로직을 추가할 수 있음
        if value > 0:
            self._age = value
        else:
            print("🚨 오류: 나이는 0보다 커야 합니다.")

p2 = PersonProperty("이순신", 45)
print(f"\n초기 나이: {p2.age}") # getter 호출
p2.age = 50                 # setter 호출
p2.age = -10                # setter의 유효성 검사에 걸림
print(f"최종 나이: {p2.age}")


# 3. Private 멤버: 강력한 접근 제한
class PersonPrivate:
    def __init__(self, secret):
        self.__secret = secret # 비공개 멤버

    def get_secret(self): # 비공개 멤버에 접근할 수 있는 public 메서드
        return self.__secret

p3 = PersonPrivate("중요한 비밀번호")
print(f"\n메서드를 통한 접근: {p3.get_secret()}")

# 비공개 멤버에 직접 접근 시도 시 오류 발생
try:
    print(p3.__secret)
except AttributeError as e:
    print(f"직접 접근 시도 결과: {e}")
```

//=====================================================================================

### Chapter 07: 데이터 분석 라이브러리

#### 1. NumPy (Numerical Python)

NumPy는 대규모 다차원 배열과 행렬 연산을 위한 파이썬의 핵심 라이브러리입니다. 내부적으로 C언어로 구현되어 매우 빠른 연산 속도를 제공하며, 데이터 과학 분야의 기반이 됩니다.

##### ◦ NumPy의 핵심 `ndarray`
-   **ndarray (N-dimensional array)**: NumPy의 기본 데이터 구조로, 모든 요소는 동일한 자료형을 가집니다.
-   **벡터화 연산(Vectorization)**: 반복문 없이 배열 전체에 대해 한 번에 연산을 수행하여 코드가 간결하고 속도가 매우 빠릅니다.

```python
# 파일명: numpy_intro.py
import numpy as np # 관례적으로 np라는 별칭을 사용합니다.

# 1. NumPy 배열 생성
# 파이썬 리스트를 np.array() 함수에 전달하여 ndarray를 만듭니다.
my_list2d = [[1, 2, 3], [4, 5, 6]]
arr2d = np.array(my_list2d)

print("--- 2차원 배열 (ndarray) ---")
print(arr2d)

# 배열의 정보 확인
print(f"배열의 모양 (shape): {arr2d.shape}")     # (2, 3) -> 2행 3열
print(f"배열의 차원 (ndim): {arr2d.ndim}")       # 2
print(f"요소의 자료형 (dtype): {arr2d.dtype}") # int32 또는 int64

# 2. 벡터화 연산
# 반복문 없이 배열의 모든 요소에 10을 더합니다.
result_np = arr2d + 10
print("\n--- 벡터화 연산 결과 (배열 + 10) ---")
print(result_np)
```

##### ◦ 자주 사용하는 NumPy 기능

```python
# 파일명: numpy_features.py
import numpy as np

# 1. 다양한 배열 생성
arr_range = np.arange(10) # 0부터 9까지의 값을 가진 배열
arr_zeros = np.zeros((2, 3)) # 2x3 크기의 0으로 채워진 배열
print(f"arange(10):\n{arr_range}")
print(f"zeros((2,3)):\n{arr_zeros}")

# 2. 배열 모양 변경 (Reshape)
arr = np.arange(12) # 0부터 11까지의 1차원 배열
reshaped_arr = arr.reshape(3, 4) # 3행 4열의 2차원 배열로 변경
print(f"\nReshaped (3,4):\n{reshaped_arr}")

# 3. 인덱싱과 슬라이싱
# 1행 2열 요소 접근 (0부터 시작)
element = reshaped_arr[1, 2] # 결과: 6
# 첫 번째 행 전체
first_row = reshaped_arr[0]  # 결과: [0 1 2 3]
print(f"\n1행 2열 요소: {element}")
print(f"첫 번째 행: {first_row}")

# 4. 불리언 인덱싱 (조건에 맞는 데이터 선택)
condition = reshaped_arr > 5 # 5보다 큰 요소에 대한 boolean 마스크 생성
filtered_arr = reshaped_arr[condition] # True인 위치의 요소만 추출
print(f"\n5보다 큰 요소들: {filtered_arr}")

# 5. 기본 통계 연산
print(f"\n전체 합계: {np.sum(reshaped_arr)}")
# axis=0: 각 열(column)을 기준으로 연산
print(f"각 열의 합계: {np.sum(reshaped_arr, axis=0)}")
# axis=1: 각 행(row)을 기준으로 연산
print(f"각 행의 평균: {np.mean(reshaped_arr, axis=1)}")```

##### ◦ NumPy 중급 기능

```python
# 파일명: numpy_intermediate.py
import numpy as np

# 1. 배열 합치기 (Concatenation)
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])
# 세로 방향(행 추가)으로 합치기
v_concat = np.concatenate((arr1, arr2), axis=0)
print(f"세로 합치기:\n{v_concat}")

# 2. 고유값 찾기 및 개수 세기 (Unique)
arr = np.array([1, 2, 5, 2, 3, 1, 5, 5, 6])
unique_vals, counts = np.unique(arr, return_counts=True)
print(f"\n고유값: {unique_vals}, 각 값의 개수: {counts}")

# 3. 조건에 따라 값 선택 (where)
arr = np.arange(1, 11)
# 짝수이면 원래 값을, 홀수이면 0으로 바꾸기
result_even = np.where(arr % 2 == 0, arr, 0)
print(f"\n짝수만 남기기 (where):\n{result_even}")

# 4. 결측치(NaN) 다루기
data = np.array([1, 2, np.nan, 4, 5, np.nan])
# nan 값을 무시하고 합계 계산
print(f"\nnansum() 결과: {np.nansum(data)}")
# nan 값을 0으로 대체
data_filled = np.where(np.isnan(data), 0, data)
print(f"결측치를 0으로 채운 배열: {data_filled}")
```

#### 2. Pandas (Python Data Analysis Library)

Pandas는 행과 열로 이루어진 2차원 테이블 형태의 데이터를 다루는 데 최적화된 라이브러리입니다. `Series`(1차원)와 `DataFrame`(2차원)이라는 핵심 자료구조를 제공합니다.

##### ◦ `Series`와 `DataFrame`

-   **`Series`**: 인덱스(index)를 가진 1차원 배열. 하나의 열(column)에 해당합니다.
-   **`DataFrame`**: 여러 개의 `Series`가 모여 만들어진 2차원 테이블. Pandas의 가장 핵심적인 데이터 구조입니다.

```python
# 파일명: pandas_intro.py
import pandas as pd

# 1. DataFrame 생성 (딕셔너리 사용)
student_data = {
    '이름': ['김판다', '이효리', '유재석', '강호동'],
    '학년': [2, 4, 1, 3],
    '점수': [85, 95, 70, 88]
}
df = pd.DataFrame(student_data)
print("--- 학생 정보 DataFrame ---")
print(df)

# 2. 열(Column) 선택
# 하나의 열을 선택하면 Series가 반환됩니다.
names_series = df['이름']
print("\n--- '이름' 열 (Series) ---")
print(names_series)

# 3. 조건으로 데이터 필터링 (Boolean Indexing)
# 점수가 90점 이상인 학생들만 추출합니다.
high_scores_df = df[df['점수'] >= 90]
print("\n--- 점수가 90점 이상인 학생 ---")
print(high_scores_df)
```

##### ◦ 자주 사용하는 Pandas 기능

```python
# 파일명: pandas_features.py
import pandas as pd
import numpy as np

data = {
    '카테고리': ['과일', '과일', '음료', '음료', '과일'],
    '상품명': ['사과', '바나나', '콜라', '주스', '포도'],
    '가격': [3000, 2000, 1500, 2500, 4000],
    '판매량': [10, 15, np.nan, 25, 12] # 결측치(NaN) 포함
}
df = pd.DataFrame(data)
print("--- 원본 데이터 ---")
print(df)

# 1. 기본 정보 확인
print("\n--- 기본 통계 요약 (describe) ---")
print(df.describe())

# 2. 새로운 열 추가 (연산 결과)
df['총매출'] = df['가격'] * df['판매량']
print("\n--- '총매출' 열 추가 후 ---")
print(df)

# 3. 결측치(NaN) 처리
# fillna(0) : NaN 값을 0으로 채웁니다.
df_filled = df.fillna(0)
print("\n--- 결측치를 0으로 채운 후 ---")
print(df_filled)

# 4. 정렬
# '가격'을 기준으로 내림차순 정렬합니다.
df_sorted = df.sort_values(by='가격', ascending=False)
print("\n--- 가격 높은 순으로 정렬 ---")
print(df_sorted)

# 5. 그룹화 (Groupby)
# '카테고리'별로 그룹을 묶어 '가격'의 평균을 계산합니다.
category_price_mean = df.groupby('카테고리')['가격'].mean()
print("\n--- 카테고리별 평균 가격 ---")
print(category_price_mean)
```

#### 3. Matplotlib

Matplotlib는 데이터를 시각화하여 그래프로 나타내는 라이브러리입니다. 데이터의 패턴, 추세, 관계 등을 한눈에 파악할 수 있게 해줍니다.

##### ◦ 기본 그래프 그리기

-   **`Figure`**: 그래프가 그려지는 전체 캔버스.
-   **`Axes`**: 실제 데이터가 그려지는 플롯 공간 (하나의 그래프).

```python
# 파일명: matplotlib_basic_plot.py
import matplotlib.pyplot as plt
import matplotlib.font_manager as fm

# 한글 폰트 설정 (Windows 예시, 환경에 맞게 경로 수정 필요)
font_path = "C:/Windows/Fonts/malgun.ttf"
font_prop = fm.FontProperties(fname=font_path)
plt.rc('font', family=font_prop.get_name())
plt.rcParams['axes.unicode_minus'] = False # 음수 기호 깨짐 방지

# 1. 데이터 준비
months = [1, 2, 3, 4, 5, 6]
sales = [150, 220, 280, 250, 310, 350]

# 2. Figure와 Axes 생성 (선택 사항이지만, 여러 그래프를 그릴 때 유용)
fig, ax = plt.subplots(figsize=(8, 5))

# 3. 꺾은선 그래프(Line Plot) 생성
ax.plot(months, sales, marker='o', linestyle='--', color='b')

# 4. 그래프 꾸미기
ax.set_title("월별 매출 추이")
ax.set_xlabel("월(Month)")
ax.set_ylabel("매출(단위: 백만원)")
ax.grid(True)

# 5. 그래프 보여주기
plt.show()
```

##### ◦ 다양한 종류의 그래프

Matplotlib는 다양한 형태의 그래프를 지원하여 데이터의 특징에 맞는 시각화를 가능하게 합니다.

```python
# 파일명: matplotlib_various_plots.py
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import matplotlib.font_manager as fm

# 한글 폰트 설정
font_path = "C:/Windows/Fonts/malgun.ttf"
font_prop = fm.FontProperties(fname=font_path).get_name()
plt.rc('font', family=font_prop)
plt.rcParams['axes.unicode_minus'] = False

# Figure와 Axes를 2x2 격자로 생성
fig, axes = plt.subplots(2, 2, figsize=(12, 10))
fig.suptitle("다양한 그래프 예제", fontsize=16)

# 1. 막대 그래프 (Bar Chart)
categories = ["A", "B", "C", "D"]
values = [10, 15, 7, 12]
axes[0, 0].bar(categories, values, color='skyblue')
axes[0, 0].set_title("막대 그래프")

# 2. 히스토그램 (Histogram)
data_hist = np.random.randn(1000)
axes[0, 1].hist(data_hist, bins=30, color='salmon', alpha=0.7)
axes[0, 1].set_title("히스토그램")

# 3. 산점도 (Scatter Plot)
x_scatter = np.random.rand(50)
y_scatter = np.random.rand(50)
axes[1, 0].scatter(x_scatter, y_scatter, color='green')
axes[1, 0].set_title("산점도")

# 4. 히트맵 (Heatmap) - Seaborn 라이브러리 활용
data_heatmap = np.random.rand(5, 5)
sns.heatmap(data_heatmap, annot=True, cmap="viridis", ax=axes[1, 1])
axes[1, 1].set_title("히트맵")

# 레이아웃 자동 조정
plt.tight_layout(rect=[0, 0, 1, 0.96])
plt.show()
```