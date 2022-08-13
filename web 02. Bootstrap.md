# 2. Bootstrap

---

## 1. CSS Layout

- CSS Layout Techniques
    - Display
    - Position
    - Float (CSS1, 1996)
    - Flexbox (2012)
    - Grid (2017)
    - 기타
        - Responsive Web Design (2010), Media Queries (2012)

### 1.1. Float

- Float
    - 박스를 왼쪽 혹은 오른쪽으로 이동시켜 텍스트를 포함 인라인요소들이 주변을 wrapping 하도록 함
    - 요소가 normal flow를 벗어나도록 함
    - 속성
        - none : 기본값
        - left : 요소를 왼쪽으로 띄움
        - right : 요소를 오른쪽으로 띄움
- 예시
    
    ```html
    <head>
    	<link rel="stylesheet" href="./ㅇ.css">
    </head>
    
    <body>
    	<div class="box left">float left</div>
    	<p>lorem300 자동 완성으로 길~게</p>
    </body>
    ```
    
    ```css
    .box {
    	width: 150px;
    	height: 150px;
    	border: 1px solid black;
    	background-color: crimson;
    	color: white;
    	margin-right: 30px;
    }
    
    .left	{
    	float: left;
    }
    ```
    
    ![Screen Shot 2022-08-07 at 15.18.20.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_15.18.20.png)
    

### 1.2. Flexbox

- Flexbox (Flexible Box)
    - 행과 열 형태로 아이템들을 배치하는 1차원 레이아웃 모델
    - 의의
        - 이전까지 normal flow를 벗어나는 수단은 float 혹은 position
        - flexbox를 통해 수동 값 부여 없이 1. 수직 정렬 2. 아이템의 너비와 높이 혹은 간격을 동일하게 배치
    - IE는 부분적으로 지원하므로 항상 확인 필요 (can i use 참고)
- Flexbox 축
    - 축
        - main axis (메인 축)
        - cross axis (교차 축)
    - flex-direction : row
        
        ![Screen Shot 2022-08-07 at 15.24.12.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_15.24.12.png)
        
- Flexbox 구성 요소
    - Flex Container (부모 요소)
        - flexbox 레이아웃을 형성하는 가장 기본적인 모델
        - Flex Item들이 놓여있는 영역
        - display 속성을 flex 혹은 inline-flex로 지정
        
        ```css
        .flex-container {
          display : flex;
        }
        ```
        
    - Flex Item (자식 요소)
        - 컨테이너에 속해 있는 컨텐츠 (박스)
- Flex 속성
    - 배치 설정
        - flex-direction
        - flex-wrap
    - 공간 나누기
        - justify-content (main axis)
        - align-content (cross axis)
    - 정렬
        - align-items (모든 아이템을 cross axis 기준으로)
        - align-self (개별 아이템)
    - 기타 속성
        - flex-grow : 남은 영역을 아이템에 분배
        - order : 배치 순서
            - 기본값은 0이며 낮은 숫자부터 출력 (음수도 가능)
            
            ![Screen Shot 2022-08-07 at 17.15.21.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_17.15.21.png)
            
- flex-direction
    - main axis 기준 방향 설정
    - 역방향의 경우 HTML 태그 선언 순서와 시각적으로 다르니 유의 (웹 접근성에 영향)
        
        ![Screen Shot 2022-08-07 at 15.55.15.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_15.55.15.png)
        
- flex-wrap
    - 아이템이 컨테이너를 벗어나는 경우 강제로 한 줄에 배치되도록 설정
        - 기본적으로 컨테이너 영역을 벗어나지 않도록 함
    - 속성
        - nowrap (기본값) : 한 줄에 배치
        - wrap : 넘치면 그 다움 줄로 배치
        
        ![Screen Shot 2022-08-07 at 15.56.21.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_15.56.21.png)
        
- flex-flow
    - flex-direction과 flex-wrap의 shorthand
    - flex-direction과 flex-wrap에 대한 설정 값을 차례로 작성
    - 예시 : `flex-flow: row nowrap;`
