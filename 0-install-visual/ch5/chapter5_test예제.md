### 📚 파트 5: 파이썬 스타일 코드

#### **1. 리스트 컴프리헨션 (List Comprehension)**

리스트 컴프리헨션은 한 줄의 코드로 리스트를 생성하는 간결하고 효율적인 문법입니다.

```python
# 기존 for문을 사용하여 리스트 생성
even_squares = []
for i in range(1, 11):
    if i % 2 == 0:  # 짝수인지 확인
        even_squares.append(i * i)
print(f"기존 반복문이용해서 출력 : {even_squares}")

# 리스트 컴프리헨션으로 동일한 작업 수행
# [표현식 for 항목 in 반복가능객체 if 조건문]
even_squares = [x * x for x in range(1, 11) if x % 2 == 0]
print(f"리스트 컴프리헨션 이용해서 출력 : {even_squares}")
# 결과: [4, 16, 36, 64, 100]
```

#### **2. 이중 반복문과 리스트 컴프리헨션**

이중 `for` 루프도 리스트 컴프리헨션으로 간결하게 표현할 수 있습니다.

```python
# 2차원 리스트를 1차원으로 만들기
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

# 이중 for문을 이용한 일반적인 방법
flattened_list = []
for row in matrix:           # 바깥쪽 루프 (행)
    for element in row:      # 안쪽 루프 (요소)
        flattened_list.append(element)
print(flattened_list)

# 리스트 컴프리헨션으로 표현
flattened_list = [element for row in matrix for element in row]
print(flattened_list)
# 결과: [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```python
# 이중 루프를 사용한 조합 생성
colors = ['빨강', '파랑']
sizes = ['S', 'M', 'L']

# (color, size) 형태의 튜플 조합을 만듭니다.
combinations = [(color, size) for color in colors for size in sizes]

print(combinations)
# 결과: [('빨강', 'S'), ('빨강', 'M'), ('빨강', 'L'), ('파랑', 'S'), ('파랑', 'M'), ('파랑', 'L')]
```

#### **3. `enumerate()`**

`enumerate()` 함수는 반복 가능한 객체의 인덱스와 값을 동시에 반환합니다.

```python
fruits = ["사과", "바나나", "체리"]

# enumerate()를 사용해 인덱스와 값을 동시에 가져와 출력합니다.
for index, fruit in enumerate(fruits):
    print(f"인덱스 {index}: {fruit}")
```

#### **4. `zip()`**

`zip()` 함수는 여러 개의 반복 가능한 객체들을 묶어 각 객체의 동일한 인덱스에 있는 요소들을 튜플로 묶어주는 역할을 합니다.

```python
names = ["철수", "영희", "민수"]
scores = [85, 90, 78]

# zip()을 사용해 이름과 점수를 짝지어 순회합니다.
for name, score in zip(names, scores):
    print(f"{name}의 점수: {score}")

# 예시 2: 길이가 다른 리스트 묶기
# zip() 함수는 가장 짧은 리스트의 길이를 기준으로 동작합니다.
names = ['Alice', 'Bob', 'Charlie', 'David']  # 4개
ages = [25, 30, 35]  # 3개

zipped_info = zip(names, ages)
print(list(zipped_info)) # 결과: [('Alice', 25), ('Bob', 30), ('Charlie', 35)]
```

```python
# 묶인 데이터 다시 풀기 (Unzipping)
student_scores = [('철수', 88), ('영희', 92), ('민준', 76)]

# zip()과 별표(*)를 함께 사용해 묶여있던 데이터를 분리합니다.
# *student_scores는 [('철수', 88), ('영희', 92), ('민준', 76)] -> ('철수', '영희', '민준'), (88, 92, 76)로 언패킹됩니다.
students, scores = zip(*student_scores)

print("학생들:", students)
print("점수들:", scores)
```

#### **5. 람다(Lambda) 함수**

람다 함수는 이름이 없는 **익명 함수**로, 한 줄짜리 간단한 기능을 수행할 때 사용합니다. `map()`, `filter()`, `sorted()`와 같은 함수와 함께 사용하면 매우 유용합니다.

```python
# 람다 함수의 기본 문법: lambda 인자: 표현식
add_lambda = lambda x, y: x + y
print(add_lambda(3, 5))  # 결과: 8

# map() 함수와 람다 함수를 활용
numbers = [1, 2, 3, 4, 5]
# map(함수, 반복가능객체): numbers의 각 요소에 람다 함수(제곱)를 적용
squared_numbers = list(map(lambda x: x * x, numbers))
print(squared_numbers) # 결과: [1, 4, 9, 16, 25]

# filter() 함수와 람다 함수를 활용
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# filter(함수, 반복가능객체): numbers의 각 요소에 람다 함수를 적용, 결과가 True인 요소만 남김
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers) # 결과: [2, 4, 6, 8, 10]

# sorted() 함수와 람다 함수를 활용
students = [('철수', 88), ('민준', 95), ('영희', 76)]
# sorted(리스트, key=정렬기준): 튜플의 두 번째 요소(점수)를 기준으로 정렬
sorted_by_score = sorted(students, key=lambda student: student[1])
print(sorted_by_score)
```