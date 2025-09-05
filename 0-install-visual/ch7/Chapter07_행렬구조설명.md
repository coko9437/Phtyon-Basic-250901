
## **NumPy 설명 (주석 형식)**

### **1. NumPy 배열 생성**

파이썬 리스트를 `np.array()` 함수에 전달하여 NumPy 배열을 만듭니다.

```python
import numpy as np

#### 1-1. 1차원 배열 생성
# 파이썬 기본 리스트를 정의합니다.
my_list = [1, 2, 3, 4, 5]

# np.array()를 사용하여 파이썬 리스트를 NumPy의 1차원 배열(ndarray)로 변환합니다.
# 구조 변경: Python list -> NumPy 1D array
arr1d = np.array(my_list)

print("1차원 배열:")
print(arr1d) # 결과: [1 2 3 4 5]
print(f"배열의 모양 (shape): {arr1d.shape}") # 결과: (5,) -> 1차원에 요소가 5개 있다는 의미


#### 1-2. 2차원 배열 (행렬) 생성
# 2차원 형태의 파이썬 리스트를 정의합니다.
my_list2d = [[1, 2, 3],
             [4, 5, 6]]

# 2차원 리스트를 NumPy의 2차원 배열로 변환합니다.
# 구조 변경: Python 2D list -> NumPy 2D array
arr2d = np.array(my_list2d)

print("\n2차원 배열:")
print(arr2d)
# 결과:
# [[1 2 3]
#  [4 5 6]]
print(f"배열의 모양 (shape): {arr2d.shape}") # 결과: (2, 3) -> 2행 3열
print(f"배열의 차원 (ndim): {arr2d.ndim}") # 결과: 2 -> 2차원 배열
print(f"배열 요소의 자료형 (dtype): {arr2d.dtype}") # 결과: int32 또는 int64
```

### **2. 배열 생성 함수**

NumPy는 `arange`, `zeros`, `linspace` 등 다양한 배열 생성 함수를 제공합니다.

```python
#### 2-1. np.arange(): 특정 범위의 연속된 값을 가진 배열 생성
# 0부터 9까지 (10은 미포함) 정수로 구성된 1차원 배열을 생성합니다.
# 구조: 지정된 범위의 1차원 배열 생성
arr_range = np.arange(10)
print(f"arange 결과:\n{arr_range}") # 결과: [0 1 2 3 4 5 6 7 8 9]

#### 2-2. np.zeros(): 모든 요소가 0인 배열 생성
# (2, 3) 형태, 즉 2행 3열 크기의 모든 요소가 0인 2차원 배열을 생성합니다.
# 구조: 지정된 shape의 0으로 채워진 배열 생성
arr_zeros = np.zeros((2, 3))
print(f"\nzeros 결과:\n{arr_zeros}")
# 결과:
# [[0. 0. 0.]
#  [0. 0. 0.]]

#### 2-3. np.linspace(): 균등한 간격의 값을 가진 배열 생성
# 0부터 10까지의 범위를 5개의 균등한 간격으로 나눈 값들로 1차원 배열을 생성합니다.
# 구조: 시작점, 끝점, 개수를 기반으로 1차원 배열 생성
arr_linspace = np.linspace(0, 10, 5)
print(f"\nlinspace 결과:\n{arr_linspace}") # 결과: [ 0.   2.5  5.   7.5 10. ]
```

### **3. 배열 모양 변경하기 (Reshape)**

`.reshape()` 함수를 사용하여 배열의 차원이나 모양을 변경합니다. 단, 전체 요소의 수는 유지되어야 합니다.

```python
# 0부터 11까지의 값을 가진 1차원 배열을 생성합니다. (총 12개 요소)
arr = np.arange(12)
print(f"원본 배열 (1차원):\n{arr}") # 결과: [ 0  1  2  3  4  5  6  7  8  9 10 11]

# .reshape()을 사용하여 배열의 모양을 변경합니다.
# 구조 변경: 1차원 배열 (12,) -> 2차원 배열 (3, 4)
reshaped_arr = arr.reshape(3, 4) # 3행 4열
print(f"\nReshape 결과 (3, 4):\n{reshaped_arr}")
# 결과:
# [[ 0  1  2  3]
#  [ 4  5  6  7]
#  [ 8  9 10 11]]

# 구조 변경: 1차원 배열 (12,) -> 3차원 배열 (2, 3, 2)
# (2 * 3 * 2 = 12, 전체 요소 수 동일)
reshaped_arr2 = arr.reshape(2, 3, 2)
print(f"\nReshape 결과 (2, 3, 2):\n{reshaped_arr2}")
# 결과:
# [[[ 0  1]
#   [ 2  3]
#   [ 4  5]]
#
#  [[ 6  7]
#   [ 8  9]
#   [10 11]]]
```

