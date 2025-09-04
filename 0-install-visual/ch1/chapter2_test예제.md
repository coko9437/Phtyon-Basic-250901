네, 요청하신 2장부터 6장까지의 연습 예제에 대한 풀이와 로직을 주석을 포함한 코드로 알려드릴게요.

-----

### 📚 파트 1: 파이썬 기본 문법 (2장)

#### **1. 변수와 자료형**

**문제 1:** 사용자에게 정수 두 개를 입력받아 사칙연산 결과(몫과 나머지 포함)를 모두 출력하는 프로그램

```python
# 사용자에게 두 개의 정수를 입력받습니다.
# input() 함수는 문자열을 반환하므로, int() 함수로 정수형으로 변환합니다.
num1 = int(input("첫 번째 정수를 입력하세요: "))
num2 = int(input("두 번째 정수를 입력하세요: "))

# 사칙연산과 몫, 나머지를 계산합니다.
addition = num1 + num2        # 덧셈
subtraction = num1 - num2     # 뺄셈
multiplication = num1 * num2    # 곱셈
division_float = num1 / num2  # 나눗셈 (실수)
division_int = num1 // num2   # 몫 (정수)
remainder = num1 % num2       # 나머지

# 결과를 출력합니다.
print(f"덧셈 결과: {addition}")
print(f"뺄셈 결과: {subtraction}")
print(f"곱셈 결과: {multiplication}")
print(f"나눗셈 결과: {division_float}")
print(f"몫: {division_int}")
print(f"나머지: {remainder}")
```

**문제 2:** 정수형, 실수형, 불린형, 문자열형 변수를 각각 선언하고, 이들을 하나의 리스트에 담아 각 요소의 자료형을 출력하는 코드

```python
# 각기 다른 자료형의 변수를 선언합니다.
int_var = 100
float_var = 3.14
bool_var = True
str_var = "Python"

# 선언한 변수들을 하나의 리스트에 담습니다.
my_list = [int_var, float_var, bool_var, str_var]

# 반복문을 사용해 리스트의 각 요소와 그 자료형을 출력합니다.
for item in my_list:
    print(f"값: {item}, 자료형: {type(item)}")
```

**문제 3:** `'100'`이라는 문자열을 정수형으로 변환한 후, `25`를 더한 값 출력

```python
# '100'이라는 문자열을 변수에 할당합니다.
text = '100'

# int() 함수를 사용해 문자열을 정수형으로 변환합니다.
# 변환된 값에 25를 더합니다.
result = int(text) + 25

# 결과를 출력합니다.
print(f"결과: {result}")
```

-----

#### **2. 입출력 함수**

**문제 1:** 사용자에게 섭씨 온도를 입력받아 화씨 온도로 변환하여 출력

```python
# 사용자에게 섭씨 온도를 입력받고, float() 함수로 실수형으로 변환합니다.
celsius = float(input("섭씨 온도를 입력하세요: "))

# 변환 공식에 따라 화씨 온도를 계산합니다.
fahrenheit = (celsius * 1.8) + 32

# 결과를 출력합니다.
print(f"섭씨 {celsius}도는 화씨 {fahrenheit}도 입니다.")
```

**문제 2:** 사용자에게 두 개의 숫자를 입력받아, 첫 번째 숫자를 두 번째 숫자로 나눈 몫과 나머지 출력

```python
# 사용자에게 두 개의 숫자를 입력받고 정수형으로 변환합니다.
num1 = int(input("첫 번째 숫자를 입력하세요: "))
num2 = int(input("두 번째 숫자를 입력하세요: "))

# 몫(//)과 나머지(%) 연산자를 사용하여 계산합니다.
quotient = num1 // num2
remainder = num1 % num2

# 결과를 출력합니다.
print(f"{num1}을(를) {num2}(으)로 나눈 몫은 {quotient}입니다.")
print(f"{num1}을(를) {num2}(으)로 나눈 나머지는 {remainder}입니다.")
```

-----

#### **3. 리스트**

**문제 1:** 학생 5명의 점수를 입력받아 리스트에 저장한 후, 총점과 평균을 출력

