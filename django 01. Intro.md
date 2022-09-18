## 1. Intro

### 1.1. Framework

- Framework
    - 누군가 만들어 놓은 코드를 재사용하는 것은 이미 익숙한 개발 문화
        - 웹 서비스에도 적용 가능
    - 전 세계의 수많은 개발자들이 수없이 많이 개발해 봤고, 그 과정에서 자주 사용되는 부분들을 재사용할 수 있게 좋은 구조의 코드로 만들어 두었음
        - 그러한 코드들을 모아 놓은 것 = 프레임워크
        - 서비스 개발에 필요한 기능들을 미리 구현해서 모아 놓은 것
    - Frame(뼈대, 틀) + Work(일하다)
        - 제공받은 도구들과 뼈대, 규약을 가지고 무언가를 만드는 일
        - 특정 프로그램을 개발하기 위한 여러 도구들과 규약을 제공하는 것
    - 소프트웨어 프레임워크 : 복잡한 문제를 해결하거나 서술하는 데 사용되는 기본 개념 구조
    - Framework를 잘 사용하기만 하면 웹 서비스 개발에 있어서 모든 것들을 하나부터 열까지 직접 개발할 필요 없이 만들고자 하는 본질(로직)에 집중해 개발할 수 있음
        - 소프트웨어의 생산성과 품질을 높임
- 웹 프레임워크 인기 순위 (2020 Github Star 수 기준)
    1. Laravel
    2. Django
    3. Flask
    4. Spring Boot
    5. Express
    6. Ruby on Rails
    7. Meteor
    8. Nest
    9. Koa
- Django 장점
    - Python으로 작성된 프레임워크
        - 언어의 강력함과 거대한 커뮤니티
    - 수많은 유용한 기능들
    - 검증된 웹 프레임워크
        - 화해, Toss, 두나무, 당근마켓, 요기요 등
        - 유명한 많은 서비스들이 사용한다는 것 = 안정적으로 서비스를 할 수 있다

### 1.2. Web

- WWW (World Wide Web)
    - 전 세계에 퍼져 있는 거미줄 같은 연결망
    - 인터넷을 이용한다는 건 전세계의 컴퓨터가 연결되어 있는 하나의 인프라를 이용하는 것
- 연결되어 있는 세계
    - 우리가 구글 홈페이지에 접속할 수 있는 이유는 구글 본사 컴퓨터와 우리 컴퓨터 간에 통신이 연결되어 있기 때문
    - 전세계는 아주 두껍고 튼튼한 해저케이블로 연결되어 있음
        - 해양 생물로 인해 문제가 생긴다면 인터넷이 잠시 느려지거나 마비될 수 있음
    - 세계는 촘촘하고 거대한 유선으로 연결되어 있고 많은 전봇대를 거쳐 집으로 인터넷이 연결됨
    - 유선 연결의 한계
        - 오지, 개발도상국 등에는 충분한 인프라가 없음
        - 정보의 빈곤 발생
    - 전세계를 무선으로 연결 → 스타링크 프로젝트 by Space X
        - 지구를 아주 많은 소형 위성으로 감싸서 케이블이 아닌 위성끼리 데이터 교환
        - 문제점
            - Starlink Train : 스타링크 위성으로 인해 가려지는 천체
            - 우주 쓰레기

### 1.3. 클라이언트와 서버

