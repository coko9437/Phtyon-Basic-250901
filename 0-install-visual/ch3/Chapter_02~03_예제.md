
---

## 🐍 파이썬 문법 모음집 (Chapter 02 ~ 03)

### Chapter 02: 기초 문법

#### 1. 변수와 자료형

##### ◦ 자료형 변환 (Type Casting)
데이터의 타입을 의도적으로 다른 타입으로 변환하는 것을 의미합니다.

```python
# 파일명: type_casting_examples.py

# float(실수) -> int(정수) : 소수점 이하를 버립니다.
a = int(10.3)
print(f"10.3을 정수로 변환: {a}")

# int(정수) -> float(실수) : 소수점이 추가됩니다.
b = float(a)
print(f"{a}를 실수로 변환: {b}")

# 숫자 -> str(문자열)
x = str(123)
print(f"숫자 123을 문자열로 변환: '{x}'")
print(f"변환 후 타입: {type(x)}")

# float(실수)가 담긴 str(문자열) -> float(실수)
# 숫자처럼 보이는 문자열은 실제 숫자 타입으로 변환해야 연산이 가능합니다.
a_str = '76.3'
b_float = float(a_str) # 문자열 '76.3'을 실수 76.3으로 변환
c_float = 2.3

# print(a_str + c_float) # TypeError: 문자열과 실수는 직접 더할 수 없음
# 변환된 b_float와 c_float는 정상적으로 덧셈 연산이 가능합니다.
print(f"실수 덧셈 결과: {b_float + c_float}")
```

##### ◦ 불리언(Boolean)과 비교
`True`는 숫자 `1`로, `False`는 숫자 `0`으로 취급될 수 있습니다. 또한, 내용이 없는 문자열(`""`)이나 숫자 `0`은 `False`로 간주됩니다.

```python
# 파일명: boolean_comparison.py

# 1 == True 비교는 1 == 1과 같으므로 True를 반환합니다.
print(f"1 == True 결과: {1 == True}")

# "" == False 비교는 '내용 없는 문자열'과 False를 비교하는 것이므로 False를 반환합니다.
# bool("")가 False라는 것과는 다른 개념입니다.
print(f"\"\" == False 결과: {\"\" == False}")

# bool() 함수로 명시적으로 변환하면, 내용 없는 문자열은 False로 취급됩니다.
print(f"bool(\"\")의 결과: {bool('')}")
```

#### 2. 입출력 함수

##### ◦ `print()` 함수와 포매팅(Formatting)
데이터를 화면에 출력할 때, 변수와 문자열을 조합하는 다양한 방법이 있습니다.

```python
# 파일명: print_formatting.py

name = "상용"
age = 42

# 1. % 연산자 방식 (전통적인 방식)
# %s는 문자열, %d는 정수를 의미하는 서식 지정자입니다.
print("이름: %s, 나이: %d" % (name, age))

# 2. f-string (Python 3.6+ 권장)
# 문자열 앞에 f를 붙이고, 중괄호 {} 안에 변수나 표현식을 직접 넣어 사용합니다.
# 가장 직관적이고 가독성이 높아 권장되는 방식입니다.
print(f"이름: {name}, 나이: {age}")```

##### ◦ `input()` 함수
사용자로부터 키보드 입력을 받아 **문자열**로 반환합니다.

```python
# 파일명: user_input.py

# input() 함수는 사용자 입력을 기다립니다.
lunch_menu = input("오늘 점심 뭐 먹죠? ")

# 입력받은 값은 lunch_menu 변수에 저장됩니다.
print(f"오늘 먹을 점심 메뉴는 '{lunch_menu}' 입니다.")
```

#### 3. 리스트 (List)
하나의 변수에 여러 개의 데이터를 순서대로 저장하는 자료형입니다. 다양한 타입의 데이터를 함께 담을 수 있으며, 값을 변경할 수 있습니다(mutable).

