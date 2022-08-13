# 4. OOP

---

# 1. 객체 지향 프로그래밍 (OOP)

## 1.1. 객체 지향 프로그래밍이란?

- 객체 지향 프로그래밍
    - OOP : Object-Oriented Programming
    - 컴퓨터 프로그래밍의 패러다임 (= 방법론 ex. 라면에 스프 먼저 or 면 먼저)
    - 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 개의 독립된 단위(= 객체)와 그 객체 간의 상호작용으로 파악하는 프로그래밍 방법
        - 각각의 객체는 메시지를 주고받고, 데이터를 처리할 수 있음
        - 객체 = 변수 + 함수 (정보와 행동을 묶어둔 것)
    - ex. 콘서트 : 가수 객체, 감독 객체, 관객 객체
- 절차 지향 vs 객체 지향
    - 절차 지향 : 데이터와 함수로 인한 변화
    - 객체 지향 : 데이터와 기능(메서드) 분리, 추상화된 구조(인터페이스)
- 객체지향 프로그래밍이 필요한 이유
    - 복잡한 현실 세계를 프로그램 설계에 반영 (추상화)
- 객체 지향의 장단점
    - 장점
        - 클래스 단위로 모듈화시켜 개발할 수 있으므로 많은 인원이 참여하는 대규모 소프트웨어 개발에 적합
        - 필요한 부분만 수정하기 쉽기 때문에 프로그램의 유지보수가 쉬움
    - 단점
        - 설계 시 많은 노력과 시간이 필요 (다양한 객체들의 상호작용 구조 설계)
            - 가벼운 프로그램의 경우 OOP 적용 안 하는 게 효율적
        - 실행 속도가 상대적으로 느림
            - 절차 지향 프로그래밍이 컴퓨터의 처리구조와 비슷해서 빠름

## 1.2. OOP 기초

### 1.2.1. 객체 / 인스턴스 / 클래스

- 객체
    - 클래스에서 정의한 것을 토대로 메모리에 할당된 것
    - 프로그램에서 사용되는 데이터 또는 식별자에 의해 참조되는 공간
    - 변수, 자료 구조, 함수, 메서드가 될 수 있음
    - 쉽게 설명하면 속성과 행동으로 구성된 모든 것!
- 클래스
    - 공통된 속성(attribute)과 조작법(method)를 가진 객체들의 분류
    - 설계도 → 실제로 존재하지 않음
    - 클래스를 만든다 = 타입(list)을 만든다
- 인스턴스
    - 특정 클래스의 실제 데이터 예시
    - 파이썬에서 모든 것은 객체, 모든 객체는 특정 클래스의 인스턴스
- 클래스와 객체, 인스턴스
    - 클래스 (설계도) : 가수
    - 객체 (실제 사례) : 이찬혁
        - 이찬혁은 객체다 (O)
        - 이찬혁은 인스턴스다 (X)
        - 이찬혁은 가수의 인스턴스다 (O)
    - 객체는 특정 타입의 인스턴스
        - 123, 900, 5는 모두 int의 인스턴스
        - ‘hello’, ‘bye’는 모두 string의 인스턴스
        - [23, 12, 1], []은 모두 list의 인스턴스
        
        ```python
        class Person :
        		pass
        print(type(Person)) # <class 'type'>
        
        person1 = Person()
        print(isinstance(person1, Person)) # True
        print(type(person1)) # <class '__main__.Person'>
        ```
        
- 파이썬과 객체
    - 파이썬은 모든 것이 객체 (object)
    - 파이썬의 모든 것엔 속성과 행동이 존재
    - 객체 = 속성 + 기능
- 객체의 특징
    - 타입(type) : 어떤 연산자와 조작이 가능한가?
    - 속성(attribute) : 어떤 상태(데이터)를 가지는가?
    - 조작법(method) : 어떤 행위(함수)를 할 수 있는가?
- 객체와 클래스 기본 문법
    - 클래스 정의 : `class MyClass :`
    - 인스턴스 생성 : `my_instance = MyClass()`
    - 메서드 호출 : `my_instance.my_method()`
    - 속성 : `my_instance.my_attribute`