- 클라이언트-서버 구조
    - 우리가 사용하는 대부분의 웹 서비스는 클라이언트-서버 구조를 기반으로 동작
    - 클라이언트와 서버 역시 하나의 컴퓨터이며 이들의 상호작용은 다음과 같음
        - CLIENT → requests → SERVER
        - SERVER → responses → CLIENT
    - 클라이언트
        - 웹 사용자의 인터넷에 연결된 장치 (ex. wi-fi에 연결된 컴퓨터 또는 모바일)
        - Chrome 또는 Firefox와 같은 웹 브라우저
        - 서비스를 요청하는 주체
    - 서버
        - 웹 페이지, 사이트 또는 앱을 저장하는 컴퓨터
        - 클라이언트가 웹 페이지에 접근하려고 할 때 서버에서 클라이언트 컴퓨터로 웹 페이지 데이터를 응답해 사용자의 웹 브라우저에 표시됨
        - 요청에 대해 서비스를 응답하는 주체
    - 상호작용 예시 : 구글 홈페이지 접속
        - 세계 어딘가에 있는 인터넷에 연결된 구글 컴퓨터에게 ‘구글 홈페이지.html’ 파일을 달라고 요청하는 것
        - 구글 컴퓨터는 요청을 받고 인터넷을 통해서 html 파일을 우리 컴퓨터에게 응답해줌
        - 웹 브라우저가 전달받은 html 파일을 우리가 볼 수 있도록 해석해줌
        - 여기서 ‘구글 홈페이지.html’ 을 달라고 요청한 컴퓨터, 웹 브라우저를 클라이언트, 파일을 제공한 컴퓨터, 프로그램을 서버라고 함
            - 어떠한 자원을 달라고 요청하는 쪽 → 클라이언트
            - 자원을 제공해주는 쪽 → 서버
- Django
    - 우리가 사용하는 웹은 클라이언트-서버 구조로 이루어짐
    - 이중 Django는 서버를 구현하는 웹 프레임워크

### 1.4. 웹 브라우저와 웹 페이지

- 웹 브라우저
    - 웹에서 페이지를 찾아 보여주고, 사용자가 하이퍼링크를 통해 다른 페이지로 이동할 수 있도록 하는 프로그램
    - 웹 페이지 파일을 우리가 보는 화면으로 바꿔주는 렌더링 프로그램
    - 예시
        - 우리가 보고 있는 웹 페이지는 HTML 문서 파일 하나
        - ex. 구글
            - 우리는 구글 로고가 있는 예쁜 화면을 보지만 사실 빼곡한 코드로 작성된 html 문서를 서버로부터 전달받음
            - 이 코드를 받아서 우리가 보는 화면을 바꿔주는 것이 웹 브라우저
        - HTML, CSS, JS 등의 코드를 읽어 실제 사람이 볼 수 있는 화면으로 만들어 줌
- 웹 페이지
    - 웹에 있는 문서
        - 우리가 보는 화면 한 장 한 장이 웹 페이지
    - 종류
        - 정적 웹 페이지
        - 동적 웹 페이지
    - 정적 웹 페이지 (Static Web Page)
        - 있는 그대로를 제공하는 것 (served as-is)
        - 한 번 작성된 HTML 파일의 내용이 변하지 않고 모든 사용자에게 동일한 모습으로 전달되는 것
            - = 서버에 미리 저장된 HTML 파일 그대로 전달된 웹 페이지
            - = 같은 상황에서 모든 사용자에게 동일한 정보를 표시
    - 동적 웹 페이지 (Dynamic Web Page)
        - 사용자의 요청에 따라 웹 페이지에 추가적인 수정이 되어 클라이언트에게 전달되는 웹 페이지
        - 웹 페이지의 내용을 바꿔주는 주체 = 서버
            - 서버에서 동작하고 있는 프로그램이 웹 페이지를 변경해줌
            - 파일을 처리하고 데이터베이스와의 상호작용이 이루어짐
            - 사용자의 요청을 받아서 적절한 응답을 만들어주는 프로그램을 쉽게 만들 수 있게 도와주는 프레임워크 → Django
        - 다양한 서버 사이드 프로그래밍 언어(python, java, c++ 등) 사용 가능
            - 이중 python을 이용하는 프레임워크 → Django

## 2. Django 구조

### 2.1. Design Pattern

- 디자인 패턴
    - ex. 광안대교 : 현수교
    - 각기 다른 기능을 가진 다양한 응용 소프트웨어를 개발할 때 공통적인 설계 문제가 존재하며, 이를 처리하는 해결책 사이에도 공통점 존재
        - 이러한 유사점 → 패턴
