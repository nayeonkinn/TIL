## 1. 문자열

### 1.1. 문자의 표현

- 컴퓨터에서의 문자표현
    - 글자 A를 메모리에 저장하기 위해서는 각 문자에 대해서 대응되는 숫자를 정해 놓고 이것을 메모리에 저장하는 방법 사용
    - 영어의 경우 대소문자가 총 52개이므로 6비트(64가지)면 모두 표현 가능 → 코드체계
        - 000000 : ‘a’, 000001 : ‘b’
    - 미국은 지역 별로 코드체계를 정해놓고 사용했지만 네트워크의 발전으로 서로 정보를 주고받게 되자 정보를 달리 해석하는 문제가 발생
        - 인터넷은 미국에서 발전함
    - 이에 혼동을 피하고자 1967년 미국에서 문자 인코딩 표준 ASCII(American Standard Code for Information Interchange) 제정
- ASCII
    - 7비트 인코딩으로 128문자 표현
    - 33개의 출력 불가능한 제어 문자 + 95개의 출력 가능한 (공백 포함) 문자
- 확장 ASCII
    - 표준 문자 이외의 악센트 문자, 도형 문자, 특수 문자, 특수 기호 등 부가적인 문자를 128개 추가할 수 있게 하는 부호
    - 표준 아스키는 7비트 사용하는 데 비해 확장 아스키는 8비트 모두 사용
    - 컴퓨터 생산자와 소프트웨어 개발자가 다양한 문자에 할당할 수 있음. 이렇게 할당된 확장 부호는 표준 아스키와 같이 서로 다른 프로그램이나 컴퓨터 사이에 교환되지 못함
        - 표준 아스키는 마이크로컴퓨터 하드웨어 및 소프트웨어 사이에서 세계적으로 통용되는 데 비해, 확장 아스키는 프로그램이나 컴퓨터 또는 프린터가 그것을 해독할 수 있도록 설계되어 있어야만 올바로 해독될 수 있음
- 유니코드
    - 오늘날 대부분의 컴퓨터는 문자를 읽고 쓰는 데에 ASCII 형식 사용
    - 미국 뿐 아니라 각 나라에서도 컴퓨터가 발전했으며 각 국가들은 자국의 문자를 표현하기 위해 코드체계 사용
        - 우리나라도 한글 코드체계 사용 (조합형, 완성형)
    - 인터넷이 전 세계로 발전하면서 자국의 코드체계를 타 국가가 가지고 있지 않으면 해석 오류 발생 → 다국어 처리 표준인 유니코드 등장
    - Character set : 유니코드를 저장하는 변수 크기 정의
        - UCS-2 (Universal Character Set 2)
        - UCS-4 (Universal Character Set 4)
    - 단 바이트 순서에 대해 표준화하지 못하여 파일 인식 시 해당 파일이 UCS-2인지 UCS-4인지 인식하고 각 경우를 구분해서 다르게 구현해야 하는 문제 발생 → 외부 인코딩의 필요성
- 유니코드 인코딩 (UTF : Unicode Transformation Format)
    - UTF-8 (in web)
        - MIN : 8bit, MAX : 32bit (1byte * 4)
    - UTF-16 (in windows, java)
        - MIN : 16bit, MAX : 32bit (2byte * 2)
    - UTF-32 (in unix)
        - MIN : 32bit, MAX : 32bit (4byte * 1)
- Python 인코딩
    - 2.x 버전 : ASCII (첫 줄에 utf-8 명시)
    - 3.x 버전 : 유니코드 (생략 가능)
    - 다른 인코딩 방식으로 처리 시 첫 줄에 원하는 인코딩 방식 지정

### 1.2. 문자열 처리

- 문자열 분류
    - fixed length
    - variable length
        - length controlled - 자바 언어에서의 문자열
        - delimited - C 언어에서의 문자열
- C 언어에서 문자열 처리
    - 문자열은 문자들의 배열 형태로 구현된 응용 자료형
    - 문자 배열에 문자열을 저장할 때는 항상 마지막에 끝을 표시하는 널문자(`\0`)를 넣어줘야 함
      
        ```c
        char ary[] = {'a', 'b', 'c', '\0'};
        char ary[] = "abc";
        ```
        
    - 문자열 처리에 필요한 연산을 함수 형태로 제공
        - `strlen()`, `strcpy()`, `strcmp()`, …
