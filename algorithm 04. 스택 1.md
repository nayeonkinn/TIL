# 1. 스택

## 1.1. 스택

- 스택의 특성
    - 물건을 쌓아 올리듯 자료를 쌓아 올린 현태의 자료구조
    - 스택에 저장된 자료는 선형 구조를 가짐
        - 선형구조 : 자료 간의 관계가 1대 1의 관계를 가짐
        - 비선형구조 : 자료 간의 관계가 1대 N의 관계를 가짐 (ex. 트리)
    - 스택에 자료를 삽입하거나 꺼낼 수 있음
    - 후입선출 (LIFO, Last-In-First-Out)
- 스택 구현 자료구조
    - 자료를 선형으로 저장할 저장소 → 배열
    - 저장소 자체를 스택이라 부르기도 함
    - 스택에서 마지막으로 삽입된 원소의 위치 : top
        - stack pointer, sp
- 연산
    - `push` : 자료 저장 (삽입)
    - `pop` : 삽입한 역순으로 자료를 꺼냄 (삭제)
    - `isEmpty` : 스택이 공백인지 아닌지 확인
    - `peek` : 스택의 top에 있는 원소 반환

## 1.2. 스택 구현

- `push`
    - `append` 메소드 활용
        - 데이터가 커질 경우 느림
        
        ```python
        def push(item):
            s.append(item)
        ```
        
    - top 활용 (사이즈가 정해진 경우)
      
        ```python
        def push(item, size):
            global top
            top += 1
            if top == size:
                print('overflow')  # 디버깅 용도
            else:
                stack[top] = item
        
        size = 10
        stack = [0] * size
        top = -1
        
        push(10, size)
        
        top += 1  # push 함수와 동일한 역할
        stack[top] = 20
        ```
    
- `pop`
    - `pop` 메소드 활용
      
        ```python
        def pop():
            if len(s) == 0:
                # underflow
                return
            else:
                return s.pop()
        ```
        
    - top 활용
      
        ```python
        def pop():
            global top
            if top == -1:
                print('underflow')  # 디버깅 용도
                return 0
            else:
                top -= 1
                return stack[top + 1]
        
        print(pop())
        
        if top > -1:  # pop 함수와 동일한 역할
            top -= 1
            print(stack[top + 1])
        ```
    
- 스택 구현 시 고려사항
    - 1차원 배열을 사용할 경우 구현이 용이하지만 스택의 크기 변경이 어렵다는 단점이 있음
    - 이를 해결하기 위해 저장소를 동적으로 할당하여 구현할 수 있음 → 동적 연결리스트
        - 구현이 복잡하지만 메모리를 효율적으로 사용할 수 있음

### 1.2.1. 연습 문제 : 스택

```python
stackSize = 10
stack = [0] * stackSize
top = -1

top += 1
stack[top] = 1

top += 1
stack[top] = 2

top -= 1
temp = stack[top + 1]
print(temp)  # 2

temp = stack[top]
top -= 1
print(temp)  # 1
```

```python
stack2 = []
stack2.append(10)
stack2.append(20)
print(stack2.pop())  # 20
print(stack2.pop())  # 10
```

## 1.3. 스택 응용

- 괄호 검사
    - 종류 : 대괄호, 중괄호, 소괄호
    - 조건
        - 왼쪽 괄호와 오른쪽 괄호의 개수 같음
        - 같은 괄호에서 왼쪽 괄호는 오른쪽 괄호보다 먼저 나와야 함
        - 괄호 사이에는 포함 관계만 존재
    - 과정
        - 문자열에 있는 괄호를 차례대로 조사하면서 왼쪽 괄호를 만나면 스택에 삽입, 오른쪽 괄호를 만나면 스택에서 top 괄호를 삭제
        - 이때 스택이 비어 있으면 위 조건 1, 2에 위배되고 괄호의 짝이 맞지 않으면 조건 3에 위배됨
        - 마지막 괄호까지 조사한 후에도 스택에 괄호가 남아 있으면 조건 1 위배
