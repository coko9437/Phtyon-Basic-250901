## 🐍 파이썬 마스터를 위한 심화 내용 TOP 9

### 1. `is` vs `==` : 메모리 주소와 값의 비교 (Chapter 2)
`==`는 두 변수의 **내용물(값)**이 같은지 비교하지만, `is`는 두 변수가 가리키는 **메모리 속 '위치 쪽지'(주소)**가 같은지, 즉 완전히 동일한 객체인지를 비교합니다. 특히 리스트와 같은 가변 객체를 다룰 때 이 차이를 모르면 예상치 못한 버그를 만날 수 있습니다.

```python
a = [1, 2, 3]
b = [1, 2, 3] # 내용물은 같지만, 서로 다른 집(메모리)에 사는 객체
c = a       # a와 같은 집을 가리키는 또 다른 이름표

print(f"a == b: {a == b}") # True (내용물이 같음)
print(f"a is b: {a is b}") # False (사는 집 주소가 다름)
print(f"a is c: {a is c}") # True (사는 집 주소가 같음)
```

### 2. 컴프리헨션 삼총사 : 리스트, 딕셔너리, 세트 (Chapter 5)
`for` 반복문을 단 한 줄로 압축하여 리스트, 딕셔너리, 세트를 생성하는 '파이썬다운' 궁극의 기술입니다. 코드가 간결해질 뿐만 아니라 실행 속도도 더 빠릅니다.

```python
# 리스트 컴프리헨션
squares_list = [i**2 for i in range(5)]
# [0, 1, 4, 9, 16]

# 딕셔너리 컴프리헨션
squares_dict = {i: i**2 for i in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# 세트 컴프리헨션
squares_set = {i**2 for i in [-1, 0, 1, 2, 2]}
# {0, 1, 4} (중복은 자동 제거)
```

### 3. 가변 vs 불변 객체와 함수 : 원본이 바뀌는 마법 (Chapter 3)
함수에 인수를 전달할 때, **가변 객체(리스트, 딕셔너리)**를 넘기면 함수 안에서 그 객체의 내용물을 변경할 경우 **원본 객체도 함께 변경**됩니다. 이는 객체의 '위치 쪽지'가 전달되기 때문입니다. 반면, **불변 객체(숫자, 문자열, 튜플)**는 원본이 절대 변하지 않습니다.

```python
def add_item(my_list):
    # 전달받은 리스트의 '원본'에 100을 추가
    my_list.append(100)

original_list = [10, 20]
add_item(original_list)

print(original_list) # [10, 20, 100] -> 원본이 변경됨!
```

### 4. 제너레이터 표현식 : 메모리를 아끼는 현명한 선택 (Chapter 5)
컴프리헨션과 문법이 거의 같지만, `[]` 대신 `()`를 사용합니다. 모든 값을 미리 만들어 메모리에 저장하는 컴프리헨션과 달리, 제너레이터는 값이 필요할 때마다 **그때그때 하나씩 계산**해서 만들어냅니다. 수백만 개의 데이터를 다룰 때 메모리 폭발을 막아주는 핵심 기술입니다.

```python
# 100만개의 숫자를 제곱한 리스트 (메모리 사용량이 큼)
# large_list = [i**2 for i in range(1000000)]

# 필요할 때마다 값을 하나씩 생성 (메모리 사용량이 매우 적음)
large_generator = (i**2 for i in range(1000000))

# sum()과 같은 함수가 값을 요청할 때마다 계산이 일어남
total = sum(large_generator)
```

### 5. 매직 메서드 : 나만의 객체에 영혼 불어넣기 (Chapter 6)
`__init__`, `__str__`처럼 이름 앞뒤에 더블 언더스코어(`__`)가 붙은 특별한 메서드들입니다. `print()`, `len()`, `==` 등 파이썬의 기본 기능들이 내 객체에 어떻게 작동할지를 직접 정의하여, 마치 내장 타입처럼 자연스럽게 동작하게 만들 수 있습니다.