### **4. 배열 합치기 (Concatenation)**

`np.concatenate()` 함수를 사용하여 여러 배열을 특정 축을 기준으로 합칩니다.

```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

#### 4-1. 세로 방향(axis=0)으로 합치기
# axis=0은 행(row) 방향을 의미합니다. arr1 아래에 arr2가 추가됩니다.
# 구조 변경: (2, 2) 배열 + (2, 2) 배열 -> (4, 2) 배열
v_concat = np.concatenate((arr1, arr2), axis=0)
print(f"세로 합치기 (axis=0):\n{v_concat}")
# 결과:
# [[1 2]
#  [3 4]
#  [5 6]
#  [7 8]]

#### 4-2. 가로 방향(axis=1)으로 합치기
# axis=1은 열(column) 방향을 의미합니다. arr1 옆에 arr2가 추가됩니다.
# 구조 변경: (2, 2) 배열 + (2, 2) 배열 -> (2, 4) 배열
h_concat = np.concatenate((arr1, arr2), axis=1)
print(f"\n가로 합치기 (axis=1):\n{h_concat}")
# 결과:
# [[1 2 5 6]
#  [3 4 7 8]]
```

---

//====================================================

## **Pandas 설명 (주석 형식)**

### **1. Series 와 DataFrame 생성**


Pandas의 핵심 데이터 구조는 1차원 `Series`와 2차원 `DataFrame`입니다.

```python
import pandas as pd

#### 1-1. Pandas Series 정의하기
# Series: 1차원 배열과 같은 구조로, 각 데이터에 Index를 붙여 관리합니다.
# 파이썬 리스트와 인덱스 라벨을 준비합니다.
data = [100, 200, 300, 400]
index_labels = ['A', 'B', 'C', 'D']

# pd.Series() 함수로 Series를 생성합니다.
# 구조 변경: Python list -> Pandas Series (1D)
series = pd.Series(data, index=index_labels)
print("--- Pandas Series ---")
print(series)
# 결과:
# A    100
# B    200
# C    300
# D    400
# dtype: int64

#### 1-2. DataFrame 생성하기
# DataFrame: 행(row)과 열(column)이 있는 2차원 테이블 구조입니다.
# 딕셔너리를 사용하여 데이터를 준비합니다. 딕셔너리의 key가 column 이름이 됩니다.
data_dict = {'이름': ['철수', '영희', '민수'],
             '나이': [24, 25, 23],
             '성별': ['남', '여', '남']}

# pd.DataFrame() 함수로 DataFrame을 생성합니다.
# 구조 변경: Python dictionary -> Pandas DataFrame (2D)
df = pd.DataFrame(data_dict)
print("\n--- Pandas DataFrame ---")
print(df)
# 결과:
#    이름  나이 성별
# 0  철수  24  남
# 1  영희  25  여
# 2  민수  23  남
```

### **2. DataFrame 열(Column) 선택 및 추가**

DataFrame에서 특정 열을 선택하거나, 연산을 통해 새로운 열을 추가할 수 있습니다.

```python
# '가격'과 '판매량' 데이터를 가진 DataFrame 생성
df = pd.DataFrame({
    '가격': [1000, 1500, 2000, 2500, 3000],
    '판매량': [10, 15, 20, 25, 30]
})

#### 2-1. 특정 열 선택 및 조작
# '판매량' 열을 선택하여 모든 값에 2를 곱합니다.
# 구조 변경: '판매량' 열의 내부 값들이 변경됨 (shape은 그대로)
df['판매량'] = df['판매량'] * 2
print("--- '판매량' 열 수정 후 ---")
print(df)
# 결과:
#       가격  판매량
# 0  1000   20
# 1  1500   30
# 2  2000   40
# 3  2500   50
# 4  3000   60

#### 2-2. 새로운 열 추가
# '가격' 열과 '판매량' 열을 곱하여 '총액'이라는 새로운 열을 추가합니다.
# 구조 변경: 기존 DataFrame에 새로운 열('총액')이 추가됨. (2열 -> 3열)
df['총액'] = df['가격'] * df['판매량']
print("\n--- '총액' 열 추가 후 ---")
print(df)
# 결과:
#       가격  판매량     총액
# 0  1000   20  20000
# 1  1500   30  45000
# 2  2000   40  80000
# 3  2500   50 125000
# 4  3000   60 180000
```