```python
# 파일명: list_operations_example.py

# 리스트는 정수, 실수, 문자열 등 다양한 타입을 함께 저장할 수 있습니다.
# (실무에서는 보통 같은 타입의 데이터를 담아 관리하는 것이 일반적입니다.)
a = [1, 2.0, "3"]
b = [4, 5, 6]
print(f"리스트 a: {a}")
print(f"리스트 b: {b}")

# 슬라이싱(Slicing): [시작인덱스:끝인덱스] (끝 인덱스는 포함되지 않음)
print(f"a[0:2]: {a[0:2]}") # 인덱스 0부터 1까지
# 리버스 인덱스: -1은 마지막, -2는 마지막에서 두 번째
print(f"b[-2:]: {b[-2:]}") # 마지막에서 두 번째부터 끝까지

# append(): 리스트의 맨 끝에 새로운 요소를 추가합니다.
a.append(100)
print(f"a에 100 추가 후: {a}")

# extend(): 다른 리스트의 모든 요소를 현재 리스트 끝에 추가합니다.
a.extend(b)
print(f"a에 b를 확장 후: {a}")

# + 연산자로 두 리스트를 합쳐 새로운 리스트를 만들 수도 있습니다.
c = a + b
print(f"a + b 결과: {c}")

# 슬라이싱과 스텝(step)
print(f"전체 리스트 역순 (a[::-1]): {a[::-1]}")
print(f"처음부터 2칸씩 건너뛰기 (a[::2]): {a[::2]}")

# insert()와 remove()
another_list = [1, 2, 3]
another_list.insert(1, 100) # 인덱스 1에 100을 삽입
print(f"\ninsert(1, 100) 후: {another_list}")
another_list.remove(100) # 값 100을 찾아서 제거 (첫 번째로 발견된 것만)
print(f"remove(100) 후: {another_list}")
```

#### 4. 조건문과 반복문
-   **`if-else`**: 조건의 참/거짓에 따라 다른 코드를 실행합니다.
-   **`for`**: 정해진 범위나 횟수만큼 코드를 반복 실행합니다. `range()` 함수와 함께 자주 사용됩니다.

```python
# 파일명: control_flow_examples.py

# if-else 조건문
if 3 > 4:
  print('참')
else:
  print('거짓')

# for 반복문과 range()
# range(start, stop, step): start부터 stop-1까지 step 간격으로 숫자를 생성합니다.
print("\n--- 0부터 8까지 2씩 증가 ---")
for i in range(0, 10, 2):
  print(i, end=" ")
print() # 줄바꿈

print("\n--- 10부터 2까지 1씩 감소 ---")
for i in range(10, 1, -1):
  print(i, end=" ")
print()
```

//=====================================================================================

### Chapter 03: 함수, 문자열

#### 1. 함수의 호출 방식 (Call by Object Reference)

파이썬은 "객체 참조에 의한 호출(Call by Object Reference)" 방식을 사용합니다.
-   **숫자, 문자열, 튜플 (Immutable 객체)**: 함수에 전달되어도 원본 값에 영향을 주지 않습니다. (값에 의한 호출처럼 동작)
-   **리스트, 딕셔너리 (Mutable 객체)**: 함수에 전달되면, 함수 내부에서 해당 객체를 변경할 경우 원본 객체도 함께 변경됩니다. (참조에 의한 호출처럼 동작)

```python
# 파일명: call_by_reference_example.py

def spam(eggs):
    # 1. 함수 호출 시, ham의 메모리 주소(id)가 eggs 매개변수에 복사됩니다.
    #    따라서 처음에는 ham과 eggs가 같은 객체를 가리킵니다.
    print(f"함수 내 시작 시 eggs의 id: {id(eggs)}")
    
    # 2. .append(1)은 가리키고 있는 객체 자체를 수정하는 작업입니다.
    #    따라서 원본인 ham도 [0, 1]로 변경됩니다. id는 변하지 않습니다.
    eggs.append(1)
    print(f"append 후 eggs의 id: {id(eggs)}")
    
    # 3. eggs = [2, 3]은 새로운 리스트 객체를 생성하고,
    #    eggs 변수가 그 새로운 객체를 가리키도록 재할당하는 것입니다.
    #    이 시점부터 eggs는 더 이상 원본 ham과 상관없는 다른 객체를 가리킵니다.
    eggs = [2, 3]
    print(f"재할당 후 eggs의 id: {id(eggs)}")

# --- 함수 호출 ---
ham = [0]
print(f"함수 호출 전 ham의 id: {id(ham)}")
spam(ham)
# 함수가 종료된 후, 원본 ham은 2번 단계까지만 영향을 받습니다.
print(f"함수 호출 후 ham의 값: {ham}") # 결과: [0, 1]
print(f"함수 호출 후 ham의 id: {id(ham)}")
```

#### 2. 변수의 사용 범위와 `global` 키워드

함수 안에서 전역 변수(global variable)의 값을 변경하려면 `global` 키워드를 사용해야 합니다.

