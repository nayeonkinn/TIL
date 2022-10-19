## x1. REST API

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
        - 자원의 위치로 자원을 식별 → URL
        - 고유한 이름으로 자원을 식별 → URN
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
    - URL 구조
      
        ![Screen Shot 2022-10-18 at 0.03.41.png](06%20REST%20API%209693547e5682496e99710dcbce9b95ab/Screen_Shot_2022-10-18_at_0.03.41.png)
        
        - URL은 위와 같이 여러 부분으로 구성되며 일부는 필수, 일부는 선택
        - Scheme (or protocol)
            - `**https**://www.example.com:80/path/to/myfile.html/?key=value#quick-start`
            - 브라우저가 리소스를 요청하는 데 사용해야 하는 프로토콜
            - URL의 첫 부분은 브라우저가 어떤 규약을 사용하는지를 나타냄
            - 기본적으로 웹은 HTTP(S)를 요구하며 메일을 열기 위한 `mailto:`, 파일을 전송하기 위한 `ftp:` 등 다른 프로토콜도 존재
        - Authority
            - `https://**www.example.com:80**/path/to/myfile.html/?key=value#quick-start`
            - Scheme 다음은 문자 패턴 `://`으로 구분된 Authority(권한)이 작성됨
            - Authority는 domain과 port를 모두 포함하며 `:`으로 구분
        - Domain Name
            - `https://**www.example.com**:80/path/to/myfile.html/?key=value#quick-start`
            - 요청 중인 웹 서버
            - 어떤 웹 서버가 요구되는지를 가리키며 직접 IP 주소를 사용하는 것도 가능하나 편의상 주로 Domain Name으로 사용
            - google.com의 IP 주소는 142.251.42.142
        - Port
            - `https://www.example.com:**80**/path/to/myfile.html/?key=value#quick-start`
            - 웹 서버의 리소스에 접근하는데 사용되는 기술적인 문(Gate)
            - HTTP 프로토콜의 표준 포트는 다음과 같고 생략 가능 (나머지는 생략 불가능)
                - HTTP - 80
                - HTTPS - 443
            - Django의 경우 8000(80 + 00)이 기본 포트로 설정되어 있음
        - Path
            - `https://www.example.com:80**/path/to/myfile.html**/?key=value#quick-start`
            - 웹 서버의 리소스 경로
            - 초기에는 실제 파일이 위치한 물리적 위치를 나타냈지만, 오늘날은 실제 위치가 아닌 추상화된 형태의 구조를 표현
                - ex. `/articles/create/`가 실제 articles 폴더 안에 create 폴더 안을 나타내는 것은 아님
        - Parameters
            - `https://www.example.com:80/path/to/myfile.html/**?key=value**#quick-start`
            - 웹 서버에 제공하는 추가적인 데이터
            - 파라미터는 `&` 기호로 구분되는 key-value 쌍 목록
            - 서버는 리소스를 응답하기 전에 이러한 파라미터를 사용하여 추가 작업을 수행할 수 있음
        - Anchor
            - `https://www.example.com:80/path/to/myfile.html/?key=value**#quick-start**`
            - 리소스의 다른 부분에 대한 앵커
                - 앵커 : 하이퍼링크와 비슷한 기능을 하는 인터넷 상의 다른 문서와 연결된 문자 혹은 그림
            - 리소스 내부 일종의 북마크를 나타내며, 브라우저에 해당 북마크 지점에 있는 콘텐츠를 표시
                - ex. HTML 문서에서 브라우저는 앵커가 정의한 지점으로 스크롤
            - fragment identifier(부분 식별자)라고 부르는 `#` 이후 부분은 서버에 전송되지 않음
                - ex. `#quick-start`는 서버에 전달되지 않고 브라우저에게 해당 지점으로 이동할 수 있도록 함
- [참고] URN
    - Uniform Resource Name (통합 자원 이름)
    - URL과 달리 자원의 위치에 영향을 받지 않는 유일한 이름 역할을 함 (독립적 이름)
    - URL의 단점을 극복하기 위해 등장했으며 자원이 어디에 위치한지 여부와 관계없이 이름만으로 자원을 식별
        - 하지만 이름만으로 실제 리소스를 찾는 방법은 보편화되어 있지 않아 현재는 URL을 대부분 사용
    - 예시
        - ISBN(국제표준 도서번호) : 국제적으로 책에 붙이는 고유 식별자
        - ISAN(국제표준 시청각 자료번호) : 도서의 ISBN과 유사한 시청각 작품 및 관련 버전의 고유 식별자

### 1.3. REST API

## 2. Response JSON

## 3. Django REST framework

### 3.1. Single Model

### 3.2. N:1 Relation