
---

### 📘 Chapter 02: 기초 문법 심화 문제

#### 문제 1: BMI 지수 계산 및 등급 분류기

**문제**
사용자로부터 키(cm)와 몸무게(kg)를 입력받아 BMI(체질량지수)를 계산하고, 계산된 BMI 지수에 따라 "저체중", "정상", "과체중", "비만" 등급을 출력하는 프로그램을 작성하세요.

- **BMI 계산 공식**: 몸무게(kg) ÷ (키(m) × 키(m))
- **등급 분류 기준**:
  - 20 미만: 저체중
  - 20 이상 25 미만: 정상
  - 25 이상 30 미만: 과체중
  - 30 이상: 비만

---

**풀이 과정 및 로직**
1.  사용자에게 키(cm)와 몸무게(kg)를 `input()` 함수로 입력받습니다.
2.  입력받은 값은 문자열이므로, 계산을 위해 각각 `float()` 또는 `int()`를 사용하여 숫자형으로 변환합니다.
3.  키는 cm 단위로 입력받았으므로, m 단위로 변환하기 위해 100으로 나눕니다.
4.  BMI 공식을 사용하여 BMI 지수를 계산합니다.
5.  `if-elif-else` 조건문을 사용하여 계산된 BMI 지수가 어떤 등급 분류 기준에 해당하는지 확인하고, 결과를 출력합니다.

**처리 순서**
1.  키 입력받기 (문자열)
2.  몸무게 입력받기 (문자열)
3.  입력받은 키와 몸무게를 실수(float)로 형 변환
4.  키(cm)를 키(m)로 변환
5.  BMI 공식 적용하여 계산
6.  `if-elif-else` 조건문으로 등급 판별
7.  최종 등급 출력

**정답 코드**
```python
# 파일명: bmi_calculator.py

# 1, 2, 3. 사용자로부터 키와 몸무게를 입력받아 실수로 변환합니다.
height_cm = float(input("키를 cm 단위로 입력하세요: "))
weight_kg = float(input("몸무게를 kg 단위로 입력하세요: "))

# 4. 키 단위를 cm에서 m로 변환합니다.
height_m = height_cm / 100

# 5. BMI 지수를 계산합니다.
bmi = weight_kg / (height_m ** 2)

# 6. if-elif-else 조건문으로 BMI 등급을 판별합니다.
if bmi >= 30:
    grade = "비만"
elif bmi >= 25:
    grade = "과체중"
elif bmi >= 20:
    grade = "정상"
else:
    grade = "저체중"

# 7. 결과를 소수점 둘째 자리까지 출력합니다.
print(f"당신의 BMI 지수는 {bmi:.2f}이며, '{grade}' 등급입니다.")
```

---

#### 문제 2: 숫자 맞추기 게임

**문제**
컴퓨터가 1부터 100 사이의 임의의 숫자를 하나 생성하고, 사용자가 그 숫자를 맞출 때까지 기회를 주는 게임을 만드세요. 사용자가 숫자를 입력할 때마다 컴퓨터는 자신이 생각한 숫자보다 "더 큽니다" 또는 "더 작습니다" 라는 힌트를 주어야 합니다. 숫자를 맞추면 시도한 횟수와 함께 축하 메시지를 출력하고 게임을 종료하세요.

---

**풀이 과정 및 로직**
1.  `random` 모듈을 가져와 `randint(1, 100)` 함수로 1에서 100 사이의 정답 숫자를 생성합니다.
2.  시도 횟수를 기록할 변수(예: `tries`)를 0으로 초기화합니다.
3.  `while True` 무한 루프를 사용하여 게임을 계속 진행시킵니다.
4.  루프 안에서 사용자에게 숫자를 `input()`으로 입력받고 `int()`로 변환합니다.
5.  시도 횟수를 1 증가시킵니다.
6.  `if-elif-else` 문을 사용하여 사용자의 입력값과 정답 숫자를 비교합니다.
    -   입력값이 정답보다 작으면 "더 큽니다"라고 출력합니다.
    -   입력값이 정답보다 크면 "더 작습니다"라고 출력합니다.
    -   입력값이 정답과 같으면 "정답입니다!"와 시도 횟수를 출력하고 `break`를 사용하여 루프를 탈출합니다.

**처리 순서**
1.  `random` 모듈 import
2.  1~100 사이의 정수 난수 생성하여 변수에 저장
3.  시도 횟수 변수 초기화
4.  `while` 반복문 시작
5.  사용자에게 숫자 입력받기 및 정수로 변환
6.  시도 횟수 1 증가
7.  입력값과 정답 비교하여 힌트 제공 또는 정답 처리
8.  정답일 경우, `break`로 반복문 종료
9.  게임 종료 메시지 출력

**정답 코드**
```python
# 파일명: number_guessing_game.py
# 1. random 모듈을 가져옵니다.
import random

# 2. 1부터 100 사이의 임의의 정수를 생성합니다.
answer = random.randint(1, 100)
# 3. 시도 횟수를 저장할 변수를 초기화합니다.
tries = 0

print("--- 숫자 맞추기 게임 (1~100) ---")

# 4. 정답을 맞출 때까지 무한 반복합니다.
while True:
    # 5. 사용자로부터 숫자를 입력받고 정수로 변환합니다.
    try:
        guess = int(input("숫자를 입력하세요: "))
    except ValueError:
        print("잘못된 입력입니다. 숫자만 입력해주세요.")
        continue # 루프의 처음으로 돌아감

    # 6. 시도 횟수를 1 증가시킵니다.
    tries += 1

    # 7. 사용자의 추측과 정답을 비교합니다.
    if guess < answer:
        print("더 큽니다!")
    elif guess > answer:
        print("더 작습니다!")
    else:
        # 8. 정답을 맞춘 경우
        print(f"정답입니다! {tries}번 만에 맞추셨습니다.")
        break # while 루프를 종료합니다.
```

---

#### 문제 3: 간단한 ATM기 프로그램

**문제**
초기 잔액이 100,000원인 ATM 기를 시뮬레이션하는 프로그램을 만드세요. 사용자는 "입금", "출금", "조회", "종료" 중 하나의 작업을 선택할 수 있습니다. 각 작업은 다음과 같이 동작해야 합니다.
- **입금**: 입금할 금액을 입력받아 잔액에 더합니다.
- **출금**: 출금할 금액을 입력받아 잔액에서 뺍니다. (단, 잔액보다 많은 금액은 출금할 수 없습니다.)
- **조회**: 현재 잔액을 출력합니다.
- **종료**: 프로그램을 종료합니다.

---

**풀이 과정 및 로직**
1.  초기 잔액을 저장할 변수 `balance`를 100000으로 설정합니다.
2.  `while True` 무한 루프를 사용하여 ATM 기가 계속 동작하도록 합니다.
3.  루프 안에서 사용자에게 "입금, 출금, 조회, 종료" 중 원하는 작업을 입력받습니다.
4.  `if-elif-else` 문을 사용하여 사용자의 입력에 따라 다른 동작을 수행합니다.
    -   "입금"을 선택하면, 금액을 입력받아 `balance`에 더하고 결과를 출력합니다.
    -   "출금"을 선택하면, 금액을 입력받습니다.
        -   만약 출금액이 잔액보다 크면 "잔액이 부족합니다." 메시지를 출력합니다.
        -   그렇지 않으면 `balance`에서 출금액을 빼고 결과를 출력합니다.
    -   "조회"를 선택하면, 현재 `balance`를 출력합니다.
    -   "종료"를 선택하면, "이용해주셔서 감사합니다." 메시지를 출력하고 `break`로 루프를 종료합니다.
    -   잘못된 입력을 하면 "잘못된 입력입니다." 메시지를 출력합니다.

**처리 순서**
1.  잔액 변수 `balance` 초기화
2.  `while` 루프 시작
3.  사용자에게 작업 메뉴 표시 및 선택 입력받기
4.  `if-elif-else`로 선택된 작업 분기
5.  (입금) 금액 입력받기, 잔액에 더하기, 결과 출력
6.  (출금) 금액 입력받기, 잔액 비교 후 가능하면 빼기, 결과 출력
7.  (조회) 현재 잔액 출력
8.  (종료) `break`로 루프 종료
9.  (그 외) 오류 메시지 출력

**정답 코드**
```python
# 파일명: simple_atm.py

# 1. 초기 잔액을 설정합니다.
balance = 100000
print("--- 환영합니다 ---")

# 2. 사용자가 '종료'를 입력할 때까지 반복합니다.
while True:
    # 3. 사용자에게 작업 메뉴를 보여주고 입력을 받습니다.
    print(f"\n현재 잔액: {balance}원")
    action = input("원하는 작업을 선택하세요 (입금, 출금, 조회, 종료): ")

    # 4. 사용자의 선택에 따라 다른 동작을 수행합니다.
    if action == "입금":
        # 5. 입금 처리
        amount = int(input("입금할 금액을 입력하세요: "))
        balance += amount
        print(f"{amount}원이 입금되었습니다.")

    elif action == "출금":
        # 6. 출금 처리
        amount = int(input("출금할 금액을 입력하세요: "))
        if amount > balance:
            print("오류: 잔액이 부족합니다.")
        else:
            balance -= amount
            print(f"{amount}원이 출금되었습니다.")

    elif action == "조회":
        # 7. 잔액 조회 처리
        print(f"현재 잔액은 {balance}원 입니다.")

    elif action == "종료":
        # 8. 프로그램 종료
        print("이용해주셔서 감사합니다.")
        break

    else:
        # 9. 잘못된 입력 처리
        print("잘못된 입력입니다. 다시 시도해주세요.")
```

---

#### 문제 4: 구구단 N단부터 M단까지 출력하기

**문제**
사용자로부터 시작 단(N)과 끝 단(M)을 입력받아, N단부터 M단까지의 구구단을 모두 출력하는 프로그램을 작성하세요. (단, 중첩 `for`문을 사용해야 합니다.)

---

**풀이 과정 및 로직**
1.  사용자로부터 시작 단과 끝 단을 `input()`으로 입력받고, `int()`로 변환합니다.
2.  바깥쪽 `for`문은 시작 단부터 끝 단까지 반복하도록 `range(start, end + 1)`을 사용합니다. 이 `for`문의 반복 변수는 '단'을 나타냅니다.
3.  안쪽 `for`문은 각 단에서 곱해지는 수인 1부터 9까지 반복하도록 `range(1, 10)`을 사용합니다.
4.  안쪽 `for`문 안에서 `print()` 함수와 f-string을 사용하여 "단 x 곱하는 수 = 결과" 형태로 구구단을 출력합니다.
5.  하나의 단 출력이 끝나면, 바깥쪽 `for`문에서 `print()`로 빈 줄을 하나 출력하여 단끼리 구분되도록 합니다.

**처리 순서**
1.  시작 단(N) 입력받고 정수로 변환
2.  끝 단(M) 입력받고 정수로 변환
3.  바깥쪽 `for`문 시작 (N부터 M까지 반복)
4.  현재 '단'을 출력
5.  안쪽 `for`문 시작 (1부터 9까지 반복)
6.  구구단 계산식 출력
7.  안쪽 `for`문 종료
8.  단 구분을 위한 줄바꿈 출력
9.  바깥쪽 `for`문 종료

