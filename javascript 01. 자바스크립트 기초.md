## 1. JavaScript Intro

### 1.1. JavaScript 특징

- JavaScript 특징
    - 웹 기술의 기반이 되는 언어
        - HTML 문서의 콘텐츠를 동적으로 변경할 수 있음
        - 웹이라는 공간에서 채팅, 게임 등 다양한 동작을 할 수 있게 된 기반
    - 다양한 분야로 확장이 가능한 언어
        - 자바스크립트는 웹을 위해 탄생한 언어로, 초기에는 언어의 특성상 많은 개발자에게 환영받지 못함
        - 하지만 버전이 올라가면서 하나의 단단한 언어로 자리매김
        - 단순히 웹 조작을 넘어서 서버 프로그래밍, 모바일 서비스, 컴퓨터 응용프로그래밍, 블록체인, 게임 개발 등 다양한 분야에서 활용 가능
        - 과거에는 단순히 웹 프론트엔드를 위해서만 자바스크립트 개발자를 찾았다면 이제는 그 영역이 매우 넒어져 다양한 직군에서 찾는 언어가 됨
    - 2022년 현재 가장 인기있는 언어
        - 언어의 확장성 만큼 큰 인기를 얻고 있음

### 1.2. JavaScript 역사

- JavaScript 역사
    - 자바스크립트는 웹을 조작하기 위한 언어인 만큼 웹 브라우저와도 깊은 연관
- 웹 브라우저 역할
    - URL을 통해 Web(WWW)을 탐색
    - HTML/CSS/JavaScript를 이해한 뒤 해석해서 사용자에게 하나의 화면으로 보여줌
    - 웹 서비스 이용 시 클라이언트 역할
        - 즉, 웹 페이지 코드를 이해하고 보여주는 역할
- 웹 브라우저와 스크립트 언어
    - 1993 Mosaic Web Browser
        - 유저가 웹을 쉽게 탐색할 수 있게 버튼 등을 탑재한 GUI 기반의 웹 브라우저
    - 1994 Netscape Navigator
        - Mosaic Web Browser를 개선한 후속작으로, 시장점유율 80% 차지
        - 이 때까지만 해도 정적 웹페이지를 단순히 보여주는 용도에 그침
        - 웹 브라우저에 탑재해서 웹 페이지를 동적으로 바꿔줄 스크립트 언어 개발 필요
            - 스크립트(script) 언어 : 소스 코드를 기계어로 바꿔주는 컴파일러 없이 바로 실행 가능한 언어로 속도가 느리다는 단점이 있음
    - 1995 Netscape Navigator 2.0 (Mocha)
        - Netscape에서 약 10일의 개발 기간을 통해 스크립트 언어인 Mocha 개발
        - 이후 LiveScript로 이름 변경한 뒤 브라우저에 이를 해석해주는 엔진 내장
        - 당시 인기있던 자바의 명성에 기대보고자 JavaScript로 이름 변경
    - 1995 Microsoft Internet Explorer
        - Netscape에 자극받은 Microsoft는 JavaScript를 그대로 복사한 JScript라는 언어 제작 후 이를 탑재한 웹 브라우저인 Internet Explorer 출시
        - 이후 JavaScript와 JScript는 각자의 기능을 추가하기 시작
        - 개발자들은 Netscape Navigator와 Internet Explorer 각각에 대한 코드를 작성해야 하는 상황을 맞이하게 됨
    - 1996-2000 ECMA 표준 발의
        - Netscape가 정보 통신에 관한 규약을 만드는 비영리 단체 ECMA에게 JavaScript 기반의 표준안 발의 제안하여 ECMAScript 1 출시
        - 이후 여러 문법 추가되며 ECMAScript의 버전이 올라감
        - 이 상황을 지켜보던 Microsoft, Windows에 기본으로 Internet Explorer 탑재
        - 결국 시장 점유율 95% 이상으로 증가하며 ECMAScript 표준안 지키지 않겠다 선언
    - 2001-2004 다양한 웹 브라우저 등장
        - ActionScript3 기반으로 한 Firefox 웹 브라우저 출시
        - 이에 개발자들은 세가지 웹 브라우저 지원을 위해 고통
        - 이후 Opera 등의 다양한 웹 브라우저가 계속 시장에 출시
        - 다양성으로 더욱 많은 개발자가 필요해졌고, 이는 집단 지성을 형성
    - jQuery 등의 라이브러리 등장
        - 각 브라우저의 엔진에 맞는 스크립트를 여러 번 작성하는 것은 비효율
        - 중간에 하나의 레이어를 두고 코딩하는 것 → jQuery
            - jQuery 문법에 맞춰 코딩하면 브라우저 별 엔진에 맞는 스크립트 변환은 jQuery가 알아서 변환
        - 이후 많은 코드가 jQuery로 작성됨
    - 2008 Google의 Chrome 등장과 대통합의 시대
        - V8이라는 강력한 엔진을 탑재한 Chrome 등장
            - JavaScript 해석이 다른 웹 브라우저에 비해 월등히 빠름
            - 이로 인해 웹 브라우저에 버벅임이 없고 매우 빠르게 동작
        - Chrome의 성능 앞에서 다른 웹 브라우저들이 함께 표준안을 만들자고 제안
    - 2009 ECMAScript5(ES5) 표준안 제정
    - 2015 ECMAScript6(ES6) 표준안 제정
    - 이후에도 계속해서 버전이 업데이트 되고 있으나, 큰 변화는 ES6에서 이루어짐