- function call
    - 프로그램에서의 함수 호출과 복귀에 다른 수행 순서 관리
    - 가장 마지막에 호출된 함수가 가장 먼저 실행을 완료하고 복귀하는 후입선출 구조이므로, 후입선출 구조의 스택을 이용하여 수행 순서 관리
    - 함수 호출이 발생하면 호출한 함수 수행에 필요한 지역변수, 매개변수 및 수행 후 복귀할 주소 등의 정보를 스택 프레임에 저장하여 시스템 스택에 삽입
    - 함수의 실행이 끝나면 시스템 스택의 top 원소를 삭제하면서 프레임에 저장되어 있던 복귀 주소를 확인하고 복귀
    - 함수 호출과 복귀에 따라 이 과정을 반복하여 전체 프로그램 수행이 종료되면 시스템 스택은 공백이 됨

### 1.3.1. 연습 문제 :  괄호

```python
T = int(input())
for t in range(T):
    bracket = input()

    stack = []
    result = 1

    for b in bracket:
        if b == '(':
            stack.append(b)
        else:
            if not stack:
                result = -1
                break

            if stack[-1] == '(':
                stack.pop()
            else:
                result = -1
                break

    if stack:
        result = -1
    
    print(f'#{t + 1} {result}')
```

# 2. 재귀 호출

### 2.1. 재귀 호출

- 재귀 호출
    - 자기 자신을 호출하여 순환 수행되는 것
    - 함수에서 실행해야 하는 작업의 특성에 따라 일반적인 호출방식보다 재귀호출방식을 사용하여 프로그램의 크기를 줄이고 간단하게 작성 가능
- ex. 팩토리얼
    - 마지막에 구한 하위 값을 이용하여 상위 값을 구하는 작업 반복
    - f(n) = n * f(n - 1)
- ex. 피보나치
  
    ```python
    def fibo(n):
        if n < 2:
            return n
        else:
            return f(n - 1) + f(n - 2)
    ```
    

### 2.2. 재귀함수

- 기본 구조
    - i : 현재 단계
    - N : 목표 값
    
    ```python
    def f(i, N):  # i : 현재 단계, N : 목표
        if i == N:
            print(i)
            return
        else:
            print(i)
            f(i + 1, N)
    
    f(0, 4)  # 0 1 2 3 4
    ```
    
- 재귀함수 예시
    - 크기가 N인 배열의 모든 원소에 접근하는 재귀함수
      
        ```python
        def f(i, N):
            if i == N:  # 배열을 벗어남
                return
            else:  # 남은 원소가 있는 경우
                print(A[i])
                f(i + 1, N)  # 다음 원소로 이동
        
        N = 3
        A = [1, 2, 3]
        f(0, N)  # 0번 원소부터 N개의 원소에 접근
        ```
        

# 3. Memoization

- Memoization
    - 이전에 계산한 값을 메모리에 저장해서 매번 다시 계산하지 않도록 하여 전체적인 실행속도를 빠르게 하는 기술
        - 동적 계획법의 핵심
    - 앞의 피보나치 재귀함수의 경우 수많은 중복 호출이 존재
        - fibo(n)의 값을 계산하자마자 저장하면 실행시간을 O(n)으로 줄일 수 있음
        
        ```python
        def fibo1(n):
            if n >= 2 and len(memo) <= n:
                memo.append(fibo(n - 1) + fibo(n - 2))
            return memo[n]
        
        memo = [0, 1]
        ```
    
- PC (program counter)
    - 마이크로프로세서(중앙 처리 장치) 내부에 있는 레지스터 중의 하나로서, 다음에 실행될 명령어의 주소를 가지고 있어 실행할 기계어 코드의 위치를 지정

# 4. DP

- DP (Dynamic Programming)
    - 동적 계획 알고리즘은 그리디 알고리즘과 같이 최적화 문제를 해결하는 알고리즘
    - 먼저 입력 크기가 작은 부분 문제들을 모두 해결한 후에 그 해들을 이용하여 보다 큰 크기의 부분 문제들을 해결하여, 최종적으로 원래 주어진 입력의 문제를 해결하는 알고리즘
