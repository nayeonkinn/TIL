## 1.  2차원 배열

### 1.1. 배열 순회

- 행 우선 순회
  
    ```python
    # n X m 배열
    
    # i : 행의 좌표
    # j : 열의 좌표
    
    for i in range(n):
        for j in range(m):
            array[i][j]
    ```
    
- 열 우선 순회
  
    ```python
    for j in range(m):
        for i in range(n):
            array[i][j]
    ```
    
- 지그재그 순회
  
    ```python
    for i in range(n):
        for j in range(m):
            array[i][j + (m - 1 - 2 * j) * (i % 2)]
    ```
    

### 1.2. 델타

```python
arr = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]  # 3 X 3 배열
N = 3

di = [-1, 1, 0, 0]  # 상하좌우
dj = [0, 0, -1, 1]

for i in range(1, N):
    for j in range(1, N):
        for k in range(4):
            ni = i + di[k]
            nj = j + dj[k]
            if 0 <= ni < N and 0 <= nj < N:
                print(arr[ni][nj])
```

### 1.3. 전치 행렬

```python
arr = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]  # 3 X 3 배열

for i in range(3):
    for j in range(3):
        if i < j:
            arr[i][j], arr[j][i] = arr[j][i], arr[i][j]
print(arr)  # [[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```

### 1.4. 연습 문제 1 : 델타

```python
def abs(n) :
    return n if n > 0 else -n

di = [-1, 0, 1, 0]
dj = [0, 1, 0, -1]

T = int(input())
for t in range(T) :
    input()
    arr = [list(map(int, input().split())) for _ in range(5)]
    i = j = total = 0
    for i in range(5) :
        for j in range(5) :
            for k in range(4) :
                if 0 <= i + di[k] < 5 and 0 <= j + dj[k] < 5 :
                    total += abs(arr[i + di[k]][j + dj[k]] - arr[i][j])
    print(f'#{t + 1} {total}')
```

## 2. 부분집합

- 부분집합의 수
    - 집합의 원소가 n개일 때, 공집합을 포함한 부분집합의 수는 2**n개
    - 이는 각 원소를 부분집합에 포함시키거나 포함시키지 않는 2가지 경우를 모든 원소에 적용한 경우의 수와 같음
- loop를 이용한 부분집합 생성
  
    ```python
    bit = [0, 0, 0, 0]
    for i in range(2):
        bit[0] = i
        for j in range(2):
            bit[1] = j
            for k in range(2):
                bit[2] = k
                for l in range(2):
                    bit[3] = l
                    print(bit)
    ```
    
- 비트 연산자
    - `&` : 비트 단위로 AND 연산
        - `i & (1 << j)` : i의 j번째 비트가 1인지 검사
    - `|` : 비트 단위로 OR 연산
    - `<<` : 피연산자의 비트 열을 왼쪽으로 이동
        - `1 << n` : 2**n 즉 원소가 n개일 경우의 모든 부분집합의 수
    - `>>` : 피연산자의 비트 열을 오른쪽으로 이동
- 비트 연산자를 이용한 부분집합 생성
  
    ```python
    arr = [3, 6, 7, 1, 5, 4]
    n = len(arr)  # arr 원소 개수
    
    for i in range(1 << n):  # 1 << n : 부분집합의 개수
        for j in range(n):  # 원소의 수만큼 비트 비교
            if i & (1 << j) :  # i의 j번 비트가 1인 경우
                print(arr[j], end = ' ')  # j번 원소 출력
        print()
    print()
    ```
    

### 2.1. 연습 문제 2 : 부분집합

```python
T = int(input())
for t in range(T) :
    numbers = list(map(int, input().split()))
    for i in range(1 << 10) :
        total = 0
        flag = 0
        for j in range(10) :
            if i & (1 << j) :
                total += numbers[j]
                flag = 1
        if total == 0 and flag == 1:
            result = 1
            break
        result = 0
    print(f'#{t + 1} {result}')
```

## 3. 검색

- 검색
    - 목적하는 탐색 키를 가진 항목을 찾는 것
        - 탐색 키 : 자료를 구별하여 인식할 수 있는 키
    - 종류
        - 순차 검색
        - 이진 검색
        - 해쉬