- 소프트웨어 디자인 패턴
    - 소프트웨어도 수십년간 전 세계의 개발자들이 계속 만들다 보니 자주 사용되는 구조와 해결책이 있다는 것을 알게 됨
    - 자주 사용되는 소프트웨어의 구조를 소수의 뛰어난 엔지니어가 마치 건축의 공법처럼 일반적인 구조화를 해둔 것
    - 클라이언트-서버 구조도 소프트웨어 디자인 패턴 중 하나
    - 목적
        - 특정 문맥에서 공통적으로 발생하는 문제에 대해 재사용 가능한 해결책 제시
        - 프로그래머가 어플리케이션이나 시스템을 디자인할 때 발생하는 공통된 문제들을 해결하는데 형식화된 가장 좋은 관행
    - 장점
        - 효율적인 커뮤니케이션

### 2.2. MVC & MTV

- Django 디자인 패턴
    - MVC 패턴을 기반으로 한 MTV 패턴 사용
    - 두 패턴의 큰 차이점은 없으며 일부 역할에 대해 부르는 이름이 다름
      
      
        | MVC | MTV (장고) | 역할 |
        | --- | --- | --- |
        | Model | Model | 데이터 관련 |
        | View | Template | 화면 관련 |
        | Controller | View | 중간 처리 및 응답 반환 |
- MVC 디자인 패턴
    - MVC : Model-View-Controller
    - 데이터 및 논리 제어를 구현하는데 널리 사용되는 소프트웨어 디자인 패턴
    - 하나의 프로그램을 세가지 역할로 구분한 개발 방법론
        - Model : 데이터와 관련된 로직을 관리
        - View : 레이아웃과 화면을 처리
        - Controller : 명령을 Model과 View 부분으로 연결
    - 목적
        - 더 나은 업무 분리와 향상된 관리 제공
        - 각 부분을 독립적으로 개발할 수 있어 하나를 수정하고 싶을 때 모두 건들지 않아도 됨
            - = 개발 효율성 및 유지보수가 쉬워짐
            - = 다수의 멤버로 개발하기 용이함
- MTV 디자인 패턴
    - Model
        - 데이터와 관련된 로직을 관리
        - 응용 프로그램의 데이터 구조를 정의하고 데이터베이스의 기록 관리
        - MVC 패턴에서 Model 역할에 해당
    - Template
        - 레이아웃과 화면을 처리
        - 화면상의 사용자 인터페이스 구조와 레이아웃을 정의
        - MVC 패턴에서 View 역할에 해당
    - View
        - Model & Template과 관련한 로직을 처리해서 응답 반환
        - 클라이언트의 요청에 대해 처리를 분기하는 역할
        - 동작 예시
            - 데이터가 필요하다면 Model에 접근해서 데이터를 가져오고
            - 가져온 데이터를 Template로 보내 화면을 구성하고
            - 구성된 하면을 응답으로 만들어 클라이언트에게 반환
        - MVC 패턴에서 Controller 역할에 해당

## 3. Django

### 3.1. 기본 설정

- 가상환경
    - 생성 : `python -m venv [가상환경이름]`
        - 이름은 아무런 역할을 하지 않아서 일반적으로 venv로 설정
    - 활성화 : `source [가상환경이름]/Script/activate`
        - MacOS : `source [가상환경이름]/bin/activate`
    - 비활성화 : `deactivate`
    - 가상환경 확인 : `pip list`
- 설치
    - 설치 전 가상환경 설정 및 활성화를 마치고 진행
    - Django 4.0 릴리즈로 인해 3.2(LTS) 버전을 명시해서 설치
        - `pip install django==3.2.13`
        - 4.0 릴리즈 이후(21년 12월) 버전을 명시하지 않으면 4.0 버전으로 설치되니 주의
    - 패키지 목록 생성
        - `pip freeze > requirements.txt`
        - 이후 `pip install -r requirements.txt`로 한번에 설치 가능
- [참고] LTS
    - Long Term Support (장기 지원 버전)
    - 일반적인 경우보다 장기간에 걸쳐 지원하도록 고안된 소프트웨어 버전
    - 컴퓨터 소프트웨어의 제품 수명주기 관리 정책
    - 배포자는 LTS 확정을 통해 장기적이고 안정적인 지원 보장