**정답 코드**
```python
# 파일명: gugudan_range.py

# 1, 2. 사용자로부터 시작 단과 끝 단을 입력받습니다.
start_dan = int(input("출력을 시작할 단을 입력하세요: "))
end_dan = int(input("출력을 끝낼 단을 입력하세요: "))

print(f"\n--- {start_dan}단부터 {end_dan}단까지 구구단 출력 ---")

# 3. 바깥쪽 for문: start_dan부터 end_dan까지 반복합니다.
for dan in range(start_dan, end_dan + 1):
    # 4. 현재 단의 제목을 출력합니다.
    print(f"--- {dan}단 ---")
    
    # 5. 안쪽 for문: 1부터 9까지 곱하는 수를 반복합니다.
    for i in range(1, 10):
        # 6. 구구단 결과를 출력합니다.
        print(f"{dan} x {i} = {dan * i}")
        
    # 7, 8. 한 단의 출력이 끝나면 가독성을 위해 빈 줄을 추가합니다.
    print()
```

---

#### 문제 5: 리스트에서 특정 요소 찾아 제거하기

**문제**
숫자로 이루어진 리스트 `data = [1, 2, 3, 4, 3, 2, 1]`가 있습니다. 사용자로부터 제거하고 싶은 숫자를 입력받아, 리스트 `data`에서 해당 숫자를 **모두** 제거한 후의 리스트를 출력하는 프로그램을 작성하세요. (`remove()` 메소드는 한 번에 하나만 제거하므로 반복문과 함께 사용해야 합니다.)

---

**풀이 과정 및 로직**
1.  주어진 리스트 `data`를 선언합니다.
2.  사용자로부터 제거할 숫자를 `input()`으로 입력받고 `int()`로 변환합니다.
3.  `while` 반복문을 사용합니다. 반복문의 조건은 "제거할 숫자가 `data` 리스트 안에 있는 동안(`in` 연산자 사용)"으로 설정합니다.
4.  `while` 루프가 실행된다는 것은 제거할 숫자가 리스트 안에 최소 하나 이상 존재한다는 의미입니다.
5.  루프 안에서 `data.remove(제거할_숫자)`를 실행하여 해당 숫자를 하나 제거합니다.
6.  루프는 리스트 안에 제거할 숫자가 더 이상 없을 때까지 반복되며, 발견될 때마다 하나씩 제거합니다.
7.  `while` 루프가 종료된 후, 최종적으로 변경된 `data` 리스트를 출력합니다.

**처리 순서**
1.  초기 리스트 `data` 선언
2.  사용자에게 제거할 숫자 입력받기 및 정수로 변환
3.  `while` 루프 시작 (조건: 제거할 숫자가 리스트에 `in` 하는 동안)
4.  `list.remove()` 메소드로 해당 숫자 제거
5.  `while` 루프 종료 (리스트에 해당 숫자가 더 이상 없을 때)
6.  결과 리스트 출력

**정답 코드**
```python
# 파일명: remove_all_elements.py

# 1. 초기 리스트를 정의합니다.
data = [1, 2, 3, 4, 3, 2, 1, 5, 3, 6]
print(f"초기 리스트: {data}")

# 2. 사용자로부터 제거할 숫자를 입력받습니다.
num_to_remove = int(input("리스트에서 제거하고 싶은 숫자를 입력하세요: "))

# 3. 제거할 숫자가 리스트 안에 더 이상 없을 때까지 반복합니다.
while num_to_remove in data:
    # 4. 리스트에서 해당 숫자를 제거합니다. remove()는 첫 번째로 발견된 요소만 제거합니다.
    data.remove(num_to_remove)

# 6. 최종 결과를 출력합니다.
print(f"'{num_to_remove}'를 모두 제거한 후 리스트: {data}")
```
### 📘 Chapter 03: 함수, 문자열 심화 문제

#### 문제 1: 이메일 주소 유효성 검사 함수

**문제**
사용자로부터 이메일 주소를 입력받아, 해당 이메일이 유효한 형식인지 판별하는 함수 `is_valid_email(email)`을 작성하세요. 유효성 규칙은 다음과 같습니다.
1.  반드시 `'@'` 문자를 1개 포함해야 합니다.
2.  `'@'` 문자 기준으로 나눈 앞 부분(ID)과 뒷 부분(도메인)이 모두 존재해야 합니다.
3.  도메인 부분에는 반드시 `'.'` 문자가 포함되어야 합니다.

---

**풀이 과정 및 로직**
1.  `is_valid_email` 함수를 `email`이라는 매개변수를 받도록 정의합니다.
2.  **규칙 1**: `email.count('@')`를 사용하여 `'@'`의 개수가 정확히 1개인지 확인합니다. 1개가 아니면 `False`를 반환합니다.
3.  **규칙 2**: `email.split('@')`를 사용하여 이메일을 ID 부분과 도메인 부분으로 나눕니다.
    -   나눠진 리스트의 각 요소(ID, 도메인)의 길이가 0인지 확인합니다. 즉, `id_part`나 `domain_part`가 비어있으면 `False`를 반환합니다.
4.  **규칙 3**: 도메인 부분(`domain_part`)에 `'.'`이 포함되어 있는지 `in` 연산자로 확인합니다. 포함되어 있지 않으면 `False`를 반환합니다.
5.  위의 모든 검사를 통과하면, 이메일은 유효한 형식이므로 `True`를 반환합니다.
6.  함수 외부에서 사용자에게 이메일을 입력받고, 작성한 함수를 호출하여 결과를 출력합니다.

**처리 순서**
1.  `is_valid_email(email)` 함수 정의
2.  (함수 내) `'@'` 개수 검사
3.  (함수 내) `'@'`로 분리 후 ID와 도메인이 비어있는지 검사
4.  (함수 내) 도메인 부분에 `'.'`이 있는지 검사
5.  (함수 내) 모든 조건을 통과하면 `True`, 아니면 `False` 반환
6.  (메인 코드) 사용자에게 이메일 입력받기
7.  (메인 코드) 함수 호출 및 결과에 따라 "유효/유효하지 않음" 출력

**정답 코드**
```python
# 파일명: email_validator.py

# 1. 이메일 유효성 검사 함수를 정의합니다.
def is_valid_email(email):
    """주어진 이메일 주소가 기본 형식에 맞는지 검사하는 함수"""
    
    # 2. '@' 문자가 정확히 1개 있는지 확인합니다.
    if email.count('@') != 1:
        return False
    
    # 3. '@'를 기준으로 ID와 도메인으로 나눕니다.
    id_part, domain_part = email.split('@')
    
    # ID나 도메인이 비어있는지 확인합니다.
    if id_part == "" or domain_part == "":
        return False
        
    # 4. 도메인 부분에 '.' 문자가 있는지 확인합니다.
    if '.' not in domain_part:
        return False
        
    # 5. 모든 검사를 통과하면 유효한 것으로 간주합니다.
    return True

# --- 메인 실행 부분 ---
# 6. 사용자로부터 이메일 주소를 입력받습니다.
user_email = input("검사할 이메일 주소를 입력하세요: ")

# 7. 함수를 호출하여 유효성을 검사하고 결과를 출력합니다.
if is_valid_email(user_email):
    print(f"'{user_email}'은(는) 유효한 이메일 형식입니다.")
else:
    print(f"'{user_email}'은(는) 유효하지 않은 이메일 형식입니다.")

```

---

#### 문제 2: 욕설 필터링 함수

**문제**
금지된 단어 리스트 `banned_words = ["바보", "멍청이", "해삼"]`가 있습니다. 사용자로부터 문장을 입력받아, 문장 속에 포함된 금지된 단어를 모두 `'*'`로 마스킹 처리하는 함수 `filter_sentence(sentence, banned_list)`를 작성하세요. 예를 들어 "너는 바보 멍청이"가 입력되면 "너는 ** ****"로 출력되어야 합니다.

---

**풀이 과정 및 로직**
1.  `filter_sentence` 함수를 `sentence`와 `banned_list` 두 매개변수를 받도록 정의합니다.
2.  함수 내에서 `banned_list`를 순회하는 `for` 루프를 만듭니다.
3.  루프의 각 반복에서 현재 금지된 단어(`word`)가 `sentence` 안에 있는지 확인합니다.
4.  `string.replace(old, new)` 메서드를 사용하여 `sentence` 안의 `word`를 `len(word)` 개수만큼의 `'*'`로 치환합니다. 예를 들어, "바보"는 "**"로, "멍청이"는 "***"로 바꿔야 합니다.
5.  `for` 루프가 모두 끝나면, 모든 금지 단어가 마스킹 처리된 `sentence`를 반환합니다.
6.  함수 외부에서 금지 단어 리스트를 정의하고, 사용자에게 문장을 입력받은 후, 함수를 호출하여 필터링된 결과를 출력합니다.

**처리 순서**
1.  `filter_sentence(sentence, banned_list)` 함수 정의
2.  (함수 내) 금지 단어 목록(`banned_list`)을 순회하는 `for` 루프 시작
3.  (함수 내) 현재 금지 단어(`word`)의 길이만큼 `'*'` 문자열 생성
4.  (함수 내) `sentence.replace()`를 사용하여 원본 문장의 금지 단어를 `'*'`로 치환하고, 결과를 다시 `sentence` 변수에 할당
5.  (함수 내) 루프 종료 후, 필터링된 `sentence` 반환
6.  (메인 코드) 금지 단어 리스트 정의
7.  (메인 코드) 사용자에게 문장 입력받기
8.  (메인 코드) 함수 호출 및 결과 출력

**정답 코드**
```python
# 파일명: word_filter.py

# 1. 욕설 필터링 함수를 정의합니다.
def filter_sentence(sentence, banned_list):
    """문장 속 금지된 단어를 '*'로 마스킹 처리하는 함수"""
    
    # 2. 금지 단어 리스트를 순회합니다.
    for word in banned_list:
        # 문장 안에 금지 단어가 포함되어 있다면
        if word in sentence:
            # 3. 해당 단어의 길이만큼 '*' 문자를 생성합니다.
            mask = "*" * len(word)
            # 4. 문장 속 단어를 마스킹 처리합니다.
            sentence = sentence.replace(word, mask)
            
    # 5. 모든 필터링이 끝난 문장을 반환합니다.
    return sentence

# --- 메인 실행 부분 ---
# 6. 금지된 단어 리스트를 정의합니다.
banned_words = ["바보", "멍청이", "해삼", "말미잘"]

# 7. 사용자로부터 문장을 입력받습니다.
user_sentence = input("문장을 입력하세요: ")

# 8. 함수를 호출하여 필터링된 결과를 받아옵니다.
filtered = filter_sentence(user_sentence, banned_words)

print(f"필터링 결과: {filtered}")
```

---

#### 문제 3: 숫자 리스트의 통계 계산 함수

