# 2. 제어문 및 함수

---

## 1. 제어문 (Control Statement)

- 파이썬은 기본적으로 위에서부터 아래로 차례대로 명령을 수행
- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어가 필요함
- 제어문은 순서도(flowchart)로 표현이 가능

### 1.1. 조건문

- 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용
- 기본 형식
    - 조건에는 참/거짓에 대한 조건식
        - 조건이 참인 경우 이후 들여쓰기 되어있는 코드 블록을 실행
        - 이외의 경우 else 이후 들여쓰기 되어있는 코드 블록을 실행
            - else는 선택적으로 활용할 수 있음
    - 들여쓰기 주의 : PEP8에서 권장하는 4 space 사용
    
    ```python
    a = 6
    if a > 5 :
        print('5 초과')
    else :
        print('5 이하')
    print(a)
    
    '''
    5 초과
    6
    '''
    ```
    

### 1.2. 복수 조건문

- 복수의 조건식을 활용할 경우 elif를 활용하여 표현
    - 순서 : 조건식을 동시에 검사하는 것이 아니라 순차적으로 비교
    
    ```python
    if 조건 :
        # Code block
    elif 조건 :
        # Code block
    elif 조건 :
        # Code block
    else 조건 :
        # Code block
    ```
    

### 1.3. 중첩 조건문

- 조건문은 다른 조건문에 중첩되어 사용될 수 있음
    - 들여쓰기에 유의하여 작성
    
    ```python
    if 조건 :
        # Code block
        if 조건 :
            # Code block
    else :
        # Code block
    ```
    

### 1.4. 조건 표현식

- 조건 표현식(Conditional Expression)이란?
    - 조건 표현식을 일반적으로 조건에 따라 값을 정할 때 활용
    - 삼항 연산자(Ternary Operator)로 부르기도 함
        
        ```python
        [true인 경우 값] if [조건] else [false인 경우 값]
        ```
        
        - 왼참오거 : if 조건을 기준으로 왼쪽은 참 값, 오른쪽은 거짓 값

## 2. 반복문

- 특정 조건을 만족할 때까지 같은 동작을 계속 반복하고 싶을 때 사용
- 반복문의 종류
    - while문
        - 종료 조건에 해당하는 코드를 통해 반복문을 종료
    - for문
        - 반복 가능한 객체를 모두 순회하면 종료
        - 별도의 종료 조건이 필요 없음
    - 반복 제어
        - break, continue, for-else

### 2.1. while문

- while문
    - 조건식이 참인 경우 반복적으로 코드를 실행
        - 조건이 참인 경우 들여쓰기 되어 있는 코드 블록이 실행됨
        - 코드 블록이 모두 실행되고, 다시 조건식을 검사하며 반복적으로 실행됨
        - while문은 무한 루프를 하지 않도록 종료 조건이 반드시 필요
        
        ```python
        a = 0
        while a < 5 : # 종료 조건
            print(a)
            a += 1 # 반복 시 a가 계속 증가
        print('끝')
        ```
        
    - [python tutor](https://pythontutor.com/visualize.html#mode=edit) : 코드를 시각화해서 보여주는 사이트
- 복합 연산자 (In-Place Operator)
    - 복합 연산자는 연산과 할당을 합쳐 놓은 것
    - 예시) 반복문을 통해서 개수를 카운트하는 경우
        - `cnt += 1` : `cnt = cnt =+ 1`

### 2.2. for문

- for문
    - 시퀀스(string, tuple, list, range)를 포함한 순회 가능한 객체(iterable)의 요소를 모두 순회
        - 처음부터 끝까지 모두 순회하므로 별도의 종료 조건이 필요하지 않음 (횟수 기반)
    - Iterable
        - 순회할 수 있는 자료형 (string, list, dict, tuple, range, set 등)
        - 순회형 함수 (range, enumerate)
        
        ```python
        for fruit in ['apple', 'mange', 'banana'] :
            print(fruit)
        print('끝')
        
        '''
        apple
        mango
        banana
        끝
        '''
        ```
        
- 문자열(String) 순회
    
    ```python
    chars = input() # happy
    
    # 1
    for char in chars :
        print(char)
    
    # 2
    for idx in range(len(chars)) :
        print(chars[idx])
    
    # h / a / p / p / y
    ```
    