- justify-content & align-content
    - 공간 배분
        - flex-start (기본값) : 아이템들을 axis 시작점으로
        - flex-end : 아이템들을 axis 끝 쪽으로
        - center : 아이템들을 axis 중앙으로
        - space-between : 아이템 사이의 간격을 균일하게 분배
        - space-around : 아이템을 둘러싼 영역을 균일하게 분배 (가질 수 있는 영역을 반으로 나눠서 양쪽에)
        - space-evenly : 전체 영역에서 아이템 간 간격을 균일하게 분배
    - justify-content
        - main axis를 기준으로 공간 배분
            
            ![Screen Shot 2022-08-07 at 16.01.06.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_16.01.06.png)
            
    - align-content
        - cross axis를 기준으로 공간 배분
            - 아이템이 한 줄로 배치되는 경우 확인할 수 없음
            
            ![Screen Shot 2022-08-07 at 16.02.21.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_16.02.21.png)
            
- align-items & align-self
    - cross axis를 중심으로
        - stretch (기본값) : 컨테이너를 가득 채움
        - flex-start : 위
        - flex-end : 아래
        - center : 가운데
        - baseline : 텍스트 baseline에 기준선을 맞춤
    - align-items
        - 모든 아이템을 cross axis를 기준으로 정렬
            
            ![Screen Shot 2022-08-07 at 16.43.30.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_16.43.30.png)
            
    - align-self
        - 개별 아이템을 cross axis 기준으로 정렬
            - 주의! 해당 속성은 컨테이너에 적용하는 것이 아니라 개별 아이템에 적용
            
            ![Screen Shot 2022-08-07 at 16.44.52.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_16.44.52.png)
            
- 활용 레이아웃
    - 수직 수평 가운데 정렬
        
        ![Screen Shot 2022-08-07 at 17.20.20.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_17.20.20.png)
        
    - 카드 배치
        
        ![Screen Shot 2022-08-07 at 17.20.06.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_17.20.06.png)
        

## 2. Bootstrap

- Bootstrap
    - Build fast, responsive sites with Bootstrap.
    - Quickly design and customize responsive mobile-first sites with Bootstrap, the world’s most popular front-end open source toolkit, featuring Sass variables and mixins, responsive grid system, extensive prebuilt components, and powerful JavaScript plugins.
- CDN
    - Content Delivery(Distribution) Network
    - 컨텐츠(CSS, JS, Image, Text 등)을 효율적으로 전달하기 위해 여러 노드에 가진 네트워크에 데이터를 제공하는 시스템
    - 개별 end-user의 가까운 서버를 통해 빠르게 전달 가능 (지리적 이점)
    - 외부 서버를 활용함으로써 본인 서버의 부하가 적어짐

### 2.1. Bootstrap 기본 원리

- Spacing (margin and padding)
    - `{property}{sides}-{size}`
        - `mx-0` : 가로 margin이 0
        - `mx-auto` : 수평 중앙 정렬 (가로 가운데 정렬)
        - `py-0` : 위 아래 padding이 0
    - property
        - `m` : margin
        - `p` : padding
    - sides
        - `t` : top
        - `b` : bottom
        - `s` : (start) left in LTR, right in RTL
        - `e` : (end) right in LTR, left in RTL
        - `x` : both -left and -right
        - `y` : both -top and -bottom
        - blank : all 4 sides
    - size
        - `0` : 0 (0 rem = 0px)
        - `1` : `$spacer` * .25 (0.25 rem = 4px)
        - `2` : `$spacer` * .5 (0.5 rem = 8px)
        - `3` : `$spacer` (1 rem = 16px)
        - `4` : `$spacer` * 1.5 (1.5 rem = 24px)
        - `5` : `$spacer` * 3 (3 rem = 48px)
        - `auto` : set the margin to auto
    - 예시
        
        ![Screen Shot 2022-08-07 at 18.34.18.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.34.18.png)
        
- Color
    
    ![Screen Shot 2022-08-07 at 18.37.57.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.37.57.png)
    
    ![Screen Shot 2022-08-07 at 18.38.18.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.38.18.png)
    