- 객체 비교하기
    - ==
        - 동등한
        - 변수가 참조하는 객체가 내용이 같은 경우 True
        - 두 객체가 같아 보이지만 실제로 동일한 대상을 가리키고 있다고 확인해 준 것은 아님
    - is
        - 동일한
        - 두 변수가 동일한 객체를 가리키는 경우 True
        
        ```python
        a = [1, 2, 3]
        b = [1, 2, 3]
        print(a == b, a is b) # True False
        
        a = [1, 2, 3]
        b = a
        print(a == b, a is b) # True True
        ```
        

### 1.2.2. 속성

- 속성
    - 특정 데이터 타입/클래스의 객체들이 가지게 될 상태/데이터를 의미
    - 클래스 변수/인스턴스 변수가 존재
        
        ```python
        class Person :
        		blood_color = 'red' # 클래스 변수
        		population = 100 # 클래스 변수
        
        		def __init__(self, num) :
        				self.name = name # 인스턴스 변수
        
        person1 = Person('지민')
        print(person1.name) # 지민
        ```
        
- 인스턴스 변수
    - 인스턴스가 개인적으로 가지고 있는 속성(attribute)
    - 각 인스턴스들의 고유한 변수 (= 나만 쓰는 변수)
    - 생성자 메서드(`__init__`)에서 `self.<name>`으로 정의
    - 인스턴스가 생성된 이후 `<instance>.<name>`으로 접근 및 할당
        
        ```python
        class Person :
        
        		def __init__(self, name) : # 인스턴스 변수 정의
        				self.name = name
        
        # 인스턴스 변수 접근 및 할당
        john = Person('john')
        print(john.name) # john
        john.name = 'John Kim'
        print(john.name) # John Kim
        ```
        
- 클래스 변수
    - 한 클래스의 모든 인스턴스가 공유하는 값을 의미
        - 같은 클래스의 인스턴스들은 같은 값을 갖게 됨
        - ex. 특정 사이트의 User 수 등
    - 클래스 선언 내부에서 정의 (공용)
    - `<classname>.<name>`으로 접근 및 할당
        
        ```python
        class Circle() :
        		pi = 3.14 # 클래스 변수
        
        		def __init__(self, r) :
        				self.r = r # 인스턴스 변수
        
        c1 = Circle(5)
        c2 = Circle(10)
        
        print(Circle.pi) # 3.14
        print(c1.pi) # 3.14 -> 인스턴스.클래스 변수 접근 가능!
        print(c2.pi) # 3.14
        
        Circle.pi = 5 # 클래스 변수 바꾸면
        print(Circle.pi) # 5
        print(c1.pi) # 5 
        print(c2.pi) # 5 다 바 뀜
        # c1.pi = 10로 바꿨다면 c1 안에 새로 만들기 때문에 얘만 바뀜
        ```
        
    - 클래스 변수 활용해서 사용자 수 계산하기
        - 인스턴스가 생성될 때마다 클래스 변수가 늘어나도록 설정
        
        ```python
        class Person :
        		count = 0
        		# 인스턴스 변수 설정
        		def __init__(self, name) :
        				self.name = name
        				Person.count += 1
        
        person1 = Person('아이유')
        person2 = Person('이찬혁')
        
        print(Person.count) # 2
        ```
        
- 클래스 변수와 인스턴스 변수
    - 클래스 변수를 변경할 때는 항상 클래스.클래스변수 형식으로 변경
        
        ```python
        class Circle() :
        		pi = 3.14 # 클래스 변수
        
        		def __init__(self, r) :
        				self.r = r # 인스턴스 변수
        
        c1 = Circle(5)
        c2 = Circle(10)
        
        print(Circle.pi) # 3.14
        print(c1.pi) # 3.14
        print(c2.pi) # 3.14
        
        Circle.pi = 5 # 클래스 변수 변경
        print(Circle.pi) # 5
        print(c1.pi) # 5
        print(c2.pi) # 5
        
        c2.pi = 5 # 인스턴스 변수 변경
        print(Circle.pi) # 3.14 (클래스 변수)
        print(c1.pi) # 3.14 (클래스 변수)
        print(c2.pi) # 5 (새로운 인스턴스 변수가 생성)
        ```
        

### 1.2.3. 메서드