- 정리
    - 웹 브라우저는 JavaScript를 해석하는 엔진을 가지고 있음
    - 현재의 JavaScript는 이제 시장에서 자리를 잡은 언어이며, 개발에서 큰 축을 담당
    - 더이상 jQuery 등의 라이브러리를 사용할 필요가 없음 (모든 웹 브라우저가 표준안을 따름)
    - 특히 Chrome V8의 경우 JavaScript를 번역하는 속도가 매우 빠름
        - 이에 웹 브라우저 뿐 아니라 다른 개발에서도 활용
        - node.js, react.js, electron 등의 내부 엔진으로 사용
        - 그 결과 백엔드, 모바일, 데스크탑 앱 등 모두 JavaScript로 개발이 가능해짐

### 1.3. JavaScript 실행환경 구성

- 웹 브라우저로 실행
    - 웹 브라우저에는 자바스크립트를 해석할 수 있는 엔진이 있어 실행할 수 있음
    - 특별하게 웹 브라우저에서 바로 실행할 수 있는 자바스크립트 문법들을 바닐라 자바스크립트라고 부름 (순수한 자바스크립트라는 의미)
    - 방법 1 :  HTML 파일에 직접 자바스크립트를 작성 후 웹 브라우저로 파일 열기
        - 크롬의 개발자 도구 中 콘솔 탭에서 결과 확인 가능
    - 방법 2 : `.js` 확장자를 가진 파일에 자바스크립트를 작성하고, HTML에 포함
      
        ```html
        <script type="text/javascript" scr="hello.js"></script>
        ```
        
    - 방법 3 : 웹 브라우저의 콘솔에서 바로 입력 (엔진이 있기 때문!)
- Node.js로 실행
    - 웹 브라우저를 이용하지 않고 자바스크립트를 실행할 수 있음 (엔진이 있기 때문!)
    - 설치 확인 : `node -v` or `npm -v`
        - npm : node package manager, 자바스크립트를 위한 패키지 관리자 (파이썬의 pip)
    - 자바스크립트 파일 실행 : `node hello.js`

## 2. JavaScript 기초 문법

### 2.1. 코드 작성법

- 세미콜론
    - 자바스크립트는 세미콜론을 선택적으로 사용 가능
    - 세미콜론이 없으면 ASI에 의해 자동으로 세미콜론 삽입
        - ASI : Automatic Semicolon Insertion, 자동 세미콜론 삽입 규칙
    
    ```jsx
    console.log('hello');
    console.log('javascipt')
    ```
    
- 들여쓰기와 코드 블록
    - 파이썬은 4칸 들여쓰기를 사용했으나, 자바스크립트는 2칸 들여쓰기 사용
    - 블록은 `if`, `for` 함수에서 중괄호(`{}`) 내부를 말함
        - 파이썬은 들여쓰기를 이용해 코드 블록 구분
        - 자바스크립트는 중괄호를 사용해 코드 블록 구분
- 코드 스타일 가이드
    - 핵심은 합의된 원칙과 일관성
    - 코드의 품질에 직결되는 중요한 요소
        - 가독성, 유지보수, 커뮤니케이션 등 개발 과정 전체에 영향을 끼침
    - 파이썬의 PEP8처럼 자바스크립트에도 코드 스타일 가이드 존재
        - 회사마다 여러 코드 스타일 가이드 존재 (Airbnb, Google, JavaScript Standard 등)
        - 수업은 Airbnb Style Guide 기반
- 주석
    - 한 줄 주석 : `//`
    - 여러 줄 주석 : `/* */`

### 2.2. 변수와 식별자