- 딕셔너리 순회
    - 딕셔너리는 기본적으로 key를 순회하며, key를 통해 값을 활용
    
    ```python
    grades = {'john' : 80, 'eric' : 90}
    for student in grades :
        print(student)
    
    # john / eric
    ```
    
    - 추가 메서드를 활용한 딕셔너리 순회
        - keys() : key로 구성된 결과
        - values() : value로 구성된 결과
        - items() : (key, value)의 튜플로 구성된 결과
            
            ```python
            grades = {'john' : 80, 'eric' : 90}
            
            print(grades.keys())
            print(grades.values())
            print(grades.items())
            
            # dict_keys(['john', 'eric'])
            # dict_values([80, 90])
            # dict_items([('john', 80), ('eric', 90)])
            
            for student, grade in grades.items() :
                print(student, grade)
            
            # john 80
            # eric 90
            ```
            
- enumerate 순회
    - `enumerate()`
        - (index, value) 형태의 튜플로 구성된 열거 객체를 반환
        - start 값 설정 가능
        
        ```python
        members = ['민수', '영희', '철수']
        
        enumerate(members) # <enumerate object at 0x1030aecc0>
        print(list(enumerate(members))) # [(0, '민수'), (1, '영희'), (2, '철수')]
        print(list(enumerate(members, start = 1))) # [(1, '민수'), (2, '영희'), (3, '철수')]
        
        for idx, number in enumerate(members) :
            print(idx, number)
        
        # 0 민수
        # 1 영희
        # 2 철수
        ```
        
- List Comprehension
    - 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성하는 방법
        - 가독성은 떨어짐
        
        ```python
        [code for 변수 in iterable]
        
        [code for 변수 in iterable if 조건식]
        ```
        
    - list comprehension과 map()의 차이
        - list comprehension : 복수의 리스트 항목을 for문과 list.append()를 사용하지 않고 한 줄의 코드로 작성하는 것
        - map() : 복수의 자료에 대해 map()함수의 인자로 정해진 함수에 적용시켜 새로운 값을 변환
- Dictionary Comprehension
    - 표현식과 제어문을 통해 특정한 값을 가진 딕셔너리를 간결하게 생성
        - 딕셔너리는 순회 가능하다는 사실! 잊지 마!
        
        ```python
        {key : value for 변수 in iterable}
        
        {key : value for 변수 in iterable if 조건식}
        ```
        

### 2.3. 반복문 제어

- break
    - break문을 만나면 반복문은 종료됨
        - 특정 조건에 반복문을 종료시키기 위해 사용!
- continue
    - continue 이후의 코드 블록은 수행하지 않고, 다음 반복을 수행
- pass
    - 아무것도 하지 않음
        - 특별히 할 일이 없을 때 자리를 채우는 용도로 사용 (문법)
        - 반복문 아니어도 사용 가능
    - pass vs continue 비교
        
        ```python
        # pass
        for i in range(4) :
            if i == 2 :
                pass
            print(i) # 0 1 2 3
        
        # continue
        for i in range(4) :
            if i == 2 :
                continue
            print(i) # 0 1 3
        ```
        
- else
    - 끝까지 반복문을 실행한 이후에 else문 실행
    - break를 통해 중간에 종료되는 경우 else문은 실행되지 않음
        
        ```python
        for char in 'apple' :
            if char == 'b' :
                print('b!')
                break
        else :
            print('b가 없습니다.') # b가 없습니다.
        
        for char in 'banana' :
            if char == 'b' :
                print('b!')
                break
        else :
            print('b가 없습니다.') # b!
        ```
        

## 3. 함수

### 3.1. 기초

- 함수를 사용하는 이유
    - Decomposition (분해)
        - 기능을 분해하고, 재사용 가능하게 만들고
    - Abstraction (추상화)
        - 복잡한 내용을 모르더라도 사용할 수 있도록
        - 내부 구조를 변경할 게 아니라면 몰라도 무방
            - 그것이 함수의 장점이자 프로그래밍의 매력
            - 스마트폰의 원리를 잘 몰라도 우리는 잘 사용할 수 있음
