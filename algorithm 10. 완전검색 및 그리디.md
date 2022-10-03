### 1. 반복과 재귀

- 반복을 이용한 선택정렬 구현
  
    ```python
    def selection_sort(A):
        n = len(A)
        for i in range(0, n - 1):
            minI = i
            for j in range(i + 1, n):
                if A[j] > A[minI]:
                    minI = j
            A[minI], A[i] = A[i], A[minI]
    
    A = [1, 2, 3, 4, 5]
    selection_sort(A)
    print(A) # [5, 4, 3, 2, 1]
    ```
    
- 재귀를 이용한 팩토리얼 구현
  
    ```python
    def fact(n):
        if n <= 1: # basis part
            return 1
        else: # inductive part
            return n * fact(n - 1)
    
    print(fact(5) # 120)
    ```
    
- 재귀를 이용한 $2^k$ 연산
  
    ```python
    def power_of_2(k):
        if k == 0:
            return 1
        else:
            return 2 * power_of_2(k - 1)
    
    print(power_of_2(3)) # 8
    ```
    
- 반복을 이용한 $2^k$ 연산
  
    ```python
    def power_of_2(k):
        i = 0
        power = 1
        while i < k:
            power = power * 2
            i += 1
        return power
    
    print(power_of_2(3)) # 8
    ```
    
- 연습문제
    - 선택정렬을 재귀적 알고리즘으로 작성
      
        ```python
        def selection_sort(A, s):
            if s == len(A):
                return
            
            min = s
            for i in range(s, len(A)):
                if A[min] > A[i]:
                    min = i
            A[s], A[min] = A[min], A[s]
        
            selection_sort(A, s + 1)
        
        A = [2, 4, 6, 1, 9, 8, 7, 0]
        selection_sort(A, 0)
        print(A) # [0, 1, 2, 4, 6, 7, 8, 9]
        ```
        

### 2. 부분집합

- 4개 원소를 포함한 집합에 대한 power set 구하기
  
    ```python
    bit = [-1] * 4
    for i1 in [0, 1]:
        bit[0] = i1
        for i2 in [0, 1]:
            bit[1] = i2
            for i3 in [0, 1]:
                bit[2] = i3
                for i4 in [0, 1]:
                    bit[3] = i4
                    print(bit)
    ```
    
- 바이너리 카운팅을 통한 부분집합 생성
  
    ```python
    arr = [3, 6, 7, 1, 5, 4]
    n = len(arr)
    
    for i in range(1 << n):
        for j in range(n):
            if i & (1 << j):
                print(arr[j], end = ' ')
        print()
    ```
    

### 3. 순열

- 1, 2, 3을 포함하는 모든 순열을 생성하는 함수
    - 동일한 숫자가 포함되지 않았을 때, 각 자리수 별로 loop를 이용해 구현 가능
    
    ```python
    for i in range(1, 4):
        for j in range(1, 4):
            if j != i:
                for k in range(1, 4):
                    if k != i and k != j:
                        print(i, j, k)
    
    '''
    1 2 3
    1 3 2
    2 1 3
    2 3 1
    3 1 2
    3 2 1
    '''
    ```
    
- 재귀를 이용한 순열 생성
  
    ```python
    def perm(n, k):
        if n == k:
            print(p)
            return
        
        for i in range(n, k):
            p[n], p[i] = p[i], p[n]
            perm(n + 1, k)
            p[n], p[i] = p[i], p[n]
    
    p = [1, 2, 3, 4]
    perm(0, 4)
    ```
    
    ```python
    def perm(n, k):
        if n == k:
            print(p)
            return
        
        for i in range(k):
            if not used[i]:
                p[n] = arr[i]
                used[i] = True
                perm(n + 1, k)
                used[i] = False
    
    arr = [1, 2, 3, 4]
    n = len(arr)
    p = [0] * n
    used = [False] * n
    perm(0, 4)
    ```
    
