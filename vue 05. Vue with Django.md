# 1. Vue with DRF

- 개요
  - 서버와 클라이언트 통신 방법 이해하기
  - CORS 이슈 이해하고 해결하기
  - DRF Auth System 이해하기
  - Vue와 API server 통신하기

### 1.1. Server & Client

- 서버
  - 클라이언트에게 정보와 서비스를 제공하는 컴퓨터 시스템
  - 서비스 전체를 제공 == Django Web Service
    - 장고를 통해 전달받은 HTML에는 하나의 웹 페이지를 구성할 수 있는 모든 데이터가 포함
    - 즉, 서버에서 모든 내용을 렌더링하여 하나의 HTML 파일로 제공
    - 정보를 포함한 web 서비스를 구성하는 모든 내용을 서버 측에서 제공
  - 정보를 제공 == DRF API Service
    - 장고를 통해 관리하는 정보만을 클라이언트에게 제공
    - DRF를 사용하여 JSON으로 변환
- 클라이언트
  - 서버가 제공하는 서비스에 적절한 요청을 통해 서버로부터 반환 받은 응답을 사용자에게 표현하는 기능을 가진 프로그램 혹은 시스템
  - 서버가 제공하는 서비스에 적절한 요청
    - 서버가 정의한 방식대로 요청 인자를 넘겨 요청
    - 서버는 정상적인 요청에 적합한 응답 제공
  - 모델과 다르게 잘못된 필드 명으로 요청을 보낼 경우 처리할 수 없음
  - 서버로부터 반환 받은 응답을 사용자에게 표현
    - 사용자의 요청에 적합한 데이터를 서버에 요청하여 응답 받은 결과로 적절한 화면을 구성
- 서버 & 클라이언트
  - 서버는 정보와 서비스를 제공
    - DB와 통신하며 데이터를 생성, 조회, 수정, 삭제를 담당
    - 요청을 보낸 클라이언트에게 정상적인 요청이었다면 처리한 결과를 응답
  - 클라이언트는 사용자의 정보 요청을 처리, 서버에게 응답 받은 정보를 표현
    - 서버에게 정보(데이터)를 요청
    - 응답 받은 정보를 가공하여 화면에 표현

## 2. CORS

### 2.1. Cross-Origin Resource Sharing

- What Happened?
  - 브라우저가 요청을 보내고 서버의 응답이 브라우저에 도착
    - 서버의 로그는 200(정상) 반환
    - 즉, 서버는 정상적으로 응답했지만 브라우저가 막은 것
  - 보안 상의 이유로 브라우저는 동일 출처 정책(SOP)에 의해 다른 출처의 리소스와 상호작용하는 것을 제한함
- SOP (Same - Origin Policy)
  - 동일 출처 정책
  - 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 보안 방식
  - 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄임
- Origin - 출처
  - URL의 Protocol, Host, Port를 모두 포함하여 출처라고 부름
  - Path 제외 아래 세 영역이 일치하는 경우에만 동일 출처로 인정
    - http(Scheme/Protocol)://localhost(Host):3000(Port)/posts/3(Path)
  - Same Origin 예시
    - http://localhost:3000/posts/3을 기준으로 출처 비교

            | URL | 결과 | 이유 |
            | --- | --- | --- |
            | http://localhost:3000/posts/ | 성공 | path만 다름 |
            | http://localhost:3000/comments/3 | 성공 | path만 다름 |
            | https://localhost:3000/posts/3 | 실패 | protocol이 다름 |
            | http://localhost:80/posts/3 | 실패 | port가 다름 |
            | https://domain:3000/posts/3 | 실패 | protocol과 host가 다름 |

- CORS - 교차 출처 리소스 공유
  - 추가 HTTP Header를 사용하여, 특정 출처에서 실행 중인 웹 어플리케이션이 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제
    - 어떤 출처에서 자신의 컨텐츠를 불러갈 수 있는지 서버에 지정할 수 있는 방법
  - 리소스가 자신의 출처와 다를 때 교차 출처 HTTP 요청 실행
    - 다른 출처의 리소스를 가져오기 위해서는 이를 제공하는 서버가 브라우저에게 다른 출처지만 접근해도 된다는 사실을 알려야 함
    - 교차 출처 리소스 공유 정책 (CORS policy)
- CORS policy - 교차 출처 리소스 공유 정책
  - 다른 출처에서 온 리소스를 공유하는 것에 대한 정책
  - CORS policy에 위배되는 경우 브라우저에서 해당 응답 결과를 사용하지 않음
    - 서버에서 응답을 주더라도 브라우저에서 거절
  - 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS header를 포함한 응답을 반환해야 함
    - 서버가 일을 하나 더 해줘야 한다!

### 2.2. How to set CORS

- How to set CORS
  - CORS 표준에 의해 추가된 HTTP Response Header를 통해 통제 가능
  - HTTP Response Header 예시
    - Access-Control-Allow-Origin / Access-Control-Allow-Credentials / Access-Control-Allow-Headers / Access-Control-Allow-Methods
  - Access-Control-Allow-Origin
    - 단일 출처를 지정하여 브라우저가 해당 출처가 리소스에 접근하도록 허용