- 함수의 종류
    - 내장 함수
        - 파이썬에 기본적으로 포함된 함수
        - 파이썬 개발자들이 만들어서 자동으로 설치되어 있음
    - 외장함수
        - import문을 통해 사용하며, 외부 라이브러리에서 제공하는 함수
    - 사용자 정의 함수
        - 직접 사용자가 만드는 함수
- 함수의 정의
    - 특정한 기능을 하는 코드의 조각 (묶음)
    - 특정 코드를 매번 다시 작성하지 않고, 필요 시에만 호출하여 간편히 사용
- 함수 기본 구조
    - 선언과 호출 (define & call) - 생성할 때와 사용할 때
    - 입력 (input)
    - 문서화 (docstring) - 사람들이 쉽게 활용할 수 있도록 설명
    - 범위 (scope)
    - 결과값 (output)
- 선언과 호출
    - 함수의 선언은 def 키워드 활용
    - 들여쓰기를 통해 function body 작성
        - docstring은 함수 body 앞에 선택적으로 작성
            - 작성 시엔 반드시 첫번째 문장에 문자열 “””
    - 함수는 parameter를 넘겨줄 수 있음 (재료)
    - 함수는 동작 후에 return을 통해 결과값 전달 (레시피)
    - 함수를 사용하기 위해서는 먼저 함수를 정의해야 함
        
        ```python
        def function_name(parameter) :
            # code block
            return returning_value
        ```
        
    - 함수는 함수명()으로 호출하여 사용
        - parameter가 있는 경우, 함수명(값1, 값2, …)로 호출
        
        ```python
        def foo() :
           return True # foo()
        
        def add(x, y) :
            return x + y # add(2, 3)
        ```
        

### 3.2. 결과값 (Output)

- 값에 따른 함수의 종류
    - void function
        - 명시적인 return 값이 없는 경우, None을 반환하고 종료
    - value returning function
        - 함수 실행 후, return문을 통해 값 반환
        - return을 하게 되면, 값 반환 후 함수 바로 종료
        
        ```python
        # Void function
        print('hello python') # hello python
        # print는 값을 출력하지만, 값을 반환하지는 않음
        
        # Value returning function
        float('3.14') # 3.14
        ```
        
- 주의 : print vs return
    - print를 사용하면 호출될 때마다 값이 출력됨 (주로 테스트를 위해 사용)
    - 데이터 처리를 위해서는 return 사용
    
    ```python
    # Void function 예시
    def void_product(x, y) :
        print(f'{x} x {y} = {x * y}')
    
    void_product(4, 5) # 4 * 5 = 20
    ans = void_product(4, 5) # 4 x 5 = 20
    print(ans) # None
    
    # Value returning function 예시
    def value_returning_product(x, y) :
        return x * y
    
    value_returning_product(4, 5) # (X)
    ans = value_returning_product(4, 5) # (X)
    print(ans) # 20
    ```
    
    - REPL(Read-Eval-Print-Loop) 환경에서는 마지막으로 작성된 코드의 리턴 값을 보여주므로 같은 동작을 하는 것으로 착각할 수 있음
        - jupyter notebook
- 두 개 이상의 값 반환
    - return은 항상 하나의 값만을 반환
        
        ```python
        def minus_and_product(x, y) :
            return x - y
            return x + y
        
        y = minus_and_produdt(4, 5)
        print(y) # -1
        ```
        
    - 두 개 이상의 값을 반환하려면 튜플 활용
        
        ```python
        def minus_and_product(x, y) :
            return x - y, x + y
        
        y = minus_and_produdt(4, 5)
        print(y) # (-1, 20)
        print(type(y)) # <class 'tuple'>
        ```
        

### 3.3. 입력 (Input)

- parameter와 argument
    - parameter : 함수를 정의할 때 함수 내부에서 사용되는 변수
    - argument : 함수를 호출할 때 넣어주는 값
    
    ```python
    def function(ham) : # parameter : ham
        return ham
    
    function('spam') # argument : 'spam'
    # 함수 리턴값 : spam
    ```
    
