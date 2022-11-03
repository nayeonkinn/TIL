# 01. 자바스크립트 기초

Category: javascript
Date: October 19, 2022
Git: No

---

## 1. Javascript Intro

### 1.1. Javascript 역사

- 웹 브라우저 역할
    - URL을 통해 Web(WWW)을 탐색
    - HTML/CSS/Javascript를 이해한 뒤 해석해서 사용자에게 하나의 화면으로 보여줌
    - 웹 서비스 이용 시 클라이언트 역할
        - 즉, 웹 페이지 코드를 이해하고 보여주는 역할
- 흠

## 2. Javascript 기초 문법

### 2.1. 코드 작성법

- 세미콜론
    - 자바스크립트는 세미콜론을 선택적으로 사용 가능
    - 세미콜론이 없으면 ASI에 의해 자동으로 세미콜론 삽입
        - ASI : Automatic Semicolon Insertion, 자동 세미콜론 삽입 규칙
        
        ```jsx
        console.log('hello')
        console.log('javascipt')
        ```
        
- 들여쓰기와 코드 블록
    - 들여쓰기 : 2칸 (파이썬은 4칸)
    - 블록 : `if`, `for` 함수에서 중괄호(`{}`) 내부
        - 파이썬은 들여쓰기를 이용해 코드 블록 구분
        - 자바스크립트는 중괄호를 사용해 코드 블록 구분
- 코드 스타일 가이드
    - 핵심은 합의된 원칙과 일관성
    - 코드의 품질에 직결되는 중요한 요소
        - 가독성, 유지보수, 커뮤니케이션 등 개발 과정 전체에 영향을 끼침
    - 파이썬의 PEP8처럼 자바스크립트에도 코드 스타일 가이드 존재
        - 회사마다 여러 코드 스타일 가이드 존재 (Airbnb, Google, Javascript Standard 등)
        - 수업은 Airbnb Style Guide 기반
- 주석
    - 한 줄 주석 : `//`
    - 여러 줄 주석 : `/* */`

### 2.2. 변수와 식별자

- 식별자란?
    - 변수를 구분할 수 있는 변수명
    - 식별자는 반드시 문자, 달러(`$`) 또는 밑줄(`_`)로 시작
    - 대소문자를 구분하며, 클래스명 외에는 모두 소문자로 시작
    - 예약어 사용 불가 (ex. `for`, `if`, `function` 등)
- 식별자 종류
    - 카멜 케이스 (camelCase, lower-camel-case) : 변수, 객체, 함수에 사용
        
        ```jsx
        // 변수
        let dog
        let variableName
        
        // 객체
        const userInfo = { name: 'Tom', age: 20 }
        
        // 함수
        function add() {}
        function getName() {}
        ```
        
    - 파스칼 케이스 (PascalCase, upper-camel-case) : 클래스, 생성자에 사용
        
        ```jsx
        // 클래스
        class User {
          constructor(options) {
            this.name = options.name
          }
        }
        
        // 생성자 함수
        function User(options) {
          this.name = options.name
        }
        ```
        
    - 대문자 스네이크 케이스 (SNAKE_CASE) : 상수에 사용
        - 상수 : 개발자의 의도와 상관없이 변경될 가능성이 없는 값
        
        ```jsx
        // 값이 바뀌지 않을 상수
        const API_KEY = 'my-key'
        const PI = Math.PI
        
        // 재할당이 일어나지 않는 변수
        const NUMBERS = [1, 2, 3]
        ```
        
- 변수 선언 키워드
    - `let`
        - 블록 스코프 지역 변수 선언 (동시에 값을 초기화)
    - `const`
        - 블록 스코프 읽기 전용 상수 선언 (동시에 값을 초기화)
    - `var`
        - 변수 선언 (동시에 값을 초기화)
- [참고] 선언, 할당, 초기화
    - 선언 (Declaration) : 변수를 생성하는 행위 또는 시점
    - 할당 (Assignment) : 선언된 변수에 값을 저장하는 행위 또는 시점
    - 초기화 (Initialization) : 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점
    
    ```jsx
    let foo           // 선언
    console.log(foo)  // undefined
    
    foo = 11          // 할당
    console.log(foo)  // 11
    
    let bar = 0       // 선언 + 할당
    console.log(bar)  // 0
    ```
    
- [참고] 블록 스코프
    - `if`, `for`, 함수 등의 중괄호 내부를 가리킴
    - 블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가능
    
    ```jsx
    let x = 1
    
    if (x === 1) {
      let x = 2
      console.log(x)  // 2
    }
    
    console.log(x)    // 1
    ```
    
- `let`
    - 재할당 가능 & 재선언 불가능
        
        ```jsx
        let number = 10  // 1. 선언 및 초기값 할당
        number = 20      // 2. 재할당
        ```
        
        ```jsx
        let number = 10  // 1. 선언 및 초기값 할당
        let number = 20  // 2. 재선언 불가능
        ```
        
    - 블록 스코프를 갖는 지역 변수를 선언, 선언과 동시에 원하는 값으로 초기화할 수 있음
- `const`
    - 재할당 불가능 & 재선언 불가능
        
        ```jsx
        const number = 10  // 1. 선언 및 초기값 할당
        number = 20      // 2. 재할당 불가능
        ```
        
        ```jsx
        const number = 10  // 1. 선언 및 초기값 할당
        const number = 20  // 2. 재선언 불가능
        ```
        
    - 선언 시 반드시 초기값을 설정해야 하며, 이후 값 변경이 불가능
    - `let`과 동일하게 블록 스코프를 가짐
- `var`
    - 재할당 가능 & 재선언 가능
    - ES6 이전에 변수를 선언할 때 사용되던 키워드
    - 호이스팅 되는 특성으로 인해 예기치 못한 문제 발생 가능
        - 따라서 ES6 이후부터는 `var` 대신 `const`와 `let`을 사용하는 것을 권장
    - 함수 스코프를 가짐
    - 변수 선언 시 `var`, `const`, `let` 키워드 중 하나를 사용하지 않으면 자동으로 `var`로 선언됨
- [참고] 함수 스코프
    - 함수의 중괄호 내부를 가리킴
    - 함수 스코프를 가지는 변수는 함수 바깥에서 접근 불가능
        
        ```jsx
        function foo() {
          var x = 5
          console.log(x) // 5
        }
        
        // ReferenceError: x is not defined
        console.log(x)
        ```
        
- [참고] 호이스팅 (hoisting)
    - 변수를 선언 이전에 참조할 수 있는 현상
    - `var`로 선언된 변수는 선언 이전에 참조할 수 있으며, 이러한 현상을 호이스팅이라 함
    - 변수 선언 이전의 위치에서 접근 시 undefined 반환

## 3. 함수

## 4. Array & Object