- 프로젝트
    - 프로젝트 생성
        - `django-admin startproject firstpjt .`
        - 프로젝트 이름에는 파이썬이나 장고에서 사용 중인 키워드 및 하이픈(-) 사용 불가
        - 온점 붙이지 않을 경우 현재 디렉토리에 프로젝트 디렉토리를 새로 생성하게 됨
    - 서버 실행
        - `python manage.py runserver`
        - 실행 후 메인 페이지 확인 가능
- 프로젝트 구조
  
  
    | firstpjt/ | __init__.py |
    | --- | --- |
    |  | asgi.py |
    |  | settings.py |
    |  | urls.py |
    |  | wsgi.py |
    | manage.py |  |
    - __init__.py
        - 파이썬에게 이 디렉토리를 하나의 파이썬 패키지로 다루도록 지시
        - 별도로 추가 코드를 작성하지 않음
    - asgi.py
        - Asynchronous(비동기) Server Gateway Interface
        - 장고 어플리케이션이 비동기식 웹 서버와 연결 및 소통하는 것을 도움
        - 추후 배포 시에 사용하며 지금은 수정하지 않음
    - settings.py
        - 장고 프로젝트 설정 관리
    - urls.py
        - 사이트의 url과 적절한 views의 연결 지정
    - wsgi.py
        - Web Server Gateway Interface
        - 장고 어플리케이션이 웹 서버와 연결 및 소통하는 것을 도움
        - 추후 배포 시에 사용하며 지금은 수정하지 않음
    - manage.py
        - 장고 프로젝트와 다양한 방법으로 상호작용하는 커맨드라인 유틸리티
        - `python manage.py <command> [options]`
- 어플리케이션
    - 어플리케이션 생성
        - `python manage.py startapp articles`
        - 일반적으로 앱 이름은 복수형으로 작성하는 것을 권장
    - 어플리케이션 등록
      
        ```python
        # settings.py
        
        INSTALLED_APPS = [
            'articles',
            'django.contrib.admin',
            'django.contrib.auth',
            'django.contrib.contenttypes',
            'django.contrib.sessions',
            'django.contrib.messages',
            'django.contrib.staticfiles',
        ]
        ```
        
        - 프로젝트에서 앱을 사용하기 위해서는 반드시 INSTALLED_APPS 리스트에 앱을 추가해야 함
        - INSTALLED_APPS
            - django installation에 활성화된 모든 앱을 지정하는 문자열 목록
- 어플리케이션 구조
  
  
    | articles/ | migrations/ |
    | --- | --- |
    |  | __init__.py |
    |  | admin.py |
    |  | apps.py |
    |  | models.py |
    |  | tests.py |
    |  | views.py |
    - admin.py
        - 관리자용 페이지를 설정
    - apps.py
        - 앱의 정보가 작성된 곳
        - 별도의 추가 코드를 작성하지 않음
    - models.py
        - 앱에서 사용하는 모델을 정의
        - MTV 패턴의 M에 해당
    - tests.py
        - 프로젝트의 테스트 코드 작성
    - views.py
        - view 함수들이 정의되는 곳
        - MTV 패턴의 V에 해당
- 프로젝트 vs 어플리케이션
    - 프로젝트
        - collection of apps
        - 프로젝트에는 여러 앱이 포함될 수 있음
        - 앱은 여러 프로젝트에 있을 수 있음
    - 어플리케이션
        - 실제 요청을 처리하고 페이지를 보여주는 등의 역할 담당
        - 일반적으로 하나의 역할 및 기능 단위로 작성하는 것을 권장
- 어플리케이션 주의사항
    - 반드시 생성 후 등록
        - INSTALLED_APPS에 먼저 작성하고 생성 시 앱이 생성되지 않음 (중복 앱으로 판단)
    - INSTALLED_APPS 순서
        - 순서
            1. Local apps (직접 선언한 앱)
            2. Third party apps (외부 라이브러리)
            3. Django apps (장고 기본 라이브러리)
        - 순서를 지키지 않아도 수업 과정에서는 문제가 없지만 추후 advanced 내용 대비하기 위해 지키는 것을 권장

