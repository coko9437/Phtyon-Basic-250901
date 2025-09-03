### 📚 파트 6: 객체 지향 프로그래밍 (OOP)

#### **1. 클래스(Class) 기본 개념**

\*\*클래스(Class)\*\*는 객체를 만들어 내기 위한 **'설계도'** 또는 \*\*'틀'\*\*입니다. 📏 예를 들어, '빵틀'이 있다면 그 빵틀을 이용해 똑같은 모양의 '빵'을 여러 개 만들어 낼 수 있습니다. 여기서 **클래스**는 '빵틀'에 해당하고, 만들어진 각각의 \*\*빵은 '객체(Object)'\*\*에 해당합니다.

  * **클래스**: 객체가 가져야 할 속성(데이터)과 행동(기능)을 정의한 것.
  * **객체(Object) / 인스턴스(Instance)**: 클래스라는 설계도를 바탕으로 실제 메모리에 만들어진 실체.
  * **속성(Attribute)**: 클래스 내에 정의된 변수로, 객체의 상태나 데이터를 나타냅니다.
  * **메서드(Method)**: 클래스 내에 정의된 함수로, 객체가 수행할 수 있는 동작을 나타냅니다.

<!-- end list -->

```python
# '사람'에 대한 설계도(클래스)를 만듭니다.
class Person:
    # 생성자(constructor) 메서드: 객체가 생성될 때 자동으로 호출됩니다.
    def __init__(self, name, age):
        self.name = name  # self.name은 이 객체의 '이름' 속성입니다.
        self.age = age    # self.age는 이 객체의 '나이' 속성입니다.
        print(f"{self.name} 객체가 생성되었습니다.(=생성자를 호출)")

    # 자기소개를 하는 메서드(기능)입니다.
    def introduce(self):
        # self를 이용해 자신의 속성(name, age)에 접근합니다.
        print(f"안녕하세요, 제 이름은 {self.name}이고, 나이는 {self.age}살입니다.")

    # __str__ 메서드: 객체를 문자열로 표현할 때 호출됩니다.
    def __str__(self):
        return "해당 클래스의 인스턴스를 호출시, 나타나는 문자열 메서드입니다."

# Person 클래스를 이용해 첫 번째 객체 'p1'을 생성합니다.
# __init__ 메서드가 자동으로 호출됩니다.
p1 = Person("홍길동", 30)

# Person 클래스를 이용해 두 번째 객체 'p2'를 생성합니다.
p2 = Person("이순신", 45)

# 각 객체의 메서드를 호출합니다.
print("\n--- 자기소개 시작 ---")
p1.introduce()  # p1 객체의 introduce 메서드 실행
p2.introduce()  # p2 객체의 introduce 메서드 실행

# 객체의 속성에 직접 접근할 수도 있습니다.
print(f"\n첫 번째 사람의 이름은 {p1.name}입니다.")

# __str__ 메서드 호출 예시
print(f"단순 인스턴스 자체를 출력 하는 경우 p1 : ", p1)
```

#### **2. 클래스 속성과 메서드**

```python
class SoccerPlayer(object):
    def __init__(self, name, position, back_number):
        self.name = name
        self.position = position
        self.back_number = back_number

    # 등번호를 변경하는 메서드
    def change_back_number(self, new_number):
        print(f"선수의 등번호를 변경함(back_number) : From {self.back_number} to {new_number}")
        self.back_number = new_number

    # 객체를 문자열로 표현하는 메서드
    def __str__(self):
        return f"Hello, My name is {self.name}. I Play in {self.position} in center."

jinhyun = SoccerPlayer("Jinhyun", "MF", 10)
print("현재 선수의 등번호는 : ", jinhyun.back_number)
jinhyun.change_back_number(5)
print("현재 선수의 바뀐 등번호는 : ", jinhyun.back_number)
```

-----

#### **3. 상속(Inheritance)**

**상속**은 한 클래스(자식 클래스)가 다른 클래스(부모 클래스)의 속성과 메서드를 물려받아 재사용하는 개념입니다. 이는 'is-A' 관계를 나타냅니다. 예를 들어, '자동차는 탈것이다' (Car is a Vehicle)와 같습니다.

```python
# 부모 클래스: 모든 '탈것'의 공통적인 특징을 정의합니다.
class Vehicle:
    def __init__(self, speed):
        self.speed = speed
        print(f"생성자 호출, 인스턴스 생성!!! 탈것이 시속 {self.speed}km로 생성되었습니다.")

    def drive(self):
        print(f"drive 메서드 호출 !!!탈것이 시속 {self.speed}km로 달립니다.")

# 자식 클래스: Vehicle을 상속받아 '자동차'를 정의합니다.
class Car(Vehicle):  # 괄호 안에 부모 클래스 이름을 넣어 상속받습니다.
    def honk(self):
        print("honk 메서드 호출 !!!!빵빵! 자동차가 경적을 울립니다.")

# '자동차' 객체를 생성합니다.
# Car 클래스에는 __init__이 없지만, 부모인 Vehicle의 __init__이 호출됩니다.
my_car = Car(100)

print("\n--- 기능 테스트 ---")
# 부모(Vehicle)로부터 물려받은 메서드 사용
my_car.drive()

# 자신(Car)에게만 있는 고유한 메서드 사용
my_car.honk()

# 부모(Vehicle)로부터 물려받은 속성에도 접근 가능
print(f"\n이 자동차의 현재 속도는 {my_car.speed}km/h 입니다.")
```