- 메서드
    - 특정 데이터 타입/클래스의 객체에 공통적으로 적용 가능한 행위(함수)
    - 메서드의 종류
        - 인스턴스 메서드 : 인스턴스 처리
        - 클래스 메서드 : 클래스 처리
        - 정적 메서드 : 나머지
- 인스턴스 메서드
    - 인스턴스 변수를 사용하거나, 인스턴스 변수에 값을 설정하는 메서드
    - 클래스 내부에 정의되는 메서드의 기본
    - 호출 시, 첫번째 인자로 인스턴스 자기 자신(self)이 전달됨
        - 간단하게는 self가 있으면 인스턴스 메서드!
    - self
        - 인스턴스 자기 자신
        - 파이썬에서 인스턴스 메서드는 호출 시 첫번째 인자로 인스턴스 자신이 전달되도록 설계
            - 매개변수 이름으로 self를 첫번째 인자로 정의
            - 다른 단어로 써도 작동하지만, 파이썬의 암묵적인 규칙
    - 생성자(constructor) 메서드
        - 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
        - 인스턴스 변수들의 초기값을 설정
            - 인스턴스 생성
            - `__init__` 메서드 자동 호출
        
        ```python
        class Person :
        
        		def __init__(self) : # -> 인스턴스 매서드
        				print('인스턴스가 생성되었습니다.')
        
        person1 = Person() # 인스턴스가 생성되었습니다.
        ```
        
        ```python
        class Person :
        
        		def __init__(self, name) :
        				print('인스턴스가 생성되었습니다. {name}')
        
        person1 = Person('지민') # 인스턴스가 생성되었습니다. 지민
        ```
        
    - 매직 메서드
        - Double Underscore(__)가 있는 메서드는 특수한 동작을 위해 만들어진 메서드로, 스페셜 메서드 혹은 매직 메서드라고 불림
        - 특정 상황에 자동으로 불리는 메서드
        - `__str__(self)`, `__len(self)__, __repr__(self)` 등
        - 객체의 특수 조작 행위를 지정 (함수, 연산자 등)
            - `__str__` : 해당 객체의 출력 형태를 지정
                - 프린트 함수를 호출할 때, 자동으로 호출
                - 어떤 인스턴스를 출력하면 `__str__`의 return 값이 출력
            - `__gt__` : 부등호 연산자
        
        ```python
        class Circle :
        
            def __init__(self, r) :
                self.r = r
        
            def area(self) :
                return 3.14 * self.r * self.r
        
            def __str__(self) :
                return f'[원] radius : {self.r}'
        
            def __gt__(self, other) :
                return self.r > other.r
        
        c1 = Circle(10)
        c2 = Circle(1)
        
        print(c1) # [원] radius : 10
        print(c2) # [원] radius : 1
        print(c1 > c2) # True
        print(c1 < c2) # False
        ```
        
    - 소멸자(destructor) 메서드
        - 인스턴스 객체가 소멸(파괴)되기 직전에 호출되는 메서드
        
        ```python
        class Person :
        
            def __del__(self) :
                print('인스턴스가 사라졌습니다.')
        
        person1 = Person()
        del person1 # 인스턴스가 사라졌습니다.
        ```
        