### 3.2. 요청과 응답

- 코드 작성 순서
    - 데이터의 흐름에 따라 URL → VIEW → TEMPLATE 순으로 코드 작성
      
      
        | URL | path('index/', views.index) |
        | --- | --- |
        | View | def index(request):
            return render(request, 'index.html') |
        
        | Template | articles/templates/index.html |
- URLs
  
    ```python
    # urls.py
    
    from django.contrib import admin
    from django.urls import path
    from articles import views
    
    urlpatterns = [
        path('admin/', admin.site.urls),
        path('index/', views.index),
    ]
    ```
    
- Views
  
    ```python
    # articles/views.py
    
    def index(request):
        return render(request, 'index.html')
    ```
    
    - HTTP 요청을 수신하고 HTTP 응답을 반환하는 함수 작성
    - Template에게 HTTP 응답 서식을 맡김
    - `render()`
        - 주어진 템플릿을 주어진 컨텍스트 데이터와 결합하고 렌더링 된 텍스트와 함께 HttpResponse 객체를 반환
        - `render(requst, template_name, context)`
            - request : 응답을 생성하는 데 사용되는 요청 객체
            - template_name : 템플릿의 전체 이름 또는 경로
            - context : 템플릿에서 사용할 데이터 (딕셔너리 타입)
- Templates
    - 실제 내용을 보여주는데 사용되는 파일
    - 파일의 구조나 레이아웃을 정의
    - Template 파일의 기본 경로 : app_name/templates/
        - 템플릿 폴더 이름은 반드시 templates라고 지정해야 함
- [참고] 추가 설정
  
    ```python
    # settings.py
    
    LANGUAGE_CODE = 'ko-kr'
    TIME_ZONE = 'Asia/Seoul'
    USE_I18N = True # 지금은 수정하지 않음
    USE_L10N = True # 상동
    USE_TZ = True # 상동
    ```
    
    - LANGUAGE_CODE
        - 모든 사용자들에게 제공되는 번역을 결정
        - 이 설정이 적용되려면 USE_I18N이 활성화되어 있어야 함
    - TIME_ZONE
        - 데이터베이스 연결의 시간대를 나타내는 문자열 지정
        - USE_TZ가 True이고 이 옵션이 설정된 경우, 데이터베이스에서 날짜&시간을 읽으면 UTC 대신 새로 설정한 시간대의 인식 날짜&시간이 반환됨
        - USE_TZ가 False인 상태로 이 값을 설정하면 error 발생
    - USE_I18N
        - 장고의 번역 시스템을 활성화해야 하는지 여부 지정
    - USE_L10N
        - 데이터의 지역화된 형식(localized formatting)을 기본적으로 활성화할지 여부 지정
        - True일 경우, 장고는 현재 locale의 형식을 사용하여 숫자와 날짜 표시
    - USE_TZ
        - datetimes가 기본적으로 시간대를 인식하는지 여부 지정
        - True일 경우, 장고는 내부적으로 시간대 인식 날짜와 시간 사용

## 4.Django Template

- Django Template System
    - 데이터 표현을 제어하는 도구이자 표현에 관련된 로직
    - 장고 템플릿을 이용한 HTML 정적 부분과 동적 컨텐츠 삽입
    - 템플릿 시스템의 기본 목표 숙지

### 4.1. DTL

- Django Template Language(DTL)
    - 장고 템플릿에서 사용하는 built-in template system
    - 조건, 반복, 변수 치환, 필터 등의 기능 제공
        - 파이썬처럼 일부 프로그래밍 구조(if, for 등)을 사용할 수 있지만 이것은 파이썬 코드로 실행되는 것이 아님
        - 장고 템플릿 시스템은 단순히 파이썬이 HTML에 포함된 것이 아님!
    - 프로그래밍적 로직이 아니라 프레젠테이션을 표현하기 위한 것