- 피보나치 수 DP 적용 알고리즘
  
    ```python
    def fibo2(n):
        f = [0, 1]
        for i in range(2, n + 1):
            f.append(f[i - 1] + f[i - 2])
        return f[n]
    ```
    
    - fibo1() : 재귀적, fibo2() : 반복적
    - 메모이제이션을 재귀적 구조에 사용하는 것보다 반복적 구조로 DP를 구현한 것이 성능 면에서 효율적
        - 재귀적 구조는 내부에 시스템 호출 스택을 사용하는 오버헤드 발생

# 5. DFS

- 그래프 구조 탐색
    - 비선형구조인 그래프 구조는 그래프로 표현된 모든 자료를 빠짐없이 검색하는 것이 중요
    - 두 가지 방법 : 깊이 우선 탐색(Depth First Search, DFS), 너비 우선 탐색(Breadth First Search, BFS)
- DFS
    - 시작 정점의 한 방향으로 갈 수 있는 경로가 있는 곳까지 깊이 탐색해 가다가 더 이상 갈 곳이 없게 되면 가장 마지막에 만났던 갈림길 간선이 있는 정점으로 되돌아와서 다른 방향의 정점으로 탐색을 계속 반복하여 결국 모든 정점을 방문하는 순회방법
    - 가장 마지막에 만났던 갈림길의 정점으로 되돌아가서 다시 깊이 우선 탐색을 반복해야 하므로 후입선출 구조의 스택 사용
- 과정
    - visited 배열을 false로 초기화하고 공백 스택을 생성한다.
    - 시작 정점 v를 결정하여 방문한다.
    - 정점 v에 인접한 정점 중에서
        - 방문하지 않은 정점 w가 있으면 정점 v를 스택에 push하고 정점 w를 방문한다. 그리고 w를 v로 하여 반복한다.
        - 방문하지 않은 정점이 없으면 탐색의 방향을 바꾸기 위해서 스택을 pop하여 받은 가장 마지막 방문 정점을 v로 하여 반복한다.
    - 스택이 공백이 될 때까지 반복한다.
- 코드 구현
    - 반복
      
        ```python
        def dfs(v, N):
            top = -1
            print(v)
            visited[v] = 1
            while True:
                for w in adjList[v]:
                    if visited[v] == 0:
                        top += 1
                        stack[top] = v
                        v = w
                        print(v)
                        visited[v] = 1
                        break
                    else:
                        if top != -1:
                            v = stack[top]
                            top -= 1
                        else:
                            break
        
        V, E = map(int, input().split())
        N = V + 1
        adjList = [[] for _ in range(N)]
        for _ in range(E):
            a, b = map(int, input().split())
            adjList[a].append(b)
            adjList[b].append(a)
        
        visited = [0] * N
        stack = [0] * N
        dfs(1, N)
        print()
        ```
        
    - 재귀
      
        ```python
        def dfs(v):
            print(v)
            visited[v] = 1
            for w in adjList[v]:
                if visited[w] == 0:
                    dfs(v)
        
        V, E = map(int, input().split())
        N = V + 1
        adjList = [[] for _ in range(N)]
        for _ in range(E):
            a, b = map(int, input().split())
            adjList[a].append(b)
            adjList[b].append(a)
        
        visited = [0] * N
        stack = [0] * N
        dfs(1)
        print()
        ```
        

### 5.1. 연습 문제 : DFS

```python
import sys
sys.stdin = open('input.txt', 'r') # 1 2 4 6 5 7 3

def dfs(v):
    stack = [v]
    print(v, end = ' ')
    visited[v] = 1
    
    while stack:
        for w in range(1, V + 1):
            if graph[v][w] == 1 and visited[w] == 0:
                stack.append(w)
                v = w
                print(v, end = ' ')
                visited[v] = 1
                break
        else:
            stack.pop()

V, E = map(int, input().split())
temp = list(map(int, input().split()))

graph = [[0] * (V + 1) for _ in range((V + 1))]
for i in range(0, E * 2, 2):
    graph[temp[i]][(temp[i + 1])] = 1
    graph[temp[i + 1]][temp[i]] = 1

visited = [0] * (V + 1)

dfs(1)
print()
```