- 클래스 메서드
    - 클래스가 사용할 메서드
    - `@classmethod` 데코레이터를 사용하여 정의
    - 호출 시 첫번째 인자로 클래스(cls)가 전달됨
        
        ```python
        class Person :
        
            count = 0 # 클래스 변수
        
            def __init__(self, name) : # 인스턴스 변수 설정
                self.name = name
                Person.count += 1
        
            @classmethod
            def number_of_population(cls) :
                print(f'인구수는 {cls.count}입니다.')
        
        person1 = Person('아이유')
        person2 = Person('이찬혁')
        print(Person.count) # 2
        ```
        
    - 데코레이터
        - 함수를 어떤 함수로 꾸며서 새로운 기능을 부여
        - `@데코레이터(함수)` 형태로 함수 위에 작성
        - 순서대로 적용되기 때문에 작성 순서가 중요
        - 사용 예시
            - 데코레이터 없이 함수 꾸미기
                
                ```python
                def hello():
                	print('hello')
                
                # 데코레이팅 함수
                def add_print(original) : # 파라미터로 함수를 받는다
                    def wrapper() : # 함수 내에서 새로운 함수 선언
                        print('함수 시작') # 부가기능 -> original 함수를 꾸민다.
                        original()
                        print('함수 끝') # 부가기능 -> original 함수를 꾸민다.
                    return wrapper
                
                add_print(hello)()
                # 함수 시작
                # hello
                # 함수 끝
                
                print_hello = add_print(hello) # 위와 동일
                print_hello()
                # 함수 시작
                # hello
                # 함수 끝
                ```
                
            - 데코레이터를 활용하면 쉽게 여러 함수를 원하는대로 변경 가능
                
                ```python
                # 데코레이팅 함수
                def add_print(original) :
                    def wrapper() :
                        print('함수 시작')
                        original()
                        print('함수 끝')
                    return wrapper
                
                @add_print # add_print를 사용해서 print_hello() 함수를 꾸며주도록 하는 명령어
                def print_hello() :
                    print('hello')
                
                print_hello()
                # 함수 시작
                # hello
                # 함수 끝
                ```
                
- 클래스 메서드와 인스턴스 메서드
    - 클래스 메서드 → 클래스 변수 사용
    - 인스턴스 메서드 → 인스턴스 변수 사용
    - 두 변수 다 사용하고 싶다면?
        - 클래스 메서드는 인스턴스 변수 사용 불가능
        - 인스턴스 메서드는 둘 다 사용 가능
- 스태틱 메서드
    - 인스턴스, 클래스 변수를 전혀 다루지 않는 메서드
        - 즉, 객체 상태나 클래스 상태를 수정할 수 없음
    - 속성을 다루지 않고 단지 기능(행동)만을 하는 메서드를 정의할 때 사용
    - `@staticmethod` 데코레이터를 사용하여 정의
    - 일반 함수처럼 동작하지만, 클래스의 이름공간에 귀속됨
        - 주로 해당 클래스에 한정하는 용도로 사용
        
        ```python
        class Person :
            count = 0
            def __init__(self, name) : # 인스턴스 변수 설정
                self.name = name
                Person.count += 1
        
            @staticmethod
            def check_rich(money) : # 스태틱은 cls, self 사용 X
                return money > 10000
            
        person1 = Person('아이유')
        person2 = Person('이찬혁')
        print(Person.check_rich(100000)) # True 스태틱은 클래스로 접근 가능
        print(person1.check_rich(100000)) # True 스태틱은 인스탠스로 접근 가능
        ```
        
- 인스턴스와 클래스 간의 이름 공간
    - 클래스를 정의하면 클래스와 해당하는 이름 공간 생성
    - 인스턴스를 만들면 인스턴스 객체가 생성되고 이름 공간 생성
    - 인스턴스에서 특정 속성에 접근하면 인스턴스 → 클래스 순으로 탐색
        
        ```python
        # Person 정의
        class Person :
            name = 'unknown'
            
            def talk(self) :
                print(self.name)
        
        p1 = Person()
        p1.talk() # unknown
        
        # p2 인스턴스 변수 설정 전/후
        p2 = Person()
        p2.talk() # unknown
        p2.name = 'Kim'
        p2.talk() # Kim
        
        print(Person.name) # unknown
        print(p1.name) # unknown
        print(p2.name) # Kim
        ```
        
        - p1은 인스턴스 변수가 정의되어 있지 않아 클래스 변수 출력됨
        - p2는 인스턴스 변수가 정의되어 인스턴스 변수가 출력됨
        - Person 클래스의 값이 Kim으로 변경된 것이 아닌 p2 인스턴스의 이름 공간에 name이 Kim으로 저장됨