**문제**
숫자로 이루어진 리스트를 인자로 받아, 해당 리스트의 합계, 평균, 최댓값, 최솟값을 한 번에 계산하여 **튜플(tuple) 형태로 반환**하는 함수 `calculate_stats(numbers)`를 작성하세요. 단, 빈 리스트가 입력될 경우 `(0, 0, 0, 0)`을 반환해야 합니다. (`sum()`, `len()`, `max()`, `min()` 내장 함수 사용)

---

**풀이 과정 및 로직**
1.  `calculate_stats` 함수를 `numbers`라는 매개변수를 받도록 정의합니다.
2.  먼저 `if not numbers:` 또는 `if len(numbers) == 0:` 조건문으로 입력받은 리스트가 비어있는지 확인합니다. 비어있다면 `(0, 0, 0, 0)`을 즉시 반환합니다.
3.  리스트가 비어있지 않다면, `sum(numbers)`로 합계를 계산합니다.
4.  `sum(numbers) / len(numbers)`로 평균을 계산합니다.
5.  `max(numbers)`와 `min(numbers)`로 최댓값과 최솟값을 각각 구합니다.
6.  계산된 합계, 평균, 최댓값, 최솟값을 튜플 `(total, average, maximum, minimum)` 형태로 묶어 `return`합니다.
7.  함수 외부에서 숫자 리스트를 정의하고, 함수를 호출하여 반환된 튜플을 언패킹(unpacking)하여 각 변수에 할당한 후, 결과를 보기 좋게 출력합니다.

**처리 순서**
1.  `calculate_stats(numbers)` 함수 정의
2.  (함수 내) 리스트가 비어있는지 검사 후, 비어있으면 `(0, 0, 0, 0)` 반환
3.  (함수 내) `sum()`으로 합계 계산
4.  (함수 내) `len()`을 이용해 평균 계산
5.  (함수 내) `max()`, `min()`으로 최댓값, 최솟값 계산
6.  (함수 내) 계산된 4개의 값을 튜플로 묶어 반환
7.  (메인 코드) 테스트용 숫자 리스트 생성
8.  (메인 코드) 함수 호출 및 반환된 튜플을 4개의 변수로 언패킹
9.  (메인 코드) 각 변수 값을 출력

**정답 코드**
```python
# 파일명: list_statistics.py

# 1. 통계 계산 함수를 정의합니다.
def calculate_stats(numbers):
    """숫자 리스트의 합계, 평균, 최댓값, 최솟값을 튜플로 반환하는 함수"""
    
    # 2. 리스트가 비어있는 경우를 처리합니다.
    if not numbers:
        return (0, 0, 0, 0)
    
    # 3. 합계를 계산합니다.
    total = sum(numbers)
    # 4. 평균을 계산합니다.
    average = total / len(numbers)
    # 5. 최댓값과 최솟값을 찾습니다.
    maximum = max(numbers)
    minimum = min(numbers)
    
    # 6. 계산된 모든 값을 튜플로 묶어 반환합니다.
    return (total, average, maximum, minimum)

# --- 메인 실행 부분 ---
# 7. 테스트할 숫자 리스트를 생성합니다.
data = [10, 55, 23, 78, 42, 91, 5, 100]

# 8. 함수를 호출하고, 반환된 튜플의 각 요소를 개별 변수에 할당(언패킹)합니다.
total_val, avg_val, max_val, min_val = calculate_stats(data)

# 9. 결과를 출력합니다.
print(f"입력 리스트: {data}")
print(f"합계: {total_val}")
print(f"평균: {avg_val:.2f}") # 소수점 둘째 자리까지 출력
print(f"최댓값: {max_val}")
print(f"최솟값: {min_val}")

# 빈 리스트 테스트
empty_stats = calculate_stats([])
print(f"\n빈 리스트의 통계: {empty_stats}")
```

---

#### 문제 4: 가변 인수를 이용한 문자열 합치기 함수

**문제**
여러 개의 문자열을 가변 인수(`*args`)로 받아, 이 문자열들을 주어진 구분자(`sep`)로 연결하여 반환하는 함수 `join_strings(sep, *args)`를 작성하세요.

-   `join_strings("-", "hello", "world")` 호출 시 `"hello-world"` 반환
-   `join_strings(" ", "Python", "is", "fun")` 호출 시 `"Python is fun"` 반환

---

**풀이 과정 및 로직**
1.  `join_strings` 함수를 `sep`라는 일반 매개변수와 `*args`라는 가변 인수 매개변수를 받도록 정의합니다. `*args`는 함수에 전달된 나머지 위치 인수들을 하나의 튜플로 묶어줍니다.
2.  `string.join(iterable)` 메서드는 문자열로 구성된 리스트나 튜플을 받아 해당 문자열을 구분자로 사용하여 합쳐줍니다.
3.  `sep` 변수가 바로 이 구분자 역할을 하고, `args` 튜플이 `join` 메서드에 전달될 iterable 객체입니다.
4.  따라서 함수 본문은 `return sep.join(args)` 한 줄이면 충분합니다.
5.  함수 외부에서 다양한 인수 조합으로 함수를 호출하여 결과가 올바르게 나오는지 확인합니다.

**처리 순서**
1.  `join_strings(sep, *args)` 함수 정의
2.  (함수 내) `sep`를 구분자로 사용하여 `args` 튜플의 요소들을 `join()`
3.  (함수 내) 결합된 문자열 반환
4.  (메인 코드) 다양한 구분자와 문자열들로 함수를 호출
5.  (메인 코드) 반환된 결과 출력

**정답 코드**```python
# 파일명: join_with_args.py

# 1. 가변 인수를 받는 함수를 정의합니다.
def join_strings(sep, *args):
    """
    주어진 구분자(sep)로 여러 문자열(args)을 합쳐 반환하는 함수
    sep: 구분자 문자열
    *args: 합칠 문자열들 (가변 인수)
    """
    
    # 2, 3. 구분자(sep)의 join 메서드를 사용하여 args 튜플의 모든 요소를 합칩니다.
    return sep.join(args)

# --- 메인 실행 부분 ---
# 4, 5. 다양한 예시로 함수를 호출하고 결과를 출력합니다.
result1 = join_strings("-", "hello", "world")
print(f"결과 1: {result1}")

result2 = join_strings(" ", "Python", "is", "powerful", "and", "fun")
print(f"결과 2: {result2}")

result3 = join_strings(", ", "apple", "banana", "cherry")
print(f"결과 3: {result3}")

# 인수가 하나만 들어간 경우
result4 = join_strings("-", "single")
print(f"결과 4: {result4}")
```

---

#### 문제 5: 파일명과 확장자 분리 함수

**문제**
파일명 문자열을 인자로 받아, 파일명과 확장자를 분리하여 튜플 형태로 반환하는 함수 `split_filename(filename)`을 작성하세요.

-   `split_filename("report.docx")` 호출 시 `("report", "docx")` 반환
-   `split_filename("image.jpeg")` 호출 시 `("image", "jpeg")` 반환
-   확장자가 없는 경우, 확장자는 빈 문자열로 처리합니다. (예: `split_filename("myfile")` -> `("myfile", "")`)
-   파일명에 `.`이 여러 개 있는 경우, 마지막 `.`을 기준으로 분리합니다. (예: `split_filename("archive.tar.gz")` -> `("archive.tar", "gz")`)

---

**풀이 과정 및 로직**
1.  `split_filename` 함수를 `filename` 매개변수를 받도록 정의합니다.
2.  먼저 `.`이 `filename`에 포함되어 있는지 확인합니다.
3.  **`rfind('.')`** 메서드를 사용합니다. `rfind()`는 문자열의 **오른쪽에서부터** 문자를 찾아 그 인덱스를 반환합니다. 이를 통해 마지막 `.`의 위치를 찾을 수 있습니다. 만약 문자가 없으면 -1을 반환합니다.
4.  `rfind()`로 찾은 인덱스를 기준으로 슬라이싱(`:`)을 사용하여 파일명 부분과 확장자 부분을 나눕니다.
    -   파일명 부분: `filename[:index]`
    -   확장자 부분: `filename[index+1:]` (`.` 자체는 제외)
5.  만약 `.`이 아예 없다면(`rfind()` 결과가 -1), 파일명은 전체 문자열이고 확장자는 빈 문자열(`""`)이 됩니다.
6.  분리된 파일명과 확장자를 튜플로 묶어 반환합니다.

**처리 순서**
1.  `split_filename(filename)` 함수 정의
2.  (함수 내) `filename.rfind('.')`로 마지막 `.`의 인덱스 찾기
3.  (함수 내) `.`이 발견되었다면 (인덱스 > -1)
    -   인덱스를 기준으로 슬라이싱하여 `name`과 `ext` 추출
4.  (함수 내) `.`이 발견되지 않았다면
    -   `name`은 전체 문자열, `ext`는 빈 문자열로 설정
5.  (함수 내) `(name, ext)` 튜플 반환
6.  (메인 코드) 여러 종류의 파일명으로 함수를 테스트하고 결과 출력

**정답 코드**```python
# 파일명: split_filename.py

# 1. 파일명과 확장자 분리 함수를 정의합니다.
def split_filename(filename):
    """
    파일명을 받아 (파일명, 확장자) 튜플로 분리하여 반환하는 함수.
    마지막 '.'을 기준으로 분리한다.
    """
    
    # 2. 문자열의 오른쪽부터 '.'의 위치를 찾습니다.
    last_dot_index = filename.rfind('.')
    
    # 3. '.'이 존재하고, 문자열의 맨 앞이 아니라면 ('.bashrc' 같은 경우)
    if last_dot_index > 0:
        # 3-1. 인덱스를 기준으로 파일명과 확장자를 나눕니다.
        name = filename[:last_dot_index]
        ext = filename[last_dot_index+1:]
    else:
        # 4. '.'이 없는 경우
        name = filename
        ext = ""
        
    # 5. 결과를 튜플로 반환합니다.
    return (name, ext)

# --- 메인 실행 부분 ---
# 6. 다양한 케이스로 함수를 테스트합니다.
file1 = "my_report.docx"
file2 = "archive.tar.gz"
file3 = "config"
file4 = ".bash_profile" # 맨 앞에 점이 있는 경우

print(f"'{file1}' -> {split_filename(file1)}")
print(f"'{file2}' -> {split_filename(file2)}")
print(f"'{file3}' -> {split_filename(file3)}")
print(f"'{file4}' -> {split_filename(file4)}")
```

### 📘 Chapter 04: 자료구조 심화 문제

#### 문제 1: 올바른 괄호 검사기 (스택 활용)

**문제**
문자열에 포함된 괄호 `( )`, `[ ]`, `{ }`의 짝이 올바르게 맞는지 검사하는 함수 `check_brackets(statement)`를 작성하세요. 스택(Stack) 자료구조의 원리를 활용하여 풀어보세요.

-   올바른 예: `"({[]})", "a * (b + c)"`
-   틀린 예: `"(]", "{[}", "(()"`

---