### 3.1. 순차 검색

- 순차 검색
    - 일렬로 되어 있는 자료를 순서대로 검색하는 방법
    - 가장 간단하고 직관적
    - 배열이나 연결 리스트 등 순차구조로 구현된 자료구조에서 유용함
    - 알고리즘이 단순하여 구현이 쉽지만 검색 대상의 수가 많은 경우에는 수행시간이 급격히 증가하여 비효율적임
- 자료가 정렬되어 있지 않은 경우
    - 과정
        - 첫번째 원소부터 차례대로 검색 대상과 키 값이 같은 원소가 있는지 비교하며 검색
        - 찾으면 그 원소의 인덱스 반환
        - 자료구조의 마지막에 이를 때까지 검색 대상을 찾지 못하면 검색 실패
    - 특징
        - 찾고자 하는 원소의 순서에 따라 비교횟수가 결정됨
        - 첫번째 원소를 찾을 때는 1번, 두번째 원소를 찾을 때는 2번 비교
        - 정렬되지 않은 자료에서의 평균 비교 횟수 : (n + 1) / 2
            - (1 / n) * (1 + 2 + 3 + … + n)
    - 코드 구현
      
        ```python
        def SequentialSearch(a, n, key):
            i = 0
            while i < n and a[i] != key:
                i += 1
            if i < n: return i
            else: return -1
        ```
    
- 자료가 정렬되어 있는 경우
    - 과정
        - 자료가 오름차순으로 정렬되어 있는 경우
        - 자료를 순차적으로 검색하면서 키 값을 비교하여 원소의 키 값이 검색 대상의 키 값보다 크면 찾는 원소가 없다는 것이므로 더이상 검색하지 않고 검색 종료
    - 특정
        - 찾고자 하는 원소의 순서에 따라 비교횟수가 결정됨
        - 정렬되어 있으므로 검색 실패를 반환하는 경우 평균 비교 횟수가 반으로 줄어듦
        - 시간 복잡도 : O(n)
    - 코드 구현
      
        ```python
        def SequentialSearch2(a, n, key):
            i = 0
            while i < n and a[i] < key:
                i += 1
            if i < n and a[i] == key: return i
            else: return -1
        ```
        

### 3.2. 이진 검색

- 이진 검색
    - 자료의 가운데에 있는 항목의 키 값과 비교하여 다음 검색의 위치를 결정하고 검색을 계속 진행하는 방법
    - 목적 키를 찾을 때까지 이진 검색을 순환적으로 반복 수행함으로써 검색 범위를 반으로 줄여가면서 보다 빠르게 검색 수행
    - 이진 검색을 하기 위해서는 자료가 정렬된 상태여야 함
- 과정
    - 자료의 중앙에 있는 원소를 고른다
    - 중앙 원소의 값과 찾고자 하는 목표 값을 비교한다
    - 목표 값이 중앙 원소의 값보다 작으면 자료의 왼쪽 반에 대해서 새로 검색을 수행하고, 크다면 자료의 오른쪽 반에 대해서 새로 검색을 수행한다
    - 찾고자 하는 값을 찾을 때까지 위 과정을 반복한다
- 코드 구현
    - 검색 범위의 시작점과 종료점을 이용하여 검색을 반복 수행
    - 자료에 삽입이나 삭제가 발생했을 때 배열의 상태를 항상 정렬 상태로 유지하는 추가 작업 필요
    
    ```python
    def BinarySearch(a, n, key):
        start = 0
        end = n - 1
        while start <= end:  # 주의! 같을 수도 있기 때문에 크거나 같다
            middle = (start + end) // 2
            if a[middle] == key:
                return True  # 검색 성공
            elif a[middle] > key:
                end = middle - 1
            else:
                start = middle + 1
        return False  # 검색 실패
    ```
    
    ```python
    # 재귀 함수 이용
    
    def BinarySearch2(a, low, high, key):
        if low > high:
            return False  # 검색 실패
        else:
            middle = (low + high) // 2
            if key == a[middle]:
                return True  # 검색 성공
            elif key < a[middle]:
                return BinarySearch2(a, low, middle - 1, key)
            elif key > a[middle]:
                return BinarySearch2(a, middle + 1, high, key)
    ```
    

