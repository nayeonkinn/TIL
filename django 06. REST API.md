## 1. REST API

### 1.1. HTTP

- HTTP란?
    - HyperText Transfer Protocol
    - HTML 문서와 같은 리소스(자원)들을 가져올 수 있도록 하는 프로토콜(규칙, 약속)
        - 리소스 : HTTP 요청의 대상
    - 웹 상에서 컨텐츠를 전송하기 위한 약속이자 웹에서 이루어지는 모든 데이터 교환의 기초
    - 클라이언트-서버 프로토콜이라고도 부름
    - 클라이언트와 서버는 다음과 같은 개별적인 메시지 교환에 의해 통신
        - 요청(request) : 클라이언트에 의해 전송되는 메시지
        - 응답(response) : 서버에서 응답으로 전송되는 메시지
- HTTP 특징
    - Stateless(무상태)
        - 동일한 연결에서 연속적으로 수행되는 두 요청 사이에 링크가 없음
        - 응답을 마치고 연결을 끊는 순간 클라이언트와 서버 간의 통신이 끝나며 상태 정보가 유지되지 않음
        - 이는 특정 페이지와 일관되게 상호작용 하려는 사용자에게 문제가 될 수 있으며, 이를 해결하기 위해 쿠키와 세션을 사용해 서버 상태를 요청과 연결하도록 함
- HTTP Request Methods
    - 리소스에 대한 행위(수행하고자 하는 동작)를 정의
        - 즉, 리소스에 대해 수행할 작업을 나타내는 메서드 모음을 정의
    - HTTP verbs라고도 부름
    - ex. `GET`, `POST`, `PUT`, `DELETE` 등
- 대표 HTTP Request Methods
    - `GET`
        - 서버에 리소스의 표현을 요청
        - GET을 사용하는 요청은 데이터만 검색해야 함
    - `POST`
        - 데이터를 지정된 리소스에 제출
        - 서버의 상태를 변경
    - `OUT`
        - 요청한 주소의 리소스를 수정
    - `DELETE`
        - 지정된 리소스를 삭제
- HTTP response status codes
    - 특정 HTTP 요청이 성공적으로 완료되었는지 여부를 나타냄
    - 응답은 5개의 그룹으로 나뉨
        - Informational responses (100~199)
        - Successful responses (200~299)
        - Redirection messages (300~399)
        - Client error responses (400~499)
        - Server error responses (500~599)

### 1.2. URI

- 웹에서의 리소스 식별
    - HTTP 요청의 대상을 리소스라고 함
    - 리소스는 문서, 사진 또는 기타 어떤 것이든 될 수 있음
    - 각 리소스는 URI로 식별됨
- URI
    - Uniform Resource Identifier (통합 자원 식별자)
    - 인터넷에서 하나의 리소스를 가리키는 문자열
    - 종류
        - URL : 가장 일반적인 URI로 웹 주소로 알려짐
        - URN : 특정 이름 공간에서 이름으로 리소스를 식별
- URL
    - Uniform Resource Locator (통합 자원 위치)
    - 웹에서 주어진 리소스의 주소
    - 네트워크 상에 리소스가 어디 있는지(주소)를 알려주기 위한 약속
        - 리소스는 HTML, CSS, 이미지 등이 될 수 있음

## 2. Response JSON

## 3. Django REST framework

### 3.1. Single Model

### 3.2. N:1 Relation