**풀이 과정 및 로직**
1.  스택으로 사용할 빈 리스트 `stack`을 생성합니다.
2.  여는 괄호와 닫는 괄호의 짝을 쉽게 찾기 위해 딕셔너리 `bracket_pairs = {'}':'{', ']':'[', ')':'('}`를 만듭니다.
3.  입력된 문자열 `statement`를 처음부터 끝까지 한 글자씩 순회합니다.
4.  **여는 괄호 `(`, `[`, `{`를 만나면**: 스택에 `push` (리스트의 `append`) 합니다.
5.  **닫는 괄호 `)`, `]`, `}`를 만나면**:
    -   먼저 스택이 비어있는지 확인합니다. 만약 비어있다면, 짝이 맞는 여는 괄호가 없다는 뜻이므로 `False`를 반환합니다.
    -   스택이 비어있지 않다면, 스택에서 `pop` 하여 가장 최근에 들어온 여는 괄호를 꺼냅니다.
    -   꺼내온 여는 괄호가 현재 닫는 괄호의 짝과 맞는지 `bracket_pairs` 딕셔너리를 이용해 비교합니다. 맞지 않으면 `False`를 반환합니다.
6.  문자열 순회가 모두 끝난 후, 스택을 확인합니다.
    -   만약 스택이 비어있다면, 모든 괄호의 짝이 맞은 것이므로 `True`를 반환합니다.
    -   만약 스택에 여는 괄호가 남아있다면, 짝이 맞지 않는 괄호가 있다는 뜻이므로 `False`를 반환합니다.

**처리 순서**
1.  `check_brackets(statement)` 함수 정의
2.  (함수 내) 스택용 빈 리스트, 괄호 짝 딕셔너리 생성
3.  (함수 내) 문자열을 순회하는 `for` 루프 시작
4.  (함수 내) 현재 문자가 여는 괄호이면, 스택에 `append`
5.  (함수 내) 현재 문자가 닫는 괄호이면,
    -   스택이 비었거나, `pop`한 괄호가 짝이 안 맞으면 `False` 반환
6.  (함수 내) 루프 종료 후, 스택이 비어있으면 `True`, 아니면 `False` 반환
7.  (메인 코드) 여러 예시로 함수를 테스트하고 결과 출력

**정답 코드**
```python
# 파일명: bracket_checker.py

def check_brackets(statement):
    """스택을 이용하여 괄호의 짝이 올바른지 검사하는 함수"""
    # 1. 스택으로 사용할 빈 리스트를 생성합니다.
    stack = []
    # 2. 괄호의 짝을 정의합니다. (닫는 괄호를 key로)
    bracket_pairs = {')': '(', ']': '[', '}': '{'}
    
    # 3. 입력된 문자열을 한 글자씩 순회합니다.
    for char in statement:
        # 4. 여는 괄호일 경우, 스택에 추가합니다.
        if char in "({[":
            stack.append(char)
        # 5. 닫는 괄호일 경우
        elif char in ")}]":
            # 스택이 비어있으면 짝이 맞는 여는 괄호가 없는 것이므로 False
            if not stack:
                return False
            
            # 스택에서 가장 위의 괄호를 꺼냅니다.
            last_open_bracket = stack.pop()
            
            # 꺼낸 괄호가 현재 닫는 괄호의 짝과 맞는지 확인합니다.
            if bracket_pairs[char] != last_open_bracket:
                return False
                
    # 6. 문자열 순회가 끝난 후, 스택이 비어있어야 모든 짝이 맞은 것입니다.
    return len(stack) == 0

# --- 메인 실행 부분 ---
# 7. 다양한 예시로 함수를 테스트합니다.
print(f"'({{[[]]}})'는 올바른가? {check_brackets('({{[[]]}})')}")
print(f"'a * (b + [c / d])'는 올바른가? {check_brackets('a * (b + [c / d])')}")
print(f"'([)]'는 올바른가? {check_brackets('([)]')}")
print(f"'(()'는 올바른가? {check_brackets('(()')}")
print(f"']]]'는 올바른가? {check_brackets(']]]')}")
```

---

#### 문제 2: 연락처 관리 프로그램 (딕셔너리 활용)

**문제**
이름을 키(key)로, 전화번호를 값(value)으로 사용하는 연락처(dictionary)를 관리하는 프로그램을 작성하세요. 프로그램은 "추가", "검색", "삭제", "전체 보기", "종료" 기능을 제공해야 합니다.

---

**풀이 과정 및 로직**
1.  연락처를 저장할 빈 딕셔너리 `contacts`를 생성합니다.
2.  `while True` 무한 루프를 사용하여 프로그램이 계속 실행되도록 합니다.
3.  사용자에게 원하는 기능("추가", "검색" 등)을 입력받습니다.
4.  `if-elif-else`를 사용하여 입력된 기능에 따라 분기합니다.
    -   **추가**: 이름과 전화번호를 입력받아 `contacts[name] = phone_number` 형태로 딕셔너리에 추가합니다.
    -   **검색**: 검색할 이름을 입력받습니다.
        -   `in` 연산자로 해당 이름이 `contacts` 딕셔너리의 키에 있는지 확인합니다.
        -   있으면 `contacts[name]`으로 전화번호를 찾아 출력하고, 없으면 "연락처를 찾을 수 없습니다."라고 출력합니다.
    -   **삭제**: 삭제할 이름을 입력받습니다.
        -   해당 이름이 키에 있는지 확인 후, `del contacts[name]`으로 해당 키-값 쌍을 삭제합니다.
    -   **전체 보기**: `for` 루프와 `.items()` 메서드를 사용하여 `contacts` 딕셔너리의 모든 이름과 전화번호를 출력합니다.
    -   **종료**: `break`를 사용하여 `while` 루프를 탈출합니다.

**처리 순서**
1.  빈 딕셔너리 `contacts` 생성
2.  `while` 루프 시작
3.  기능 메뉴 출력 및 사용자 입력 받기
4.  `if-elif-else`로 기능 분기
5.  (추가) 이름, 번호 입력받아 딕셔너리에 저장
6.  (검색) 이름 입력받아, 키 존재 여부 확인 후 값 출력
7.  (삭제) 이름 입력받아, 키 존재 여부 확인 후 `del`로 삭제
8.  (전체 보기) `.items()`로 루프 돌며 모든 연락처 출력
9.  (종료) `break`로 프로그램 종료

**정답 코드**```python
# 파일명: contact_manager.py

def run_contact_manager():
    """딕셔너리를 이용한 연락처 관리 프로그램을 실행하는 함수"""
    # 1. 연락처를 저장할 딕셔너리를 생성합니다.
    contacts = {}
    print("--- 연락처 관리 프로그램 ---")

    # 2. 사용자가 '종료'를 입력할 때까지 반복합니다.
    while True:
        # 3. 기능 메뉴를 보여줍니다.
        command = input("\n기능을 선택하세요 (추가, 검색, 삭제, 전체 보기, 종료): ")

        # 4. 입력된 명령어에 따라 기능을 분기합니다.
        if command == "추가":
            # 5. 연락처 추가
            name = input("이름: ")
            phone = input("전화번호: ")
            contacts[name] = phone
            print(f"'{name}'님의 연락처가 저장되었습니다.")
        
        elif command == "검색":
            # 6. 연락처 검색
            name = input("검색할 이름: ")
            if name in contacts:
                print(f"'{name}'님의 전화번호는 {contacts[name]} 입니다.")
            else:
                print(f"'{name}'님의 연락처를 찾을 수 없습니다.")

        elif command == "삭제":
            # 7. 연락처 삭제
            name = input("삭제할 이름: ")
            if name in contacts:
                del contacts[name]
                print(f"'{name}'님의 연락처가 삭제되었습니다.")
            else:
                print(f"'{name}'님의 연락처를 찾을 수 없습니다.")

        elif command == "전체 보기":
            # 8. 전체 연락처 보기
            print("\n--- 전체 연락처 목록 ---")
            if not contacts:
                print("저장된 연락처가 없습니다.")
            else:
                for name, phone in contacts.items():
                    print(f"- {name}: {phone}")
        
        elif command == "종료":
            # 9. 프로그램 종료
            print("프로그램을 종료합니다.")
            break
        
        else:
            print("잘못된 명령어입니다. 다시 입력해주세요.")

# 프로그램 실행
run_contact_manager()```

---

#### 문제 3: 로또 번호 생성기 (세트 활용)

**문제**
1부터 45까지의 숫자 중에서 중복되지 않는 6개의 숫자를 뽑아 로또 번호를 생성하는 프로그램을 작성하세요. 세트(Set) 자료구조의 '중복을 허용하지 않는' 특징을 활용하여 풀어보세요.

---

**풀이 과정 및 로직**
1.  `random` 모듈의 `randint(1, 45)` 함수를 사용해야 하므로, 먼저 `import random`을 합니다.
2.  생성된 로또 번호를 저장할 빈 세트 `lotto_numbers = set()`를 생성합니다.
3.  `while` 루프를 사용하여 세트의 크기(`len(lotto_numbers)`)가 6이 될 때까지 반복합니다.
4.  루프 안에서 `random.randint(1, 45)`로 1부터 45 사이의 난수를 생성합니다.
5.  생성된 난수를 세트에 `.add()` 합니다. 만약 이미 세트 안에 있는 숫자라면, 세트의 특성상 아무 변화도 일어나지 않고 중복 추가되지 않습니다. 세트의 크기도 변하지 않습니다.
6.  `while` 루프가 종료되면, 세트에는 중복되지 않는 6개의 숫자가 담겨 있습니다.
7.  결과를 보기 좋게 정렬하기 위해, 세트를 리스트로 변환(`list()`)한 후 `.sort()` 메서드로 정렬합니다.
8.  최종적으로 정렬된 로또 번호를 출력합니다.

**처리 순서**
1.  `random` 모듈 import
2.  빈 세트 `lotto_numbers` 생성
3.  `while` 루프 시작 (조건: 세트의 길이가 6보다 작은 동안)
4.  1~45 사이의 난수 생성
5.  생성된 난수를 세트에 `add`
6.  `while` 루프 종료
7.  결과 세트를 리스트로 변환
8.  리스트를 오름차순으로 정렬
9.  최종 로또 번호 출력

**정답 코드**
```python
# 파일명: lotto_generator.py

# 1. random 모듈을 가져옵니다.
import random

def generate_lotto():
    """세트를 이용하여 중복되지 않는 로또 번호 6개를 생성하는 함수"""
    # 2. 로또 번호를 저장할 빈 세트를 생성합니다.
    lotto_numbers = set()
    
    # 3. 세트의 요소 개수가 6개가 될 때까지 반복합니다.
    while len(lotto_numbers) < 6:
        # 4. 1부터 45까지의 임의의 숫자를 생성합니다.
        number = random.randint(1, 45)
        # 5. 세트에 숫자를 추가합니다. (중복된 숫자는 자동으로 무시됨)
        lotto_numbers.add(number)
        
    # 7. 결과를 정렬하기 위해 세트를 리스트로 변환합니다.
    sorted_lotto = sorted(list(lotto_numbers))
    
    return sorted_lotto

# --- 메인 실행 부분 ---
print("--- 로또 번호 생성기 ---")
# 9. 함수를 호출하여 생성된 로또 번호를 출력합니다.
lotto_result = generate_lotto()
print(f"생성된 로또 번호는 {lotto_result} 입니다.")
```