- 식별자
    - 변수를 구분할 수 있는 변수명
    - 식별자는 반드시 문자, 달러(`$`) 또는 밑줄(`_`)로 시작
    - 대소문자를 구분하며, 클래스명 외에는 모두 소문자로 시작
    - 예약어 사용 불가 (ex. `for`, `if`, `function` 등)
- 식별자 종류
    - 카멜 케이스 (camelCase, lower-camel-case)
        - 변수, 객체, 함수에 사용
        
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
        
    - 파스칼 케이스 (PascalCase, upper-camel-case)
        - 클래스, 생성자에 사용
        
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
        
    - 대문자 스네이크 케이스 (SNAKE_CASE)
        - 상수에 사용
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
        number = 20        // 2. 재할당 불가능
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
      
        ```jsx
        console.log(name) // undefined => 선언 이전에 참조
        
        var name = '홍길동' // 선언
        ```
        
        ```jsx
        // 위 코드를 암묵적으로 아래와 같이 이해함
        
        var name // undefined로 초기화
        console.log(name)
        
        var name = '홍길동' // 선언
        ```
        
    - 즉, 자바스크립트에서 변수들은 실제 실행 시에 코드의 최상단으로 끌어 올려지게 됨(hoisted) (이게 뭔 소리야)
        - 이러한 이유 때문에 `var`로 선언된 변수는 선언 시에 undefined로 값이 초기화되는 과정이 동시에 일어남
        - 반면 `let`, `const`는 호이스팅이 일어나면 에러를 발생시킴
        
        ```jsx
        console.log(username) // undefined
        var username = '홍길동'
        
        console.log(email) // Uncaught ReferenceError
        let email = 'gildong@gmail.com'
        
        console.log(age) // Uncaught ReferenceError
        const age = 50
        ```
        
    - 변수를 선언하기 전에 접근이 가능한 것은 코드의 논리적인 흐름을 깨뜨리는 행위이며 이러한 것을 방지하기 위해 `let`과 `const`가 추가됨
        - 즉, `var`는 사용하지 않아야 하는 키워드
    - 다만 아직까지도 많은 기존의 자바스크립트 코드는 ES6 이전의 문법으로 작성되어 있으므로 호이스팅에 대한 이해 필요
- 변수 선언 키워드 정리
  
  
    | 키워드 | 재선언 | 재할당 | 스코프 | 비고 |
    | --- | --- | --- | --- | --- |
    | let | X | O | 블록 | ES6부터 도입 |
    | const | X | X | 블록 | ES6부터 도입 |
    | var | O | O | 함수 | 사용 X |
    - 어디에 변수를 쓰고 상수를 쓸지 결정하는 것은 프로그래머의 몫
    - Airbnb 스타일 가이드에서는 기본적으로 `const` 사용 권장
        - 재할당해야 하는 경우만 `let`

### 2.3. 데이터 타입

- 데이터 타입
    - 자바스크립트의 모든 값은 특정한 데이터 타입을 가짐
    - 크게 원시 타입과 참조 타입으로 분류됨
    - Data Type
        - Primitive Type : Number, String, Boolean, undefined, null, Symbol
        - Reference Type : Objects (Array, Function, …)
- Number
    - 정수 또는 실수형 숫자를 표현하는 자료형
      
        ```jsx
        const a = 13
        const b = -5
        const c = 3.14 // float 표현
        const d = 2.998e8 // 2.998 * 10^8 = 299,800,000
        const e = Infinity
        const f = -Infinity
        const g = NaN // Not a Number를 나타내는 값
        ```
    
- NaN
    - Not-A-Number
    - NaN을 반환하는 경우
        - 숫자로써 읽을 수 없음 (`parseInt(’어쩌구’)`, `Number(undefined)`)
        - 결과가 허수인 수학 계산식 (`Math.sqrt(-1)`)
        - 피연산자가 NaN (`7 ** NaN`)
        - 정의할 수 없는 계산식 (`0 * Infinity`)
        - 문자열을 포함하면서 덧셈이 아닌 계산식 (`”가” / 3`)
    - `Number.isNaN()`
        - 주어진 값의 유형이 Number이고 값이 NaN이면 true, 아니면 false를 반환
        
        ```jsx
        Number.isNaN(NaN)       // true
        Number.isNaN(0 / 0)     // true
        
        // isNaN()으로는 true
        Number.isNaN('NaN')     // false
        Number.isNaN(undefined) // false
        Number.isNaN({})        // false
        Number.isNaN('blabla')  // false
        
        // 모두 false
        Number.isNaN(true)
        Number.isNaN(null)
        Number.isNaN(37)
        Number.isNaN('37')
        Number.isNaN('37.37')
        Number.isNaN('')
        Number.isNaN(' ')
        ```
    
