# Github Branch



### Github 복습

- 사용 목적 : 협업, 복구, 백업
- git과 github는 다르다
  - git은 분산 버전 관리 시스템, github는 git을 통해 이용하는 클라우드 서비스
- 로컬 저장소 (local)
  - 기본 명령어
    - `git init` : 로컬 저장소 생성
    - `git add {file.확장자}` : working directory에 생긴 변화사항(파일 생성, 삭제, 수정 등)을 버전으로 관리하고자 staging area에 올림
      - `git add .` : 현재 경로의 모든 파일 올림
    - `git commit -m 'commit 내용'` : 버전을 기록할 때 = commit을 남길 때
      - 내용은 최대한 상세하게 작성
    - `git status` : 현재 로컬 저장소 상태 확인
      - 습관처럼 확인해야 한다
  - file의 상태
    - untracked : git이 아직 관리하고 있지 않다 (최초 생성 시)
    - tracked : `add` 명령어를 통해서 staging area 올라간 파일
- 원격 저장소 (remote)
  - 협업과 복구 및 백업에 이용
  - 로컬 <-> 원격 저장소 연결 프로세스
    1. github에 원격 저장소 생성
    2. 로컬 저장소 생성
    3. 파일 작업 후 원격 저장소에 push
         - push 전 로컬 저장소에서 반드시 하나 이상의 commit 수행해야 함
  - 원격 저장소 연결 명령어
    - `git remote add origin {repository url}`
    - `git remote -v` : 등록한 remote repository 정보 확인
      - 실행 결과 예시
        - origin https://www.github/{username}/{reponame}.git (fetch)
        - origin https://www.github/{username}/{reponame}.git (push)
      - fetch : pull과 같이 '가져온다'는 개념
        - fetch : 원격 저장소의 커밋을 로컬 저장소로 가져오나 자동으로 병합해주지 않기 때문에 직접 병합 과정을 진행해야 함
        - pull : 원격 저장소의 커밋을 로컬 저장소로 가져오며 자동으로 병합 (어떤 내용이 바뀌는지 알기 어렵다는 단점 존재)
    - `git push -u origin master` : 로컬에서 생긴 커밋 내역 업로드
      - -u 옵션을 사용하면 해당 세팅이 저장되기 때문에 이후엔 `git push`만 써도 push할 수 있다
    - `git pull origin master` : 원격 저장소의 변화 사항을 로컬 저장소로 업데이트
    - `git clone {git repository url}` : 원격 저장소를 로컬 저장소로 복제해온다 = 다운로드



### Branch 개념

- 가지가 뻗어나가듯이 갈래가 나뉘어지기 때문에 브랜치라고 부른다
- 실제 협업 환경에서는 pull과 push가 순차적으로 이루어지지 않음 -> 병렬적인 작업이 가능하게 하는 것이 브랜치
- 브랜치란 커밋 사이를 이동할 수 있는 포인터로, 여러 개의 브랜치를 만들어서 협업 시 독립적으로 작업하는 데에 사용 (서로 영향 주지 않음)
- 브랜치를 합치는 방법에는 merge와 rebase가 있음
- master 브랜치
  - `git init` 시 자동으로 만들어지는 기본 브랜치
  - 상용 버전으로 사용할 수 있음
- HEAD 포인터
  - 마지막 커밋을 가리키는 특수한 포인터
  - 브랜치를 이동하면 HEAD 포인터도 이동됨 (브랜치마다 1개씩 존재)



### 명령어

- `git branch` : 로컬 저장소의 브랜치 목록 확인
- `git branch {branch name}` : 새로운 브랜치 생성
- `git switch {branch name}` : 브랜치 이동
  - -c 옵션 (=create) 추가 시 생성과 동시에 브랜치 이동



### Merge

- 독립적으로 작업하던 브랜치에서 기능을 완성했을 때는 나뉘어진 작업 갈래는 합치는 merge 과정 필요
- 종류
  - fast-forward merge
    - 병합할 브랜치들이 바라보는 커밋이 동일 선상에 있을 때 (= fast-forward 상태)
    - 처진 브랜치(아마 master)가 바라보는 커밋이 병합 대상 브랜치의 커밋으로 포인터만 이동
  - 3-way merge
    - 병합할 브랜치들이 base(공통으로 가지고 있는 커밋)에서 커밋을 진행해서 분기해 나가 어느 것도 base에 위치하지 않을 때
    - base를 기준으로 병합 대상 브랜치들의 변경사항 찾아내어 병합
- 명령어
  - `git merge {branch name}`



### Rebase

- 말 그대로 커밋 라인을 재배치(re-base)하여 히스토리 정리
- 브랜치 기록이 사라지며, 커밋 또한 없어지기에 파일을 잃어버릴 수 있어 협업 시 위험