- argument
    - 함수 호출 시 함수의 parameter를 통해 전달되는 값
    - argument는 소괄호 안에 할당 `func_name(argument)`
        - 필수 argument : 반드시 전달되어야 하는 argument
        - 선택 argument : 값을 전달하지 않아도 되는 경우는 기본값이 전달
    - positional argument
        - 기본적으로 함수 호출 시 argument는 위치에 따라 함수 내에 전달됨
    - keyword argument
        - 직접 변수의 이름으로 특정 argument를 전달
        - keyword argument 다음에 positional argument를 활용할 수 없음
            
            ```python
            def add(x, y) :
                return x + y
            
            add(x = 2, y = 5) # O : keyword
            add(2, y = 5) # O : positional(기본값) + keyword
            add(x = 2, 5) # X : ERROR! keyword가 오는 순간 순서가 없어짐
            ```
            
    - default arguments values
        - 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 함
            - 정의된 것보다 더 적은 개수의 argument들로 호출될 수 있음
            
            ```python
            def add(x, y = 0)
                return x + y
            
            add(2) # x = 2, y = 0
            ```
            
- 가변 인자 (*args)
    - print 함수의 arguments 개수가 변해도 잘 동작하는 이유는?
        
        ```python
        print('hello') # hello
        print('you', 'need', 'python') # you need python
        ```
        
        - 애스터리스크(asterisk) 혹은 언패킹 연산자라고 불리는 * 덕분
    - 가변 인자
        - 여러 개의 positional argument를 하나의 필수 parameter로 받아서 사용
        - 몇 개의 positional argument를 받을지 모르는 함수 정의 시 유용
        
        ```python
        def add(*args) :
            for arg in args :
                print(arg)
        ```
        
    - 패킹 & 언패킹
        - 패킹 : 여러 개의 데이터를 묶어서 변수에 할당하는 것
            
            ```python
            numbers = (1, 2, 3, 4, 5) # 패킹
            print(numbers) # (1, 2, 3, 4, 5)
            ```
            
        - 언패킹 : 시퀀스 속의 요소들을 여러 개의 변수에 나누어 할당하는 것
            
            ```python
            numbers = (1, 2, 3, 4, 5)
            a, b, c, d, e = numbers # 언패킹
            print(a, b, c, d, e) # 1 2 3 4 5
            ```
            
        - 언패킹시 변수의 개수와 할당하고자 하는 요소의 개수가 동일해야 함
            
            ```python
            numbers = (1, 2, 3, 4, 5) # 패킹
            a, b, c, d, e, f = numbers # 언패킹
            # ValueError: not enough values to unpack (expected 6, got 5)
            ```
            
        - 언패킹 시 왼쪽의 변수에 asterisk(*)를 붙이면, 할당하고 남은 요소를 리스트에 담을 수 있음 (파이썬만의 편리한 문법)
            
            ```python
            numbers = (1, 2, 3, 4, 5) # 패킹
            
            a, b, *rest = numbers # 1, 2를 제외한 나머지를 rest에 대입
            print(a, b, rest) # 1 2 [3, 4, 5]
            
            a, *rest, e = numbers # 1, 5를 제외한 나머지를 rest에 대입
            print(rest) # [2, 3, 4]
            ```
            
    - asterisk(*)와 가변 인자
        - *는 시퀸스 언패킹 연산자라고도 불리며 말 그대로 시퀀스를 풀어 헤치는 연산자
            - 주로 튜플이나 리스트를 언패킹하는 데 사용
            - *를 활용하여 가변 인자를 만들 수 있음
            
            ```python
            def func(*args) :
                print(args)
                print(type(args))
            
            func(1, 2, 3, 'a', 'b')
            
            # (1, 2, 3, 'a', 'b')
            # <class 'tuple'>
            ```
            
    - 예시
        - packing을 통해 받은 모든 숫자들의 합을 구하는 함수 만들기
            
            ```python
            def sum_all(*numbers) :
                result = 0
                for number in numbers :
                    result += number
                return result
            ```
            
        - 반드시 받아야 하는 인자와 추가적인 인자를 구분해서 사용할 수 있음
            
            ```python
            def print_family_name(father, mother, *pets) :
                print(f'아버지 : {father}')
                print(f'어머니 : {mother}')
                print('반려동물들..')
                for name in pets :
                    print(f'반려동물 : {name}')
            
            print_family_name('아부지', '어무니', '멍멍이', '냥냥이')
            
            '''
            아버지 : 아부지
            어머니 : 어무니
            반려동물들..
            반려동물 : 멍멍이
            반려동물 : 냥냥이
            '''
            ```
            