- String
    - 문자열을 표현하는 자료형
    - 작은 따옴표, 큰 따옴표 모두 가능
    - 곱셈, 나눗셈, 뺄셈은 안 되지만 덧셈을 통해 문자열을 붙일 수 있음
    - Quote를 사용하면 선언 시 줄 바꿈 불가
        - 대신 escape sequence `\n` 사용
    - Template Literal을 사용하면 줄 바꿈 가능하면 문자열 사이에 변수도 삽입 가능
        - 단 escape sequence 사용 불가 (= 파이썬의 f-string)
        
        ```jsx
        const word = `안녕
        들 하세요`
        console.log(word)
        
        const age = 10
        const message = `홍길동은 ${age}세 입니다.`
        console.log(message)
        ```
    
- Template Literal
    - 내장된 표현식을 허용하는 문자열 작성 방식
    - ES6+부터 지원
    - 백틱을 이용하며, 여러 줄에 걸쳐 문자열을 정의할 수도 있고 자바스크립트의 변수를 문자열 안에 바로 연결할 수 있는 이점
    - 표현식을 넣을 수 있는데, 이는 $와 중괄호로 표기 (`${expression}`로 표기)
- Empty Value
    - 값이 존재하지 않음을 표현하는 값으로 `null`과 `undefined`가 존재
    - 동일한 역할을 하는 이 두개의 키워드가 존재하는 이유는 단순한 자바스크립트의 설계 실수
    - 큰 차이를 두지 말고 interchangeable하게 사용할 수 있도록 권장
- null
    - null 값을 나타내는 특별한 키워드
    - 변수의 값이 없음을 의도적으로 표현할 때 사용하는 데이터 타입
- undefined
    - 값이 정의되어 있지 않음을 표현
    - 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당됨
- null vs undefined
    - null과 undefined의 가장 대표적인 차이점은 typeof 연산자를 통해 타입을 확인했을 때 나타남
      
        ```jsx
        typeof null       // "object"
        typeof undefined  // "undefined"
        ```
        
    - null이 원시 타입임에도 불구하고 object로 출력되는 이유는 자바스크립트 설계 당시의 버그를 지금까지 해결하지 못한 것
    - 쉽계 해결할 수 없는 이유는 이미 null 타입에 의존성을 띄고 있는 많은 프로그램들이 망가질 수 있기 때문 (하위 호환 유지)
- Boolean
    - true와 false
    - 참과 거짓을 표현
    - 조건문 또는 반복문에서 유용하게 사용
        - 조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 자동 형변환 규칙에 따라 true 또는 false로 변환됨
- ToBoolean Conversions (자동 형변환)
  
  
    | 데이터 타입 | false | true |
    | --- | --- | --- |
    | undefined | 항상 false | X |
    | null | 항상 false | X |
    | Number | 0, -0, NaN | 나머지 모든 경우 |
    | String | 빈 문자열 | 나머지 모든 경우 |
    | Object | X | 항상 true |

### 2.4. 연산자

- 할당 연산자
    - 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당
    - 다양한 연산에 대한 단축 연산자 지원
    - Increment 및 Decrement 연산자
        - Increment(++) : 피연산자의 값을 1 증가
        - Decrement(--) : 피연산자의 값을 1 감소
        - += 또는 -=와 같이 더 분명한 표현 권장
- 비교 연산자
    - 피연산자들(숫자, 문자, Boolean 등)을 비교하고 결과값을 boolean으로 반환
    - 문자열은 유니코드 값을 사용하며 표준 사전 순서를 기반으로 비교
        - 알파벳끼리 비교할 경우
            - 알파벳 순서상 후순위가 더 크다
            - 소문자가 대문자보다 더 크다
- 동등 연산자 (==)
    - 두 연산자가 같은 값으로 평가되는지 비교 후 boolean 값 반환
    - 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
    - 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별
    - 예상치 못한 결과가 발생할 수 있으므로 특별한 경우를 제외하고 사용하지 않음
    
    ```jsx
    const a = 1
    const b = '1'
    
    console.log(a == b)      // true
    console.log(a == true)   // true
    
    // 자동 형변환 예시
    console.log(8 * null)    // 0 (null은 0)
    console.log('5' - 1)     // 4
    console.log('5' + 1)     // '51'
    console.log('five' * 2)  // NaN
    ```
    