- 메서드 정리
    - 인스턴스 메서드
        - 호출한 인스턴스를 의미하는 self 매개변수를 통해 인스턴스를 조작
    - 클래스 메서드
        - 클래스를 의미하는 cls 매개변수를 통해 클래스를 조작
    - 스태틱 메서드
        - 클래스 변수나 인스턴스 변수를 사용하지 않는 경우에 사용
        - 객체 상태나 클래스 상태를 수정할 수 없음
    - 예시
        
        ```python
        class MyClass :
        
        		def method(self) :
        				return 'instance method', self
        
        		@classmethod
        		def classmethod(cls) :
        				return 'class method', cls
        
        		@staticmethod
        		def staticmethod() :
        				return 'static method'
        ```
        
        - 인스턴스 메서드를 호출한 결과
            
            ```python
            obj = MyClass()
            
            print(obj.method())
            # ('instance method', <__main__.MyClass object at 0x100dd7e20>)
            
            print(MyClass.method(obj))
            # ('instance method', <__main__.MyClass object at 0x100dd7e20>)
            # 권장되는 방법은 아님. 수동으로 이렇게 넣어도 되지만 안 해도 자동으로 들어간다.
            ```
            
        - 클래스 자체에서 각 메서드를 호출하는 경우
            
            ```python
            # 인스턴스 메서드는 호출할 수 없음
            
            print(MyClass.classmethod())
            # ('class method', <class '__main__.MyClass'>)
            
            print(MyClass.staticmethod())
            # static method
            
            MyClass.method()
            # method() missing 1 required positional argument: 'self'
            # 클래스는 self 자동으로 안 들어감 (인스턴스라면 들어가지만)
            ```
            
        - 인스턴스는 클래스 메서드와 스태틱 메서드 모두 접근할 수 있음
            
            ```python
            print(obj.classmethod()) # ('class method', <class '__main__.MyClass'>)
            
            print(MyClass.classmethod()) # ('class method', <class '__main__.MyClass'>)
            
            print(obj.staticmethod()) # static method
            ```
            

# 2. 객체지향의 핵심 개념

- 객체 지향의 핵심 4가지
    - 추상화
    - 상속
    - 다형성
    - 캡슐화

## 2.1. 추상화

- 추상화
    - 복잡한 것은 숨기고, 필요한 것만 드러내기
        - 함수, 변수, 클래스
    - 현실 세계를 프로그램 설계에 반영하기 위해 사용

## 2.2. 상속

- 상속
    - 두 클래스 사이 부모-자식 관계를 정립하는 것
        - 상위 클래스-하위 클래스라고도 함
    - 클래스는 상속이 가능
        - 모든 파이썬 클래스는 object를 상속 받음
            - 타고 타고 올라가다 보면 object가 있음!
    - 작성 방법 : `class ChildClass(ParentClass) :`
    - 하위 클래스는 상위 클래스에 정의된 속성, 행동, 관계 및 제약 조건을 모두 상속받음
    - 부모 클래스의 속성, 메서드가 자식 클래스에 상속되므로, 코드 재사용성이 높아짐
    - 메서드 오버라이딩을 통해 자식 클래스에서 재정의 가능
    - 상속관계에서의 이름 공간은 인스턴스, 자식 클래스, 부모 클래스 순으로 탐색
- 상속을 하는 이유
    - 상속 없이 구현하는 경우
        - 정보를 나타내기 어려움 (ex. 학생, 교수)
        - 메서드 중복 정의
    - 상속을 통한 메서드 재사용
- 상속 관련 함수와 메서드
    - `isinstance(object, classinfo)`
        - classinfo의 instance거나 subclass인 경우 True
    - `issubclass(class, classinfo)`
        - class가 classinfo의 subclass면 True
        - classinfo는 클래스 객체의 튜플일 수 있으며, classinfo의 모든 항목을 검사
            - classinfo의 어느 하나라도 맞으면 True 반환
    - `super()`
        - 자식클래스에서 부모클래스를 사용하고 싶은 경우
        
        ```python
        class Person :
            def __init__(self, name, age, number, email) :
                self.name = name
                self.age = age
                self.number = number
                self.email = email
        
        class Student(Person) :
            def __init__(self, name, age, number, email, student_id) :
                # Person 클래스
                super().__init__(name, age, number, email)
                self.student_id = student_id
        ```
        
- 다중 상속
    - 두 개 이상의 클래스를 상속받는 경우
    - 상속받은 모든 클래스의 요소를 활용 가능
    - 중복된 속성이나 메서드가 있는 경우 상속 순서에 의해 결정됨
        - 앞에 쓴 부모 클래스가 우선시됨
    - 모든 언어에서 가능한 건 아님