-----

#### **4. 다형성(Polymorphism)**

**다형성**은 하나의 메서드 이름이 여러 클래스에서 다르게 동작하는 것을 의미합니다. 부모 클래스의 메서드를 자식 클래스에서 재정의(override)하여 각 객체의 특성에 맞는 동작을 구현할 수 있습니다.

```python
# 부모 클래스: Animal
class Animal:
    def speak(self):
        # 이 메서드는 자식 클래스에서 재정의될 것을 가정합니다.
        pass

# 자식 클래스: Dog
class Dog(Animal):
    def speak(self):
        return "멍멍!"

# 자식 클래스: Cat
class Cat(Animal):
    def speak(self):
        return "야옹~"

# --- 다형성 실행 ---
# animals 리스트에는 Animal의 자식 클래스 객체들이 담겨 있습니다.
animals = [Dog(), Cat()]

# 반복문을 통해 각 동물의 소리를 들어봅니다.
for animal in animals:
    # animal 변수는 루프마다 Dog 객체였다가 Cat 객체가 됩니다.
    # 똑같이 animal.speak()를 호출했지만, 실제 객체가 무엇이냐에 따라 다른 결과가 출력됩니다.
    print(f"이 동물의 소리는? {animal.speak()}")
```

-----

#### **5. 가시성(Visibility)과 속성 접근 제어**

파이썬은 기본적으로 속성(변수)에 대한 접근을 제한하지 않지만, 개발자 간의 약속을 통해 접근 수준을 제어합니다. `@property`를 사용하면 더 세련된 접근 제어가 가능합니다.

  * **Public (공개)**: 아무 접두사 없음. (`name`) 어디서든 자유롭게 접근 가능.
  * **Protected (보호)**: 언더스코어 한 개. (`_age`) 클래스 내부와 자식 클래스에서 사용하자는 약속.
  * **Private (비공개)**: 언더스코어 두 개. (`__wallet_balance`) 클래스 내부에서만 사용. 외부에서 직접 접근하려고 하면 이름이 변경(`Name Mangling`)되어 오류가 발생합니다.

**문제점: 직접 접근의 위험성**

```python
class PersonDirect:
    def __init__(self, name, age):
        self.name = name
        self.age = age  # 나이(age) 속성에 누구나 직접 접근 가능

# 객체 생성
p1 = PersonDirect("홍길동", 30)
print(f"초기 나이: {p1.age}")

# 🚨 문제점: 나이에 말도 안 되는 값을 직접 할당할 수 있습니다.
p1.age = -100  # 나이가 음수가 되는 것을 막을 방법이 없음
print(f"변경된 나이: {p1.age}")  # 논리적으로 잘못된 데이터가 저장됨
```

**해결책: `@property`를 사용한 접근 제어**

```python
class PersonProperty:
    def __init__(self, name, age):
        self.name = name
        self._age = age  # 실제 데이터는 '_age'에 저장 (보호 멤버)

    @property # getter: 'age' 속성을 읽으려고 할 때 호출됩니다.
    def age(self):
        print(">> getter가 호출되었습니다.")
        return self._age

    @age.setter # setter: 'age' 속성에 값을 할당하려고 할 때 호출됩니다.
    def age(self, value):
        print(">> setter가 호출되었습니다.")
        if value > 0:
            self._age = value
        else:
            print("🚨 오류: 나이는 0보다 커야 합니다.")

# 객체 생성
p2 = PersonProperty("이순신", 45)

# 값 읽기 (getter 호출)
print(f"초기 나이: {p2.age}") # p2.age()가 아닌 p2.age처럼 속성처럼 사용

# 값 변경 (setter 호출)
print("\n--- 유효한 값으로 변경 시도 ---")
p2.age = 50
print(f"변경된 나이: {p2.age}")

print("\n--- 유효하지 않은 값으로 변경 시도 ---")
p2.age = -10 # setter 내부의 유효성 검사에 걸림
print(f"유효하지 않은 값 할당 후 나이: {p2.age}")
```

**비공개 멤버 (`__`)**

```python
class PersonPrivate:
    def __init__(self, secret):
        # 비공개 멤버: 클래스 외부에서는 직접 접근할 수 없습니다.
        self.__secret = secret

    def get_secret(self):
        return self.__secret

p3 = PersonPrivate("중요한 비밀번호")

# 메서드를 통해서는 접근 가능
print(f"메서드를 통한 접근: {p3.get_secret()}")

# 🚨 오류 발생: 비공개 멤버에 직접 접근 시도
try:
    print(p3.__secret)
except AttributeError as e:
    print(f"\n직접 접근 시도 결과: {e}")
```

-----

**접근 방식 비교**

| 접근 방식 | 코드 예시 | 장점 | 단점 |
|:---:|:---:|:---:|:---:|
| 직접 접근 (Public) | `p1.age = -100` | 코드가 간단하고 직관적 | 데이터 무결성을 해치기 쉬움 |
| `@property` 사용 | `p2.age = 50` | 속성처럼 편하게 사용하면서 값 검증 등 제어가 가능 | 코드가 조금 더 길어짐 |
| 비공개 멤버 (`__`) | `p3.__secret` | 클래스 외부에서의 접근을 강력하게 방지 | 유연성이 떨어지고, 작정하고 접근하면 불가능하진 않음 |