- 일치 연산자 (===)
    - 두 피연산자의 값과 타입이 모두 같은 경우 true 반환
    - 같은 객체를 가리키거나, 같은 타입이면서 같은 값인지 비교
    - 엄격한 비교가 이뤄지며 암묵적 타입 변환이 발생하지 않음
        - 엄격한 비교 : 두 비교 대상의 타입과 값 모두 같은지 비교하는 방식
    
    ```jsx
    const a = 1
    const b = '1'
    
    console.log(a === b)          // false
    console.log(a === Number(b))  // true
    ```
    
- 논리 연산자
    - 세 가지 논리 연산자로 구성
        - and 연산 : `&&`
        - or 연산 : `||`
        - not 연산 : `!`
    - 단축 평가 지원
        - ex. `false && true` : false
        - ex. `true || false` : true
    
    ```jsx
    true && false   // false
    true && true    // true
    
    false || true   // true
    false || false  // false
    
    !true   // false
    
    1 && 0  // 0
    0 && 1  // 0
    4 && 7  // 7
    
    1 || 0  // 1
    0 || 1  // 1
    4 || 7  // 4
    ```
    
- 삼항 연산자 (Ternary Operator)
    - 3개의 피연산자를 사용하여 조건에 따라 값을 반환
    - 가장 앞의 조건식이 참이면 콜론 앞의 값 반환, 그 반대일 경우 콜론 뒤의 값 반환
    - 삼항 연산자의 결과 값을 반환하기 때문에 변수에 할당 가능
    
    ```jsx
    true ? 1 : 2   // 1
    false ? 1 : 2  // 2
    
    const result = Math.PI > 4 ? 'Yep' : 'Nope'
    console.log(result)  // Nope
    ```
    

### 2.5. 조건문

- 조건문의 종류와 특징
    - `if`
        - 조건 표현식의 결과값을 boolean 타입으로 변환 후 참/거짓 판단
    - `switch`
        - 조건 표현식의 결과값이 어느 값(case)에 해당하는지 판별
        - 주로 특정 변수의 값에 따라 조건을 분기할 때 활용
            - 조건이 많아질 경우 if문보다 가독성이 나을 수 있음
- `if`
    - `if`, `else if`, `else`
    - 조건은 소괄호 안에 작성, 실행할 코드는 중괄호 안에 작성
    - 블록 스코프 생성
- `switch`
    - 표현식의 결과값을 이용한 조건문
    - 표현식의 결과값과 case문의 오른쪽 값 비교
    - break 및 default문은 선택적으로 사용 가능
    - break문이 없는 경우 break문을 만나거나 default문을 실행할 때까지 다음 조건문 실행
    - 블록 스코프 실행
    
    ```jsx
    switch(expression) {
      case 'first value': {
        // do something
        break
      }
      case 'second value': {
        // do something
        break
      }
      default: {
        // do something
      }
    }
    
    // break 없는 경우 모든 case 실행됨 (Fall-through 현상)
    ```
    
- `if` vs `switch`
    - 조건이 많은 경우 switch문을 통해 가독성 향상을 기대할 수 있음
    - 일반적으로 중첩 else if문은 유지보수하기 힘들다는 문제가 있음

### 2.6. 반복문

- 반목문 종류
    - `whlie`
    - `for`
    - `for…in`
    - `for…of`
- `while`
    - 조건문이 참이기만 하면 문장을 계속해서 수행
      
        ```jsx
        let i = 0
        
        while (i < 6) {
          console.log(i)
          i += 1
        }
        
        // 0, 1, 2, 3, 4, 5
        ```
    
- `for`
    - 특정한 조건이 거짓으로 판별될 때까지 반복
      
        ```jsx
        for (let i = 0; i < 6; i++) {
          console.log(i)
        }
        
        // 0, 1, 2, 3, 4, 5
        ```
        
        - `for` 동작 예시
            1. 반복문 진입 및 변수 i 선언
            2. 조건문 평가 후 코드 블록 실행
            3. 코드 블록 실행 이후 i 값 증가
- `for…in`
    - 객체(object)의 속성을 순회할 때 사용
    - 배열도 순회 가능하지만 인덱스 순으로 순회한다는 보장이 없으므로 권장하지 않음 (???)
      
        ```jsx
        const fruits = {a: 'apple', b: 'banana'}
        
        for (const key in fruits) {
          console.log(key) // a, b
          console.log(fruits[key]) // apple, banana
        }
        ```
    
- `for…of`
    - 반복 가능한 객체를 순회할 때 사용
    - 반복 가능한 객체의 종류 : Array, Set, String 등
      
        ```jsx
        const numbers = [0, 1, 2, 3]
        
        for (const number of numbers) {
          console.log(number) // 0, 1, 2, 3
        }
        ```
    
