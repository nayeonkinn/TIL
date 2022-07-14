# Github



### Remote Repository 생성

1. Github
    1. [Settings] - [Repositories]에서 Repository default branch를 master로 설정
        - 최근 BLM 영향으로 branch 이름의 기본값이 master 에서 main으로 변경되었다. 하지만 대부분의 회사에서는 여전히 master라는 이름으로 사용하기 때문에 master로 다시 변경하여 진행한다.
    2. create new repository
2. Local
    1. `mkdir {filename}` 이용해 새로운 디렉토리 생성
    2. 해당 디렉토리에서 `git init`하여 git 초기값 설정
    3. `git remote add origin {remote repository url}`
        - origin
          
            repository url 별명 (url을 매번 쓰기엔 길다.)
            
            일반적으로 내가 쓰는 레포지토리 별명은 origin으로 한다.
        
    4. `git remote` 명령어를 통해 origin 이름으로 원격 저장소 추가된 것 확인
    5. `touch README.md`로 README 파일 생성 후 내용 자유롭게 수정
        - 주의!  github에서 직접 수정하면 충돌 생길 수 있다.
    6. `git add {파일명.확장자}`하여 staging area에 파일 추가
        - 파일이 여러 개라면 띄어쓰기로 구분 ex. 파일명.확장자 파일명.확장자
        - git add . : 현재 위치한 wd의 모든 수정 사항 add
    7. `git commit -m 'first commit'` : commit
    8. `git push -u origin master` : push
        - -u : 현재 push 값이 기본값으로 저장되는 옵션. 한 번 사용한 후엔 `git push`만 써서 push할 수 있다. (한 번 쓰기 전에는 불가능)
        - master : local branch 이름



### git을 쓰는 이유

- 협업
- 복구
- 백업



### repository clone

1. `git clone {remote repository url}` : remote repo를 local로 복사
2. `git push origin master` : local repo의 최신 커밋을 remote repo로 push



### 버전 충돌

- 버전 충돌 일어나는 경우
    1. github에서 README.md 수정 후 commit
    2. local에서도 README.md 수정 후 commit, push → push rejected
- push reject된 후 git pull 하면 해당 파일에 버전별 차이점 표시되며 버전 선택 가능
    - incoming change : 리모트로 받아온 수정사항
    - current change : 현재 wd에서의 수정사항
- 결론 : pull과 push를 잘 해야 한다.



### 실습 : TIL Remote Repository 생성

1. 원격 레포지토리 생성
2. 로컬 레포지토리 생성
    1. 리드미 파일 만들기
    2. 내용 기입
3. 리모트와 로컬 연결
4. Push 명령어로 리드미 파일 업로드
- 궁금점 : 빈 상태의 원격 레포지토리 clone해서 쓰면 안 되는가? → 문제는 없지만 일반적으로 위처럼 한다.