---

#### 문제 4: 문자열에 가장 많이 나타나는 알파벳 찾기 (`collections.Counter` 활용)

**문제**
영어 문장을 입력받아, 그 문장에서 가장 많이 사용된 알파벳과 그 횟수를 출력하는 프로그램을 작성하세요. `collections` 모듈의 `Counter`를 사용하면 매우 쉽게 해결할 수 있습니다. (대소문자는 구분하지 않으며, 공백이나 특수문자는 세지 않습니다.)

---

**풀이 과정 및 로직**
1.  `collections` 모듈에서 `Counter`를 `import` 합니다.
2.  사용자로부터 영어 문장을 입력받습니다.
3.  입력받은 문장을 `.lower()` 메서드로 모두 소문자로 변환하여 대소문자 구분을 없앱니다.
4.  알파벳만 골라내기 위해, 빈 리스트 `alphabets`를 만들고, 소문자로 변환된 문장을 순회하며 `char.isalpha()`가 `True`인 문자만 `alphabets` 리스트에 추가합니다.
5.  `Counter(alphabets)`를 실행하여 리스트에 있는 각 알파벳의 빈도를 계산한 `Counter` 객체를 생성합니다.
6.  `Counter` 객체의 `.most_common(1)` 메서드를 호출합니다. 이 메서드는 가장 빈번하게 나타나는 요소와 그 횟수를 `[(요소, 횟수)]` 형태의 리스트로 반환합니다. `(1)`을 인자로 주면 가장 빈번한 1개만 가져옵니다.
7.  결과 리스트의 첫 번째 요소 `[0]`를 가져와 언패킹하여 가장 많이 나온 알파벳과 횟수를 변수에 저장하고 출력합니다.

**처리 순서**
1.  `from collections import Counter`
2.  사용자에게 문장 입력받기
3.  문장을 모두 소문자로 변환
4.  문자열을 순회하며 알파벳인 문자만 추출하여 새로운 리스트 생성
5.  `Counter`를 이용해 알파벳 리스트의 빈도수 계산
6.  `.most_common(1)`로 가장 빈번한 알파벳과 횟수 찾기
7.  결과 출력

**정답 코드**
```python
# 파일명: most_common_char.py

# 1. collections 모듈에서 Counter 클래스를 가져옵니다.
from collections import Counter

# 2. 사용자로부터 영어 문장을 입력받습니다.
sentence = input("영어 문장을 입력하세요: ")

# 3. 모든 문자를 소문자로 변환하여 대소문자 구분을 없앱니다.
lower_sentence = sentence.lower()

# 4. 문자열을 순회하며 알파벳인 문자만 추출하여 리스트에 담습니다.
alphabets = []
for char in lower_sentence:
    if char.isalpha(): # isalpha()는 해당 문자가 알파벳인지 확인합니다.
        alphabets.append(char)

# 5. Counter를 사용하여 각 알파벳의 빈도를 계산합니다.
char_counts = Counter(alphabets)

# 6. 가장 많이 등장한 알파벳과 횟수를 찾습니다.
# most_common(1)은 [('가장흔한문자', 횟수)] 형태의 리스트를 반환합니다.
if char_counts: # 문장이 비어있지 않을 경우
    most_common_char, count = char_counts.most_common(1)[0]
    
    # 7. 결과를 출력합니다.
    print(f"가장 많이 사용된 알파벳은 '{most_common_char}'이며, {count}번 사용되었습니다.")
else:
    print("입력된 문장에 알파벳이 없습니다.")
```

---

#### 문제 5: 놀이공원 대기줄 시뮬레이션 (`collections.deque` 활용)

**문제**
놀이공원의 대기줄을 `collections.deque`를 사용하여 시뮬레이션하는 프로그램을 작성하세요. "대기", "탑승", "현황", "종료" 명령어를 처리해야 합니다.
-   **대기**: 대기할 사람의 이름을 입력받아 대기줄(큐)의 맨 뒤에 추가합니다. (Enqueue)
-   **탑승**: 대기줄의 맨 앞에 있는 사람이 놀이기구에 탑승(제거)합니다. (Dequeue)
-   **현황**: 현재 대기줄에 있는 모든 사람을 순서대로 출력합니다.

---

**풀이 과정 및 로직**
1.  `collections` 모듈에서 `deque`를 `import` 합니다.
2.  `deque()`를 호출하여 대기줄로 사용할 빈 `deque` 객체 `waiting_line`을 생성합니다.
3.  `while True` 루프를 사용하여 프로그램을 계속 실행합니다.
4.  사용자에게 명령어("대기", "탑승" 등)를 입력받습니다.
5.  `if-elif-else`로 명령어에 따라 분기합니다.
    -   **대기**: 사람 이름을 입력받아 `waiting_line.append(name)`으로 큐의 오른쪽에 추가합니다.
    -   **탑승**: 먼저 `if waiting_line:`으로 대기줄이 비어있는지 확인합니다.
        -   비어있지 않으면 `waiting_line.popleft()`로 큐의 왼쪽(맨 앞)에서 사람을 제거하고, 탑승 메시지를 출력합니다.
        -   비어있으면 "대기 중인 사람이 없습니다."라고 출력합니다.
    -   **현황**: 대기줄이 비어있는지 확인 후, 비어있으면 메시지를 출력하고, 아니면 `for` 루프로 `waiting_line`을 순회하며 현재 대기자 목록을 출력합니다.
    -   **종료**: `break`로 루프를 종료합니다.

**처리 순서**
1.  `from collections import deque`
2.  빈 `deque` 객체 `waiting_line` 생성
3.  `while` 루프 시작
4.  명령어 입력받기
5.  `if-elif-else`로 기능 분기
6.  (대기) 이름 입력받아 `append()`
7.  (탑승) 대기줄 확인 후, 비어있지 않으면 `popleft()`
8.  (현황) 대기줄 확인 후, `for` 루프로 전체 출력
9.  (종료) `break`

**정답 코드**
```python
# 파일명: amusement_park_queue.py

# 1. collections 모듈에서 deque를 가져옵니다.
from collections import deque

def simulate_queue():
    """deque를 이용하여 놀이공원 대기줄을 시뮬레이션하는 함수"""
    # 2. 대기줄로 사용할 deque 객체를 생성합니다.
    waiting_line = deque()
    print("--- 놀이공원 대기줄 시뮬레이터 ---")
    
    # 3. '종료' 명령이 나올 때까지 반복합니다.
    while True:
        # 4. 사용자로부터 명령어를 입력받습니다.
        command = input("\n명령어를 입력하세요 (대기, 탑승, 현황, 종료): ")
        
        # 5. 명령어에 따라 기능을 분기합니다.
        if command == "대기":
            # 6. 대기줄에 사람 추가 (Enqueue)
            name = input("대기할 사람의 이름: ")
            waiting_line.append(name)
            print(f"'{name}'님이 대기줄에 추가되었습니다.")
            
        elif command == "탑승":
            # 7. 대기줄에서 사람 탑승 (Dequeue)
            if waiting_line: # 대기줄이 비어있지 않다면
                person = waiting_line.popleft()
                print(f"'{person}'님이 놀이기구에 탑승했습니다.")
            else:
                print("대기 중인 사람이 없습니다.")
                
        elif command == "현황":
            # 8. 현재 대기줄 현황 출력
            print("\n--- 현재 대기줄 ---")
            if waiting_line:
                for i, person in enumerate(waiting_line, 1):
                    print(f"{i}. {person}")
            else:
                print("대기 중인 사람이 없습니다.")
                
        elif command == "종료":
            # 9. 시뮬레이션 종료
            print("시뮬레이션을 종료합니다.")
            break
            
        else:
            print("잘못된 명령어입니다.")

# 시뮬레이션 함수 실행
simulate_queue()
```

### 📘 Chapter 05: 파이썬 스타일 코딩 심화 문제

#### 문제 1: 파일 확장자별로 그룹핑하기

**문제**
`['file1.py', 'doc1.docx', 'image1.jpg', 'script2.py', 'photo2.jpg']` 와 같은 파일명 리스트가 주어졌을 때, 리스트 컴프리헨션(List Comprehension)을 사용하여 확장자별로 파일명을 그룹핑한 딕셔너리를 생성하세요.

-   **결과 예시**: `{'py': ['file1.py', 'script2.py'], 'docx': ['doc1.docx'], 'jpg': ['image1.jpg', 'photo2.jpg']}`

---

**풀이 과정 및 로직**
1.  먼저 파일명 리스트에서 모든 확장자를 중복 없이 추출해야 합니다.
    -   리스트 컴프리헨션과 `split('.')`을 사용하여 `[f.split('.')[-1] for f in filenames]`와 같이 확장자 리스트를 만듭니다.
    -   이 리스트를 `set()`으로 변환하여 중복을 제거합니다.
2.  이제 중복 없는 확장자 목록(set)을 순회하며 딕셔너리를 만듭니다.
3.  딕셔너리 컴프리헨션을 사용합니다. `{key_expression: value_expression for item in iterable}`
    -   `key_expression`은 각 확장자(`ext`)가 됩니다.
    -   `value_expression`은 다시 리스트 컴프리헨션을 사용하여, 전체 파일명 리스트를 순회하며 현재 확장자(`ext`)로 끝나는(`endswith()`) 파일명만 모은 리스트가 됩니다.
4.  이 두 단계를 결합하여 하나의 딕셔너리 컴프리헨션으로 완성합니다.

**처리 순서**
1.  입력 파일명 리스트 정의
2.  리스트에 있는 모든 확장자를 중복 없이 추출 (Set 활용)
3.  딕셔너리 컴프리헨션 시작
4.  (Key) 중복 없는 확장자 set을 순회하며 각 확장자를 키로 사용
5.  (Value) 내부 리스트 컴프리헨션을 사용하여, 현재 키(확장자)와 일치하는 파일명들로 리스트를 생성
6.  완성된 딕셔너리 출력

**정답 코드**
```python
# 파일명: group_by_extension.py

# 1. 파일명 리스트를 정의합니다.
filenames = ['file1.py', 'doc1.docx', 'image1.jpg', 'script2.py', 'photo2.jpg', 'archive.tar.gz', 'main.py']

# 2. 리스트 컴프리헨션으로 모든 확장자를 추출한 후 set으로 중복을 제거합니다.
extensions = {f.split('.')[-1] for f in filenames if '.' in f}

# 3. 딕셔너리 컴프리헨션을 사용하여 확장자별로 그룹핑합니다.
# 4. (Key) extensions를 순회하며 ext를 키로 사용합니다.
# 5. (Value) 전체 filenames 리스트를 다시 순회하며, 파일명이 해당 ext로 끝나는 경우만 모아 리스트를 만듭니다.
grouped_files = {ext: [f for f in filenames if f.endswith('.' + ext)] for ext in extensions}

# 6. 결과를 출력합니다.
import pprint # 딕셔너리를 예쁘게 출력하기 위해 import
pprint.pprint(grouped_files)
```