- `strlen()` 함수 구현
  
    ```python
    def strlen(a):
        i = 0
        while a[i] != '\0':
            i += 1
        return i
    
    a = ['a', 'b', 'c', '\0']
    print(strlen(a))
    ```
    
- 자바에서의 문자열 처리 (객체지향 언어)
    - 문자열 데이터를 저장, 처리해주는 클래스 제공
    - string 클래스 사용
        - `String str="abc";` 또는 `String str = new String("abc")`
        - java.lang.String 클래스에는 기본적인 객체 메타 데이터 외에도 네 가지 필드들이 포함되어 있음
            - hash값 - hash
            - 문자열의 길이 - count
            - 문자열 데이터의 시작점 - offset
            - 실제 문자열 배열에 대한 참조 - value
    - 문자열 처리에 필요한 연산을 연산자, 메소드 형태로 제공
        - `+`, `length()`, `replace()`, `split()`, `substring()`, …
- Python에서의 문자열 처리
    - char 타입 없음
    - 텍스트 데이터의 취급 방법이 통일되어 있음
    - 문자열 기호
        - ‘(홑따옴표), “(쌍따옴표), ‘’’(홑따옴표 3개), “””(쌍따옴표 3개)
        - + 연결
        - * 반복
    - 문자열은 시퀀스 자료형으로 분류되어 인덱싱, 슬라이싱 연산 사용 가능
    - 문자열 클래스에서 제공되는 메소드
        - `replace()`, `split()`, `isalpha()`, `find()`
    - 문자열은 튜플과 같이 요소값을 변경할 수 없음 (immutable)
- C, 자바, 파이썬 문자열 처리 차이점
    - C : 아스키 코드로 저장
      
        ```c
        char *name = "홍길동";
        int count = strlen(name);
        printf("%d", count); // 6
        ```
        
    - 자바 : 유니코드(UTF-16, 2byte)로 저장
      
        ```java
        String name = "홍길동"
        System.out.println(name.length()); // 3
        ```
        
    - 파이썬 : 유니코드(UTF-8)로 저장
      
        ```python
        name = "홍길동"
        print(len(name)) # 3
        ```
    
- 문자열 비교
    - C : `strcmp()` 함수 제공
    - 자바 : `equals()` 메서드 제공
        - 문자열 비교에서 `==` 연산은 메모리 참조가 같은지를 묻는 것
    - 파이썬 : `==` 연산자, `is` 연산자 제공
        - `==` 연산자는 내부적으로 특수 메서드 `__eq__()`를 호출
        
        ```python
        s1 = 'abc'
        s2 = 'abc'
        s3 = 'def'
        s4 = s1
        s5 = s1[:2] + 'c'
        
        print(s1 == s2)  # T
        print(s1 == s3)  # F
        print(s1 == s4)  # T
        print(s1 == s5)  # T
        
        print(s1 is s2)  # True
        print(s1 is s3)  # False
        print(s1 is s4)  # True
        print(s1 is s5)  # False
        
        print(id(s1))  # 2102748036912
        print(id(s2))  # 2102748036912 -> 내용이 같으면 같은 주소 참조
        ```
    
- `strcmp()` 함수 구현
  
    ```python
    # 방법 1
    def my_strcmp(str1, str2):
        i = 0
        while str1[i] != '\0' or str2[i] != '\0':
            if str1[i] != str2[i]:
                return 1 if ord(str1[i]) - ord(str2[i]) > 0 else -1
            i += 1
        return 0
    
    print(my_strcmp('ad\0', 'abcd\0'))
    
    # 방법 2
    def my_strcmp(str1, str2):
        if str1 == str2:
            return 0
        elif str1 > str2:
            return 1
        else:
            return -1
    
    print(my_strcmp('ad\0', 'abcd\0'))
    ```
    