- DTL Syntax
    1. Variable
    2. Filters
    3. Tags
    4. Comments
- Variable
    - `{{ variable }}`
    - 변수명은 영어, 숫자와 밑줄의 조합으로 구성될 수 있으나 밑줄로는 시작할 수 없음
        - 공백, 구두점 문자 사용 불가
    - 온점을 사용하여 변수 속성에 접근할 수 있음
    - `{’key’ : value}`와 같이 딕셔너리 형태로 `render()`의 세번째 인자로 넘겨주며, 여기서 정의한 key에 해당하는 문자열이 템플릿에서 사용 가능한 변수명이 됨
    - 실습
      
        ```python
        # urls.py
        
        urlpatterns = [
            path('admin/', admin.site.urls),
            path('index/', views.index),
            path('greeting/', views.greeting),
        ]
        ```
        
        ```python
        # articles/views.py
        
        def greeting(request):
            foods = ['apple', 'banana', 'coconut',]
            info = {
                'name' : 'Alice'
            }
            context = {
                'foods' : foods,
                'info' : info,
            }
            return render(request, 'greeting.html', context)
        ```
        
        - context는 다른 이름으로 사용 가능하지만 관행적으로 사용
        
        ```html
        <!-- articles/templates/greeting.html -->
        
        <p>안녕하세요 저는 {{ info.name }} 입니다.</p>
        <p>저는 {{ foods.0 }}을 가장 좋아합니다.</p>
        ```
        
        - dot-lookup(dot-notation)으로 배열의 인덱스 및 딕셔너리의 키 값에 접근 가능
- Filters
    - `{{ variable|filter }}`
    - 표시할 변수를 수정할 때 사용
    - ex. name 변수를 모두 소문자로 출력 `{{ name|lower }}`
    - chained 가능하며 일부 필터는 인자를 받기도 함
        - `{{ name|truncatewords:30 }}`
    - 60개의 built-in template filters 제공
    - 실습
      
        ```python
        # urls.py
        
        urlpatterns = [
            ...
            path('dinner/', views.dinner),
        ]
        ```
        
        ```python
        # articles/views.py
        
        import random
        from django.shortcuts import render
        
        ...
        
        def dinner(request):
            foods = ['족발', '햄버거', '치킨', '초밥',]
            pick = random.choice(foods)
            context = {
                'pick' : pick,
                'foods' : foods,
            }
            return render(request, 'dinner.html', context)
        ```
        
        ```html
        <!-- articles/templates/dinner.html -->
        
        <p>{{ pick }}은 {{ pick.length }}글자</p>
        <p>{{ foods|join:", " }}</p>
        ```
    
- Tags
    - `{% tag %}`
    - 출력 텍스트를 만들거나, 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행
    - 일부 태그는 시작과 종료 태그가 필요 (`{% if %}{% endif %}`)
    - 24개의 built-in template tags 제공
    - 실습
      
        ```html
        <!-- articles/templates/dinner.html -->
        
        <p>메뉴판</p>
          <ul>
            {% for food in foods %}
              <li>{{ food }}</li>
            {% endfor %}
          </ul>
        ```
    
- Comments
    - `{# #}`
    - 장고 템플릿에서 라인의 주석을 표현하기 위해 사용
    - 유효하지 않은 템플릿 코드가 포함될 수 있음
        - ex. `{# {% if %} text {% endif %} #}`
    - 한 줄 주석에만 사용 (줄 바꿈 허용 X)
    - 여러 줄 주석은 `{% comment %}`와 `{% endcomment %}` 사이에 입력
    - 실습
      
        ```html
        <!-- articles/templates/dinner.html -->
        
        {# 이것은 주석입니다. #}
        
        {% comment %}
          <p>여러 줄</p>
          <p>주석</p>
          <p>입니다.</p>
        {% endcomment %}
        ```
        

### 4.2. Template Inheritance

- 템플릿 상속
    - 기본적으로 코드의 재사용성에 초점을 맞춤
    - 사이트의 모든 공통 요소를 포함하고, 하위 템플릿이 재정의(overide)할 수 있는 블록을 정의하는 기본 skeleton 템플릿을 만들 수 있음
    - 모든 템플릿에 부트스트랩을 적용하려면?