- 다중 상속 관련 함수와 메서드
    - MRO 메서드 (Method Resolution Order)
        - 해당 인스턴스의 클래스가 어떤 부모 클래스를 가지는지 확인하는 메서드
        - 기존의 (인스턴스 → 클래스) 순으로 이름 공간을 탐색하는 과정에서 상속 관계에 있으면 (인스턴스 → 자식 클래스 → 부모 클래스)로 확장
        - `FirstChild.mro()`와 같이 씀

## 2.3. 다형성

- 다형성(Polymorphism)이란?
    - 여러 모양을 뜻하는 그리스어
    - 동일한 메서드가 클래스에 따라 다르게 행동할 수 있음을 의미
    - 즉, 서로 다른 클래스에 속해있는 객체들이 동일한 메시지에 대해 다른 방식으로 응답할 수 있음
- 메서드 오버라이딩
    - 클래스 상속 시 부모 클래스에서 정의한 메서드를 자식 클래스에서 같은 이름의 메서드로 덮어씀
        - 부모 클래스의 메서드 이름과 기본 기능을 그대로 사용하지만, 특정 기능을 바꾸고 싶을 때 사용
    - 부모 클래스의 메서드를 실행시키고 싶은 경우 super를 활용
- 추가) 오버로딩
    - 이름이 같은 함수를 매개변수만 다르게 여러 개 만들어서 다르게 활용
    - 다른 언어에 있는데 파이썬에는 없음 → *args

## 2.4. 캡슐화

- 캡슐화
    - 객체의 일부 구현 내용에 대해 외부로부터의 직접적인 액세스를 차단
        - 민감 정보를 숨김 ex. 주민등록번호
    - 파이썬에서 암묵적으로 존재하지만, 언어적으로는 존재하지 않음
- 접근제어자 종류
    - Public Access Modifier
    - Protected Access Modifier
    - Private Access Modifier
- Public Member
    - 언더바 없이 시작하는 메서드나 속성
    - 어디서나 호출이 가능, 하위 클래스 오버라이드 허용
    - 일반적으로 작성되는 메서드와 속성의 대다수를 차지
    
    ```python
    class Person:
        
        def __init__(self, name, age):
            self.name = name
            self.age = 30
    
    # Person 클래스의 인스턴스인 p1은 이름과 나이 모두 접근 가능
    p1 = Person('김싸피', 30)
    print(p1.name)
    print(p1.age)
    ```
    
- Protected Member
    - 언더바 1개로 시작하는 메서드나 속성
    - 암묵적 규칙에 의해 부모 클래스 내부와 자식 클래스에서만 호출 가능
    - 하위 클래스 오버라이드 허용
    
    ```python
    class Person:
        
        def __init__(self, name, age):
            self.name = name
            self._age = 30
        
        def get_age(self) :
            return self._age
    
    # 인스턴스를 만들고 get_age 메서드를 활용하여 호출할 수 있음
    p1 = Person('나연', 60)
    print(p1.get_age()) # 30
    
    # _age에 직접 접근하여도 확인 가능! 파이썬에서 암묵적으로 활용될 뿐
    print(p1._age) # 30
    ```
    
- Private Member
    - 언더바 2개로 시작하는 메서드나 속성
    - 본 클래스 내부에서만 사용이 가능
    - 하위클래스 상속 및 호출 불가능 (오류)
    - 외부 호출 불가능 (오류)
    
    ```python
    class Person:
        
        def __init__(self, name, age):
            self.name = name
            self.__age = age
        
        def get_age(self): 
            return self.__age
    
    # 인스턴스를 만들고 get_age 메서드를 활용하여 호출할 수 있음
    p1 = Person('김싸피', 30)
    print(p1.get_age()) # 30
    
    # __age에 직접 접근 불가능
    print(p1._age)
    # AttributeError: 'Person' object has no attribute '__age'
    ```
    