- 문자열 숫자를 정수로 변환
    - C : `atoi()` 함수 제공 (역함수 `itoa()`)
    - 자바 : 숫자 클래스의 `parse` 메서드 제공 (역함수 `toString()` 메서드)
        - ex. `Integer.parseInt(String)`
    - 파이썬 : 숫자와 문자 변환 함수 제공
        - ex. `int("123")`, `float("3.14")`, `str(123)`, `repr(123)`
- `atoi()` 함수 구현 (`int()` 함수와 동일)
  
    ```python
    def atoi(s):
        i = 0
        for x in s:
            i = i * 10 + ord(x) - ord('0')
        return i
    
    s = '123'
    a = atoi(s)
    print(a + 1) # 124
    ```
    

### 1.3. 연습 문제 : 문자열 뒤집기

```python
s = 'Reverse this strings'

# 방법 1
reverse = ''
for i in range(len(s) - 1, -1, -1):
    reverse += s[i]
print(reverse) # sgnirts siht esreveR

# 방법 2
s = list(s)
for i in range(len(s) // 2):
  s[i], s[-i - 1] = s[-i - 1], s[i]
reverse = ''.join(s)
print(reverse)
```

### 1.4. 연습 문제 : `itoa()` 구현

```python
def itoa(num):
    if num == 0:
        return('0')
        
    char = ''
    plus = True
    if num < 0:
        plus = False
        num *= -1

    while num > 0:
        char += chr(num % 10 + ord('0'))
        num //= 10
    
    if plus:
        return(char[::-1])
    else:
        return('-' + char[::-1])

print(itoa(123)) # 123
print(itoa(-123)) # -123
print(itoa(0)) # 0
```

## 2. 패턴 매칭

- 패턴 매칭 알고리즘 비교
    - 찾고자 하는 문자열 패턴의 길이 m, 총 문자열 길이 n
    
    | 알고리즘 | 수행시간 |
    | --- | --- |
    | 고지식한 패턴 검색 알고리즘 | O(mn) |
    | 카프-라빈 알고리즘 | O(n) |
    | KMP 알고리즘 | O(n) |
    | 보이어-무어 알고리즘 | 최악의 경우 O(mn), 일반적으로 O(n) ↓ |

### 2.1. 고지식한 알고리즘 (Brute Force)

- 특징
    - 본문 문자열을 처음부터 끝까지 차례대로 순회하면서 패턴 내의 문자들을 일일이 비교하는 방식으로 동작
- 시간 복잡도
    - 최악의 경우 텍스트의 모든 위치에서 패턴을 비교해야 하므로 O(MN)
    - 비교 횟수를 줄이는 방법? → KMP 알고리즘
- 코드 구현
  
    ```python
    p = 'is' # 찾을 패턴
    t = 'This is a book~!' # 전체 텍스트
    
    def BruteForce(p, t):
        i = 0 # t 인덱스
        j = 0 # p 인덱스
        while i < len(t) and j < len(p):
            if t[i] != p[j]:
                i -= j
                j = -1
            i += 1
            j += 1
        if j == len(p):
            return i - len(p)
        else:
            return -1
    ```
    

### 2.2. KMP 알고리즘

- 특징
    - 불일치가 발생한 텍스트 스트링의 앞 부분에 어떤 문자가 있는지를 미리 알고 있으므로, 불일치가 발생한 앞 부분에 대하여 다시 비교하지 않고 매칭을 수행
    - 패턴을 전처리하여 배열 next[M]을 구해서 잘못된 시작을 최소화함
        - next[M] : 불일치가 발생했을 경우 이동할 다음 위치
- 시간 복잡도
    - O(M + N)
