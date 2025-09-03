### 📚 파트 3: 함수와 문자열

#### **1. 참조에 의한 호출 (Call by Reference)**

파이썬에서 리스트와 같은 **가변(mutable)** 객체를 함수에 매개변수로 전달하면, 함수 내부에서 객체에 대한 변경(e.g., `append()`)이 함수 외부에도 영향을 미칩니다. 그러나 새로운 객체를 **재할당**하면 함수 내부의 변수는 새로운 객체를 참조하게 되고, 함수 외부의 변수와는 관계가 끊어집니다.

```python
# 함수 내부에서 리스트 조작 실험
def spam(eggs):
    # (1) 함수 호출 시, 매개변수 eggs는 ham이 참조하는 리스트 객체와 동일한 id를 가집니다.
    print(f"eggs의 id(메모리위치주솟값 정수로표현) : {id(eggs)}")

    # (2) eggs 리스트에 '1'을 추가합니다.
    # 이 작업은 원본 리스트 객체 자체를 변경하므로,
    # 함수 외부의 ham 리스트에도 영향을 줍니다.
    eggs.append(1)
    print(f"eggs.append(1) 후, eggs의 id2(메모리위치주솟값 정수로표현) : {id(eggs)}")

    # (3) eggs에 새로운 리스트 객체 [2, 3]을 재할당합니다.
    # 이제 eggs 변수는 원래의 리스트가 아닌 새로운 리스트를 가리키게 됩니다.
    # 이 시점부터 eggs와 ham은 서로 다른 객체를 참조합니다.
    eggs = [2, 3]
    print(f"eggs = [2,3] 후, eggs의 id3(메모리위치주솟값 정수로표현) :{id(eggs)}")

# 함수 사용
ham = [0] # 요소가 0인 리스트를 준비합니다.
# (0) spam(ham) 호출 전, ham 리스트의 메모리 주소(id)를 출력합니다.
print(f"spam(ham)호출 하기 전의 ham의 id(메모리위치주솟값 정수로표현) : {id(ham)}")

# 함수를 호출합니다.
spam(ham)

# (4) 함수 실행 후, ham의 id를 출력합니다.
# eggs.append(1)로 인해 ham 리스트의 내용이 변경되었지만,
# ham이 참조하는 객체 자체는 변경되지 않았으므로 id는 동일합니다.
print(f"spam(ham)호출 하기 후의 ham의 id(메모리위치주솟값 정수로표현) : {id(ham)}")
# (5) 최종적으로 ham 리스트의 값을 출력합니다.
# eggs.append(1)의 결과는 반영되었지만, eggs = [2,3]의 재할당은 반영되지 않았습니다.
```

#### **2. `global` 키워드**

`global` 키워드는 함수 내부에서 전역 변수의 값을 변경하고자 할 때 사용합니다. 이 키워드를 사용하지 않으면 함수 내부에서 선언된 변수는 자동으로 지역 변수로 취급됩니다.

```python
def f():
    global s # s를 지역 변수가 아닌 전역 변수 s로 사용하겠다고 선언
    s = "lsy" # 전역 변수 s의 값을 'lsy'로 변경
    print(s) # 'lsy' 출력

s = "abc" # 전역 변수 s를 'abc'로 초기화
f() # 함수 f() 호출, s의 값이 'lsy'로 변경됨
print(s) # 변경된 전역 변수 s의 값 'lsy' 출력
```

#### **3. 가변 인수(`*`)와 언패킹**

함수의 매개변수 앞에 별표(`*`)를 붙이면, 인수의 개수와 상관없이 여러 개의 인수를 받아 **튜플**로 묶어줍니다.

```python
def abc(*a):
    # 언패킹: 튜플 a의 첫 번째, 두 번째 요소를 x, y에 할당하고,
    # 나머지 모든 요소를 z 리스트에 할당합니다.
    x, y, *z = a
    return x, y, z

print(abc(1, 2, 3))     # x=1, y=2, z=[3]
print(abc(1, 2, 3, 4))  # x=1, y=2, z=[3, 4]
print(abc(1, 2, 3, 4, 5)) # x=1, y=2, z=[3, 4, 5]
```

#### **4. 키워드 가변 인수(`**`)**

두 개의 별표(`**`)를 사용하면, `key=value` 형태로 전달되는 키워드 인수를 **딕셔너리** 형태로 받습니다.

```python
def aaa(**keys):
    # 전달받은 키워드 인수를 딕셔너리 형태로 출력합니다.
    print(keys)
    # 딕셔너리에서 'first' 키에 해당하는 값을 출력합니다.
    print(f"value : {keys['first']}")

# first, second, third 키워드 인수를 전달합니다.
aaa(first=1, second=2, third=3)
```

#### **5. 문자열 슬라이싱**

문자열은 리스트와 같이 슬라이싱이 가능하며, `[start:end:step]` 구문을 사용해 원하는 부분 문자열을 얻을 수 있습니다.

```python
str = "abc"
# str[0:2:1]: 인덱스 0부터 2 미만까지 1단계씩 슬라이싱. 'ab' 출력.
print(str[0:2:1])
# str[::-1]: 처음부터 끝까지 역순으로 슬라이싱. 'cba' 출력.
print(str[::-1])
```

#### **6. 파일 입출력 및 문자열 처리**

파일을 읽고 특정 단어의 개수를 세는 예제입니다.

```python
# 'yesterday.txt' 파일을 읽기 모드('r')로 엽니다.
f = open("yesterday.txt","r")
# readlines() 함수로 파일의 모든 줄을 읽어 리스트로 저장합니다.
yesterday_lyric = f.readlines()
# 파일을 닫습니다.
f.close()

contents = "" # 전체 내용을 저장할 빈 문자열
for line in yesterday_lyric:
    # 각 줄의 앞뒤 공백을 제거(strip())하고 줄바꿈 문자를 추가하여 이어붙입니다.
    contents = contents + line.strip() + "\n"

# 전체 내용을 대문자(upper())로 변환한 후, 'YESTERDAY' 단어의 개수를 셉니다.
# 대소문자 구분을 없애기 위해 모두 대문자로 변환합니다.
number_of_yesterday = contents.upper().count("YESTERDAY")
# 결과를 출력합니다.
print(f"노래 가사에서 yesterday 단어 갯수 확인 : {number_of_yesterday}")
```

#### **7. f-string에서의 소수점 서식 지정**

f-string을 사용하여 소수점 자리를 원하는 대로 제어하는 방법입니다.

```python
number = 3.14159265

# 소수점 둘째 자리까지 표기: .2f
print(f"둘째 자리까지: {number:.2f}")

# 소수점 넷째 자리까지 표기: .4f
print(f"넷째 자리까지: {number:.4f}")

# 소수점 자리를 표기하지 않음 (정수로 표기): .0f
print(f"정수로: {number:.0f}")
```