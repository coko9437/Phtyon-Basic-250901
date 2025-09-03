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

### 📚 파트 2: 함수와 문자열 (3장)

#### **1. 함수**

**문제 1:** 사용자에게 세 개의 숫자를 입력받아, 이 중 가장 큰 숫자를 반환하는 함수를 작성하고 호출

```python
# 세 개의 숫자를 입력받아 가장 큰 값을 반환하는 함수를 정의합니다.
def find_max(num1, num2, num3):
    return max(num1, num2, num3) # 내장 함수 max()를 사용해 가장 큰 값을 반환

# 사용자에게 세 개의 숫자를 입력받고 정수형으로 변환합니다.
a = int(input("첫 번째 숫자: "))
b = int(input("두 번째 숫자: "))
c = int(input("세 번째 숫자: "))

# 함수를 호출하고 결과를 출력합니다.
largest_number = find_max(a, b, c)
print(f"가장 큰 수는 {largest_number}입니다.")
```

**문제 2:** 재귀 함수를 사용하여 팩토리얼(factorial)을 계산하는 함수 작성

```python
# 재귀 함수를 사용해 팩토리얼을 계산하는 함수를 정의합니다.
def factorial(n):
    # n이 1 이하일 경우, 1을 반환하며 재귀 호출을 멈춥니다.
    if n <= 1:
        return 1
    # 그렇지 않으면 n * (n-1)의 팩토리얼을 재귀적으로 호출합니다.
    else:
        return n * factorial(n - 1)

# 함수를 호출하고 결과를 출력합니다.
num = 5
print(f"{num}의 팩토리얼: {factorial(num)}")
```

**문제 3:** 가변 인자(variable-length arguments)를 받는 함수를 작성하여, 입력된 모든 숫자의 합을 구하고 반환하는 프로그램

```python
# *args를 사용해 가변 인자를 받는 함수를 정의합니다.
# *args는 입력된 모든 인자를 튜플 형태로 받습니다.
def sum_all(*args):
    # sum() 내장 함수를 사용해 튜플의 모든 요소의 합을 계산하고 반환합니다.
    return sum(args)

# 함수를 다양한 인자로 호출하고 결과를 출력합니다.
print(f"합계: {sum_all(1, 2, 3)}")
print(f"합계: {sum_all(10, 20, 30, 40)}")
```

-----

#### **2. 문자열**

**문제 1:** 사용자에게 문장을 입력받아, 그 문장의 단어 개수를 출력하는 프로그램

```python
# 사용자에게 문장을 입력받습니다.
sentence = input("문장을 입력하세요: ")

# split() 함수를 사용해 문장을 공백 기준으로 단어 리스트로 만듭니다.
words = sentence.split()

# len() 함수를 사용해 단어 리스트의 길이를 얻어 단어의 개수를 계산합니다.
word_count = len(words)

# 결과를 출력합니다.
print(f"문장 내 단어의 개수: {word_count}")
```

**문제 2:** 주어진 문자열 `s = "Hello World"`에서 'World'를 'Python'으로 바꾸는 코드

```python
s = "Hello World"

# replace() 메서드를 사용해 'World'를 'Python'으로 바꾼 새로운 문자열을 만듭니다.
new_s = s.replace("World", "Python")

# 결과를 출력합니다.
print(f"변경 전: {s}")
print(f"변경 후: {new_s}")
```

**문제 3:** 문자열 `s = "Hello World"`를 뒤집어 `dlroW olleH`와 같이 출력하는 코드

```python
s = "Hello World"

# 슬라이싱 기법 [::]를 사용해 문자열을 뒤집습니다.
# [시작:끝:단계]에서 단계를 -1로 지정하면 역순으로 순회합니다.
reversed_s = s[::-1]

# 결과를 출력합니다.
print(f"뒤집힌 문자열: {reversed_s}")
```

-----

### 📚 파트 3: 자료구조 (4장)

