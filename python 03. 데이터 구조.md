# 3. 데이터 구조

---

- 데이터 구조의 활용
    - 데이터 구조를 사용하기 위해서는 메서드를 활용
        - 메서드 : 클래스 내부에 정의한 함수 (함수와 동일)
    - 데이터 구조.메서드() 형태로 활용 (주어.동사()라고 생각하세요~)
- 파이썬 공식 문서 표기법 (배커스-나우르 표기법)
    - ex. `str.replace(old, new[, count])`
        - old, new는 필수, [, count]는 선택

## 1. 순서가 있는 데이터 구조

### 1.1. 문자열

- 문자열 (String Type)
    - 문자들의 나열 (sequence of characters)
    - 모든 문자는 str 타입 (변경 불가능한 immutable)
- 문자열 조회/탐색 및 검증 메서드
    - `s.find(x)`
        - x의 첫 번째 위치를 반환. 없으면 -1을 반환
        - 오류 나지 않음!
        
        ```python
        print('apple'.find('p')) # 1
        print('apple'.find('k')) # -1
        ```
        
    - `s.index(x)`
        - x의 첫 번째 위치를 반환. 없으면 오류 발생
        
        ```python
        print('apple'.index('p')) # 1
        print('apple'.index('k')) # ValueError: substring not found
        ```
        
    - `s.startswith(x)` / `s.endswith(x)`
        - 문자열이 x로 시작하면/끝나면 True를 반환
        - [PEP8 파이썬 스타일 가이드](https://www.python.org/dev/peps/pep-0008/)에서는 접두/접미 문자를 검색 시, 화이트 스페이스나 인코딩 문제를 피하기 위해 문자열 분할보다 startswith, endswith
        를 권장
        
        ```python
        a = 'hello python!'
        print(a.startswith('hello')) # True
        print(a.endswith('python')) # False
        ```
        
- 문자열 관련 검증 메서드
    - `s.isalpha()`
        - 알파벳 문자 여부
        - 단순 알파벳이 아닌 유니코드 상 letter (한국어도 포함)
        
        ```python
        print('abc'.isalpha()) # True
        print('ㄱㄴㄷ'.isalpha()) # True
        print('hi...'.isalpha()) # False
        ```
        
    - `s.isspace()`
        - 문자열이 공백으로 이루어져 있는지 여부
        
        ```python
        a = '    n'
        b = '\n \t '
        print(a.isspace()) # False
        print(b.isspace()) # True
        ```
        
    - `s.isupper()`
        - 대문자 여부
        
        ```python
        print('Ab'.isupper()) # False
        ```
        
    - `s.islower()`
        - 소문자 여부
        
        ```python
        print('ab'.islower()) # True
        ```
        
    - `s.istitle()`
        - 타이틀 형식 여부 (첫번째 대문자, 다음부터 소문자 형식인지)
        
        ```python
        print('Title Title'.istitle()) # True
        ```
        
- 문자열 관련 검증 메서드 (숫자)
    - `isdecimal()` ⊆ `isdigit()` ⊆ `isnumeric()`
    - `isdecimal()` : 주어진 문자열이 int형으로 변환이 가능한지 알아내는 함수이기 때문에 특수문자 중 숫자모양을 숫자로 치지 않음
    - `isdigit()` : 글자가 숫자 모양으로 생겼으면 무조건 True
    - `isnumeric()` : 숫자값 표현에 해당하는 문자열까지 True (제곱근, 분수, 거듭제곱 특수문자도 True)
    
    ```python
    print('⅔'.isdecimal()) # False
    print('⅔'.isdigit()) # False
    print('⅔'.isnumeric()) # True
    
    print('④⑤'.isdecimal()) # False
    print('④⑤'.isdigit()) # True
    print('④⑤'.isnumeric()) # True
    ```
    
- 문자열 변경 메서드
    - `s.replace(old, new[, count])`
        - 바꿀 대상 글자를 새로운 글자로 바꿔서 반환
        - count를 지정하면 해당 개수만큼만 시행
        
        ```python
        print('coone'.replace('o', 'a')) # canne
        print('wooooowoo'.replace('o', '!', 2)) #w!!ooowoo
        ```
        
    - `s.strip([chars])`
        - 공백이나 특정 문자를 제거 (strip, lstrip, rstrip)
        - 문자열을 지정하지 않으면 공백을 제거함
        
        ```python
        print('    wow\n'.strip()) # 'wow'
        print('    wow\n'.rstrip()) # '    wow'
        print('!hihi'.lstrip('!')) # 'hihi'
        ```
        
    - `s.split(sep = None, maxsplit = -1)`
        - 공백이나 특정 문자를 기준으로 문자열 분리하여 리스트로 반환
        - sep이 None이거나 지정되지 않으면 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음
        - maxsplit이 -1인 경우에는 제한이 없음
        
        ```python
        print('a,b,c'.split('-')) # ['a,b,c']
        print('a b c'.split(' ')) # ['a', 'b', 'c']
        ```
        
    - `‘seperator’.join([iterable])`
        - 구분자로 iterable을 합쳐 문자열 반환
        - 구분자가 join 메서드를 제공하는 문자열임!!!
        - iterable에 문자열이 아닌 값이 있으면 TypeError 발생
        
        ```python
        print('!'.join('ssafy')) # 's!s!a!f!y'
        print(' '.join(['3', '5'] # '3 5'
        ```
        
    - `s.capitalize()`
        - 가장 첫 번째 글자를 대문자로 변경
    - `s.title()`
        - 어퍼스트로피와 공백을 기준으로 각 단어의 첫글자는 대문자로, 나머지는 소문자로 변환
    - `s.upper()`
        - 모두 대문자로 변경
    - `s.lower()`
        - 모두 소문자로 변경
    - `s.swapcase()`
        - 대, 소문자 서로 변경
- 문자열은 immutable(불변형)인데, 문자열 변경이 되는 이유?
    - 기존의 문자열을 변경하는 게 아니라, 변경된 문자열을 새롭게 만들어서 반환
        - ex. replace, strip, title 등
        
        ```python
        word = 'ssafy'
        print(word) # ssafy
        print(id(word)) # 4347144816
        
        word = 'test'
        print(word) # test
        print(id(word)) # 4343637424 -> 문자열이 바뀐 것이 아니라 새로 생성된 것
        ```
        

### 1.2. 리스트

- 값 추가 및 삭제 메서드
    - `L.append(x)`
        - 리스트 마지막에 항목 x를 추가
        - `L[len(L):] = [x]`와 동일
        
        ```python
        cafe = ['starbucks', 'tomntoms']
        print(cafe) # ['starbucks', 'tomntoms']
        print(id(cafe)) # 4347140800
        
        cafe.append('banapresso')
        print(cafe) # ['starbucks', 'tomntoms', 'banapresso']
        print(id(cafe)) # 4347140800 -> id 동일
        ```
        
    - `L.insert(i, x)`
        - 리스트 인덱스 i에 항목 x를 삽입
        - 리스트 길이보다 큰 경우 맨 뒤에 추가
        
        ```python
        cafe.insert(2, 'start')
        print(cafe) # ['starbucks', 'tomntoms', 'start', 'banapresso']
        
        cafe.insert(10000, 'end')
        print(cafe) # ['starbucks', 'tomntoms', 'start', 'banapresso', 'end]
        ```
        
    - `L.extend(iterable)`
        - 리스트에 iterable의 항목을 추가함 (+=와 같은 기능)
        - `L[len(L):] = iterable`와 동일
        
        ```python
        cafe.extend(['coffee'])
        print(cafe) # ['starbucks', 'tomntoms', 'start', 'banapresso', 'end', 'coffee']
        
        cafe.extend('cup')
        print(cafe) # ['starbucks', 'tomntoms', 'start', 'banapresso', 'end', 'coffee', 'c', 'u', 'p']
        ```
        
    - `L.remove(x)`
        - 리스트 가장 왼쪽에 있는 항목 x를 제거
        - 항목이 존재하지 않을 경우 ValueError
        
        ```python
        numbers = [1, 2, 3, 'hi']
        print(numbers) # [1, 2, 3, 'hi']
        
        numbers.remove('hi')
        print(numbers) # [1, 2, 3]
        
        numbers.remove('ho')
        print(numbers) # ValueError: list.remove(x): now in list
        ```
        
    - `L.pop(i)`
        - 리스트의 인덱스 i에 있는 항목을 반환 후 제거
        - i가 지정되지 않으면 마지막 항목을 삭제하고 반환
        
        ```python
        numbers = [1, 2, 3, 'hi']
        word = numbers.pop()
        print(word) # hi
        print(numbers) # [1, 2, 3]
        
        word2 = numbers.pop(0)
        print(word2) # 1
        print(numbers) # [2, 3]
        ```
        
    - `L.clear()`
        - 모든 항목을 삭제함
        
        ```python
        numbers.clear()
        print(numbers) # []
        ```
        
- 탐색 및 정렬 메서드
    - `L.index(x)`
        - 리스트에 있는 항목 중 가장 왼쪽에 있는 항목 x의 인덱스를 반환
        - 없는 경우 ValueError
        
        ```python
        numbers = [1, 2, 3, 4]
        print(numbers.index(3)) # 2
        print(numbers.index(100)) # ValueError: 100 is not in list
        ```
        
    - `L.count(x)`
        - 리스트에서 항목 x가 몇 개 존재하는지 개수를 반환
        
        ```python
        numbers = [1, 2, 3, 1, 1, 1, 2, 2]
        print(numbers.count(1)) # 4
        print(numbers.count(100)) # 0
        ```
        
    - `L.sort()`
        - 원본 리스트 정렬 후 None 리턴
            - `sorted()`의 경우에는 원본은 그대로 두고 복사해서 새로운 리스트 생성
        - 파라미터 : key, reverse
        
        ```python
        numbers = [3, 2, 5, 7]
        result = numbers.sort()
        print(numbers, result) # [2, 3, 5, 7] None
        
        numbers = [3, 2, 6, 8]
        # result = numbers.sorted() -> 문법 이거 아니에요!
        result = sorted(numbers)
        print(numbers, result) # [3, 2, 6, 8] [2, 3, 6, 8]
        ```
        
    - `L.reverse()`
        - 리스트를 거꾸로 뒤집음 (정렬하는 것이 아님)
        - 원본 리스트 정렬 후 None 리턴
            - `reversed()`는 원본은 그대로 두고 복사해서 새로운 리스트 생성
        - 파라미터 : key, reverse
        
        ```python
        numbers = [3, 2, 5, 1]
        result = numbers.reverse()
        print(numbers, result) # [1, 5, 2, 3] None
        ```
        

### 1.3. 튜플

- 튜플 관련 메서드
    - 튜플은 변경할 수 없기 때문에 값에 영향을 미치지 않는 메서드만을 지원
        - index, count
    - 리스트 매서드 중 항목을 변경하는 메서드들을 제외하고 대부분 동일
    
    ```python
    day_name = ('월', '화', '수', '목', '금')
    
    print(day_name[-3]) # 수
    print(day_name * 2) # ('월', '화', '수', '목', '금', '월', '화', '수', '목', '금')
    print(id(day_name)) # 4343472880
    
    day_name += False, True
    print(day_name) # ('월', '화', '수', '목', '금', False, True)
    print(id(day_name)) # 4342708640 -> 변경
    ```
    

### 1.4. 연산자

- 멤버십 연산자
    - in을 통해 특정 요소가 속해 있는지 여부 확인
    
    ```python
    print('apple' in 'a') # False
    print('a' in 'apple') # True
    print('서순' in ['서순', '요까일엇무']) # True
    ```
    
    - 포함 여부 확인
        - `in`
        - `not in`
- 시퀀스형 연산자
    - 산술연산자 (+)
        - 시퀀스 간의 concatenation(연결/인쇄)
    - 반복연산자 (*)
        - 시퀀스를 반복

## 2. 순서가 없는 데이터 구조

### 2.1. 셋

- 셋 자료형
    - 순서가 없기 때문에 인덱스를 이용한 접근 불가능
    - 담고 있는 요소를 삽입, 변경, 삭제 가능 → 가변 자료형 (mutable)
- 추가 및 변경 메서드
    - `s.add(x)`
        - 항목 x가 셋 s에 없다면 추가
        
        ```python
        a = {'a', 'b', 'c'}
        a.add('d')
        print(a) # {'a', 'd', 'c', 'b'}
        ```
        
    - `s.update(t)`
        - 셋 t에 있는 모든 항목 중 셋 s에 없는 항목을 추가
        - 반드시 iterable 데이터 구조 전달해야 함
        
        ```python
        a = {'사과', '바나나', '수박'}
        a.update(['딸기', '바나나', '참외'])
        print(a) # {'참외', '사과', '딸기', '바나나', '수박'}
        ```
        
- 요소 삭제 메서드
    - `s.remove(x)`
        - 항목 x를 셋 s에서 삭제
        - 항목이 존재하지 않을 경우 KeyError
        
        ```python
        a.remove('딸기')
        print(a) # {'참외', '사과', '참', '바나나', '수박'}
        
        a.remove('딸기')
        print(a) # KeyError: '딸기'
        ```
        
    - `s.discard(x)`
        - 항목 x가 셋 s에 있는 경우, 항목 x를 셋 s에서 삭제
        - 에러 나지 않음!
        
        ```python
        print(a) # {'참외', '사과', '바나나', '수박'}
        
        a.discard('사과')
        print(a) # {'참외', '바나나', '수박'}
        
        a.discard('사과')
        print(a) # {'참외', '바나나', '수박'}
        ```
        
    - `s.pop()`
        - 셋 s에서 랜덤하게 항목을 반환하고, 해당 항목을 제거
        - set이 비어있을 경우 KeyError
        
        ```python
        a = {'사과', '바나나', '수박'}
        element = a.pop()
        print(a) # ex. {'바나나', '수박'}
        print(element) # ex. 사과
        
        b = {}
        element = b.pop() # TypeError: pop expected at least 1 argument, got 0
        print(b) # {}
        print(element) # ex. 사과
        ```
        
    - `s.clear()`
        - 모든 항목을 제거
        
        ```python
        a.clear()
        print(a) # set()
        ```
        
- 집합 관련 메서드
    - `s.isdisjoint(t)`
        - 셋 s가 셋 t의 서로 같은 항목을 하나라도 갖고 있지 않은 경우 True 반환 (서로소)
    - `s.issubset(t)`
        - 셋 s가 셋 t의 하위 셋인 경우 True 반환
    - `s.issuperset(t)`
        - 셋 s가 셋 t의 상위 셋인 경우 True 반환
    
    ```python
    a = {'사과', '바나나', '수박'}
    b = {'포도', '망고'}
    c = {'사과', '포도', '망고', '수박', '바나나'}
    
    print(a.isdisjoint(b)) # a와 b가 서로소인가? True
    print(b.issubset(c)) # b가 c의 하위 셋인가? True
    print(a.issuperset(c)) # a가 c의 상위 셋인가? False
    ```
    
- 기타 메서드
    - `s.copy()`
        - 셋의 얕은 복사본을 반환

### 2.2. 딕셔너리

- 조회 메서드
    - `d.get(key[, default])`
        - key를 통해 value를 가져옴
        - KeyError가 발생하지 않으며, 디폴트 값을 설정할 수 있음 (기본 None)
    - `d.setdefault(key[, default])`
        - key를 통해 value를 가져옴 (`get()` 메서드와 비슷!)
        - key가 딕셔너리에 없을 경우, default 값을 갖는 key 를 삽입한 후 default 를 반환
            - 만일 default가 주어지지 않을 경우, None 반환
    - `d.keys()`
        - 딕셔너리의 모든 key 가져움
    - `d.values()`
        - 딕셔너리의 모든 value 가져움
    - `d.items()`
        - 딕셔너리의 모든 key - value 쌍 가져움
- 추가 및 삭제 메서드
    - `d.pop(key[, default])`
        - key가 딕셔너리에 있으면 제거하고 해당 값을 반환
        - 그렇지 않으면 default 반환
        - default 값이 없으면 KeyError
        
        ```python
        my_dict = {'apple' : '사과', 'banana' : '바나나'}
        data = my_dict.pop('apple')
        print(data, my_dict) # 사과 {'banana': '바나나'}
        
        data = my_dict.pop('apple', 0)
        print(data, my_dict) # 0 {'banana': '바나나'}
        ```
        
    - `d.update([other])`
        - 값을 제공하는 key, value로 덮어씀
        - 다른 딕셔너리나 key/value 쌍으로 되어있는 모든 iterable 사용 가능
        
        ```python
        my_dict = {'apple' : '사', 'banana' : '바나나'}
        my_dict.update(apple = '사과')
        print(my_dict) # {'apple': '사과', 'banana': '바나나'}
        ```
        
- 기타 메서드
    - `d.clear()`
        - 모든 항목을 제거
    - `d.copy()`
        - 딕셔너리 d의 얕은 복사본을 반환
    

## 3. 얕은 복사와 깊은 복사

- 데이터 분류
    - mutable과 immutable에 따라 복사가 달라짐
    - mutable : list, dict, set
    - immutable : 리터럴(number, string, bool), `range()`, `tuple()`, `frozenset()`
        - `frozenset()` : set과 거의 동일하나 immutable함
- 복사 방법
    - 할당 (Assignment)
    - 얕은 복사 (Shallow copy)
    - 깊은 복사 (Deep copy)
- 할당
    - 대입 연산자 (=)
        
        ```python
        original_list = [1, 2, 3]
        copy_list = original_list
        print(original_list, copy_list) # [1, 2, 3] [1, 2, 3]
        
        copy_list[0] = 'hello'
        print(original_list, copy_list) # ['hello', 2, 3] ['hello', 2, 3]
        ```
        
        - 대입 연산자를 통한 복사는 해당 객체에 대한 참조를 복사
        - 해당 주소의 일부 값을 변경하는 경우 이를 참조하는 모든 변수에 영향
- 얕은 복사
    - 슬라이스 연산자 활용하여 같은 원소를 가진 리스트지만 연산된 결과를 복사 (다른 주소)
        
        ```python
        a = [1, 2, 3]
        b = a[:]
        print(a, b) # [1, 2, 3] [1, 2, 3]
        
        b[0] = 5
        print(a, b) # [1, 2, 3] [5, 2, 3]
        ```
        
    - `list()` 함수 활용도 가능하며 동일함
    - 주의사항 : 복사하는 리스트의 원소가 주소를 참조하는 경우
        
        ```python
        a = [1, 2, ['a', 'b']]
        b = a[:]
        print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]
        
        b[2][0] = 0
        print(a, b) # [1, 2, [0, 'b']] [1, 2, [0, 'b']]
        ```
        
- 깊은 복사
    - 새로운 객체를 만들고 원본 객체 내에 있는 객체에 대한 복사를 재귀적으로 삽입
    - 내부에 있는 모든 객체까지 새롭게 값이 변경
        
        ```python
        import copy
        
        a = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
        b = copy.deepcopy(a)
        print(a, b)
        # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
        # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
        
        b[0][2] = 'hello'
        print(a, b)
        # [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
        # [[1, 2, 'hello'], [4, 5, 6], [7, 8, 9]]
        ```