# 1. 트리

- 트리
    - 비선형 구조
    - 원소들 간에 1:n 관계를 가지는 자료구조
    - 원소들 간에 계층관계를 가지는 자료구조
    - 상위 원소에서 하위 원소로 내려가면서 확장되는 트리 모양의 구조
- 특성
    - 한 개 이상의 노드로 이루어진 유한 집합
        - 노드 중 최상위 노드를 루트(root)라 함
        - 나머지 노드들은 n(≥ 0)개의 분리 집합으로 분리될 수 있음
    - 각 노드들은 각각 하나의 트리가 되며(재귀적) 루트의 부 트리(subtree)라고 함
        - 시작 노드 : 정점(node, vertex)
        - 마지막 노드 : 단말노드, 잎(leaf) 노드
- 용어
    - 노드(node) : 트리의 원소
    - 간선(edge) : 노드를 연결하는 선 (부모와 자식 노드를 연결)
    - 루트 노드(root node) : 트리의 시작 노드
    - 형제 노드(sibling node) : 같은 부모 노드의 자식 노드들
    - 조상 노드 : 간선을 따라 루트 노드까지 이르는 경로에 있는 모든 노드들
    - 서브 트리(subtree) : 부모 노드와 연결된 간선을 끊었을 때 생성되는 트리
    - 자손 노드 : 서브 트리에 있는 하위 레벨의 노드들
    - 차수(degree)
        - 노드의 차수 : 노드에 연결된 자식 노드의 수
        - 트리의 차수 : 트리에 있는 노드의 차수 중에서 가장 큰 값
        - 단말 노드(리프 노드) : 차수가 0인 노드 (자식 노드가 없는 노드)
    - 높이
        - 노드의 높이 : 루트에서 노드에 이르는 간선의 수 (노드의 레벨)
        - 트리의 높이 : 트리에 있는 노드의 높이 중에서 가장 큰 값 (최대 레벨)
        - 높이는 0부터 시작!

# 2. 이진 트리

## 2.1. 개념

- 이진 트리
    - 모든 노드들이 2개의 서브트리를 갖는 특별한 형태의 트리
    - 각 노드가 자식 노드를 최대 2개까지만 가질 수 있는 트리
        - 왼쪽 자식 노드(left child node)
        - 오른쪽 자식 노드(right child node)
- 특성
    - 레벨 i에서의 노드의 최대 개수는 2^i개
    - 높이가 h인 이진 트리가 가질 수 있는 노드의 개수는 최소 h+1개, 최대 2^(h+1)-1개
- 종류
    - 포화 이진 트리(Full Binary Tree)
        - 모든 레벨에 노드가 포화상태로 차 있는 이진 트리
        - 높이가 h일 때, 최대의 노드 개수인 2^(h+1)-1개를 가짐
        - 루트를 1번으로 하여  2^(h+1)-1까지 정해진 위치에 대한 노드 번호를 가짐
    - 완전 이진 트리(Complete Binary Tree)
        - 높이가 h이고 노드 수가 n개일 때(단, h+1 ≤ n ≤ 2^(h+1)-1) 포화 이진 트리의 노드 번호 1번부터 n번까지 빈 자리가 없는 이진 트리
    - 편향 이진 트리(Skewed Binary Tree)
        - 높이 h에 대한 최소 개수의 노드를 가지면서 한쪽 방향의 자식 노드만을 가진 이진 트리

## 2.2. 순회

- 순회
    - 트리의 노드들을 체계적으로 방문하는 것
    - 기본적인 순회 방법 3가지
        - 전위순회(preorder traversal) : VLR
        - 중위순회(inorder traversal) : LVR
        - 후위순회(postorder traversal) : LRV
- 전위 순회
    - 수행 방법
        - 현재 노드 n을 방문하여 처리 → V
        - 현재 노드 n의 왼쪽 서프트리로 이동 → L
        - 현재 노드 n의 오른쪽 서프트리로 이동 → R
    - 알고리즘
      
        ```python
        def preorder_traverse(T):
            if T:
                visit(T)
                preorder_traverse(T.left):
                preorder_traverse(T.right):
        ```
    
- 중위 순회
    - 수행 방법
        - 현재 노드 n의 왼쪽 서프트리로 이동 → L
        - 현재 노드 n을 방문하여 처리 → V
        - 현재 노드 n의 오른쪽 서프트리로 이동 → R
    - 알고리즘
      
        ```python
        def inorder_traverse(T):
            if T:
                inorder_traverse(T.left):
                visit(T)
                inorder_traverse(T.right):
        ```
    
- 후위 순회
    - 수행 방법
        - 현재 노드 n의 왼쪽 서프트리로 이동 → L
        - 현재 노드 n의 오른쪽 서프트리로 이동 → R
        - 현재 노드 n을 방문하여 처리 → V
    - 알고리즘
      
        ```python
        def postorder_traverse(T):
            if T:
                postorder_traverse(T.left):
                postorder_traverse(T.right):
                visit(T)
        ```
    