- getter 메서드와 setter 메서드
    - 변수에 접근할 수 있는 메서드를 별도로 생성
        - getter 메서드 : 변수의 값을 읽는 메서드
            - `@property`  데코레이터 사용
        - setter 메서드 : 변수의 값을 설정하는 성격의 메서드
            - `@변수.setter` 사용
        - 위 데코레이터 쓸 경우 변수처럼 사용 가능 (`()` 안 써도 됨)
    
    ```python
    class Person:
        
        def __init__(self, age):
            self._age = age 
            
        @property
        def age(self):
            return self._age
        
        @age.setter
        def age(self, new_age):
            if new_age <= 19:
                raise ValueError('Too Young For SSAFY')
                return
            
            self._age = new_age
    
    # 인스턴스를 만들어서 나이에 접근하면 정상적으로 출력
    p1 = Person(20)
    print(p1.age) # 20
    
    # p1 인스턴스의 나이를 다른 값으로 바꿔도 정상적으로 반영
    p1.age = 33
    print(p1.age) # 33
    
    # setter 함수에는 조건문이 있음. 걸릴 경우 오류 발생
    p1.age = 19
    print(p1.age) # ValueError: Too Young For SSAFY
    ```
    

- 객체 지향의 핵심 4가지 정리
    - 추상화 : 복잡한 것 숨기고 필요한 것 나타냄
    - 상속 : 부모 클래스, 자식 클래스 관계 → 물려받아 재사용
    - 다형성 : 이름은 같은데 동작은 다른 것 → 오버라이딩 (자식이 변경)
    - 캡슐화 : 민감한 정보 숨기는 것 (못 보게, 못 고치게) → getter, setter, _

# 3. 에러와 예외 처리

## 3.1. 디버깅

- 버그란?
    - 최초의 버그는 1945년 코볼 발명자 그레이스 호퍼가 발견
    - 컴퓨터 회로에 나방이 들어가 합선을 일으켜 비정상적으로 동작 → 이때부터 버그라고 부름
- 디버깅의 정의
    - 잘못된 프로그램을 수정하는 것 (de + bugging)

## 3.2. 에러와 예외

- 문법 에러 (Syntax Error)
    - 문법 에러가 발생하면 파이썬 프로그램은 실행되지 않음
    - 파일 이름, 줄번호, ^ 문자를 통해 파이썬이 코드를 읽어나갈 때 문제가 발생한 위치를 표현
    - 줄에서 에러가 감지된 가장 앞의 위치를 가리키는 캐럿 기호(^)를 표시
    - 종류
        - Invalid syntax : 문법 에러
        - assign to literal : 잘못된 할당
        - EOL (End of Line) : 따옴표 오류
        - EOF (End of File) : 괄호 닫기 오류
- 예외 (Exception)
    - 실행 도중 예상치 못한 상황을 맞이하면 프로그램 실행을 멈춤
        - 문법이나 표현식이 문법적으로 올바르더라도 발생하는 에러
    - 실행 중에 감지되는 에러들을 예외라고 부름
    - 예외는 여러 타입으로 나타나고, 타입이 메시지의 일부로 출력됨
        - NameError, TypeError 등
    - 모든 내장 예외는 Exception Class를 상속받아 이뤄짐
    - 사용자 정의 예외를 만들어 관리할 수 있음
    - 종류
        - ZeroDivisionError : 어떤 수를 0으로 나누고자 할 때 발생
        - NameError : namespace 상에 이름이 없는 경우
        - TypeError : 자료형이 올바르지 못하거나 필수 매개변수 개수가 맞지 않는 경우
        - ValueError : 자료형은 올바르나 값이 적절하지 않거나 없는 경우
        - IndexError : 인덱스가 존재하지 않거나 범위를 벗어나는 경우
        - KeyError : 해당 키가 존재하지 않는 경우
        - ModuleNotFoundError : 존재하지 않는 모듈을 임포트하는 경우
        - ImportError : 모듈은 있으나 존재하지 않는 클래스/함수를 가져오는 경우
        - KeyboardInterrupt : 임의로 프로그램을 중단한 경우
        - IndentationError : 들여쓰기가 적절하지 않는 경우