- django-cors-headers library 사용하기
  - django-cors-headers github에서 내용 확인
  - 응답에 CORS header를 추가해주는 라이브러리
  - 다른 출처에서 장고 어플리케이션에 대한 브라우저 내 요청을 허용함
  - 라이브러리 설치 및 requirements.txt 업데이트
  - App 추가 및 MIDDLEWARE 추가 주석 해제
    - 주의 : CorsMiddleware는 가능한 한 CommonMiddleware보다 먼저 정의되어야 함
  - CORS_ALLOWED_ORIGINS에 교차 출처 자원 공유를 허용할 도메인 등록
    - 만약 모든 Origin을 허용하고자 한다면 `CORS_ALLOWED_ALL_ORIGINS = True`

### 2.3. Vue with DRF (feat. CORS)

- [참고] 지금의 요청 방식은 효율적인가?
  - 비효율적인 부분이 존재
    - 전체 게시글 정보를 요청해야 새로 생성된 게시글을 확인할 수 있음
    - 만약 vuex state를 통해 전체 게시글 정보를 관리하도록 구성한다면?
    - 내가 새롭게 생성한 게시글은 확인할 수 있겠지만 나 이외의 유저들이 새롭게 생성한 게시글은 언제 불러와야 할까?
    - 무엇을 기준으로 새로운 데이터가 생겼다는 것을 확인할 수 있을까?
  - 내가 구성하는 서비스에 따라 데이터 관리 방식을 고려해 보아야 함

## 3. DRF Auth System

### 3.1. Authentication & Authorization

- Authentication - 인증, 입증
  - 자신이라고 주장하는 사용자가 누구인지 확인하는 행위
    - 즉, 내가 누구인지를 확인하는 과정
  - 모든 보안 프로세스의 첫 번째 단계 (가장 기본 요소)
  - 401 Unauthorized
    - 비록 HTTP 표준에서는 미승인(unauthorized)을 명확히 하고 있지만, 의미상 이 응답은 비인증(unauthenticated)을 의미
- Authorization - 권한 부여, 허가
  - 사용자에게 특정 리소스 또는 기능에 대한 액세스 권한을 부여하는 과정(절차)
  - 보안 환경에서 권한 부여는 항상 인증이 먼저 필요함
    - 사용자는 조직에 대한 액세스 권한을 부여 받기 전에 먼저 자신의 ID가 진짜인지 먼저 확인해야 함
  - 서류의 등급, 웹 페이지에서 글을 조회 & 삭제 & 수정할 수 있는 방법, 제한 구역
    - 인증이 되었어도 모든 권한을 부여받는 것은 아님
  - 403 Forbidden
    - 401과 다른 점은, 서버는 클라이언트가 누구인지 알고 있음
- Authentication and authorization work together
  - 회원가입 후 로그인 시 서비스를 이용할 수 있는 권한 생성
    - 인증 이후에 권한이 따라오는 경우가 많음
  - 단, 모든 인증을 거쳐도 권한이 동일하게 부여되는 것은 아님
    - 장고에서 로그인을 했더라도 다른 사람의 글까지 수정/삭제가 가능하진 않음
  - 세션, 토큰, 제3자를 활용하는 등의 다양한 인증 방식이 존재

### 3.2. How to authentication determined

- 인증 여부 확인 방법
  - DRF 공식문서에서 제안하는 인증 절차 방법
    -
  - settings.py에 작성하여야 할 설정
    - 기본적인 인증 절차를 어떠한 방식으로 둘 것인가를 설정하는 것
    - 예시의 2가지 방법 외에도 각 프레임워크마다 다양한 인증 방식이 있음
  - 우리가 사용할 방법은 DRF가 기본으로 제공해주는 인증 방식 중 하나인 TokenAuthentication
  - 모든 상황에 대한 인증 방식을 정의하는 것이므로, 각 요청에 따라 다른 인증 방식을 거치고자 한다면 다른 방식이 필요
  - view 함수마다(각 요청마다) 다른 인증 방식을 설정하고자 한다면 decorator 활용
  - [참고] permisson_classes
    - 권한 관련 설정
    - 권한 역시 특정 view 함수마다 다른 접근 권한을 요구할 수 있음
- 다양한 인증 방식
  - BasicAuthentication
  - SeddionAuthentication
  - RemoteUserAuthentication
  - TokenAuthentication
- TokenAuthentication 사용 방법
  - INSTALLED_APPS에 rest_framework.authtoken 등록
- 토큰 생성 및 관리 문제점
  - 기본 제공 방식에서 고려하여야 할 사항들
    - 토큰 생성 시점
    - 생성한 토큰 관리 방법
    - 유저와 관련된 각종 기능 관리 방법
      - 회원가입, 로그인, 회원 정보 수정, 비밀번호 변경 등

### 3.3. dj-rest-auth

- dj-rest-auth
  - 회원가입, 인증(소셜미디어 인증 포함), 비밀번호 재설정, 사용자 세부 정보 검색, 회원 정보 수정 등을 위한 REST API end point 제공
  - 주의 : django-rest-auth는 더 이상 업데이트를 지원하지 않음 → dj-rest-auth 사용
- dj-rest-auth 사용 방법
  - 패키지 설치
  - App 등록
  - url 등록
- 시작하기 전에
  - auth.User를 accounts.User로 변경 필요
  - auth.User로 설정된 DB 제거
  - my_api/settings.py 주석 해제

### 3.4. Permission setting

- Permission setting
  - 권한 설정 방법 확인
    - DRF 공식 문서 > API Guide > Permissions 확인

## 4. DRF Auth with Vue

## 5. DRF-spectacular