---

#### 문제 2: 학생 점수 정렬하기 (람다 함수 활용)

**문제**
학생들의 이름, 국어 점수, 영어 점수가 튜플로 묶인 리스트 `students = [('홍길동', 90, 85), ('이순신', 100, 95), ('강감찬', 80, 90)]`가 있습니다. `sorted()` 함수와 `lambda` 함수를 사용하여 다음 조건에 따라 학생 리스트를 정렬하세요.

1.  **국어 점수**가 높은 순서(내림차순)로 정렬하여 출력하세요.
2.  **영어 점수**가 높은 순서(내림차순)로 정렬하여 출력하세요.
3.  **국어와 영어 점수의 합**이 높은 순서(내림차순)로 정렬하여 출력하세요.

---

**풀이 과정 및 로직**
1.  `sorted(iterable, key=lambda ..., reverse=True)` 함수의 구조를 활용합니다. `reverse=True`는 내림차순 정렬을 의미합니다.
2.  **국어 점수 기준 정렬**:
    -   `key` 인자에 `lambda` 함수를 전달합니다.
    -   람다 함수는 리스트의 각 요소(튜플)를 `x`로 받습니다.
    -   국어 점수는 튜플의 인덱스 1에 있으므로, `lambda x: x[1]`을 `key`로 사용합니다.
3.  **영어 점수 기준 정렬**:
    -   마찬가지로 `lambda` 함수를 사용합니다.
    -   영어 점수는 인덱스 2에 있으므로, `lambda x: x[2]`를 `key`로 사용합니다.
4.  **점수 합계 기준 정렬**:
    -   `lambda` 함수 안에서 간단한 계산을 수행할 수 있습니다.
    -   국어 점수(`x[1]`)와 영어 점수(`x[2]`)의 합 `x[1] + x[2]`를 반환하는 `lambda x: x[1] + x[2]`를 `key`로 사용합니다.

**처리 순서**
1.  학생 데이터 리스트 정의
2.  (국어 점수) `sorted()` 함수에 `key=lambda x: x[1]`, `reverse=True`를 적용하여 정렬 및 출력
3.  (영어 점수) `sorted()` 함수에 `key=lambda x: x[2]`, `reverse=True`를 적용하여 정렬 및 출력
4.  (합계 점수) `sorted()` 함수에 `key=lambda x: x[1] + x[2]`, `reverse=True`를 적용하여 정렬 및 출력

**정답 코드**
```python
# 파일명: sort_students_lambda.py

# 1. 학생 데이터 리스트를 정의합니다. (이름, 국어, 영어)
students = [('홍길동', 90, 85), ('이순신', 100, 95), ('강감찬', 80, 90)]
print(f"원본 데이터: {students}\n")

# 2. 국어 점수(인덱스 1) 기준으로 내림차순 정렬
sorted_by_korean = sorted(students, key=lambda student: student[1], reverse=True)
print("--- 국어 점수 높은 순 ---")
print(sorted_by_korean)

# 3. 영어 점수(인덱스 2) 기준으로 내림차순 정렬
sorted_by_english = sorted(students, key=lambda student: student[2], reverse=True)
print("\n--- 영어 점수 높은 순 ---")
print(sorted_by_english)

# 4. 국어, 영어 점수의 합계 기준으로 내림차순 정렬
sorted_by_sum = sorted(students, key=lambda student: student[1] + student[2], reverse=True)
print("\n--- 총점 높은 순 ---")
print(sorted_by_sum)
```

---

#### 문제 3: 매트릭스(2차원 리스트) 행과 열 바꾸기 (zip, *)

**문제**
다음과 같은 3x4 매트릭스(2차원 리스트)가 있습니다.
`matrix = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]`
`zip()` 함수와 별표(`*`) 언패킹을 사용하여 이 매트릭스의 행과 열을 바꾼 4x3 매트릭스를 만드세요.

---

**풀이 과정 및 로직**
1.  별표(`*`) 연산자는 리스트나 튜플 같은 컨테이너의 내용물을 '풀어헤치는(unpacking)' 역할을 합니다.
2.  `*matrix`를 실행하면, `[[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]]`는 `[1, 2, 3, 4]`, `[5, 6, 7, 8]`, `[9, 10, 11, 12]` 세 개의 개별 리스트로 풀립니다.
3.  `zip()` 함수는 여러 개의 iterable 객체를 받아, 같은 인덱스에 있는 요소들을 튜플로 묶어줍니다.
4.  `zip(*matrix)`는 `zip([1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12])`와 동일하게 동작합니다.
    -   첫 번째 묶음: 각 리스트의 0번째 인덱스인 `1, 5, 9`가 `(1, 5, 9)` 튜플로 묶입니다.
    -   두 번째 묶음: 각 리스트의 1번째 인덱스인 `2, 6, 10`이 `(2, 6, 10)` 튜플로 묶입니다.
    -   이 과정이 마지막 인덱스까지 반복됩니다.
5.  `zip()`의 결과는 zip 객체이므로, `list()`로 감싸주어 리스트 형태로 변환합니다. 최종 결과가 튜플이 아닌 리스트로 구성되길 원한다면, 리스트 컴프리헨션 `[list(row) for row in zip(*matrix)]`를 사용합니다.

**처리 순서**
1.  원본 매트릭스(2차원 리스트) 정의
2.  `*`를 사용하여 매트릭스를 개별 행 리스트로 언패킹
3.  `zip()` 함수에 언패킹된 리스트들을 인자로 전달
4.  `zip()`의 결과를 `list()`로 변환하여 최종 결과 생성
5.  결과 출력

**정답 코드**
```python
# 파일명: transpose_matrix.py

# 1. 3x4 매트릭스를 정의합니다.
matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
]
print("--- 원본 매트릭스 ---")
for row in matrix:
    print(row)

# 2, 3, 4. zip과 *를 사용하여 행과 열을 바꿉니다.
# *matrix는 [1,2,3,4], [5,6,7,8], [9,10,11,12] 세 개의 리스트로 분리됩니다.
# zip은 이 세 리스트의 각 인덱스별 요소를 묶어줍니다.
transposed_matrix_tuples = list(zip(*matrix))

# 결과가 튜플이 아닌 리스트로 구성되길 원한다면 리스트 컴프리헨션을 사용합니다.
transposed_matrix_lists = [list(row) for row in zip(*matrix)]

# 5. 결과를 출력합니다.
print("\n--- 행/열 변환 결과 (튜플 리스트) ---")
print(transposed_matrix_tuples)

print("\n--- 행/열 변환 결과 (리스트의 리스트) ---")
for row in transposed_matrix_lists:
    print(row)
```

---

#### 문제 4: 조건부 할인 가격 계산하기

**문제**
상품 가격 리스트 `prices = [1000, 5000, 800, 12000, 3500]`가 있습니다. 리스트 컴프리헨션과 `if-else` 표현식을 사용하여, 10000원 이상인 상품은 20% 할인, 5000원 이상 10000원 미만인 상품은 10% 할인, 그 외 상품은 할인을 적용하지 않은 최종 가격 리스트를 생성하세요.

---

**풀이 과정 및 로직**
1.  리스트 컴프리헨션의 기본 구조 `[표현식 for 항목 in 리스트]`를 사용합니다.
2.  `표현식` 부분에 삼항 연산자(ternary operator)와 유사한 `A if 조건 else B` 구조를 중첩하여 사용합니다.
3.  **가장 먼저 검사할 조건**: `price >= 10000`
    -   참일 경우: `price * 0.8` (20% 할인)
4.  **거짓일 경우(else)**: 다시 `if-else` 표현식이 들어갑니다.
    -   **두 번째 검사할 조건**: `price >= 5000`
    -   참일 경우: `price * 0.9` (10% 할인)
    -   거짓일 경우: `price` (할인 없음)
5.  이 로직을 하나의 리스트 컴프리헨션 라인으로 합칩니다. `[price * 0.8 if price >= 10000 else (price * 0.9 if price >= 5000 else price) for price in prices]`
6.  결과가 실수(float)로 나올 수 있으므로, `int()`를 사용하여 정수로 변환해 줄 수 있습니다.

**처리 순서**
1.  원본 가격 리스트 정의
2.  리스트 컴프리헨션 시작 (`for price in prices`)
3.  (표현식 부분) `if price >= 10000` 조건으로 20% 할인가 계산
4.  (표현식 부분) `else` 뒤에 중첩 `if price >= 5000` 조건으로 10% 할인가 계산
5.  (표현식 부분) 두 번째 `else` 뒤에 할인 없는 원가 사용
6.  계산된 가격들로 새로운 리스트 생성 및 출력

**정답 코드**
```python
# 파일명: conditional_discount.py

# 1. 상품 가격 리스트를 정의합니다.
prices = [1000, 5000, 800, 12000, 3500, 25000]
print(f"원본 가격: {prices}")

# 2-6. 중첩된 if-else 표현식을 포함한 리스트 컴프리헨션으로 최종 가격 리스트를 생성합니다.
final_prices = [
    int(price * 0.8) if price >= 10000  # 10000원 이상이면 20% 할인
    else int(price * 0.9) if price >= 5000 # 5000원 이상이면 10% 할인
    else price # 그 외에는 할인 없음
    for price in prices
]

print(f"할인 적용 후 가격: {final_prices}")
```

---

#### 문제 5: 알파벳 쌍 만들기

**문제**
알파벳 대문자(`'ABC'`)와 소문자(`'abc'`) 문자열이 있습니다. 리스트 컴프리헨션을 사용하여, 대문자와 소문자가 서로 다른 경우에만 모든 조합의 쌍을 리스트로 만드세요. (예: `('A', 'a')`, `('B', 'b')` 같은 쌍은 제외)

---

**풀이 과정 및 로직**
1.  중첩 `for`문이 포함된 리스트 컴프리헨션을 사용합니다. `[(대문자, 소문자) for 대문자 in ... for 소문자 in ...]`
2.  리스트 컴프리헨션의 마지막에 `if` 필터링 조건을 추가합니다.
3.  필터링 조건은 '대문자와 소문자가 서로 다른 경우'입니다.
4.  대문자를 소문자로 바꾸거나(`upper.lower()`) 소문자를 대문자로 바꿔서(`lower.upper()`) 두 문자가 같은지 비교하면 됩니다.
5.  예를 들어, `upper.lower() != lower` 조건은 `A`와 `a`일 때 `False`가 되고, `A`와 `b`일 때는 `True`가 됩니다.
6.  이 조건을 만족하는 `(upper, lower)` 튜플 쌍만 최종 리스트에 포함시킵니다.

**처리 순서**
1.  대문자, 소문자 문자열 정의
2.  리스트 컴프리헨션 시작
3.  (for) 바깥쪽 `for`문으로 대문자 문자열 순회
4.  (for) 안쪽 `for`문으로 소문자 문자열 순회
5.  (if) `upper.lower() != lower` 필터링 조건 추가
6.  (표현식) `(upper, lower)` 튜플 생성
7.  생성된 리스트 출력