- 가변 키워드 인자 (**kwargs)
    - 몇 개의 키워드 인자를 받을지 모르는 함수를 정의할 때 유용
    - **kwargs는 딕셔너리로 묶여 처리되며, parameter에 **를 붙여 표현
        
        ```python
        def family(**kwargs) :
            for key, value in kwargs.items() :
                print(key, ':', value)
        
        family(father = '아부지', mother = '어무니', baby = '아기')
        
        '''
        father : 아부지
        mother : 어무니
        baby : 아기
        '''
        ```
        
        - family 함수 argument는 문자열로 쓰면 안 됨!
    - 반드시 받아야 하는 키워드 인자와 추가적인 키워드 인자를 구분해서 사용할 수 있음
        
        ```python
        def print_family_name(father, mother, **pets) :
            print(f'아버지 : {father}')
            print(f'어머니 : {mother}')
            if pets :
                print('반려동물들..')
                for species, name in pets.items() :
                    print(f'{species} : {name}')
        
        print_family_name('아부지', '어무니', dog = '멍멍이', cat = '냥냥이')
        
        '''
        아버지 : 아부지
        어머니 : 어무니
        반려동물들..
        dog : 멍멍이
        cat : 냥냥이
        '''
        ```
        
- 가변 인자(*args)와 가변 키워드 인자(**kwargs)
    - 가변 인자와 가변 키워드 인자를 함께 사용할 수 있음
        
        ```python
        def print_family_name(*parents, **pets) :
            print(f'아버지 : {parents[0]}')
            print(f'어머니 : {parents[1]}')
            if pets :
                print('반려동물들..')
                for species, name in pets.items() :
                    print(f'{species} : {name}')
        
        print_family_name('아부지', '어무이', dog = '멍멍이', cat = '냥냥이')
        
        '''
        아버지 : 아부지
        어머니 : 어무이
        반려동물들..
        dog : 멍멍이
        cat : 냥냥이
        '''
        ```
        

### 3.4. 범위 (Scope)

- 파이썬에서의 범위
    - 범위 scope = 공간이라고 이해하자!
    - 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간은 global scope로 구분
    - scope
        - global scope : 코드 어디에서든 참조할 수 있는 공간
        - local scope : 함수가 만든 scope → 함수 내부에서만 참조 가능
    - variable
        - global variable : global scope에 정의된 변수
        - local variable : local scope에 정의된 변수
- 변수 수명주기 (lifecycle)
    - 변수는 각자의 수명주기가 존재
        - built-in scope : 파이썬이 실행된 이후부터 영원히 유지 (임의 변경 불가능)
            - 파이썬이 존재하는 한!
        - global scope : 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
            - 우리 프로그램이 살아있는 한!
        - local scope : 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지
            - 함수가 진행되는 한! (함수 끝나면 사라짐)
    - 예시
        
        ```python
        def func() :
            a = 20
            print('local', a) # local 20
        
        func()
        print('global', a) # NameError: name 'a' is not defined
        ```
        
        - a는 local scope에서만 존재
            - 함수 종료 후 수명주기 종료
- 이름 검색 규칙 (Name Resolution)
    - 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있음
    - LEGB Rule : 이름 찾는 순서 규칙
        - Local scope : 지역 범위 (현재 작업 중인 범위)
        - Enclosed scope : 지역 범위 한 단계 위 범위
        - Global scope : 최상단에 위치한 범위
        - Built-in scope : 모든 것을 담고 있는 범위
            - 정의하지 않고 사용할 수 있는 모든 것! ex. `print()`
    - 함수 내에서는 바깥 scope의 변수에 접근 가능하나 수정은 할 수 없음
    - 집 안에서 리모컨 찾는 과정이랑 같음 (내 방부터 거실까지 차례로 찾아감)
    - 예시
        
        ```python
        print(sum) # <built-in function sum>
        print(sum(range(2))) # 1
        sum = 5
        print(sum) # 5
        print(sum(range(2))) # TypeError: 'int' object is not callable
        ```
        
        - global scope 이름 공간의 sum 변수에 5가 할당
        - 이후 sum은 LEGB에 의해 Built-in scope의 내장 함수보다 global scope의 5가 먼저 탐색
        
        ```python
        a = 0
        b = 1
        def enclosed() :
            a = 10
            c = 3
            def local(c) :
                print(a, b, c)
            local(300)
            print(a, b, c)
        enclosed()
        print(a, b)
        
        '''
        10 1 300
        10 1 3
        0 1
        '''
        ```
        