- `for...in` vs `for...of`
  
    ```jsx
    const arr = [3, 5, 7]
    
    for (const i in arr) {
      console.log(i) // 0, 1, 2
    }
    
    for (const i of arr) {
      console.log(i) // 3, 5, 7
    }
    ```
    
    - `for…in`
        - 속성 이름을 통해 반복
        - 객체 순회 적합
        
        ```jsx
        // Array
        const numbers = [10, 20, 30]
        for (const number in numbers) {
          console.log(number) // 0, 1, 2
        }
        
        // Object
        const capitals = {
          korea: '서울',
          france: '파리',
          japan: '도쿄'
        }
        for (const capital in capitals) {
          console.log(capital) // korea, france, japan
        }
        ```
        
    - `for…of`
        - 속성 값을 통해 반복
        - iterable 순회 적합
        
        ```jsx
        // Array
        const numbers = [10, 20, 30]
        for (const number of numbers) {
          console.log(number) // 10, 20, 30
        }
        
        // Object
        const capitals = {
          korea: '서울',
          france: '파리',
          japan: '도쿄'
        }
        for (const capital of capitals) {
          console.log(capital) // TypeError: capitals is not iterable
        }
        ```
    
- [참고] `for...in`, `for...of`와 `const`
    - `for` (`for (let i = 0; i < arr.length; i++) {}`)
        - 최초 정의한 i를 재할당하면서 사용하기 때문에 `const` 사용하면 에러 발생
    - `for…in`, `for…of`
        - 재할당이 아니라 매 반복 시 해당 변수를 새로 정의하여 사용하므로 에러가 발생하지 않음
- 조건문과 반복문 정리
  
  
    | 키워드 | 종류 | 연관 키워드 | 스코프 |
    | --- | --- | --- | --- |
    | if | 조건문 | - | 블록 스코프 |
    | switch | 조건문 | case, break, default | 블록 스코프 |
    | while | 반복문 | break, continue | 블록 스코프 |
    | for | 반복문 | break, continue | 블록 스코프 |
    | for…in | 반복문 | 객체 순회 | 블록 스코프 |
    | for…of | 반복문 | iterable 순회 | 블록 스코프 |

## 3. 함수

- 함수 개요
    - 참조 타입 중 하나로써 function 타입에 속함
    - 자바스크립트에서 함수를 정의하는 방법은 주로 2가지로 구분
        - 함수 선언식 (function declaration)
        - 함수 표현식 (function expression)

### 3.1. 함수의 정의

- 함수 선언식
    - 일반적인 프로그래밍 언어의 함수 정의 방식
      
        ```jsx
        function add(num1, num2) {
          return num1 + num2
        }
        
        add(2, 7) // 9
        ```
    
- 함수 표현식
    - 표현식 내에서 함수를 정의하는 방식
    - 함수 표현식은 함수의 이름을 생략한 익명 함수로 정의 가능
      
        ```jsx
        const sub = function (num1, num2) {
          return num1 - num2
        }
        
        sub(7, 2) // 5
        ```
        
    - 표현식에서 함수 이름을 명시하는 것도 가능
        - 다만 이 경우 함수 이름은 호출에 사용되지 못하고 디버깅 용도로 사용
        
        ```jsx
        const mySub = function namedSub(num1, num2) {
          return num1 - num2
        }
        
        mySub(1, 2) // -1
        namedSub(1, 2) // ReferenceError: namedSub is not defined
        ```
    
- 기본 인자
    - 인자 작성 시 `=` 문자 뒤 기본 인자 선언 가능
      
        ```jsx
        const greeting = function (name = 'Anonymous') {
          return `Hi ${name}`
        }
        
        greeting() // Hi Anonymous
        ```
    
- 매개변수와 인자의 개수 불일치 허용
    - 매개변수보다 인자의 개수가 많을 경우
      
        ```jsx
        const noArgs = function () {
          return 0
        }
        
        noArgs(1, 2, 3) // 0
        
        const twoArgs = function (arg1, arg2) {
          return [arg1, arg2]
        }
        
        twoArgs(1, 2, 3) // [1, 2]
        ```
        
    - 매개변수보다 인자의 개수가 적을 경우
      
        ```jsx
        const threeArgs = function (arg1, arg2, arg3) {
          return [arg1, arg2, arg3]
        }
        
        threeArgs() // [undefined, undefined, undefined]
        threeArgs(1) // [1, undefined, undefined]
        threeArgs(1, 2) // [1, 2, undefined]
        ```
    