#### **1. 튜플**

**문제 1:** 튜플 `('사과', '바나나', '딸기')`에서 '바나나'를 '포도'로 변경하고, 새로운 튜플을 생성

```python
fruits_tuple = ('사과', '바나나', '딸기')

# 튜플은 변경 불가능하므로, 리스트로 변환하여 값을 수정합니다.
temp_list = list(fruits_tuple)
temp_list[1] = '포도'

# 수정된 리스트를 다시 튜플로 변환하여 새로운 튜플을 만듭니다.
new_fruits_tuple = tuple(temp_list)

# 결과를 출력합니다.
print(f"변경 전 튜플: {fruits_tuple}")
print(f"변경 후 튜플: {new_fruits_tuple}")
```

**문제 2:** 튜플 `t = ('A', 'B', 'C', 'D', 'E')`를 순서를 뒤집은 새로운 튜플로 만들기

```python
t = ('A', 'B', 'C', 'D', 'E')

# 방법 1: 리스트로 변환 후 reverse() 메서드 사용
# temp_list = list(t)
# temp_list.reverse()
# reversed_t = tuple(temp_list)

# 방법 2: 슬라이싱을 이용해 새로운 튜플 생성 (가장 간단한 방법)
reversed_t = t[::-1]

# 결과를 출력합니다.
print(f"원래 튜플: {t}")
print(f"뒤집힌 튜플: {reversed_t}")
```

**문제 3:** 리스트 `l = [1, 2, 3]`과 튜플 `t = (4, 5, 6)`을 하나의 리스트로 합치기

```python
l = [1, 2, 3]
t = (4, 5, 6)

# 방법 1: extend() 메서드와 list() 함수를 사용
# l.extend(list(t))
# print(l) # [1, 2, 3, 4, 5, 6]

# 방법 2: + 연산자를 사용 (튜플을 리스트로 변환한 후 합침)
combined_list = l + list(t)

# 결과를 출력합니다.
print(f"합쳐진 리스트: {combined_list}")
```

-----

#### **2. 세트**

**문제 1:** 리스트 `['A', 'B', 'C', 'A', 'D']`에서 중복을 제거하고, 'A'와 'E'가 포함되어 있는지 확인

```python
my_list = ['A', 'B', 'C', 'A', 'D']

# set() 함수를 사용해 리스트의 중복을 제거하고 세트로 변환합니다.
my_set = set(my_list)
print(f"중복이 제거된 세트: {my_set}")

# in 키워드를 사용해 특정 요소가 세트 안에 있는지 확인합니다.
print(f"'A'가 세트에 포함되어 있는가?: {'A' in my_set}")
print(f"'E'가 세트에 포함되어 있는가?: {'E' in my_set}")
```

**문제 2:** 두 개의 세트 `set1 = {1, 2, 3}`과 `set2 = {3, 4, 5}`를 생성하여 합집합, 교집합, 차집합 구하기

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# 합집합: union() 메서드 또는 | 연산자 사용
union_set = set1.union(set2)
print(f"합집합: {union_set}")

# 교집합: intersection() 메서드 또는 & 연산자 사용
intersection_set = set1.intersection(set2)
print(f"교집합: {intersection_set}")

# 차집합: difference() 메서드 또는 - 연산자 사용
difference_set = set1.difference(set2)
print(f"차집합 (set1 - set2): {difference_set}")
```

**문제 3:** 주어진 문장에서 중복을 제거하고 알파벳 순으로 정렬하여 출력

```python
sentence = 'the quick brown fox jumps over the lazy dog'

# split() 함수로 문장을 단어 리스트로 만듭니다.
words = sentence.split()

# set() 함수로 리스트의 중복을 제거합니다.
unique_words = set(words)

# sorted() 함수로 세트를 정렬된 리스트로 변환합니다.
sorted_words = sorted(list(unique_words))