- 파이썬 내장 예외 (built-in-exceptions)
    - 클래스 계층 구조 ([docs.python.org/ko/3/library/exceptions.html#exxception-hierarchy](http://docs.python.org/ko/3/library/exceptions.html#exxception-hierarchy))

## 3.3. 예외 처리

- 예외 처리
    - try문(statement) / except절(clause)을 이용하여 예외 처리를 할 수 있음
    - try문
        - 오류가 발생할 가능성이 있는 코드 실행
        - 예외가 발생되지 않으면 except 없이 실행 종료
    - except문
        - 예외가 발생하면 except절이 실행
        - 예외 상황을 처리하는 코드를 받아서 적절한 조치를 취함
- 작성 방법
    
    ```python
    try :
        try (명령문)
    except (예외그룹1) as (변수1) :
        (예외처리 명령문 1)
    except (예외그룹2) as (변수2) :
        (예외처리 명령문 2)
    finally : # (선택사항) 모든 상황에 반드시 수행하는 문장
        finally (명령문)
    ```
    
    - try문은 반드시 하나 이상의 except문이 필요
- 예시
    
    ```python
    try :
        num = input('숫자 입력 : ')
        print(int(num))
    except ValueError:
        print('숫자가 아닙니다.')
    ```
    
- 에러 메시지 처리 (as)
    - as 키워드를 활용하여 원본 에러 메시지를 사용할 수 있음
        - 예외를 다른 이름에 대입
        
        ```python
        # IndexError: list index out of range
        
        try :
            empty_list = []
            print(empty_list[-1])
        except IndexError as err :
            print(f'{err}, 오류가 발생했습니다.')
        
        # list index out of range, 오류가 발생했습니다.
        ```
        
- 에외 처리 종합
    - 구문
        - try : 코드를 실행
        - except : try문에서 예외가 발생 시 실행
        - else : try문에서 예외가 발생하지 않으면 실행
        - finally : 예외 발생 여부와 관계없이 항상 실행
- 실습
    - 100을 사용자가 입력한 값으로 나누고 출력하는 코드
        - 발생 가능한 에러 : 0으로 나눔, 문자열 입력 등
            
            ```python
            try :
                num = input('100으로 나눌 값을 입력하시오 : ')
                print(100 / int(num))
            except ValueError :
                print('숫자를 넣어주세요.')
            except ZeroDivisionError :
                print('0으로 나눌 수 없습니다.')
            except:
                print('에러는 모르지만 에러가 발생했습니다.')
            ```
            
            - 순차적으로 실행되므로 가장 작은 범주부터 예외 처리를 해야 함
    - 파일을 열고 읽는 코드
        - 파일 열기 시도
            - 파일 없는 경우 → 해당 파일이 없습니다. 출력 (except)
            - 파일 있는 경우 → 파일 내용을 출력 (else)
        - 해당 파일 읽기 작업 종료 메시지 출력 (finally)
            
            ```python
            try :
                f = open('file.txt')
            except FileNotFoundError :
                print('해당 파일이 없습니다.')
            else :
                print('파일을 읽기 시작합니다.')
                print(f.read())
                print('파일을 모두 읽었습니다.')
                f.close()
            finally :
                print('파일 읽기를 종료합니다.')
            
            # 파일이 없는 경우
            '''
            해당 파일이 없습니다.
            파일 읽기를 종료합니다.
            '''
            
            # 파일이 있는 경우
            '''
            파일을 읽기 시작합니다.
            (파일 내용)
            파일을 모두 읽었습니다.
            파일 읽기를 종료합니다.
            '''
            ```
            
- try문 관련 여담
    - try보다는 if가 빠름
    - if로 조건 잘 쪼개서 만드는 게 더 효율적인 프로그래밍 (이지만 문화에 따라 다름)

## 3.4. 예외 발생시키기

- `raise`
    - `raise`를 통해 예외를 강제로 발생시킬 수 있음
    - 활용법 : `raise <에러>('메시지')`
    
    ```python
    def avg(scores):
        if len(scores) == 0 :
            raise Exception('학생이 없습니다.')
        return sum(scores) / len(scores)
    
    avg([]) # Exception: 학생이 없습니다.
    ```
    
- `assert`
    - 상태를 검증하는 데에 사용되며 거짓일 경우 무조건 `AssertionError`가 발생
    - 일반적으로 디버깅용도로 사용됨
    - 활용법 : `assert (Boolean expression), (error message)`
    
    ```python
    assert len([1, 2]) == 1, '길이가 1이 아닙니다.'
    # AssertionError: 길이가 1이 아닙니다.
    ```