- 템플릿 상속 관련 태그
    - `{% extends %}`
        - 자식 템플릿이 부모 템플릿을 확장한다는 것을 알림
        - 반드시 템플릿 최상단에 작성되어야 함 (2개 이상 사용 불가)
    - `{% block content %}{% endblock content %}`
        - 하위 템플릿에서 재지정할 수 있는 블록을 정의 → 하위 템플릿이 채울 수 있는 공간
        - 가독성을 높이기 위해 선택적으로 endblock 태그에 이름을 지정할 수 있음
          
            ```html
            <!-- 두 코드는 같음 -->
            
            {% block content %}
            {% endblock %}
            
            {% block content %}
            {% endblock content %}
            ```
    
- 템플릿 상속 예시
    - base라는 이름의 skeleton 템플릿을 작성
    - 부트스트랩 CDN 작성
      
        ```html
        <!-- articles/templates/base.html -->
        
        <!DOCTYPE html>
        <html lang="en">
        <head>
          <meta charset="UTF-8">
          <meta http-equiv="X-UA-Compatible" content="IE=edge">
          <meta name="viewport" content="width=device-width, initial-scale=1.0">
          <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.5/dist/umd/popper.min.js" integrity="sha384-Xe+8cL9oJa6tN/veChSP7q+mnSPaj5Bcu9mPX5F5xIGE0DVittaqT5lorf0EI7Vk" crossorigin="anonymous"></script>
          <title>Document</title>
        </head>
        <body>
          {% block content %}
          {% endblock content %}
          <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0/dist/js/bootstrap.min.js" integrity="sha384-ODmDIVzN+pFdexxHEHFBQH3/9/vQ9uori45z4JjnFsRydbmQbmL5t1tQ0culUzyK" crossorigin="anonymous"></script>
        </body>
        </html>
        ```
        
    - index 템플릿에서 base 템플릿을 상속받음
    - 부트스트랩이 적용되었는지 확인
      
        ```html
        <!-- index.html -->
        
        {% extends 'base.html' %}
        
        {% block content %}
          <h1>만나서 반가워요!</h1>
          <a href="/greeting/">greeting</a>
          <a href="/dinner/">dinner</a>
        {% endblock content %}
        ```
    
- 추가 템플릿 경로
    - base.html의 위치를 앱 안의 template 디렉토리가 아닌 프로젝트 최상단의 templates 디렉토리 안에 위치하고 싶다면?
    - 기본 template 경로가 아닌 다른 경로를 추가하기 위해 아래 코드 작성
      
        ```python
        # settings.py
        
        TEMPLATES = [
            {
                'BACKEND': 'django.template.backends.django.DjangoTemplates',
                **'DIRS': [BASE_DIR / 'templates',],**
                'APP_DIRS': True,
                'OPTIONS': {
                    'context_processors': [
                        'django.template.context_processors.debug',
                        'django.template.context_processors.request',
                        'django.contrib.auth.context_processors.auth',
                        'django.contrib.messages.context_processors.messages',
                    ],
                },
            },
        ]
        ```
        
        - app_name/templates/ 디렉토리 경로 외 추가 경로를 설정한 것
        - base.html의 위치를 아래와 같이 이동 후 상속에 문제가 없는지 확인
          
          
            | articles/ |  |
            | --- | --- |
            | firstpjt/ |  |
            | templates/ | base.html |
- [참고] BASE_DIR
  
    ```python
    # settings.py
    
    BASE_DIR = Path(__file__).resolve().parent.parent
    ```
    
    - settings.py에서 특정 경로를 절대 경로로 편하게 작성할 수 있도록 장고에서 미리 지정해둔 경로 값
    - 객체 지향 파일 시스템 경로
        - 운영체제별로 파일 경로 표기법이 다르기 때문에 어떤 운영체제에서 실행되더라도 맞게 해석될 수 있도록 하기 위해 사용