### **3. 데이터 정렬 및 그룹화 (Groupby)**

데이터를 특정 기준으로 정렬하거나 그룹으로 묶어 통계량을 계산할 수 있습니다.

```python
# 상품 데이터 DataFrame 생성
df_product = pd.DataFrame({
    '카테고리': ['과일', '과일', '음료', '음료', '과일'],
    '상품명': ['사과', '바나나', '콜라', '주스', '포도'],
    '가격': [3000, 2000, 1500, 2500, 4000]
})

#### 3-1. 정렬하기
# '가격' 열을 기준으로 오름차순(ascending=True)으로 정렬합니다.
# 구조 변경: 행(row)의 순서가 '가격' 값에 따라 재배치됨.
df_sorted = df_product.sort_values(by='가격', ascending=True)
print("--- 가격 기준 오름차순 정렬 ---")
print(df_sorted)
# 결과:
#   카테고리  상품명    가격
# 2    음료   콜라  1500
# 1    과일  바나나  2000
# 3    음료   주스  2500
# 0    과일   사과  3000
# 4    과일   포도  4000

#### 3-2. 그룹화 (Groupby)
# '카테고리' 열을 기준으로 데이터를 그룹화하고, 각 그룹의 '가격' 합계를 계산합니다.
# 구조 변경: 2차원 DataFrame이 '카테고리'를 인덱스로 갖는 1차원 Series로 요약됨.
df_grouped = df_product.groupby('카테고리')['가격'].sum()
print("\n--- 카테고리별 가격 합계 ---")
print(df_grouped)
# 결과:
# 카테고리
# 과일    9000
# 음료    4000
# Name: 가격, dtype: int64
```

---

//====================================================
### **3. Matplotlib**

Matplotlib(맷플롯립)은 파이썬에서 데이터를 시각화하여 그래프로 나타내는 데 가장 널리 사용되는 라이브러리입니다. 라인 플롯, 바 차트, 히스토그램, 산점도 등 거의 모든 종류의 그래프를 그릴 수 있으며, 데이터 분석 결과를 시각적으로 표현하고 인사이트를 얻는 데 필수적입니다.

#### **🎨 Matplotlib의 역할**

Matplotlib는 숫자 데이터를 그림으로 바꾸는 다리 역할을 합니다. 복잡한 숫자나 표만으로는 파악하기 어려운 데이터의 패턴, 추세, 관계 등을 그래프를 통해 한눈에 이해할 수 있게 도와줍니다.

#### **뼈대 구성 요소**

Matplotlib 그래프는 보통 두 가지 주요 요소로 구성됩니다.

*   **Figure (피규어)**: 그래프가 그려지는 전체 캔버스나 종이입니다. 하나의 Figure 안에는 여러 개의 그래프(Axes)가 포함될 수 있습니다.
*   **Axes (축)**: 실제 데이터가 그려지는 플롯 공간입니다. x축, y축, 눈금, 레이블 등 그래프의 모든 구성 요소를 포함합니다. '하나의 그래프'라고 생각하면 쉽습니다.

#### **한글 폰트 설정**

Matplotlib에서 한글을 사용하려면 별도의 폰트 설정이 필요합니다. 각 운영체제에 맞는 폰트 경로를 확인하고 설정해야 합니다.

