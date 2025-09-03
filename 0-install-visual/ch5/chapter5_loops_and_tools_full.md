# Chapter 5: 반복문과 유용한 도구들

---

## 🔹 리스트 컴프리헨션 (List Comprehension)
리스트 컴프리헨션은 한 줄의 코드로 리스트를 간결하게 생성하는 방법입니다.

### ✅ 기본 문법
```python
new_list = [표현식 for 항목 in 반복_가능한_객체]
```

### 예시 1: 제곱수 리스트 만들기
```python
# 기존 for문 방식
squares = []
for x in range(1, 6):
    squares.append(x**2)
print(squares)  # [1, 4, 9, 16, 25]

# 리스트 컴프리헨션 방식
squares = [x**2 for x in range(1, 6)]
print(squares)  # [1, 4, 9, 16, 25]
```

### 예시 2: 조건문 포함
```python
# 기존 방식
even_squares = []
for i in range(1, 11):
    if i % 2 == 0:
        even_squares.append(i * i)
print(even_squares)

# 리스트 컴프리헨션
even_squares = [x * x for x in range(1, 11) if x % 2 == 0]
print(even_squares)  # [4, 16, 36, 64, 100]
```

### 예시 3: 이중 반복문
```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]
flattened_list = [element for row in matrix for element in row]
print(flattened_list)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 예시 4: 조합 생성
```python
colors = ['빨강', '파랑']
sizes = ['S', 'M', 'L']
combinations = [(color, size) for color in colors for size in sizes]
print(combinations)
# [('빨강', 'S'), ('빨강', 'M'), ('빨강', 'L'), ('파랑', 'S'), ('파랑', 'M'), ('파랑', 'L')]
```

### 예시 5: 2차원 리스트 생성
```python
matrix = [[0 for j in range(4)] for i in range(3)]
print(matrix)
# [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]
```

### 성능 비교 (for문 vs 리스트 컴프리헨션)
```python
import time

NUM_ELEMENTS = 10_000_000

# for문
start_time = time.time()
result_for_loop = []
for i in range(NUM_ELEMENTS):
    result_for_loop.append(i * i)
end_time = time.time()
print(f"일반 for문 실행 시간: {end_time - start_time:.5f}초")

# 리스트 컴프리헨션
start_time = time.time()
result_comprehension = [i * i for i in range(NUM_ELEMENTS)]
end_time = time.time()
print(f"리스트 컴프리헨션 실행 시간: {end_time - start_time:.5f}초")
```

---

## 🔹 enumerate()
반복문에서 인덱스와 값을 동시에 가져올 때 사용합니다.

```python
fruits = ["사과", "바나나", "체리"]
for index, fruit in enumerate(fruits):
    print(f"인덱스 {index}: {fruit}")
```

---

## 🔹 zip()
여러 개의 리스트를 동시에 묶어주는 함수입니다.

### 예시 1: 같은 길이의 리스트 묶기
```python
names = ["철수", "영희", "민수"]
scores = [85, 90, 78]

for name, score in zip(names, scores):
    print(f"{name}의 점수: {score}")
```

### 예시 2: 길이가 다른 리스트 묶기
```python
names = ['Alice', 'Bob', 'Charlie', 'David']
ages = [25, 30, 35]
print(list(zip(names, ages)))
# [('Alice', 25), ('Bob', 30), ('Charlie', 35)]
```

### 예시 3: Unzipping
```python
student_scores = [('철수', 88), ('영희', 92), ('민준', 76)]
students, scores = zip(*student_scores)
print(students)  # ('철수', '영희', '민준')
print(scores)    # (88, 92, 76)
```

---

## 🔹 람다 함수 (Lambda Function)
람다 함수는 이름 없는 익명 함수로, 주로 **짧고 간단한 연산**을 정의할 때 사용합니다.

### ✅ 기본 문법
```python
lambda 인자1, 인자2, ... : 표현식
```

### 특징
- 이름이 없음 (익명)
- 한 줄 표현식만 가능 (자동 반환)
- 보통 **map(), filter(), sorted()** 등과 함께 사용

### 예시 1: 일반 함수 vs 람다 함수
```python
# 일반 함수
def add(x, y):
    return x + y

# 람다 함수
add_lambda = lambda x, y: x + y

print(add(3, 5))        # 8
print(add_lambda(3, 5)) # 8
```

### 예시 2: map()과 함께 사용
```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = list(map(lambda x: x * x, numbers))
print(squared_numbers)  # [1, 4, 9, 16, 25]
```

### 예시 3: filter()와 함께 사용
```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # [2, 4, 6, 8, 10]
```

### 예시 4: sorted()와 함께 사용
```python
students = [('철수', 88), ('민준', 95), ('영희', 76)]
sorted_by_score = sorted(students, key=lambda student: student[1])
print(sorted_by_score)  # [('영희', 76), ('철수', 88), ('민준', 95)]
```