# 결과를 출력합니다.
print(f"정렬된 단어 목록 (중복 제거): {sorted_words}")
```

-----

#### **3. 딕셔너리**

**문제 1:** 주어진 문자열 `sentence = 'hello world'`에서 각 문자가 몇 번 나타나는지 딕셔너리로 저장하고 출력

```python
sentence = 'hello world'
char_count = {} # 문자의 빈도수를 저장할 빈 딕셔너리 생성

# 문자열을 순회하며 각 문자의 개수를 셉니다.
for char in sentence:
    # 이미 딕셔너리에 키가 있으면 값을 1 증가시키고,
    if char in char_count:
        char_count[char] += 1
    # 없으면 새로 추가하며 값을 1로 초기화합니다.
    else:
        char_count[char] = 1

# 결과를 출력합니다.
print(f"문자 빈도수: {char_count}")

# (참고) Counter 모듈을 사용하면 더 쉽게 구현할 수 있습니다.
# from collections import Counter
# print(Counter(sentence))
```

**문제 2:** 딕셔너리 `d = {'a': 1, 'b': 2, 'c': 3}`의 키와 값을 서로 바꾸어 `{1: 'a', 2: 'b', 3: 'c'}`와 같은 새로운 딕셔너리 만들기

```python
d = {'a': 1, 'b': 2, 'c': 3}

# 키-값 쌍을 바꿀 새로운 딕셔너리를 생성합니다.
inverted_d = {value: key for key, value in d.items()}

# 결과를 출력합니다.
print(f"원래 딕셔너리: {d}")
print(f"키와 값이 바뀐 딕셔너리: {inverted_d}")
```

**문제 3:** 딕셔너리 `scores = {'math': 80, 'english': 90, 'science': 75}`에서 점수가 80점 이상인 과목만 출력

```python
scores = {'math': 80, 'english': 90, 'science': 75}

# 딕셔너리의 키와 값을 동시에 순회하기 위해 items() 메서드를 사용합니다.
for subject, score in scores.items():
    # 조건문을 사용해 점수가 80점 이상인지 확인합니다.
    if score >= 80:
        # 조건에 맞는 과목과 점수를 출력합니다.
        print(f"과목: {subject}, 점수: {score}")
```

-----

### 📚 파트 4: 파이썬 스타일 코드 (5장)

#### **1. 문자열의 분리 및 결합**

**문제 1:** 파일 경로를 `split()` 함수를 사용하여 디렉토리와 파일 이름으로 분리

```python
file_path = 'C:/Users/User/Documents/file.txt'

# '/'를 기준으로 문자열을 분리합니다.
parts = file_path.split('/')

# 분리된 리스트에서 디렉토리와 파일 이름을 가져옵니다.
directory = parts[:-1]      # 마지막 요소를 제외한 모든 요소
file_name = parts[-1]       # 마지막 요소

# 결과를 출력합니다.
print(f"전체 경로: {file_path}")
print(f"디렉토리: {directory}")
print(f"파일 이름: {file_name}")
```

**문제 2:** 리스트 `['a', 'b', 'c', 'd']`의 각 요소 사이에 ` ,  `를 넣어 `a, b, c, d`와 같은 문자열로 만들기

```python
my_list = ['a', 'b', 'c', 'd']

# ', '을 구분자로 사용해 join() 함수로 리스트의 요소들을 합칩니다.
result_string = ', '.join(my_list)

# 결과를 출력합니다.
print(f"합쳐진 문자열: {result_string}")
```

-----

#### **2. 리스트 컴프리헨션**

**문제 1:** 1부터 10까지의 숫자 중 홀수만 포함하는 리스트를 리스트 컴프리헨션을 사용하여 만들기

```python
# [표현식 for 항목 in 반복가능객체 if 조건] 형식으로 작성
# i % 2 == 1 이라는 조건으로 홀수만 필터링합니다.
odd_numbers = [i for i in range(1, 11) if i % 2 == 1]