```python
# 예시 1: 기본 코드 구조 및 한글 폰트 설정
import matplotlib.pyplot as plt
import matplotlib.font_manager as fm
import os

# 각 운영체제에 맞는 폰트 경로를 설정합니다.
# 아래는 일반적인 경로이며, 설치된 폰트에 따라 다를 수 있습니다.
if os.name == 'nt': # Windows
    font_path = "C:/Windows/Fonts/malgun.ttf" # 맑은 고딕
elif os.name == 'posix': # Mac OS or Linux
    # Mac의 경우 '/System/Library/Fonts/AppleSDGothicNeo.ttc' 등을 사용합니다.
    # Linux의 경우 '/usr/share/fonts/truetype/nanum/NanumGothic.ttf' 등 설치된 폰트 경로를 사용합니다.
    # 여기서는 예시로 나눔고딕을 가정합니다.
    font_path = "/usr/share/fonts/truetype/nanum/NanumGothic.ttf"
else:
    print("지원되지 않는 운영체제입니다.")
    font_path = None

if font_path and os.path.exists(font_path):
    font_prop = fm.FontProperties(fname=font_path)

    # Matplotlib의 전역 폰트를 설정합니다.
    # rc : runtime configuration (실행 환경 설정)
    plt.rc('font', family=font_prop.get_name())
else:
    print("지정된 폰트 파일을 찾을 수 없습니다. 기본 폰트로 실행됩니다.")
    font_prop = None # 폰트가 없을 경우 None으로 설정


# 음수 기호가 깨지는 현상을 방지합니다.
plt.rcParams['axes.unicode_minus'] = False

# 그래프를 그릴 Figure 객체를 생성합니다. figsize로 캔버스 크기를 조절합니다.
plt.figure(figsize=(8, 5))

# plt.plot() 함수로 데이터를 그래프에 그립니다.
plt.plot([1, 2, 3, 4], [10, 20, 25, 30], label="라인 그래프")

# 그래프의 각 부분에 이름을 설정합니다. fontproperties를 지정해야 한글이 깨지지 않습니다.
if font_prop:
    plt.xlabel("X축 이름", fontproperties=font_prop)
    plt.ylabel("Y축 이름", fontproperties=font_prop)
    plt.title("그래프 제목", fontproperties=font_prop)
    plt.legend(prop=font_prop) # 범례에도 폰트 속성 적용
else:
    plt.xlabel("X-axis Name")
    plt.ylabel("Y-axis Name")
    plt.title("Graph Title")
    plt.legend()


# 그리드(격자)를 추가하여 가독성을 높입니다.
plt.grid(True)

# plt.show() 함수를 호출하여 완성된 그래프를 화면에 표시합니다.
plt.show()
```

---

## **NumPy 설명 (주석 형식)**

### **1. NumPy 배열 생성**

파이썬 리스트를 `np.array()` 함수에 전달하여 NumPy 배열을 만듭니다.

```python
import numpy as np

#### 1-1. 1차원 배열 생성
# 파이썬 기본 리스트를 정의합니다.
my_list = [1, 2, 3, 4, 5]

# np.array()를 사용하여 파이썬 리스트를 NumPy의 1차원 배열(ndarray)로 변환합니다.
# 구조 변경: Python list -> NumPy 1D array
arr1d = np.array(my_list)

print("1차원 배열:")
print(arr1d) # 결과: [1 2 3 4 5]
print(f"배열의 모양 (shape): {arr1d.shape}") # 결과: (5,) -> 1차원에 요소가 5개 있다는 의미


#### 1-2. 2차원 배열 (행렬) 생성
# 2차원 형태의 파이썬 리스트를 정의합니다.
my_list2d = [[1, 2, 3],
             [4, 5, 6]]

# 2차원 리스트를 NumPy의 2차원 배열로 변환합니다.
# 구조 변경: Python 2D list -> NumPy 2D array
arr2d = np.array(my_list2d)

print("\n2차원 배열:")
print(arr2d)
# 결과:
# [[1 2 3]
#  [4 5 6]]
print(f"배열의 모양 (shape): {arr2d.shape}") # 결과: (2, 3) -> 2행 3열
print(f"배열의 차원 (ndim): {arr2d.ndim}") # 결과: 2 -> 2차원 배열
print(f"배열 요소의 자료형 (dtype): {arr2d.dtype}") # 결과: int32 또는 int64
```

### **2. 배열 생성 함수**

NumPy는 `arange`, `zeros`, `linspace` 등 다양한 배열 생성 함수를 제공합니다.