- global문
    - 현재 코드 블록 전체에 적용되며, 나열된 식별자(이름)이 global variable임을 나타냄
    - global에 나열된 이름은
        - 같은 코드 블록에서 global 앞에 등장할 수 없음
        - prameter, for 루프 대상, 클래스/함수 등으로 정의되지 않아야 함
    - 예시
        
        ```python
        # 함수 내부에서 글로벌 변수 변경하기
        a = 10
        def fun1() :
            global a
            a = 3
        
        print(a) # 10
        func1()
        print(a) # 3
        ```
        
        - local scope에서 global 변수 값의 변경
        - global 키워드를 사용하지 않으면 local scope에 a 변수가 생성됨
    - 주의사항 : global 변수 사용 제한 예시
        
        ```python
        a = 10
        def func1() :
            print(a) # global a 선언 전에 사용
            global a
            a = 3
        
        print(a)
        func1()
        print(a)
        # SyntaxError: name 'a' is used prior to global declaration
        ```
        
        ```python
        a = 10
        def func1(a) :
            global a # parameter에 global 사용 불가
            a = 3
        
        print(a)
        func1()
        print(a)
        # SyntaxError: name 'a' is parameter and global
        ```
        
- nonlocal
    - global을 제외하고 가장 가까운 (둘러싸고 있는) scope의 변수를 연결하도록 함
    - nonlocal에 나열된 이름은
        - 같은 코드 블록에서 nonlocal 앞에 등장할 수 없음
        - prameter, for 루프 대상, 클래스/함수 등으로 정의되지 않아야 함
    - global과는 달리 이미 존재하는 이름과의 연결만 가능함
    - 예시
        
        ```python
        x = 0
        def func1() :
            x = 1
            def func2() :
                nonlocal x
                x = 2
            func2()
            print(x) # 2
        
        func1()
        print(x) # 0
        ```
        
        - enclosed scope(func1)의 변수 x의 변경
- nonlocal vs global
    - 선언된 적 없는 변수의 활용
        
        ```python
        # global
        def func1() :
            global out
            out = 3
        
        func1()
        print(out) # 3
        
        # nonlocal
        def func1() :
            def func2() :
                nonlocal y
                y = 2
            func2()
            print(y)
        
        func1() # SyntaxError: no binding for nonlocal 'y' found
        ```
        
        - nonlocal은 이름공간상에 존재하는 변수만 가능
- 함수의 범위 주의사항
    - 기본적으로 함수에서 선언된 변수는 local scope에 생성되며 함수 종료 시 사라짐
    - 해당 scope에 변수가 없는 경우 LEGB rule에 의해 이름 검색
        - 변수에 접근은 가능하지만 해당 변수를 수정할 수는 없음
            - 값을 할당하는 경우 해당 scope의 이름공간에 새롭게 생성됨
        - 그러니 함수 내에서 필요한 상위 scope 변수는 argument로 넘겨서 활용할 것
    - 상위 scope에 있는 변수를 수정하고 싶다면 global, nonlocal 키워드 활용 가능
        - 단, 코드가 복잡해지면서 변수의 변경을 추적하기 어렵고 예기치 못한 오류 발생
        - 가급적 사용하지 않는 것을 권장하며, 대신 argument로 넘기고 리턴 값 사용하세용

### 3.5. 응용