- 연습문제
    - 6자리 숫자에 대해서 완전검색을 적용해서 baby-gin 검사
      
        ```python
        def is_baby_gin(lst):
            tri = run = 0
            if lst[0] == lst[1] and lst[1] == lst[2]:
                tri += 1
            if lst[3] == lst[4] and lst[4] == lst[5]:
                tri += 1
            if lst[0] + 1 == lst[1] and lst[1] + 1 == lst[2]:
                run += 1
            if lst[3] + 1 == lst[4] and lst[4] + 1 == lst[5]:
                run += 1
            if tri + run == 2:
                return True
            return False
        
        def permutations(idx, p, used):
            if idx == 6:
                if is_baby_gin(p):
                    return True
                return False
            
            for i in range(len(numbers)):
                if i not in used: 
                    if permutations(idx + 1, p + [numbers[i]], used + [i]):
                        return True
            return False
        
        T = int(input())
        for t in range(1, T + 1):
            numbers = list(map(int, input()))
            print(permutations(0, [], []))
        ```
        

### 4. 조합

- 재귀를 이용한 조합 생성
  
    ```python
    def comb(n, r):
        if r == 0:
            print(temp)
        elif n < r:
            return
        else:
            temp[r - 1] = arr[n - 1]
            comb(n - 1, r - 1)
            comb(n - 1, r)
    
    arr = [1, 2, 3, 4]
    n = len(arr)
    r = 3
    temp = [-1] * r
    comb(n, r)
    ```
    
    ```python
    def comb(n, r, s):
        if r == 0:
            print(temp)
        
        else:
            for i in range(s, n - r + 1):
                temp[r - 1] = arr[i]
                comb(n, r - 1, i + 1)
    
    arr = [1, 2, 3, 4]
    n = len(arr)
    r = 3
    temp = [-1] * r
    comb(n, r, 0)
    ```
    
- 10개의 원소 중 3개를 고르는 조합
  
    ```python
    for i in range(8):
        for j in range(i + 1, 9):
            for k in range(j + 1, 10):
                print(i, j, k)
    ```
    

### 5. 탐욕 알고리즘

- 탐욕 기법을 통한 baby-gin 문제 해결
  
    ```python
    T = int(input())
    for t in range(T) :
        c = [0] * 10
    
        cards = input()
        for card in cards :
            c[int(card)] += 1
    
        i = tri = run = 0
        while i < 10 :
            if c[i] >= 3 :
                tri += 1
                c[i] -= 3
                continue
            if c[i] >= 1 and c[i + 1] >= 1 and c[i + 2] >= 1 :
                run += 1
                c[i] -= 1
                c[i + 1] -= 1
                c[i + 2] -= 1
                continue
            i += 1
    
        if tri + run == 2 :
            result = 1
        else :
            result = 0
        print(f'#{t + 1} {result}')
    ```
    

### 6. 활동 선택 문제

- 반복을 이용한 회의실 배정
  
    ```python
    k = 10
    meeting = [[1, 4], [1, 6], [6, 10], [5, 7], [3, 8], [5, 9], [3, 5], [8, 11], [2, 13], [12, 14]]
    
    meeting.sort(key = lambda x:x[1])
    answer = [meeting[0]]
    for m in meeting:
        if m[0] >= answer[-1][1]:
            answer.append(m)
    print(answer)
    ```
    
- 재귀를 이용한 회의실 배정
  
    ```python
    def recursive_selection(i, j):
        m = i + 1
        while m < j and meeting[m][0] < meeting[i][1]:
            m += 1
        
        if m < j:
            return {tuple(meeting[m])} | recursive_selection(m, j)
        else:
            return set()
    
    k = 10
    meeting = [[1, 4], [1, 6], [6, 10], [5, 7], [3, 8], [5, 9], [3, 5], [8, 11], [2, 13], [12, 14]]
    meeting.sort(key = lambda x:x[1])
    print(recursive_selection(0, k))
    ```