```python
#### 2-1. np.arange(): 특정 범위의 연속된 값을 가진 배열 생성
# 0부터 9까지 (10은 미포함) 정수로 구성된 1차원 배열을 생성합니다.
# 구조: 지정된 범위의 1차원 배열 생성
arr_range = np.arange(10)
print(f"arange 결과:\n{arr_range}") # 결과: [0 1 2 3 4 5 6 7 8 9]

#### 2-2. np.zeros(): 모든 요소가 0인 배열 생성
# (2, 3) 형태, 즉 2행 3열 크기의 모든 요소가 0인 2차원 배열을 생성합니다.
# 구조: 지정된 shape의 0으로 채워진 배열 생성
arr_zeros = np.zeros((2, 3))
print(f"\nzeros 결과:\n{arr_zeros}")
# 결과:
# [[0. 0. 0.]
#  [0. 0. 0.]]

#### 2-3. np.linspace(): 균등한 간격의 값을 가진 배열 생성
# 0부터 10까지의 범위를 5개의 균등한 간격으로 나눈 값들로 1차원 배열을 생성합니다.
# 구조: 시작점, 끝점, 개수를 기반으로 1차원 배열 생성
arr_linspace = np.linspace(0, 10, 5)
print(f"\nlinspace 결과:\n{arr_linspace}") # 결과: [ 0.   2.5  5.   7.5 10. ]
```

### **3. 배열 모양 변경하기 (Reshape)**

`.reshape()` 함수를 사용하여 배열의 차원이나 모양을 변경합니다. 단, 전체 요소의 수는 유지되어야 합니다.

```python
# 0부터 11까지의 값을 가진 1차원 배열을 생성합니다. (총 12개 요소)
arr = np.arange(12)
print(f"원본 배열 (1차원):\n{arr}") # 결과: [ 0  1  2  3  4  5  6  7  8  9 10 11]

# .reshape()을 사용하여 배열의 모양을 변경합니다.
# 구조 변경: 1차원 배열 (12,) -> 2차원 배열 (3, 4)
reshaped_arr = arr.reshape(3, 4) # 3행 4열
print(f"\nReshape 결과 (3, 4):\n{reshaped_arr}")
# 결과:
# [[ 0  1  2  3]
#  [ 4  5  6  7]
#  [ 8  9 10 11]]

# 구조 변경: 1차원 배열 (12,) -> 3차원 배열 (2, 3, 2)
# (2 * 3 * 2 = 12, 전체 요소 수 동일)
reshaped_arr2 = arr.reshape(2, 3, 2)
print(f"\nReshape 결과 (2, 3, 2):\n{reshaped_arr2}")
# 결과:
# [[[ 0  1]
#   [ 2  3]
#   [ 4  5]]
#
#  [[ 6  7]
#   [ 8  9]
#   [10 11]]]
```

### **4. 배열 합치기 (Concatenation)**

`np.concatenate()` 함수를 사용하여 여러 배열을 특정 축을 기준으로 합칩니다.

```python
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

#### 4-1. 세로 방향(axis=0)으로 합치기
# axis=0은 행(row) 방향을 의미합니다. arr1 아래에 arr2가 추가됩니다.
# 구조 변경: (2, 2) 배열 + (2, 2) 배열 -> (4, 2) 배열
v_concat = np.concatenate((arr1, arr2), axis=0)
print(f"세로 합치기 (axis=0):\n{v_concat}")
# 결과:
# [[1 2]
#  [3 4]
#  [5 6]
#  [7 8]]

#### 4-2. 가로 방향(axis=1)으로 합치기
# axis=1은 열(column) 방향을 의미합니다. arr1 옆에 arr2가 추가됩니다.
# 구조 변경: (2, 2) 배열 + (2, 2) 배열 -> (2, 4) 배열
h_concat = np.concatenate((arr1, arr2), axis=1)
print(f"\n가로 합치기 (axis=1):\n{h_concat}")
# 결과:
# [[1 2 5 6]
#  [3 4 7 8]]
```

---

## **Pandas 설명 (주석 형식)**

### **1. Series 와 DataFrame 생성**

Pandas의 핵심 데이터 구조는 1차원 `Series`와 2차원 `DataFrame`입니다.