**정답 코드**
```python
# 파일명: alphabet_pairs.py

# 1. 대문자와 소문자 문자열을 정의합니다.
uppercase_chars = 'ABC'
lowercase_chars = 'abc'

# 2-6. 중첩 for문과 if 필터가 포함된 리스트 컴프리헨션을 사용합니다.
# 대문자를 소문자로 바꾼 것과 소문자가 다를 경우에만 쌍을 만듭니다.
# 즉, 'A'와 'a', 'B'와 'b' 같은 쌍은 제외됩니다.
pairs = [
    (upper, lower) 
    for upper in uppercase_chars 
    for lower in lowercase_chars 
    if upper.lower() != lower
]

# 7. 결과를 출력합니다.
print(f"생성된 알파벳 쌍: {pairs}")
# 결과: [('A', 'b'), ('A', 'c'), ('B', 'a'), ('B', 'c'), ('C', 'a'), ('C', 'b')]
```
### 📘 Chapter 06: 객체 지향 프로그래밍 심화 문제

#### 문제 1: 은행 계좌 클래스 만들기

**문제**
`BankAccount` 클래스를 작성하세요. 이 클래스는 다음과 같은 특징을 가집니다.

1.  **속성**:
    -   `account_holder` (예금주 이름)
    -   `account_number` (계좌 번호, 생성 시 자동으로 부여)
    -   `__balance` (잔액, 외부에서 직접 접근할 수 없는 private 변수)
2.  **메서드**:
    -   `__init__(self, holder_name, initial_balance=0)`: 예금주 이름과 초기 잔액으로 객체를 생성합니다. 계좌 번호는 `1000-` 뒤에 4자리 난수를 붙여 생성합니다.
    -   `deposit(self, amount)`: 입금 기능. 입금액은 0보다 커야 합니다.
    -   `withdraw(self, amount)`: 출금 기능. 출금액은 0보다 커야 하며, 잔액보다 많을 수 없습니다.
    -   `get_balance(self)`: 현재 잔액을 조회하는 기능 (private 변수인 `__balance`에 안전하게 접근).
    -   `__str__(self)`: 계좌 정보를 "계좌번호: [...], 예금주: [...], 잔액: [...]원" 형태로 출력하는 기능.

---

**풀이 과정 및 로직**
1.  `random` 모듈을 `import`하여 계좌번호 생성에 사용합니다.
2.  `BankAccount` 클래스를 정의하고, `__init__` 메서드에서 예금주, 초기 잔액, 계좌번호를 초기화합니다. 잔액은 `__balance`로, 계좌번호는 `f"1000-{random.randint(1000, 9999)}"` 와 같이 생성합니다.
3.  `deposit` 메서드에서는 `amount`가 0보다 큰지 확인하고, `__balance`에 더해줍니다.
4.  `withdraw` 메서드에서는 `amount`가 0보다 크고 `__balance`보다 작거나 같은지 확인하고, `__balance`에서 빼줍니다. 조건에 맞지 않으면 오류 메시지를 출력합니다.
5.  `get_balance` 메서드는 단순히 `self.__balance`를 반환하여 외부에서 잔액을 읽을 수 있는 통로(getter)를 제공합니다.
6.  `__str__` 메서드는 f-string을 사용하여 정해진 형식의 문자열을 반환합니다.

**처리 순서**
1.  `random` 모듈 import
2.  `BankAccount` 클래스 정의
3.  `__init__`: `account_holder`, `__balance`, `account_number` 속성 초기화
4.  `deposit`: 금액 유효성 검사 후 잔액 증가
5.  `withdraw`: 금액 및 잔액 유효성 검사 후 잔액 감소
6.  `get_balance`: `__balance` 값 반환
7.  `__str__`: 정해진 포맷으로 계좌 정보 문자열 반환
8.  (테스트) 계좌 객체 생성, 입금/출금 테스트, `print()`로 정보 출력

**정답 코드**
```python
# 파일명: bank_account.py

# 1. 계좌번호 생성을 위해 random 모듈을 가져옵니다.
import random

# 2. BankAccount 클래스를 정의합니다.
class BankAccount:
    # 3. 생성자 메서드: 객체 초기화
    def __init__(self, holder_name, initial_balance=0):
        self.account_holder = holder_name
        self.account_number = f"1000-{random.randint(1000, 9999)}"
        # 잔액은 외부에서 직접 수정하지 못하도록 private 변수로 선언
        self.__balance = initial_balance
        print(f"{self.account_holder}님 계좌 개설 완료. (계좌번호: {self.account_number})")

    # 4. 입금 메서드
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            print(f"{amount}원 입금 완료. 현재 잔액: {self.__balance}원")
        else:
            print("입금액은 0보다 커야 합니다.")

    # 5. 출금 메서드
    def withdraw(self, amount):
        if amount <= 0:
            print("출금액은 0보다 커야 합니다.")
        elif amount > self.__balance:
            print(f"잔액 부족. (현재 잔액: {self.__balance}원)")
        else:
            self.__balance -= amount
            print(f"{amount}원 출금 완료. 현재 잔액: {self.__balance}원")

    # 6. 잔액 조회 메서드 (Getter)
    def get_balance(self):
        return self.__balance

    # 7. 객체를 출력할 때 호출될 메서드
    def __str__(self):
        return f"계좌번호: {self.account_number}, 예금주: {self.account_holder}, 잔액: {self.__balance}원"


# --- 메인 실행 부분 ---
# 8. 객체를 생성하고 테스트합니다.
my_account = BankAccount("홍길동", 10000)
print(my_account)

my_account.deposit(5000)
my_account.withdraw(3000)
my_account.withdraw(15000) # 잔액 부족 테스트
my_account.deposit(-1000)   # 잘못된 입금액 테스트

print(f"\n최종 계좌 정보: {my_account}")
# print(my_account.__balance) # AttributeError: 외부에서 직접 접근 불가
print(f"get_balance()를 통한 잔액 조회: {my_account.get_balance()}원")
```

---

#### 문제 2: 상속을 이용한 도형 넓이 계산기

**문제**
`Shape`라는 부모 클래스와, 이를 상속받는 `Rectangle`(직사각형), `Circle`(원) 자식 클래스를 만드세요.

1.  `Shape` 클래스는 `get_area()` 메서드를 가지며, 호출 시 `NotImplementedError`를 발생시켜 자식 클래스에서 반드시 이 메서드를 구현(오버라이딩)하도록 강제합니다.
2.  `Rectangle` 클래스는 `width`와 `height`를 속성으로 가지며, `get_area()`는 `width * height`를 반환합니다.
3.  `Circle` 클래스는 `radius`를 속성으로 가지며, `get_area()`는 `3.14 * radius * radius`를 반환합니다.

---

**풀이 과정 및 로직**
1.  `Shape` 클래스를 정의하고, `get_area` 메서드 내부에 `raise NotImplementedError`를 작성합니다. 이는 이 클래스를 직접 사용하는 것이 아니라, 상속을 위한 '추상적인' 기반 클래스임을 명시하는 좋은 방법입니다.
2.  `Rectangle` 클래스를 `Shape`를 상속받도록 `class Rectangle(Shape):`와 같이 정의합니다. `__init__`에서 `width`와 `height`를 받고, `get_area` 메서드를 `width * height`를 반환하도록 재정의(오버라이딩)합니다.
3.  `Circle` 클래스도 `Shape`를 상속받도록 `class Circle(Shape):`와 같이 정의합니다. `__init__`에서 `radius`를 받고, `get_area` 메서드를 원의 넓이 공식에 맞게 재정의합니다.
4.  여러 도형 객체(직사각형, 원)를 하나의 리스트에 담고, `for` 루프를 돌면서 각 객체의 `get_area()`를 호출합니다. 객체의 실제 타입에 따라 각기 다른 `get_area()`가 호출되는 '다형성'을 확인합니다.

**처리 순서**
1.  `Shape` 부모 클래스 정의 및 `get_area`에 `NotImplementedError` 구현
2.  `Rectangle` 자식 클래스 정의, `Shape` 상속, `__init__` 및 `get_area` 오버라이딩
3.  `Circle` 자식 클래스 정의, `Shape` 상속, `__init__` 및 `get_area` 오버라이딩
4.  여러 도형 객체를 리스트에 저장
5.  `for` 루프를 통해 리스트의 각 도형 넓이를 계산하고 출력 (다형성 확인)

**정답 코드**
```python
# 파일명: shape_calculator.py

# 1. 부모 클래스 Shape를 정의합니다.
class Shape:
    def get_area(self):
        # 자식 클래스에서 반드시 이 메서드를 구현하도록 강제합니다.
        raise NotImplementedError("get_area() 메서드가 구현되지 않았습니다.")

# 2. Rectangle 클래스가 Shape 클래스를 상속받습니다.
class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    # 부모의 get_area() 메서드를 재정의(오버라이딩)합니다.
    def get_area(self):
        return self.width * self.height

# 3. Circle 클래스가 Shape 클래스를 상속받습니다.
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    # 부모의 get_area() 메서드를 재정의(오버라이딩)합니다.
    def get_area(self):
        return 3.14 * (self.radius ** 2)

# --- 메인 실행 부분 ---
# 4. 여러 종류의 도형 객체를 리스트에 담습니다.
shapes = [
    Rectangle(10, 5),
    Circle(7),
    Rectangle(4, 8)
]

# 5. 리스트를 순회하며 각 도형의 넓이를 계산하고 출력합니다.
# shape 변수에는 Rectangle 객체와 Circle 객체가 번갈아 할당되지만,
# 동일한 .get_area() 호출로 각 객체에 맞는 넓이 계산법이 실행됩니다. (다형성)
for shape in shapes:
    # isinstance()는 객체가 특정 클래스의 인스턴스인지 확인합니다.
    shape_type = "직사각형" if isinstance(shape, Rectangle) else "원"
    print(f"{shape_type}의 넓이: {shape.get_area()}")
```

---

#### 문제 3: RPG 게임 캐릭터 클래스 설계

**문제**
간단한 텍스트 기반 RPG 게임의 `Character` 클래스를 만드세요.

1.  **속성**: `name`, `hp`(체력), `power`(공격력)
2.  **메서드**:
    -   `__init__(self, name, hp, power)`: 캐릭터 생성
    -   `attack(self, other_character)`: 다른 캐릭터(`other_character`)를 공격하여, 자신의 `power`만큼 상대방의 `hp`를 감소시킵니다. 공격 메시지를 출력합니다.
    -   `is_alive(self)`: 캐릭터의 `hp`가 0보다 큰지 여부를 `True`/`False`로 반환합니다.
    -   `show_status(self)`: 캐릭터의 현재 상태(이름, 남은 HP)를 출력합니다.

---

**풀이 과정 및 로직**
1.  `Character` 클래스를 정의하고 `__init__`에서 `name`, `hp`, `power`를 초기화합니다.
2.  `attack` 메서드는 `other_character`를 인자로 받습니다. `other_character` 역시 `Character` 클래스의 인스턴스일 것입니다.
    -   `other_character.hp -= self.power` 와 같이 상대방의 `hp`를 자신의 `power`만큼 감소시킵니다.
    -   공격 상황을 설명하는 `print` 문을 추가합니다.