- 내장 함수
    - 파이썬 인터프리터에는 항상 사용할 수 있는 많은 함수와 형이 내장되어 있음
    - map
        - `map(function, iterable)`
        - 순회 가능한 데이터 구조의 모든 요소에 함수 적용하고, 그 결과를 map object로 반환
            
            ```python
            numbers = [1, 2, 3]
            result = map(str, numbers)
            print(result, type(result)) # <map object at 0x102baba00> <class 'map'>
            print(list(result)) # ['1', '2', '3']
            ```
            
    - filter
        - `filter(function, iterable)`
        - 순회 가능한 데이터 구조의 모든 요소에 함수 적용하고, 그 결과가 true인 것들을 filter object로 반환
            
            ```python
            def odd(n) :
                return n % 2
            numbers = [1, 2, 3]
            result = filter(odd, numbers)
            print(result, type(result)) # <filter object at 0x10482b9a0> <class 'filter'>
            print(list(result)) # [1, 3]
            ```
            
    - zip
        - `zip(*iterables)`
        - 복수의 iterable을 모아 튜플을 원소로 하는 zip object를 반환
            
            ```python
            girls = ['jane', 'ashley']
            boys = ['justin', 'eric']
            pair = zip(girls, boys)
            print(pair, type(pair)) # <zip object at 0x1009d9f00> <class 'zip'>
            print(list(pair)) # [('jane', 'justin'), ('ashley', 'eric')]
            ```
            
    - lambda 함수
        - `lambda [parameter] : 표현식`
        - 표현식을 계산한 결과값을 반환하는 함수로, 이름이 없는 함수여서 익명함수라고도 불림
        - 특징
            - return 문을 가질 수 없음
            - 간편 조건문 외 조건문이나 반복문을 가질 수 없음
        - 장점
            - 함수를 정의해서 사용하는 것보다 간결하게 사용 가능
            - def를 사용할 수 없는 곳에서도 사용 가능
            
            ```python
            # 삼각형의 넓이를 구하는 공식 - def
            def triangle_area(b, h) :
                return 0.5 * b * h
            print(triangle_area(5, 6)) # 15.0
            
            # 삼각형의 넓이를 구하는 공식 - 람다
            triangle_area = lambda b, h : 0.5 * b * h
            print(triangle_area(5, 6)) # 15.0
            ```
            
- 재귀함수 (recursive function)
    - 자기 자신을 호출하는 함수
    - 무한한 호출을 목표로 하는 것이 아니며, 알고리즘 설계 및 구현에서 유용하게 활용
        - 알고리즘 중 재귀함수로 로직을 표현하기 쉬운 경우가 있음 (예 : 점화식)
        - 변수의 사용이 줄어들며, 코드의 가독성이 높아짐
    - 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성
    - 예시 : 팩토리얼 구현
        - 재귀함수
            
            ```python
            def factorial(n) :
                if n == 0 or n == 1 :
                    return 1
                else :
                    return n * factorial(n - 1)
            print(factorial(4)) # 24
            ```
            
        - 반복문
            
            ```python
            def factorial(n) :
                result = 1
                while n > 1 :
                    result *= n
                    n -= 1
                return result
            
            print(fact(4)) # 24
            ```
            
        - 반복문 vs 재귀함수
            - 알고리즘 자체가 재귀적인 표현이 자연스러운 경우 재귀함수를 사용
            - 재귀 호출은 변수 사용을 줄여줄 수 있음
            - 재귀 호출은 입력 값이 커질수록 연산 속도가 오래 걸림
    - 주의사항
        - 재귀함수는 base case에 도달할 때까지 함수를 호출
        - 메모리 스택이 넘치게 되면(stack overflow) 프로그램이 동작하지 않음
        - 파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 1,000번으로, 호출 횟수가 이를 넘어가게 되면 Recursion Error 발생

## 4. 모듈

- 모듈과 패키지
    - 모듈 : 다양한 기능을 하나의 파일로
    - 패키지 : 다양한 파일을 하나의 폴더로
    - 라이브러리 : 다양한 패키지를 하나의 묶음으로
        - 라이브러리 vs 프레임워크
            - buzzword(정의가 명확하지 않은 주제)이기는 하나 라이브러리는 도구 느낌, 프레임워크는 알아서 일하는 포크레인 느낌
    - pip : 이것을 관리하는 관리자
    - 가상환경 : 패키지의 활용 공간

### 4.1. 모듈과 패키지

- 모듈과 패키지
    - 모듈
        - 특정 기능을 하는 코드를 파이썬 파일(.py) 단위로 작성한 것
    - 패키지
        - 특정 기능과 관련된 여러 모듈의 집합
        - 패키지 안에는 또 다른 서브 패키지를 포함
- 모듈과 패키지 불러오기
    - `import module`
    - `from module import var, function, Class`
    - `from module import *`
    - `from package import module`
    - `from package.module import var, function, Class`

### 4.2. 파이썬 표준 라이브러리