- Spread syntax (`…`)
    - 전개 구문
    - 전개 구문을 사용하면 배열이나 문자열과 같이 반복 가능한 객체를 배열의 경우는 요소, 함수의 경우는 인자로 확장할 수 있음
        - 배열과의 사용 (배열 복사)
          
            ```jsx
            let parts = ['shoulders', 'knees']
            let lyrics = ['head', ...parts, 'and', 'toes']
            /// ['head', 'shoulders', 'knees', 'and', 'toes']
            ```
            
        - 함수와의 사용 (Rest parameters)
            - 정해지지 않은 수의 매개변수를 배열로 받을 수 있음
            
            ```jsx
            function restOpr = function (arg1, arg2, ...restArgs) {
              return [arg1, arg2, restArgs]
            }
            
            restArgs(1, 2, 3, 4, 5) // [1, 2, [3, 4, 5]]
            restArgs(1, 2) // [1, 2, []]
            ```
            

### 3.2. 선언식과 표현식

- 함수의 타입
    - 선언식 함수와 표현식 함수 모두 타입은 function으로 동일
      
        ```jsx
        // 함수 표현식
        const add = function (args) {}
        
        // 함수 선언식
        function sub(args) {}
        
        console.log(typeof add) // function
        console.log(typeof sub) // function
        ```
    
- 호이스팅
    - 함수 선언식으로 정의한 함수는 var로 정의한 변수처럼 호이스팅 발생
        - 즉, 함수 호출 이후에 선언해도 동작
        
        ```jsx
        add(2, 7) // 9
        
        function add(num1, num2) {
          return num1 + num2
        }
        ```
        
    - 반면 함수 표현식으로 선언한 함수는 함수 정의 전에 호출 시 에러 발생
        - 함수 표현식으로 정의된 함수는 변수로 평가되어 변수의 scope 규칙을 따름
        
        ```jsx
        sub(7, 2) // Uncaught ReferenceError: Cannot access 'sub' before initialization
        
        const sub = function (num1, num2) {
          return num1 - num2
        }
        ```
    
- 선언식과 표현식 정리
  
  
    |  | 선언식 (declaration) | 표현식 (expression) |
    | --- | --- | --- |
    | 공통점 | 데이터 타입, 함수 구성 요소 (이름, 매개변수, 바디) | 데이터 타입, 함수 구성 요소 (이름, 매개변수, 바디) |
    | 차이점 | 익명 함수 불가능, 호이스팅 O | 익명 함수 가능, 호이스팅 X |
    | 비고 | - | Airbnb Style Guide 권장 방식 |

### 3.3. Arrow Function

- 화살표 함수
    - 함수를 비교적 간결하게 정의할 수 있는 문법
    - `function` 키워드와 중괄호를 이용한 구문을 짧게 사용하기 위해 탄생
        - `function` 키워드 생략 가능
        - 함수의 매개변수가 하나 뿐이라면 매개변수의 `()` 생략 가능
        - 함수의 내용이 한 줄이라면 `{}`와 `return`도 생략 가능
    - 화살표 함수는 항상 익명 함수 → 함수 표현식에서만 사용 가능
    - 명확성과 일관성을 위해 항상 인자 주위에는 괄호를 포함하는 것을 권장
    - 예시
      
        ```jsx
        const arrow1 = function (name) {
          return `hello, ${name}`
        }
        
        // 1. function 키워드 삭제
        const arrow2 = (name) => {return `hello, ${name}`}
        
        // 2. 인자가 1개일 경우에만 () 생략 가능
        const arrow2 = name => {return `hello, ${name}`}
        
        // 3. 함수 바디가 return을 포함한 표현식 1개일 경우에 {} & return 삭제 가능
        const arrow2 = name => `hello, ${name}`
        ```
        
    - 응용 예시
      
        ```jsx
        // 1. 인자가 없다면 () or _로 표시 가능
        let noArgs = () => 'No args'
        noArgs = _ => 'No args'
        
        // 2-1. object를 return한다면 return을 명시적으로 적음
        let returnObject = () => {return {key: 'value'}}
        
        // 2-2. return을 적지 않으려면 괄호를 붙여야 함
        returnObject = () => ({key: 'value'})
        ```
    
- 즉시 실행 함수 (IIFE, Immediately Invoked Function Expression)
    - 선언과 동시에 실행되는 함수
    - 함수의 선언 끝에 `()`를 추가하여 선언되자마자 실행하는 형태
        - `()`에 값을 넣어 인자로 넘겨줄 수 있음
    - 즉시 실행 함수는 선언과 동시에 실행되기 때문에 같은 함수를 다시 호출할 수 없음
        - 이러한 특징을 살려 초기화 부분에 많이 사용
    - 일회성 함수이므로 익명함수로 사용하는 것이 일반적
      
        ```jsx
        (function(num) {return num ** 3})(2) // 8
        
        (num => num ** 3)(2) // 8
        ```
        