- Text
    
    ![Screen Shot 2022-08-07 at 18.39.32.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.39.32.png)
    
- Display
    
    ![Screen Shot 2022-08-07 at 18.41.32.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.41.32.png)
    
- Position
    
    ![Screen Shot 2022-08-07 at 18.43.55.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.43.55.png)
    

### 2.2. Bootstrap 컴포넌트

- Components
    - 부트스트랩의 다양한 UI 요소를 활용할 수 있음
    - 기본 제공된 components를 변환해서 사용
- Buttons
    - 클릭했을 때 어떤 동작이 일어나도록 하는 요소
        
        ![Screen Shot 2022-08-07 at 18.59.16.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_18.59.16.png)
        
    - Dropdowns
        - dropdown, dropdown-menu, dropdown-item 클래스를 활용해 옵션 메뉴를 만들 수 있음
            
            ![Screen Shot 2022-08-07 at 19.10.31.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.10.31.png)
            
            ![Screen Shot 2022-08-07 at 19.40.39.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.40.39.png)
            
- Forms > Form control
    - form-control 클래스를 사용해 input 및 form 태그 스타일링할 수 있음
        
        ![Screen Shot 2022-08-07 at 19.41.05.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.41.05.png)
        
        ![Screen Shot 2022-08-07 at 19.41.15.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.41.15.png)
        
- Navbar
    - 네비게이션 바 제작
        
        ![Screen Shot 2022-08-07 at 19.42.43.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.42.43.png)
        
        ![Screen Shot 2022-08-07 at 19.42.50.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.42.50.png)
        
- Carousel
    - 콘텐츠(사진)를 순환시키기 위한 슬라이드쇼
        
        ![Screen Shot 2022-08-07 at 19.44.39.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.44.39.png)
        
        ![Screen Shot 2022-08-07 at 19.44.53.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.44.53.png)
        
- Modal
    - 사용자와 상호작용하기 위해서 사용하며, 긴급 상황을 알리는 데 주로 사용
    - 현재 열려있는 페이지 위에 또 다른 레이어를 띄움
    - 페이지를 이동하면 자연스럽게 사라짐 (제거하지 않고도 배경 클릭 시 사라짐)
        
        ![Screen Shot 2022-08-07 at 19.46.51.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.46.51.png)
        
        ![Screen Shot 2022-08-07 at 19.47.12.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.47.12.png)
        
- Flexbox
    
    ![Screen Shot 2022-08-07 at 19.49.27.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.49.27.png)
    
- Card > Grid Card
    
    ![Screen Shot 2022-08-07 at 19.51.20.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.51.20.png)
    
    ![Screen Shot 2022-08-07 at 19.51.45.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_19.51.45.png)
    
    - 화면이 작아지면 1줄에 표시되는 카드의 개수가 줄어듦