3.  `is_alive` 메서드는 `self.hp > 0` 이라는 조건식의 결과를 바로 `return`하면 됩니다.
4.  `show_status` 메서드는 f-string을 사용하여 현재 `name`과 `hp`를 출력합니다.
5.  두 개의 `Character` 객체(예: '전사', '마법사')를 생성하고, 한쪽의 `hp`가 0 이하가 될 때까지 `while` 루프를 돌며 서로 공격하는 전투 시뮬레이션을 구현합니다.

**처리 순서**
1.  `Character` 클래스 정의
2.  `__init__`: `name`, `hp`, `power` 초기화
3.  `attack`: 상대방 객체의 `hp`를 자신의 `power`만큼 감소시키고 메시지 출력
4.  `is_alive`: `self.hp > 0` 결과 반환
5.  `show_status`: 현재 상태 출력
6.  (테스트) 두 캐릭터 객체 생성
7.  `while` 루프 시작 (조건: 두 캐릭터가 모두 `is_alive()`)
8.  (루프 내) 캐릭터1이 캐릭터2 공격, 캐릭터2 상태 출력
9.  (루프 내) 캐릭터2가 살아있으면 캐릭터2가 캐릭터1 공격, 캐릭터1 상태 출력
10. 루프 종료 후, 승자 판별 메시지 출력

**정답 코드**```python
# 파일명: rpg_character.py
import time

# 1-5. Character 클래스를 정의합니다.
class Character:
    def __init__(self, name, hp, power):
        self.name = name
        self.hp = hp
        self.power = power
        print(f"{self.name}(HP: {self.hp}, 공격력: {self.power}) 생성!")

    def attack(self, other_character):
        damage = self.power
        other_character.hp -= damage
        print(f"💥 {self.name}이(가) {other_character.name}을(를) 공격하여 {damage}의 피해를 입혔습니다.")

    def is_alive(self):
        return self.hp > 0

    def show_status(self):
        print(f"[{self.name}] 현재 HP: {self.hp if self.hp > 0 else '사망'}")

# --- 메인 실행 부분: 전투 시뮬레이션 ---
# 6. 두 캐릭터 객체를 생성합니다.
warrior = Character("전사", 100, 15)
wizard = Character("마법사", 70, 25)

print("\n--- 전투 시작! ---")

# 7. 두 캐릭터가 모두 살아있는 동안 전투를 반복합니다.
turn = 1
while warrior.is_alive() and wizard.is_alive():
    print(f"\n--- 턴 {turn} ---")
    
    # 전사의 턴
    warrior.attack(wizard)
    wizard.show_status()
    if not wizard.is_alive(): break
    
    time.sleep(1) # 잠시 멈춰서 진행 상황을 보기 쉽게 함
    
    # 마법사의 턴
    wizard.attack(warrior)
    warrior.show_status()
    
    turn += 1
    time.sleep(1)

# 10. 전투 종료 후 승자를 발표합니다.
print("\n--- 전투 종료! ---")
if warrior.is_alive():
    print(f"승자: {warrior.name}")
else:
    print(f"승자: {wizard.name}")
```

---

#### 문제 4: 클래스 변수를 이용한 객체 수 세기

**문제**
`Notebook`이라는 클래스를 만들 때, 지금까지 생성된 노트북 객체가 총 몇 개인지 추적하고 싶습니다. 클래스 변수(class variable)를 사용하여 이 기능을 구현하세요.

1.  `Notebook` 클래스는 `count`라는 클래스 변수를 가집니다.
2.  객체가 생성될 때마다(`__init__` 호출 시) `count`가 1씩 증가해야 합니다.
3.  `Notebook.get_total_notebooks()`라는 클래스 메서드(class method)를 만들어 현재까지 생성된 총 노트북 수를 반환하도록 하세요.

---

**풀이 과정 및 로직**
1.  **클래스 변수**: `class Notebook:` 바로 아래에 `count = 0` 과 같이 변수를 선언합니다. 이 변수는 모든 `Notebook` 객체가 공유합니다.
2.  **`__init__` 메서드**: 객체가 생성될 때마다 클래스 변수 `count`의 값을 1 증가시켜야 합니다. 클래스 변수에 접근할 때는 `Notebook.count` 또는 `self.count`와 같이 클래스 이름을 통해 접근합니다. `Notebook.count += 1`이 명확한 표현입니다.
3.  **클래스 메서드**: 일반 메서드는 첫 인자로 `self`(인스턴스)를 받지만, 클래스 메서드는 `@classmethod` 데코레이터를 붙이고 첫 인자로 `cls`(클래스 자체)를 받습니다.
    -   `@classmethod`를 `get_total_notebooks` 메서드 위에 붙입니다.
    -   `def get_total_notebooks(cls):` 와 같이 정의하고, 내부에서 `cls.count`를 반환합니다.

**처리 순서**
1.  `Notebook` 클래스 정의
2.  클래스 바로 아래에 `count = 0` 클래스 변수 선언
3.  `__init__` 메서드에서 `Notebook.count += 1` 코드 추가
4.  `@classmethod` 데코레이터를 사용하여 `get_total_notebooks(cls)` 메서드 정의
5.  (메서드 내) `return cls.count`
6.  (테스트) 여러 개의 노트북 객체를 생성하고, `Notebook.get_total_notebooks()`를 호출하여 개수가 올바르게 증가하는지 확인

**정답 코드**
```python
# 파일명: notebook_counter.py

# 1, 2. Notebook 클래스와 클래스 변수를 정의합니다.
class Notebook:
    # 이 변수는 모든 Notebook 인스턴스가 공유합니다.
    count = 0 
    
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
        # 3. 객체가 생성될 때마다 클래스 변수 count를 1 증가시킵니다.
        Notebook.count += 1
        print(f"'{self.brand} {self.model}' 노트북 생성. (총 {Notebook.count}대)")

    # 4. 클래스 메서드를 정의합니다.
    # @classmethod는 이 메서드가 인스턴스가 아닌 클래스에 속해있음을 나타냅니다.
    @classmethod
    def get_total_notebooks(cls):
        # cls는 Notebook 클래스 자체를 가리킵니다.
        # 5. 클래스 변수 count를 반환합니다.
        return cls.count

# --- 메인 실행 부분 ---
# 6. 여러 노트북 객체를 생성하며 count가 증가하는지 확인합니다.
print(f"프로그램 시작 전 총 노트북 수: {Notebook.get_total_notebooks()}")

note1 = Notebook("Samsung", "Galaxy Book")
note2 = Notebook("LG", "Gram")
note3 = Notebook("Apple", "MacBook Pro")

print(f"\n모든 객체 생성 후 총 노트북 수: {Notebook.get_total_notebooks()}")
```

---

#### 문제 5: 데이터 처리 클래스 만들기 (상속과 다형성 응용)

**문제**
다양한 형식의 데이터를 처리하는 클래스를 상속과 다형성을 이용해 설계하세요.

1.  `DataProcessor`라는 추상적인 부모 클래스를 만듭니다. 이 클래스는 `process(self, data)` 메서드를 가지며, 상속받는 자식 클래스에서 구현하도록 강제합니다.
2.  `StringProcessor` 클래스는 `DataProcessor`를 상속받아, 문자열 데이터를 받아 모든 알파벳을 대문자로 바꾸는 `process` 메서드를 구현합니다.
3.  `ListProcessor` 클래스는 `DataProcessor`를 상속받아, 숫자 리스트를 받아 오름차순으로 정렬하는 `process` 메서드를 구현합니다.
4.  `NumberProcessor` 클래스는 `DataProcessor`를 상속받아, 숫자를 받아 제곱근을 구하는 `process` 메서드를 구현합니다. (`math.sqrt` 사용)

---

**풀이 과정 및 로직**
1.  `DataProcessor` 클래스를 만들고 `process` 메서드에서 `NotImplementedError`를 발생시킵니다.
2.  `StringProcessor`를 `DataProcessor`로부터 상속받고, `process` 메서드에서 입력된 문자열 `data`에 `.upper()`를 적용하여 반환합니다.
3.  `ListProcessor`를 `DataProcessor`로부터 상속받고, `process` 메서드에서 `sorted(data)`를 사용하여 정렬된 리스트를 반환합니다.
4.  `math` 모듈을 `import`하고, `NumberProcessor`를 `DataProcessor`로부터 상속받습니다. `process` 메서드에서 `math.sqrt(data)`를 계산하여 반환합니다.
5.  다양한 종류의 데이터와 그에 맞는 프로세서 객체들을 리스트에 `(데이터, 프로세서)` 튜플 형태로 담습니다.
6.  `for` 루프를 돌면서 각 데이터와 프로세서를 가져와 `processor.process(data)`를 실행하고 결과를 출력합니다. 같은 `process` 호출이지만, 어떤 프로세서 객체인지에 따라 완전히 다른 작업이 수행되는 다형성을 보여줍니다.

**처리 순서**
1.  `math` 모듈 import
2.  `DataProcessor` 부모 클래스 정의 및 `process` 추상 메서드 구현
3.  `StringProcessor` 자식 클래스 정의, `process` 오버라이딩 (대문자 변환)
4.  `ListProcessor` 자식 클래스 정의, `process` 오버라이딩 (리스트 정렬)
5.  `NumberProcessor` 자식 클래스 정의, `process` 오버라이딩 (제곱근 계산)
6.  (테스트) 데이터와 프로세서 객체들을 짝지어 리스트에 저장
7.  `for` 루프로 리스트를 순회하며 각 `processor.process(data)` 실행 및 결과 출력

**정답 코드**
```python
# 파일명: data_processors.py

# 1. 제곱근 계산을 위해 math 모듈을 가져옵니다.
import math

# 2. 추상적인 부모 클래스를 정의합니다.
class DataProcessor:
    def process(self, data):
        raise NotImplementedError("process() 메서드를 자식 클래스에서 구현해야 합니다.")

# 3. 문자열 처리 클래스
class StringProcessor(DataProcessor):
    def process(self, data):
        print("문자열 처리기: 대문자로 변환합니다.")
        return data.upper()

# 4. 리스트 처리 클래스
class ListProcessor(DataProcessor):
    def process(self, data):
        print("리스트 처리기: 오름차순으로 정렬합니다.")
        return sorted(data)

# 5. 숫자 처리 클래스
class NumberProcessor(DataProcessor):
    def process(self, data):
        print("숫자 처리기: 제곱근을 계산합니다.")
        return math.sqrt(data)

# --- 메인 실행 부분 ---
# 6. 처리할 데이터와 사용할 프로세서를 짝지어 리스트에 담습니다.
tasks = [
    ("hello python", StringProcessor()),
    ([5, 2, 8, 1, 9], ListProcessor()),
    (144, NumberProcessor()),
    ("Object Oriented", StringProcessor())
]

# 7. tasks 리스트를 순회하며 각 데이터를 맞는 처리기로 처리합니다.
for data, processor in tasks:
    print(f"\n원본 데이터: {data}")
    processed_data = processor.process(data)
    print(f"처리 결과: {processed_data}")
```