## 4. 배열 & 객체

### 4.1. 배열 (Array)

- 배열
    - 키와 속성들을 담고 있는 참조 타입의 객체
    - 순서를 보장하는 특징
    - 주로 대괄호를 이용하여 생성하고, 0을 포함한 양의 정수 인덱스로 특정 값에 접근 가능
    - 배열의 길이는 `array.lenth` 형태로 접근 가능
        - 배열의 마지막 원소는 `array.length - 1`로 접근
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    
    console.log(numbers[0]) // 1
    console.log(numbers[-1]) // undefined
    console.log(numbers.length) // 5
    
    console.log(numbers[numbers.length - 1]) // 5
    console.log(numbers[numbers.length - 2]) // 4
    console.log(numbers[numbers.length - 3]) // 3
    console.log(numbers[numbers.length - 4]) // 2
    console.log(numbers[numbers.length - 5]) // 1
    ```
    

### 4.2. 배열 메서드 기초

- `array.reverse()`
    - 원본 배열 요소들의 순서를 반대로 정렬
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    numbers.reverse()
    console.log(numbers) // [5, 4, 3, 2, 1]
    ```
    
- `array.push(value)`
    - 배열의 가장 뒤에 요소 추가
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    numbers.push(100)
    console.log(numbers) // [1, 2, 3, 4, 5, 100]
    ```
    
- `array.pop()`
    - 배열의 마지막 요소 제거
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    numbers.pop()
    console.log(numbers) // [1, 2, 3, 4]
    ```
    
- `array.unshift(value)` & `array.shift(value)`
    - 배열의 가장 앞에 요소를 추가 또는 제거
- `array.includes(value)`
    - 배열에 특정 값이 존재하는지 판별 후 true 또는 false 반환
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    console.log(numbers.includes(1)) // true
    console.log(numbers.includes(100)) // false
    ```
    
- `array.indexOf(value)`
    - 배열에 특정 값이 존재하는지 확인 후 가장 첫 번째로 찾은 요소의 인덱스 반환
    - 해당 값이 없는 경우 -1 반환
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    let result
    
    result = numbers.indexOf(3)
    console.log(result) // 2
    
    result = numbers.indexOf(100)
    console.log(result) // -1
    ```
    
- `array.join([separator])`
    - 배열의 모든 요소를 연결하여 반환
    - 구분자는 선택적으로 지정 가능하며, 생략 시 쉼표를 기본 값으로 사용
    
    ```jsx
    const numbers = [1, 2, 3, 4, 5]
    let result
    
    result = numbers.join()
    console.log(result) // 1,2,3,4,5
    
    result = numbers.join('')
    console.log(result) // 12345
    
    result = numbers.join(' ')
    console.log(result) // 1 2 3 4 5
    
    result = numbers.join('-')
    console.log(result) // 1-2-3-4-5
    ```
    

### 4.3. 배열 메서드 심화

- Array Helper Methods
    - 배열을 순회하며 특정 로직을 수행하는 메서드
    - 메서드 호출 시 인자로 callback 함수를 받는 것이 특징
        - callback 함수 : 어떤 함수의 내부에서 실행될 목적으로 인자로 넘겨받는 함수
            - ex. django에서 path 함수에 전달되는 views.index 함수
- forEach
    - `array.forEach((element, index, array) => {})`
    - 인자로 주어지는 함수(콜백 함수)를 배열의 각 요소에 대해 한 번씩 실행
    - 콜백 함수는 3가지 매개변수로 구성
        - element : 배열의 요소
        - index : 배열 요소의 인덱스
        - array : 배열 자체
    - 반환 값 없음
    
    ```jsx
    const colors = ['red', 'blue', 'green']
    
    printFunc = function (color) {
      console.log(color)
    }
    colors.forEach(printFunc) // red, blue, green
    
    // 함수 정의를 인자로 넣기
    colors.forEach(function (color) {
      console.log(color)
    })
    
    // 화살표 함수 적용
    colors.forEach((color) => {
      console.log(color)
    })
    ```
    
- map
    - `array.map((element, index, array) => {})`
    - 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
    - 콜백 함수의 반환 값을 요소로 하는 새로운 배열 반환
    - 기존 배열 전체를 다른 형태로 바꿀 때 유용
    - forEach + return
- filter
- reduce
- find
- some
- every