- 파이썬에 기본적으로 설치된 모듈과 내장 함수
    - [https://docs.python.org/ko/3/library/index.html](https://docs.python.org/ko/3/library/index.html)
- 파이썬 패키지 관리자 (pip)
    - PyPI(Python Package Index)에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템
    - 패키지 설치
        - 최신 버전 / 특정 버전 / 최소 버전을 명시하여 설치할 수 있음
        - 이미 설치되어 있는 경우 이미 설치되어 있음을 알리고 아무것도 하지 않음
        - 명령어 (bash, cmd 환경에서 사용)
            - `$ pip install SomePackage`
            - `$ pip install SomePackage==1.0.5`
            - `$ pip install SomePackage>=1.0.4`
    - 패키지 삭제
        - pip는 패키지 업그레이드를 하는 경우 과거 버전을 자동으로 지워줌
        - `$ pip uninstall SomePackage`
    - 패키지 목록 및 특정 패키지 정보
        - `$ pip list`
        - `$ pip show SomePackage`
    - 패키지 관리하기
        - 아래의 명령어들을 통해 패키지 목록을 관리하고 설치할 수 있음
        - 일반적으로 패키지를 기록하는 파일의 이름은 requirements.txt로 정의함
        - `$ pip freeze > requirements.txt`
            - 강의장에서 내가 설치한 라이브러리 목록 박제
        - `$ pip install -r requirements.txt`
            - 내 컴퓨터에 박제된 라이브러리 목록을 설치하는 방식으로 활용
    - 다양한 파이썬 프로젝트에서 사용됨

### 4.3. 사용자 모듈과 패키지

- 패키지
    - 패키지는 여러 모듈/하위 패키지로 구조화
    - `package.module`와 같이 활용
    - 모든 폴더에는 __ init__.py를 만들어 패키지로 인식
        - python 3.3부터는 파일이 없어도 되지만 하위 버전 호환 및 프레임워크 등에서의 동작을 위해 파일을 생성하는 것을 권장
- 패키지 만들기
    - 계산 기능이 들어간 calculator 패키지를 아래와 같이 구성
        - check.py에서 calculator의 tools.py의 기능을 사용
        - 폴더 구조
            - my_package/
                - __ init__.py
                - check.py
                - calculator/
                    - __ init__.py
                    - tools.py
    - 모듈 만들기 - calculator
        - calculator/tools.py에 add 함수와 minus 함수 작성
            
            ```python
            def add(num1, num2) :
                return num1 + num2
            
            def minus(num1, num2) :
                return num1 - num2
            ```
            
    - 모듈 활용하기 - check
        - 모듈을 활용하기 위해서는 import 문을 통해 가져옴
            
            ```python
            from calculator import tools
            
            print(dir(tools)) # tools에 어떤 변수와 메서드를 가지고 있는지 나열
            
            print(tools.add(3.5)) # 8
            print(tools.minus(3.5)) # -2
            ```
            

### 4.4. 가상환경

- 가상환경
    - 파이썬 표준 라이브러리가 아닌 외부 패키지와 모듈을 사용하는 경우 모두 pip를 통해 설치를 해야 함
    - 복수의 프로젝트를 하는 경우 버전이 상이할 수 있음
        - 과거 외주 프로젝트 - django 버전 2.x
        - 신규 회사 프로젝트 - django 버전 3.x
    - 이러한 경우 가상환경을 만들어 프로젝트별로 독립적인 패키지를 관리할 수 있음
    - 특정 디렉토리에 가상환경을 만들고, 고유한 파이썬 패키지 집합을 가질 수 있음
        - 특정 폴더에 가상환경이(패키지 집합 폴더 등) 있고 실행 환경(예 : bash)에서 가상환경을 활성화시켜 해당 폴더에 있는 패키지를 관리, 사용함
- 가상환경 생성
    - 가상환경을 생성하면, 해당 디렉토리에 별도의 파이썬 패키지가 설치됨
    - `$ python -m venv {이름}`
- 가상환경 활성화/비활성화
    - 활성화 : `source venv/Scripts/activate` (윈도우)
        - pip list 확인하면 가상환경 켜기 전후가 다름
    - 비활성화 : `$ deactivate` 명령어를 사용
- 가상환경 예시
    - 동일 컴퓨터에서 별도의 가상환경 존재
        - 각 프로젝트별 가상환경
        - venv 폴더별로 고유한 프로젝트가 설치됨