```python
class Book:
    def __init__(self, title, pages):
        self.title = title
        self.pages = pages
    
    # print(book)을 호출하면 이 메서드가 실행됨
    def __str__(self):
        return f"'{self.title}' ({self.pages}쪽)"
    
    # len(book)을 호출하면 이 메서드가 실행됨
    def __len__(self):
        return self.pages

my_book = Book("파이썬의 정석", 300)
print(my_book) # '__str__' 호출 -> '파이썬의 정석' (300쪽)
print(len(my_book)) # '__len__' 호출 -> 300```

### 6. NumPy 브로드캐스팅 : 차원을 넘나드는 계산 마법 (Chapter 7)
서로 크기(shape)가 다른 배열끼리도 `for`문 없이 산술 연산을 가능하게 해주는 NumPy의 강력한 기능입니다. 코드가 극도로 간결해지고 C언어 수준의 빠른 속도로 연산을 수행합니다.

```python
import numpy as np

matrix = np.array([[1, 2, 3], 
                   [4, 5, 6]]) # (2, 3) 크기

# for문 없이 matrix의 모든 요소에 100을 더함
result = matrix + 100 
print(result)
# [[101, 102, 103],
#  [104, 105, 106]]
```

### 7. Pandas `loc` vs `iloc` : 데이터 선택의 두 가지 길 (Chapter 7)
DataFrame에서 데이터를 선택하는 핵심 방법입니다. 이 둘의 차이를 명확히 아는 것이 Pandas 숙련도의 척도입니다.
- **`.loc[행, 열]`**: **이름(Label)** 기반으로 선택합니다. (예: `df.loc['2023-01-05', '판매량']`)
- **`.iloc[행, 열]`**: **정수 위치(Integer position)** 기반으로 선택합니다. (예: `df.iloc[4, 1]`)

```python
import pandas as pd
df = pd.DataFrame({'A': [10, 20], 'B': [30, 40]}, index=['row1', 'row2'])

# loc: 이름 기반
print(df.loc['row1', 'A']) # 10

# iloc: 위치 기반
print(df.iloc[0, 0]) # 10
```

### 8. Pandas `groupby` : 데이터 분해, 적용, 결합의 미학 (Chapter 7)
데이터를 특정 기준으로 여러 그룹으로 **분해(Split)**하고, 각 그룹별로 함수를 **적용(Apply)**한 뒤, 그 결과들을 다시 하나로 **결합(Combine)**하는 데이터 집계의 핵심 기능입니다. 복잡한 집계 연산을 단 한 줄로 표현할 수 있게 해줍니다.

```python
import pandas as pd
df = pd.DataFrame({'팀': ['A', 'B', 'A', 'B'], '점수': [10, 15, 20, 25]})

# '팀' 별 '점수'의 평균 구하기
team_avg_score = df.groupby('팀')['점수'].mean()
print(team_avg_score)
# 팀
# A    15.0
# B    20.0
# Name: 점수, dtype: float64
```

### 9. `with` 구문과 파라미터 바인딩 : 안전한 데이터 처리의 정석 (Chapter 8)
- **`with` 구문**: 파일이나 데이터베이스 연결 같은 자원을 사용한 뒤, 예외 발생 여부와 상관없이 **언제나 안전하게 자원을 닫아주는(`close()`)** 세련된 방법입니다.
- **파라미터 바인딩 (`?`, `%s`)**: SQL 쿼리에 사용자 입력을 직접 합치지 않고, 값을 분리해서 전달하는 방식입니다. 해킹 공격의 일종인 **SQL Injection을 막아주는 필수 보안 규칙**입니다.

```python
import sqlite3

user_id_to_find = 'admin'

# with 구문으로 자동 자원 관리 & 파라미터 바인딩으로 보안 강화
with sqlite3.connect('my_db.db') as conn:
    cursor = conn.cursor()
    sql = "SELECT * FROM users WHERE user_id = ?"
    cursor.execute(sql, (user_id_to_find,)) # 값은 튜플로 전달
    user_data = cursor.fetchone()
```