### 3.3. 해쉬 검색

- 해쉬 검색
    - 데이터와 데이터를 저장할 인덱스를 연관시켜 짧은 시간에 찾을 수 있도록 한 알고리즘

## 4. 정렬

### 4.1. 인덱스

- 인덱스
    - 데이터베이스에서 유래한 용어로 테이블에 대한 동작 속도를 높여주는 자료 구조를 일컫음
        - 데이터베이스 분야가 아닌 곳에서는 Look up table 등의 용어 사용하기도 함
    - 인덱스를 저장하는데 필요한 디스크 공간은 보통 테이블을 저장하는데 필요한 디스크 공간보다 작음
        - 인덱스는 보통 키-필드만 가지고 있고 다른 테이블의 세부 항목들을 가지고 있지 않기 때문
- 배열을 사용한 인덱스
    - 대량의 데이터를 매번 정렬하면 속도가 저하되기 때문에 배열 인덱스 사용
    - 원본 데이터 배열과 별개로 배열 인덱스 생성할 경우, 데이터 삽입 시 상대적으로 크기가 작은 인덱스 배열을 정렬하기 때문에 속도가 빠름

### 4.2. 선택 정렬

- 선택 정렬
    - 주어진 자료들 중 가장 작은 값의 원소부터 차례대로 선택하여 위치를 교환
    - 과정
        - 주어진 리스트 중에서 최소값을 찾는다
        - 그 값을 리스트의 맨 앞에 위치한 값과 교환한다
        - 맨 처음 위치를 제외한 나머지 리스트를 대상으로 위의 과정을 반복한다
        - 미정렬 원소가 하나 남은 상황에서는 마지막 원소가 가장 큰 값을 갖게 되므로 실행을 종료하고 선택 정렬이 완료된다
    - 시간 복잡도 : O(n²)
- 코드 구현
  
    ```python
    def SelectionSort(a, n):
        for i in range(n - 1):
            minIdx = i
            for j in range(i + 1, n):
                if a[minIdx] > a[j]:
                    minIdx = j
            a[i], a[minIdx] = a[minIdx], a[i]
    ```
    

### 4.3. 셀렉션 알고리즘

- 셀렉션 알고리즘
    - 저장되어 있는 자료로부터 k번째로 큰 혹은 작은 원소를 찾는 방법
    - 과정
        - 정렬 알고리즘을 이용하여 자료 정렬하기
        - 원하는 순서에 있는 원소 가져오기
- k번째로 작은 원소를 찾는 알고리즘
    - 1번부터 k번째까지 작은 원소들을 찾아 배열의 앞쪽으로 이동시키고 배열의 k번째를 반환
    - k가 비교적 작을 때 유용하며 O(kn)의 수행시간을 필요로 함
    
    ```python
    def Select(arr, k):
        for i in range(k):
            minIdx = i
            for j in range(i + 1, len(arr)):
                if arr[minIdx] > arr[j]:
                    minIdx = j
            arr[i], arr[minIdx] = arr[minIdx], arr[i]
        return arr[k - 1]
    ```
    

### 4.4. 연습 문제 3 : 달팽이

```python
di = [0, 1, 0, -1] # 방향
dj = [1, 0, -1, 0]
ji = [1, -1, -1, 1] # 값 조정
jj = [-1, -1, 1, 1]

T = int(input())
for t in range(T) :
    N = int(input())
    snail = [[0] * N for _ in range(N)]
    i = j = turn =  0
    num = 1
    while num <= N ** 2 :
        while 0 <= i < N and 0 <= j < N and snail[i][j] == 0 :
            snail[i][j] = num
            num += 1
            i += di[turn]
            j += dj[turn]
        i += ji[turn]
        j += jj[turn]
        turn = (turn + 1) % 4

    print(f'#{t + 1}')
    for row in range(N) :
        print(" ".join(map(str, snail[row])))
```