```python
# 파일명: global_keyword_example.py

def modify_global_variable():
    # 이 함수 안에서 s는 전역 변수 s를 가리킨다고 선언합니다.
    global s
    # 이제 s에 값을 할당하면 전역 변수 s의 값이 직접 변경됩니다.
    s = "I am a global variable now"
    print(f"함수 내에서 출력: {s}")

# 전역 변수 s를 선언합니다.
s = "I am a local variable"
print(f"변경 전 전역 변수: {s}")

# 함수를 호출하여 전역 변수를 수정합니다.
modify_global_variable()

# 함수 호출 후 전역 변수 s의 값이 변경된 것을 확인할 수 있습니다.
print(f"변경 후 전역 변수: {s}")
```

#### 3. 가변 인수 (Variable Arguments)

##### ◦ `*args` (위치 가변 인수)
-   여러 개의 위치 인수를 하나의 **튜플(tuple)**로 묶어 받습니다.
-   언패킹(`*`)을 활용하여 유연하게 사용할 수 있습니다.

```python
# 파일명: args_example.py

def unpack_args(*a):
    """
    가변 인수를 받아 첫 번째, 두 번째, 그리고 나머지를 분리하여 반환합니다.
    """
    # a는 (1, 2, 3, 4, 5)와 같은 튜플입니다.
    # 튜플 언패킹을 사용하여 x, y, 그리고 나머지(*z)로 나눕니다.
    x, y, *z = a
    return x, y, z

print(f"abc(1,2,3) 결과: {unpack_args(1, 2, 3)}") # z = [3]
print(f"abc(1,2,3,4) 결과: {unpack_args(1, 2, 3, 4)}") # z = [3, 4]
print(f"abc(1,2,3,4,5) 결과: {unpack_args(1, 2, 3, 4, 5)}") # z = [3, 4, 5]
```

##### ◦ `**kwargs` (키워드 가변 인수)
-   `이름=값` 형태로 전달된 여러 개의 키워드 인수를 하나의 **딕셔너리(dictionary)**로 묶어 받습니다.

```python
# 파일명: kwargs_example.py

def process_keyword_args(**kwargs):
    """
    키워드 가변 인수를 딕셔너리로 받아 처리합니다.
    """
    # kwargs는 {'first': 1, 'second': 2, 'third': 3} 형태의 딕셔너리입니다.
    print(f"전체 키워드 인수 (딕셔너리): {kwargs}")
    
    # 딕셔너리처럼 키를 사용하여 값에 접근할 수 있습니다.
    if 'first' in kwargs:
        print(f"'first' 키의 값: {kwargs['first']}")

process_keyword_args(first=1, second=2, third=3)
```

#### 4. 문자열 고급 활용

##### ◦ 슬라이싱과 파일 처리
문자열은 리스트와 유사하게 슬라이싱이 가능하며, 파일에서 읽어온 텍스트 데이터를 처리하는 데 널리 사용됩니다.

```python
# 파일명: string_advanced.py

# 문자열 슬라이싱
my_str = "abcdefg"
print(f"my_str[0:2:1]: {my_str[0:2]}") # 인덱스 0부터 1까지 (기본 스텝 1)
print(f"my_str[::-1]: {my_str[::-1]}") # 문자열 뒤집기

# 파일 읽기 및 단어 수 세기
# 'yesterday.txt' 파일이 같은 폴더에 있어야 합니다.
try:
    with open("yesterday.txt", "r", encoding="utf-8") as f:
        # readlines()는 파일의 모든 줄을 읽어 리스트로 반환합니다.
        yesterday_lyric_lines = f.readlines()

    # 리스트의 각 줄을 하나의 문자열로 합칩니다.
    # line.strip()은 각 줄의 앞뒤 공백 및 줄바꿈 문자를 제거합니다.
    contents = ""
    for line in yesterday_lyric_lines:
        contents = contents + line.strip() + " "
    
    # 대소문자 구분 없이 세기 위해 모두 대문자로 변환(.upper()) 후 "YESTERDAY" 개수를 셉니다.
    number_of_yesterday = contents.upper().count("YESTERDAY")
    print(f"\n노래 가사에서 'yesterday' 단어 개수: {number_of_yesterday}")
except FileNotFoundError:
    print("\n'yesterday.txt' 파일을 찾을 수 없습니다.")
```

##### ◦ f-string을 이용한 숫자 포매팅
f-string은 소수점 자릿수 지정 등 숫자 서식을 편리하게 지정할 수 있습니다.

```python
# 파일명: fstring_formatting.py

number = 3.14159265

# :.nf 형태로 소수점 n째 자리까지 표기합니다. (자동으로 반올림됨)
print(f"소수점 둘째 자리까지: {number:.2f}") # 3.14
print(f"소수점 넷째 자리까지: {number:.4f}") # 3.1416
print(f"정수로 (소수점 0자리): {number:.0f}") # 3
```