- 코드 구현
  
    ```python
    '''
    간선 수
    부모-자식
    4
    1 2 1 3 3 4 3 5
    '''
    
    def find_root(V):
        for i in range(1, V + 1):
            if par[i] == 0:
                return i
    
    def preorder(n):
        if n:
            print(n)
            preorder(ch1[n])
            preorder(ch2[n])
    
    def inorder(n):
        if n:
            inorder(ch1[n])
            print(n)
            inorder(ch2[n])
    
    def postorder(n):
        if n:
            postorder(ch1[n])
            postorder(ch2[n])
            print(n)
    
    E = int(input())
    arr = list(map(int, input().split()))
    V = E + 1
    root = 1
    ch1 = [0] * (V + 1)
    ch2 = [0] * (V + 1)
    par = [0] * (V + 1)
    for i in range(E):
        p, c = arr[i * 2], arr[i * 2 + 1]
        if ch1[p] == 0:
            ch1[p] = c
        else:
            ch2[p] = c
            
        par[c] = p
    
    root = find_root(V)
    print(root) # 1
    
    # preorder(root) # 1 2 3 4 5
    # inorder(root) # 2 1 4 3 5
    # postorder(root) # 2 4 5 3 1
    ```
    
    ```python
    # root에서 시작하지 않은 경우 시작점보다 위까지 순회하지 않음
    
    def pre(n):
        if n <= size:
            print(tree[n])
            pre(2 * n)
            pre(2 * n + 1)
    
    tree = [0, 'A', 'B', 'C', 'D', 'E', 'F'] # 완전이진트리
    size = len(tree) - 1
    pre(1) # A B D E C F
    pre(2) # B D E
    ```
    
    ```python
    # 트리의 개수 세기 = 순회한 정점 수
    
    def preorder(n): # global cnt
        global cnt
        if n:
            cnt += 1
            preorder(ch1[n])
            preorder(ch2[n])
    
    def f(n): # return
        if n == 0:
            return 0
        else:
            L = f(ch1[n])
            R = f(ch2[n])
            return L + R
    ```
    

### 2.2.1. 연습 문제 : 순회

```python
def preorder(n):
    if n:
        print(n, end = ' ')
        preorder(ch1[n])
        preorder(ch2[n])

V = int(input())
E = V - 1
arr = list(map(int, input().split()))
ch1 = [0] * (V + 1)
ch2 = [0] * (V + 1)

for i in range(E):
    p, c = arr[2 * i], arr[2 * i + 1]
    if ch1[p] == 0:
        ch1[p] = c
    else:
        ch2[p] = c

preorder(1)
```

## 2.3. 이진 트리의 표현

- 배열을 이용한 이진 트리의 표현
    - 이진 트리에 각 노드 번호 부여
        - 루트 번호 1
        - 레벨 n에 있는 노드에 대하여 왼쪽부터 오른쪽으로 2^n부터 2^(n+1)-1까지 번호를 차례로 부여
    - 노드 번호의 성질
        - i번 노드의 부모 노드 번호 : i//2
        - i번 노드의 왼쪽 자식 노드 번호 : 2*i
        - i번 노드의 오른쪽 자식 노드 번호 : 2*i+1
        - 레벨 n의 노드 번호 시작 번호 : 2^n
        - 노드 번호를 배열의 인덱스로 사용
        - 높이가 h인 이진 트리를 위한 배열의 크기는 2^(h+1)-1
    - 단점
        - 편향 이진 트리의 경우에 사용하지 않는 배열 원소에 대한 메모리 공간 낭비 발생
        - 트리의 중간에 새로운 노드를 삽입하거나 기존의 노드를 삭제할 경우 배열의 크기 변경 어려워 비효율적 → 연결리스트 이용 가능
- [참고] 이진 트리의 저장
    - 부모 번호를 인덱스로 자식 번호를 저장
      
        ```python
        for i in range(E):
            p, c = arr[i * 2], arr[i * 2 + 1]
            if ch1[p] == 0:
                ch1[p] = c
            else:
                ch2[p] = c
        ```
        
    - 자식 번호를 인덱스로 부모 번호를 저장
      
        ```python
        for i in range(E):
            par[c] = p
        ```
        
    - 루트 찾기, 조상 찾기
      
        ```python
        c = 5
        while par[c] != 0:
            c = par[c]
            anc.append(c) # 조상 목록
        
        root = c
        ```
    
- 연결 자료구조를 이용한 이진 트리의 표현
    - 이진 트리의 모든 노드는 최대 2개의 자식 노드를 가지므로 일정한 구조의 단순 연결 리스트 노드를 사용하여 구현

## 2.4. 수식 트리

- 수식 트리
    - 수식을 표현하는 이진 트리
    - = 수식 이진 트리(Expression Binary Tree)
    - 루트 노드, 가지 노드 → 연산자
    - 잎 노드 → 피연산자
- 순회
    - 중위 순회 : A / B * C * D + E (식의 중위 표기법)
    - 후위 순회 : A B / C * D * E + (식의 후위 표기법)
    - 전위 순회 : + * * / A B C D E (식의 전위 표기법)

# 3. 이진 탐색 트리

## 3.1. 개념