```python
# 점수를 저장할 빈 리스트를 생성합니다.
scores = []
# 5명의 학생 점수를 입력받기 위해 5번 반복합니다.
for i in range(5):
    # 사용자에게 점수를 입력받고, 정수형으로 변환하여 리스트에 추가합니다.
    score = int(input(f"학생 {i+1}의 점수를 입력하세요: "))
    scores.append(score)

# sum() 함수로 리스트의 총점을 계산합니다.
total_score = sum(scores)
# len() 함수로 리스트의 길이를 얻고 평균을 계산합니다.
average_score = total_score / len(scores)

# 결과를 출력합니다.
print(f"입력된 점수: {scores}")
print(f"총점: {total_score}")
print(f"평균: {average_score}")
```

**문제 2:** 리스트 `[1, 2, 3, 4, 5]`를 이용하여 `[5, 4, 3, 2, 1]`로 역순으로 만드는 코드

```python
my_list = [1, 2, 3, 4, 5]

# 방법 1: 리스트의 reverse() 메서드 사용 (원래 리스트를 변경)
# my_list.reverse()
# print(f"reverse() 메서드 사용: {my_list}")

# 방법 2: 슬라이싱을 이용해 새로운 리스트 생성 (원래 리스트는 그대로)
reversed_list = my_list[::-1]
print(f"슬라이싱을 이용한 역순: {reversed_list}")
```

**문제 3:** 리스트 `['사과', '바나나', '딸기']`와 리스트 `['배', '포도']`를 합쳐 새로운 리스트를 만드는 코드

```python
list1 = ['사과', '바나나', '딸기']
list2 = ['배', '포도']

# 방법 1: + 연산자를 사용해 두 리스트를 합칩니다.
combined_list = list1 + list2
print(f"두 리스트의 합: {combined_list}")

# 방법 2: extend() 메서드를 사용해 list1에 list2를 추가합니다.
# list1.extend(list2)
# print(f"extend() 메서드 사용: {list1}")
```

-----

#### **4. 조건문**

**문제 1:** 사용자에게 나이를 입력받아, '성인', '청소년', '어린이' 출력

```python
# 사용자에게 나이를 입력받고, 정수형으로 변환합니다.
age = int(input("나이를 입력하세요: "))

# if/elif/else 조건문을 사용해 나이에 따라 다른 문자열을 출력합니다.
if age >= 19:
    print("성인")
elif age >= 13:
    print("청소년")
else:
    print("어린이")
```

**문제 2:** 두 개의 숫자를 입력받아 더 큰 수 출력, 같으면 '두 수는 같습니다' 출력

```python
# 사용자에게 두 숫자를 입력받고 정수형으로 변환합니다.
num1 = int(input("첫 번째 숫자를 입력하세요: "))
num2 = int(input("두 번째 숫자를 입력하세요: "))

# if/elif/else 조건문을 사용해 두 수를 비교합니다.
if num1 > num2:
    print(f"더 큰 수는 {num1}입니다.")
elif num2 > num1:
    print(f"더 큰 수는 {num2}입니다.")
else:
    print("두 수는 같습니다.")
```

-----

#### **5. 반복문**

**문제 1:** `for`문과 `range()` 함수를 사용하여 1부터 100까지의 숫자 중 짝수의 합을 구하는 프로그램

```python
# 짝수의 합을 저장할 변수를 0으로 초기화합니다.
total = 0

# 1부터 100까지 2씩 증가하며 반복하여 짝수를 얻습니다.
for i in range(2, 101, 2):
    total += i # total = total + i

# 결과를 출력합니다.
print(f"1부터 100까지의 짝수의 합: {total}")
```

**문제 2:** `while`문과 `input()` 함수를 사용하여 사용자가 '종료'를 입력할 때까지 계속해서 입력받는 프로그램

```python
while True: # 무한 반복
    user_input = input("입력하세요 ('종료'를 입력하면 끝납니다): ")
    # 사용자가 '종료'를 입력했는지 확인합니다.
    if user_input == '종료':
        print("프로그램을 종료합니다.")
        break # 조건이 충족되면 반복문을 탈출합니다.
    else:
        print(f"입력값: {user_input}")
```

**문제 3:** `for`문을 사용하여 구구단 2단을 출력하는 프로그램

```python
# for 반복문을 사용해 1부터 9까지 순회합니다.
for i in range(1, 10):
    # 2 * i 의 결과를 계산하고 출력합니다.
    result = 2 * i
    print(f"2 x {i} = {result}")
```

-----