- 코드 구현
  
    ```python
    # T : target / P : pattern
    
    def pre_process(P):
    
        lps = [0] * len(P)
    
        # lps를 만들기 위한 prefix에 대한 idx,
        j = 0
        
        """
        i : pattern에서 지나가고 있는 id
        j : 지나가고 있는 idx와 pattern의 앞부분과 같은 부분에 대한 idx
        """
    
        # 처음부터 끝까지 순회를 돌면서
        for i in range(1, len(P)):
            # i 와 j가 같으면 lps의 i 자리에 j+1을 넣어줍니다. (prefix idx 위치에 있는 char와 같으면 lps에 숫자 추가)
            if P[i] == P[j]:
                lps[i] = j + 1
                j += 1
            # 다르다면, j를 초기화 해주어 pattern의 가장 처음부터 인식하도록 합니다.
            # 그 자리에서 기존의 j자리(비교를 하고 있던 자리)가 아닌 pattern 처음으로 돌아가 비교를 해줍니다.
            else:
                j = 0
                if P[i] == P[j]:
                    lps[i] = j + 1
                    j += 1
        return lps
    
    def KMP(T, P):
    
        lps = pre_process(P)
    
        # i : text를 순회하는 index
        i = 0
        # j : pattern을 순회하는 index
        j = 0
    
        position = -1
        while i < len(T):
            # 같으면 이동
            if P[j] == T[i]:
                i += 1
                j += 1
            else:
                # 다른데 j가 0이 아니라면, i의 자리는 유지한 채 j만 이동하여 비교 시작
                if j != 0:
                    j = lps[j - 1]
                # 다른데 j가 0이라면, i를 한칸만 이동하여 처음부터 진행하듯이 진행
                else:
                    i += 1
            # j가 pattern을 다 순회하면 성공
            if j == len(P):
                position = i - j
                break
        return position
    
    T = 'abcdabeeababcdabcef'
    P = 'eaba'
    
    position = KMP(T, P)
    print(position)
    ```
    

### 2.3. 보이어-무어 알고리즘

- 특징
    - 오른쪽에서 왼쪽으로 비교
    - 대부분의 상용 소프트웨어에서 채택하고 있는 알고리즘
    - 패턴의 오른쪽 끝에 있는 문자가 불일치하고 이 문자가 패턴 내에 존재하지 않는 경우, 이동 거리는 패턴의 길이만큼이 됨
    - 오른쪽 끝에 있는 문자가 불일치하고 이 문자가 패턴 내에 존재하는 경우 일치하는 문자를 찾아서 n칸 점프
    - 앞의 두 알고리즘과 다르게 텍스트 문자를 다 보지 않아도 됨
- 시간 복잡도
    - 최악의 경우 O(mn), 입력에 따라 다르지만 일반적으로 O(n)보다 적음

### 2.4. 연습 문제 : 고지식한 방법 구현

```python
p = 'python'
t = 'c and python'

def BruteForce(p, t):
    i = 0
    j = 0

    while i < len(t) and j < len(p):
        if t[i] != p[j]:
            i -= j
            j = -1
        i += 1
        j += 1
    if j == len(p):
        return len(t) - j
    else:
        return -1

print(BruteForce(p, t)) # 6
```

## 3. 문자열 암호화

### 3.1. 시저(카이사르) 암호

- 특징
    - 줄리어스 시저가 사용했다고 하는 암호
        - 기원전 100년경 로마에서 활약한 장군
    - 평문에서 사용되고 있는 알파벳을 일정한 문자 수만큼 평행이동시킴으로써 암호화 진행
    - 1만큼 이동했을 때 1을 키값이라 함

### 3.2. 단일 치환 암호

- 특징
    - 문자 변환표를 이용한 암호화
    - 단순한 카이사르 암호화보다 훨씬 강력함
    - 복호화하기 위해서는 모든 키의 조합 필요
    - 암호화 키의 총 수는 26!
        - 1초에 10억 개의 키를 적용하는 속도로 조사해도 120억년 이상의 시간 소요

### 3.3. bit열 암호화

- 특징
    - 배타적 논리합(exclusive-or) 연산 사용
      
      
        | x | XOR | y |
        | --- | --- | --- |
        | 0 | 0 | 0 |
        | 0 | 1 | 1 |
        | 1 | 0 | 1 |
        | 1 | 1 | 0 |

## 4. 문자열 압축

### 4.1. Run-length encoding 알고리즘

- 특징
    - 저장소의 크기를 줄이며 정확한 정보를 저장하는 방법
    - 같은 값이 몇 번 반복되는가를 나타냄으로써 압축
    - 이미지 파일포맷 중 BMP 파일포맷의 압축 방법
    - 더 효율적이고 일반적인 압축방법 → 허프만 코딩 알고리즘