```python
import pandas as pd

#### 1-1. Pandas Series 정의하기
# Series: 1차원 배열과 같은 구조로, 각 데이터에 Index를 붙여 관리합니다.
# 파이썬 리스트와 인덱스 라벨을 준비합니다.
data = [100, 200, 300, 400]
index_labels = ['A', 'B', 'C', 'D']

# pd.Series() 함수로 Series를 생성합니다.
# 구조 변경: Python list -> Pandas Series (1D)
series = pd.Series(data, index=index_labels)
print("--- Pandas Series ---")
print(series)
# 결과:
# A    100
# B    200
# C    300
# D    400
# dtype: int64

#### 1-2. DataFrame 생성하기
# DataFrame: 행(row)과 열(column)이 있는 2차원 테이블 구조입니다.
# 딕셔너리를 사용하여 데이터를 준비합니다. 딕셔너리의 key가 column 이름이 됩니다.
data_dict = {'이름': ['철수', '영희', '민수'],
             '나이': [24, 25, 23],
             '성별': ['남', '여', '남']}

# pd.DataFrame() 함수로 DataFrame을 생성합니다.
# 구조 변경: Python dictionary -> Pandas DataFrame (2D)
df = pd.DataFrame(data_dict)
print("\n--- Pandas DataFrame ---")
print(df)
# 결과:
#    이름  나이 성별
# 0  철수  24  남
# 1  영희  25  여
# 2  민수  23  남
```

### **2. DataFrame 열(Column) 선택 및 추가**

DataFrame에서 특정 열을 선택하거나, 연산을 통해 새로운 열을 추가할 수 있습니다.

```python
# '가격'과 '판매량' 데이터를 가진 DataFrame 생성
df = pd.DataFrame({
    '가격': [1000, 1500, 2000, 2500, 3000],
    '판매량': [10, 15, 20, 25, 30]
})

#### 2-1. 특정 열 선택 및 조작
# '판매량' 열을 선택하여 모든 값에 2를 곱합니다.
# 구조 변경: '판매량' 열의 내부 값들이 변경됨 (shape은 그대로)
df['판매량'] = df['판매량'] * 2
print("--- '판매량' 열 수정 후 ---")
print(df)
# 결과:
#       가격  판매량
# 0  1000   20
# 1  1500   30
# 2  2000   40
# 3  2500   50
# 4  3000   60

#### 2-2. 새로운 열 추가
# '가격' 열과 '판매량' 열을 곱하여 '총액'이라는 새로운 열을 추가합니다.
# 구조 변경: 기존 DataFrame에 새로운 열('총액')이 추가됨. (2열 -> 3열)
df['총액'] = df['가격'] * df['판매량']
print("\n--- '총액' 열 추가 후 ---")
print(df)
# 결과:
#       가격  판매량     총액
# 0  1000   20  20000
# 1  1500   30  45000
# 2  2000   40  80000
# 3  2500   50 125000
# 4  3000   60 180000
```

### **3. 데이터 정렬 및 그룹화 (Groupby)**

데이터를 특정 기준으로 정렬하거나 그룹으로 묶어 통계량을 계산할 수 있습니다.

```python
# 상품 데이터 DataFrame 생성
df_product = pd.DataFrame({
    '카테고리': ['과일', '과일', '음료', '음료', '과일'],
    '상품명': ['사과', '바나나', '콜라', '주스', '포도'],
    '가격': [3000, 2000, 1500, 2500, 4000]
})

#### 3-1. 정렬하기
# '가격' 열을 기준으로 오름차순(ascending=True)으로 정렬합니다.
# 구조 변경: 행(row)의 순서가 '가격' 값에 따라 재배치됨.
df_sorted = df_product.sort_values(by='가격', ascending=True)
print("--- 가격 기준 오름차순 정렬 ---")
print(df_sorted)
# 결과:
#   카테고리  상품명    가격
# 2    음료   콜라  1500
# 1    과일  바나나  2000
# 3    음료   주스  2500
# 0    과일   사과  3000
# 4    과일   포도  4000

#### 3-2. 그룹화 (Groupby)
# '카테고리' 열을 기준으로 데이터를 그룹화하고, 각 그룹의 '가격' 합계를 계산합니다.
# 구조 변경: 2차원 DataFrame이 '카테고리'를 인덱스로 갖는 1차원 Series로 요약됨.
df_grouped = df_product.groupby('카테고리')['가격'].sum()
print("\n--- 카테고리별 가격 합계 ---")
print(df_grouped)
# 결과:
# 카테고리
# 과일    9000
# 음료    4000
# Name: 가격, dtype: int64
```네, 알겠습니다. Matplotlib에 대한 설명과 함께, 이전에 제공해주신 NumPy와 Pandas의 설명을 요청하신 주석 형식에 맞게 재구성하여 제공해 드리겠습니다.

