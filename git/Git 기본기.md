# Git 기본기



### README.md

- 프로젝트에 대한 설명 문서
- Github 프로젝트에서 가장 먼저 보는 문서
- 일반적으로 소프트웨어와 함께 배포
- 작성 형식은 따로 없으나, 일반적으로 마크다운을 이용해 작성



### Repository

- 특정 디렉토리를 버전 관리하는 저장소
    - `git init` 명령어로 로컬 저장소를 생성
    - .git 디렉토리에 버전 관리에 필요한 모든 것이 들어있음
- Remote Repository와 Local Repository가 있음
    - 여기서 다루는 건 Local Repository



### Local Repository 생성

- 로컬 레포지토리 생성 명령어 : `git init`
    - git 사용하기 위해 가장 기본적으로 필요한 요소를 초기화한다. = 초기값을 세팅한다.
    - init 이후 (master) 새로 붙는다.
    - `ls -a` (= all) 명령어를 통해 .git 폴더 확인할 수 있다
        - 변경되지 않도록 숨김 폴더로 생성된다.
        - .git 폴더 존재한다는 건 깃이 관리하는 레포지토리라는 의미
    - 주의! 홈 폴더에서 실행하면 무시무시한 일이 벌어진다



### Working Directory & Staging Area & Repository

- 커밋은 이 3가지 영역을 바탕으로 동작
    - Working Directory : 내가 작업하고 있는 실제 디렉토리
    - Staging Area : 커밋(commit)으로 남기고 싶은, 특정 버전으로 관리하고 싶은 파일이 있는 곳
    - Repository : 커밋(commit)들이 저장되는 곳



### Untracked & Staged & Committed

- untracked 파일
    - git이 추적하지/관리하지 않는 파일으로, 파일의 최초 상태
- staged 파일
    - `git add` 명령어를 통해 staged 상태가 된다 (tracked)
- committed 파일
    - `git commit` 명령어를 통해 committed 상태가 된다
- 이후 파일을 수정한 경우 modified → staged → committed 순서



### VS Code

- git bash에서 `code .` 명령어 치면 해당 위치에서 VS Code 실행된다
- VS Code에서 터미널 실행했는데 bash로 선택되지 않았다면 (터미널 상단에서 확인)
    1. 기본 프로필 선택
    2. git bash 선택
    3. 휴지통 눌러서 터미널 끄고 다시 실행



### Commit 설정

- git config --global user.email "you@example.com"
- git config --global user.name "Your Name"



### Tip

- `clear` 명령어 단축키 : ctrl + L



### Git 기본 명령어

- `git status` : 깃 공간의 상태 확인
- `git log` : 커밋 기록 확인
    - 기록 중 복잡한 긴 문자는 커밋의 고유 아이디
    - `git log --oneline` : 커밋 로그 중 중요한 정보만 간단하게 보여줌
- `git diff <commit id> <commit id>` : 두 commit 간 차이 보여줌



### Commit 메시지

- 다른 개발자들이 변경사항 직접 확인하지 않아도 어떤 내용인지 명확하게 알 수 있도록 작성해야 한다.



### Staging Area를 사용하는 이유

- 우리가 commit을 남기고 싶은 파일만 = 관리하고 싶은 파일만 관리할 수 있다
- staging area가 없다면
    - 올리고 싶지 않은 파일을 working directory에서 빼낸 뒤 commit해야 하는 불편함 생김