- Grid System
    - 요소들의 디자인과 배치에 도움을 주는 시스템
    - 기본 요소
        - column : 실제 컨텐츠를 포함하는 부분
        - gutter : 칼럼과 칼럼 사이의 공간 (사이 간격)
        - container : column들을 담고 있는 공간
    - bootstrap gride system은 flexbox로 제작됨
    - container, rows, column으로 컨텐츠를 배치하고 정렬
        - 12개의 column
        - 6개의 grid breakpoints
        
        ```html
        <div class="container">
        	<div class="row">
        		<div class="col"></div>
        		<div class="col"></div>
        		<div class="col"></div>
        	</div>
        </div>
        ```
        
    - breakpoints
        
        ![Screen Shot 2022-08-07 at 20.23.20.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_20.23.20.png)
        
    - 예시
        
        ```html
        <div class="container">
        	<h2 class="text-center">column</h2>
        	<div class="row">
        		<div class="col"></div>
        		<div class="col"></div>
        		<div class="col"></div>
        	</div>
          <hr>
        
        	<div class="row">
        		<div class="box col"></div>
        		<div class="box col"></div>
        		<div class="w-100"></div>
        		<div class="box col"></div>
        		<div class="box col"></div>
        	</div>
        	<hr>
        
        	<div class="row">
        		<div class="box col-3">3</div>
        		<div class="box col-6">6</div>
        		<div class="box col-3">9</div>
        	</div>
        	<hr>
        
        	<div class="row">
        		<div class="box col-1">1</div>
        		<div class="box col-1">2</div>
        		<div class="box col-1">3</div>
        		<div class="box col-1">4</div>
        		<div class="box col-1">5</div>
        		<div class="box col-1">6</div>
        		<div class="box col-1">7</div>
        		<div class="box col-1">8</div>
        		<div class="box col-1">9</div>
        		<div class="box col-1">10</div>
        		<div class="box col-1">11</div>
        		<div class="box col-1">12</div>
        		<div class="box col-1">13</div>
        	</div>
        	<hr>
        
        	<div class="row">
        		<div class="box col-9">col-9</div>
        		<div class="box col-4">col-4</div>
        		<div class="box col-3">col-3</div>
        	</div>
        	<hr>
        </div>
        ```
        
        ![Screen Shot 2022-08-07 at 20.30.30.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_20.30.30.png)
        
        ```html
        <div class="container">
        	<h2 class="text-center">Grid breakpoints</h2>
        	<div class="row">
        		<div class="box col-sm-8 col-md-4 col-lg-5">1</div>
        		<div class="box col-8 col-sm-2 col-md-4 col-lg-2">2</div>
        		<div class="box col-2 col-sm-2 col-md-4 col-lg-5">3</div>
        	</div>
        	<hr>
        
        	<h2 class="text-center">nesting</h2>
        	<div class="row">
        		<div class="box col-6">
        			<div class="row">
        				<div class="box col-3">1</div>
        				<div class="box col-3">2</div>
        				<div class="box col-3">3</div>
        				<div class="box col-3">4</div>
        			</div>
        		</div>
        		<div class="box col-6">1</div>
        		<div class="box col-6">2</div>
        		<div class="box col-6">3</div>
        	</div>
        	<hr>
        
        	<h2 class="text-center">offset</h2>
        	<div class="row">
        		<div class="box col-md-4 offset-4">col-md-4 offset-4</div>
        		<div class="box col-md-4 offset-md-4 offset-lg-2">col-md-4 offset-md-4 offset-lg-2</div>
        	</div>
        	<hr>
        </div>
        ```
        
        ![Screen Shot 2022-08-07 at 20.47.41.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_20.47.41.png)
        
        ```html
        <div class="container">
        	<h2 class="text-center">alignment</h2>
        	<div class="row parent justify-content-center align-items-center">
        		<div class="box col-4">justify-content-center / align-items-center</div>
        	</div>
        	<hr>
        
          <div class="row parent">
        		<div class="box col-4 align-self-start">1</div>
        		<div class="box col-4 align-self-center">2</div>
        		<div class="box col-4 align-self-end">3</div>
        	</div>
        	<hr>
        </div>	
        ```
        
        ![Screen Shot 2022-08-07 at 20.51.33.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_20.51.33.png)
        
        ![Screen Shot 2022-08-07 at 20.54.19.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_20.54.19.png)
        
    - media query
        - 예를 들어 "뷰포트가 480 픽셀보다 넓다."라고 지정한 규칙에 브라우저 및 장치 환경이 일치하는 경우에만 CSS를 적용할 수 있는 방법을 제공
            
            ![Screen Shot 2022-08-07 at 20.58.01.png](2%20Bootstrap%20066c1be3ba5745bda2af14e842dac8d9/Screen_Shot_2022-08-07_at_20.58.01.png)
            

## 3. Responsive web

- Responsive web design
    - 다양한 화면 크기를 가진 디바이스들이 등장함에 따라 responsive web design 개념 등장
    - 반응형 웹은 별도 기술 이름이 아닌 웹 디자인에 대한 접근 방식, 반응형 레이아웃 작성에 도움이 되는 사례들의 모음 등을 기술하는 데에 사용되는 용어
    - 예시
        - Media Queries, Flexbox, Bootstrap Grid System, The viewport meta tag