---

### **3. Matplotlib**

Matplotlib(맷플롯립)은 파이썬에서 데이터를 시각화하여 그래프로 나타내는 데 가장 널리 사용되는 라이브러리입니다. 라인 플롯, 바 차트, 히스토그램, 산점도 등 거의 모든 종류의 그래프를 그릴 수 있으며, 데이터 분석 결과를 시각적으로 표현하고 인사이트를 얻는 데 필수적입니다.

#### **🎨 Matplotlib의 역할**

Matplotlib는 숫자 데이터를 그림으로 바꾸는 다리 역할을 합니다. 복잡한 숫자나 표만으로는 파악하기 어려운 데이터의 패턴, 추세, 관계 등을 그래프를 통해 한눈에 이해할 수 있게 도와줍니다.

#### **뼈대 구성 요소**

Matplotlib 그래프는 보통 두 가지 주요 요소로 구성됩니다.

*   **Figure (피규어)**: 그래프가 그려지는 전체 캔버스나 종이입니다. 하나의 Figure 안에는 여러 개의 그래프(Axes)가 포함될 수 있습니다.
*   **Axes (축)**: 실제 데이터가 그려지는 플롯 공간입니다. x축, y축, 눈금, 레이블 등 그래프의 모든 구성 요소를 포함합니다. '하나의 그래프'라고 생각하면 쉽습니다.

#### **한글 폰트 설정**

Matplotlib에서 한글을 사용하려면 별도의 폰트 설정이 필요합니다. 각 운영체제에 맞는 폰트 경로를 확인하고 설정해야 합니다.

```python
# 예시 1: 기본 코드 구조 및 한글 폰트 설정
import matplotlib.pyplot as plt
import matplotlib.font_manager as fm
import os

# 각 운영체제에 맞는 폰트 경로를 설정합니다.
# 아래는 일반적인 경로이며, 설치된 폰트에 따라 다를 수 있습니다.
if os.name == 'nt': # Windows
    font_path = "C:/Windows/Fonts/malgun.ttf" # 맑은 고딕
elif os.name == 'posix': # Mac OS or Linux
    # Mac의 경우 '/System/Library/Fonts/AppleSDGothicNeo.ttc' 등을 사용합니다.
    # Linux의 경우 '/usr/share/fonts/truetype/nanum/NanumGothic.ttf' 등 설치된 폰트 경로를 사용합니다.
    # 여기서는 예시로 나눔고딕을 가정합니다.
    font_path = "/usr/share/fonts/truetype/nanum/NanumGothic.ttf"
else:
    print("지원되지 않는 운영체제입니다.")
    font_path = None

if font_path and os.path.exists(font_path):
    font_prop = fm.FontProperties(fname=font_path)

    # Matplotlib의 전역 폰트를 설정합니다.
    # rc : runtime configuration (실행 환경 설정)
    plt.rc('font', family=font_prop.get_name())
else:
    print("지정된 폰트 파일을 찾을 수 없습니다. 기본 폰트로 실행됩니다.")
    font_prop = None # 폰트가 없을 경우 None으로 설정


# 음수 기호가 깨지는 현상을 방지합니다.
plt.rcParams['axes.unicode_minus'] = False

# 그래프를 그릴 Figure 객체를 생성합니다. figsize로 캔버스 크기를 조절합니다.
plt.figure(figsize=(8, 5))

# plt.plot() 함수로 데이터를 그래프에 그립니다.
plt.plot([1, 2, 3, 4], [10, 20, 25, 30], label="라인 그래프")

# 그래프의 각 부분에 이름을 설정합니다. fontproperties를 지정해야 한글이 깨지지 않습니다.
if font_prop:
    plt.xlabel("X축 이름", fontproperties=font_prop)
    plt.ylabel("Y축 이름", fontproperties=font_prop)
    plt.title("그래프 제목", fontproperties=font_prop)
    plt.legend(prop=font_prop) # 범례에도 폰트 속성 적용
else:
    plt.xlabel("X-axis Name")
    plt.ylabel("Y-axis Name")
    plt.title("Graph Title")
    plt.legend()


# 그리드(격자)를 추가하여 가독성을 높입니다.
plt.grid(True)

# plt.show() 함수를 호출하여 완성된 그래프를 화면에 표시합니다.
plt.show()
```

---