- 이진 탐색 트리
    - 탐색 작업을 효율적으로 하기 위한 자료구조
    - 모든 원소는 서로 다른 유일한 키를 가짐
    - key(왼쪽 서브프리) < key(루트 노드) < key(오른쪽 서브트리)
    - 왼쪽 서브트리와 오른쪽 서브트리도 이진 탐색 트리
    - 중위 순회하면 오름차순으로 정렬된 값을 얻을 수 있음

## 3.2. 연산

- 탐색 연산
    - 루트에서 시작
    - 탐색할 키 값 x를 루트 노드의 키 값과 비교
        - x = root : 원하는 원소를 찾았으므로 탐색연산 성공
        - x > root : 루트노드의 왼쪽 서브트리에 대해서 탐색연산 수행
        - x < root : 루트노드의 오른쪽 서브트리에 대해서 탐색연산 수행
    - 서브트리에 대해서 순환적으로 탐색 연산 반복
- 삽입 연산
    - 먼저 탐색 연산 수행
        - 삽일할 원소와 같은 원소가 트리에 있으면 삽입할 수 없으므로, 같은 원소가 트리에 있는지 탐색하여 확인
        - 탐색에서 탐색 실패가 결정되는 위치가 삽입 위치가 됨
    - 탐색 실패한 위치에 원소 삽입

## 3.3. 성능

- 이진 탐색 트리 성능
    - 탐색, 삽입, 삭제 : 트리의 높이만큼 시간 소요 → O(h)
    - 평균의 경우 (이진 트리가 균형적으로 생성되어 있는 경우) → O(logN)
    - 최악의 경우 (한쪽으로 치우친 경사 이진트리의 경우) → O(N) (순차탐색과 시간복잡도가 같음)
- 검색 알고리즘 비교
    - 배열에서의 순차 검색 → O(N)
    - 정렬된 배열에서의 순차 검색 → O(N)
    - 정렬된 배열에서의 이진 탐색 → O(logN)
        - 고정 배열 크기의 삽입, 삭제 시 추가 연산 필요
    - 이진 탐색 트리에서의 평균 → O(logN)
        - 최악의 경우 : O(N)
        - 완전 이진 트리 또는 균형 트리로 바꿀 수 있다면 최악의 경우를 없앨 수 있음
            - 새로운 원소를 삽입할 때 삽입 시간을 줄임
            - 평균과 최악의 시간이 같음 → O(logN)
    - 해쉬 검색 → O(1)
        - 추가 저장 공간이 필요

## 3.4. [참고] 힙

- 힙
    - 완전 이진 트리에 있는 노드 중에서 키값이 가장 큰 노드나 키값이 가장 작은 노드를 찾기 위해서 만든 자료구조
    - 최대 힙 (max heap)
        - 키값이 가장 큰 노드를 찾기 위한 완전 이진 트리
        - 부모 노드의 키값 > 자식 노드의 키값
        - 루트 노드 : 키값이 가장 큰 노드
    - 최소 힙 (min heap)
        - 키값이 가장 작은 노드를 찾기 위한 완전 이진 트리
        - 부모 노드의 키값 < 자식 노드의 키값
        - 루트 노드 : 키값이 가장 작은 노드
- 연산
    - 삽입
        - 순서
            - 삽입할 자리 확장
            - 확장한 자리에 삽입할 원소 저장
            - 자리 바꾸기 (조건에 맞지 않는 경우)
            - 자리 확정
    - 삭제
        - 힙에서는 루트 노드의 원소만을 삭제할 수 있음
        - 루트 노드의 원소를 삭제하여 반환
        - 힙의 종류에 따라 최대값 또는 최소값을 구할 수 있음
        - 순서
            - 루트 노드의 원소 삭제
            - 마지막 노드 삭제
            - 자리 바꾸기 (조건에 맞지 않는 경우)
            - 자리 확정
    - 코드 구현
      
        ```python
        # 힙 연산 (최대 힙)
        
        def enq(n): # 삽입
            global last
            last += 1
            heap[last] = n
        
            c = last
            p = c // 2
            while p and heap[p] < heap[c]:
                heap[p], heap[c] = heap[c], heap[p]
                c = p
                p = c // 2
            print(heap)
        
        def deq(): # 삭제
            global last
            tmp = heap[1]
            heap[1] = heap[last]
            last -= 1
            p = 1
            c = p * 2 # 왼쪽 자식
            while c <= last:
                if c + 1 <= last and heap[c] < heap[c + 1]:
                    c += 1 # 비교 대상을 오른쪽 자신으로 변경
                if heap[p] < heap[c]:
                    heap[p], heap[c] = heap[c], heap[p]
                    p = c
                    c = p * 2
                else: # 부모가 더 크면 비교 중단
                    break
            return tmp
        
        heap = [0] * 10
        last = 0
        
        enq(2)
        enq(5)
        enq(7)
        enq(3)
        enq(4)
        enq(6)
        
        while last:
            print(deq())
        ```
    
- 우선순위 큐
    - 힙의 키를 우선순위로 활용하여 우선순위 큐 구현 가능