# 결과를 출력합니다.
print(f"1부터 10까지의 홀수: {odd_numbers}")
```

**문제 2:** 리스트 `['Apple', 'Banana', 'Cherry']`의 모든 문자열을 소문자로 변환하여 새로운 리스트 만들기

```python
fruits = ['Apple', 'Banana', 'Cherry']

# str.lower() 메서드를 각 요소에 적용하여 소문자로 변환합니다.
lower_fruits = [fruit.lower() for fruit in fruits]

# 결과를 출력합니다.
print(f"소문자로 변환된 리스트: {lower_fruits}")
```

**문제 3:** 주어진 두 리스트의 모든 가능한 곱셈 조합으로 이루어진 리스트를 리스트 컴프리헨션을 사용하여 만들기

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

# 이중 for문을 사용하여 모든 조합을 만듭니다.
# 외부 for문이 list1을 순회하고, 내부 for문이 list2를 순회하며 곱셈을 수행합니다.
multiplication_list = [a * b for a in list1 for b in list2]

# 결과를 출력합니다.
print(f"모든 곱셈 조합: {multiplication_list}")
```

-----

#### **3. 람다 함수와 별표(`*`) 활용**

**문제 1:** `map()` 함수와 람다 함수를 사용하여 리스트 `[1, 2, 3, 4]`의 각 요소에 10을 더한 새로운 리스트 만들기

```python
my_list = [1, 2, 3, 4]

# map(함수, iterable) 함수는 리스트의 각 요소에 람다 함수를 적용합니다.
# 람다 함수는 각 요소(x)에 10을 더하는 역할을 합니다.
result_map = map(lambda x: x + 10, my_list)

# map() 객체를 리스트로 변환하여 출력합니다.
print(f"map()과 람다 함수 결과: {list(result_map)}")
```

**문제 2:** 별표를 활용하여, 주어진 리스트 `numbers = [1, 2, 3, 4, 5]`의 모든 요소를 하나의 함수로 전달하여 곱한 값을 반환하는 함수를 작성하고 호출

```python
# *args를 사용해 가변 인자를 받는 함수를 정의합니다.
def multiply_all(*args):
    result = 1
    # 튜플 형태로 받은 모든 인자를 순회하며 곱합니다.
    for number in args:
        result *= number
    return result

numbers = [1, 2, 3, 4, 5]

# 함수 호출 시 리스트 앞에 *를 붙여 리스트의 요소를 개별 인자로 언패킹합니다.
product = multiply_all(*numbers)

# 결과를 출력합니다.
print(f"모든 요소의 곱: {product}")
```

**문제 3:** 딕셔너리 `d = {'a': 1, 'b': 2, 'c': 3}`를 언패킹하여 함수에 키와 값을 전달하고 출력하는 코드

```python
d = {'a': 1, 'b': 2, 'c': 3}

# 키워드 가변 인자(**kwargs)를 받는 함수를 정의합니다.
# **kwargs는 키와 값 쌍을 딕셔너리 형태로 받습니다.
def print_items(**kwargs):
    # 받은 딕셔너리의 키와 값을 출력합니다.
    for key, value in kwargs.items():
        print(f"키: {key}, 값: {value}")

# 함수 호출 시 딕셔너리 앞에 **를 붙여 키와 값 쌍을 언패킹하여 전달합니다.
print_items(**d)
```

-----

### 📚 파트 5: 객체 지향 프로그래밍 (6장)

제공해주신 자료인 `06_객체 지향 프로그래밍.docx` 파일에는 클래스, 객체, 상속에 대한 개념 설명과 예제 코드는 있었지만, 다른 챕터들처럼 명시적인 \*\*'연습 예제'\*\*는 포함되어 있지 않았어요.

혹시 객체 지향 프로그래밍에 대한 추가적인 연습 문제나 개념 설명이 필요하시면, 제가 직접 만들어 드릴 수 있으니 편하게 말씀해주세요\!