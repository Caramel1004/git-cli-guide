## 📚효율적인 App 버전 관리 == ⚙ git 관리
>로컬 서버로 개발 할때는 vscode에서 github에 commit push pull등 GUI로 처리하는 경우가 많았는데<br>
>AWS EC2로 웹 플랫폼을 배포하면서 ubuntu OS 환경에서 git명령어를 수월하게 사용하기 위해 git의 명령어를 정리 했습니다.
<br>

# 목차
1. [git 초기 설정 및 확인](#git-초기-설정-및-확인)
2. [git 원격 저장소를 로컬 브랜치에 병합하여 연결](#git-원격-저장소를-로컬-브랜치에-병합하여-연결)
3. [git 서버에 올려진 원격 저장소 가져오기](#git-서버에-올려진-원격-저장소-가져오기)
4. [git 변경된 코드 업데이트](#git-변경된-코드-업데이트)

git 명령어 한번에 보기: [git 명령어 한번에 보기](#git-명령어-한번에-보기)

# git 초기 설정 및 확인

> - git 닉네임 설정
>```
>git config --global user.name "(본인이 설정 할 닉네임)"
>```

> - git 이메일 설정
>```
>git config --global user.email "(본인 이메일)"
>```

>- git 설정된 닉네임 확인
>```
>git config --global user.name
>```

>- git 설정된 이메일 확인
>```
>git config --global user.email
>```

>- git 브랜치 명 설정
>```
>git config --global init.defaultBranch main
>```

>- git에 설정된 목록 보기
>    - vi 에디터에서 나가기 : Control + z
>```
>git config --list
>```
>OR
>```
>git config -l
>```
---

# git 원격 저장소를 로컬 브랜치에 병합하여 연결

### - git 서버에 원격 저장소 생성
1. 내 github에 접속 후 맨 상단에 repositories 클릭
2. 상단 맨 오른쪽에 초록색 New 버튼 클릭
3. (선택 사항)README.md를 생성

### - 로컬 서버에서 git에 업로드 할 소스 코드 폴더에 로컬 저장소 생성

- #### 1. 터미널에서 업로드 할 소스코드 폴더로 이동
>    - vscode or intellij로 해당 소스코드 폴더를 열었다면 <br>
>    터미널에 이미 해당 폴더에 위치해 있습니다.
>    - iTerm2 OR Terminal OR gitbash를 이용한다면 해당 폴더로 이동 해야 합니다.<br>
>    아래 명령로 해당 폴더로 이동 합니다.
>    
>```
>cd ~/desktop/...
>```

- #### 2. 새로운 저장소 생성
>```
>git init
>```
- #### 3 . 로컬 서버에서 변경되거나 추가된 파일 스테이징에 추가
> -  로컬 서버에서 변경되거나 추가된 모든 파일을 스테이징에 추가
>```
>git add .
>```
>```
>git add *
>```
> - 로컬 서버에서 변경되거나 추가된 일부 파일 선택해서 스테이징에 추가
>```
>git add <파일 이름 or 폴더 이름>
>```

- #### 4. 로컬 서버에서 스테이징된 변경 사항들을 커밋
>   - 간결한 메세지를 입력하는 경우
>```
>git commit -m "메세지 입력"
>```
>   - 디테일한 메세지를 입력하는 경우
>     - commit 후 작성 창에서 자세히 입력
>```
>git commit
>```
>   - 스테이징 추가 과정과 커밋을 동시에 하는 경우
>```
>git commit -am "메세지 입력"
>```

- #### 5. 최초 브랜치 생성
> - 보통 기본 브랜치명은 main 권장
>   - tmi로 원래는 기본 브랜치명으로 master라는 용어를 많이 사용 되어 왔고 <br>
>   브랜치를 추가할때 slave라는 용어가 보편적으로 많이 사용되어 왔지만 <br> 이는 인종차별적 의미가 있어
>   사용을 지양하고 있습니다.
>```
>git branch -M main
>```
### - 원격 저장소를 로컬 브랜치에 병합
- #### 6. git 원격 저장소 연결
> - 원격 저장소 조회
>   - 추가된 원격 저장소가 없으면 아무것도 없음
>   - 추가된 원격 저장소가 있으면 추가된 원격 저장소 URL 있음
>```
> git remote -v
>```
> - 원격 저장소 추가
>   - 원격 저장소에 로컬 브랜치 병합
> ```
> git remote add origin https://github.com/....
>```
> - 원격 저장소 수정
> ```
> git remote set-url origin https://github.com/....
>```
>- 원격 저장소 삭제
> ```
> git remote remove origin
>```

- #### 7. git 원격 저장소에 초기 브랜치 등록 및 커밋 내용 push
> - 원격 저장소에 이미 파일이 있는 경우 == 처음 repository생성 할 때 리드미파일을 추가한 경우
>   - 이 경우는 반드시 pull하고 push진행
>```
>git pull <리모트 명> <브랜치 명>
>```
> - 예시
>```
>git pull origin main
>```
> - 원격 저장소에 파일이 아예 없는 경우 == 처음 repository생성 할 때 리드미파일 추가 안한 경우
>```
>git push -u origin main
>```
> OR
>```
>git push --set-upstream origin main
>```


# git 서버에 올려진 원격 저장소 가져오기
- #### 1. 원격 저장소 복제
>     - 원하는 폴더로 이동 후 그 폴더에 클론 하면 됩니다.
>```
>  git clone <원격 저장소 URL>
>```
> - 예시
> ```
>  git clone https://github.com/Caramel1004/git-cli.git
> ```

# git 변경된 코드 업데이트
- #### 1. 로컬서버에서 작업 후 스테이징 영역으로 올림
    - git add . 명령어를 사용하여 모든 파일을 올려 커밋하는것을 지양 합니다.
>```
>  git add <파일명 or 폴더명>
>```
- #### 2. 스테이징 영역으로 올린 파일 및 폴더 커밋
    - 파일 하나하나 변경된 내용을 정확하게 기록하는걸 지향합니다.
>```
>  git commit -m "코드 리팩토링"
>```
- #### 3. 커밋 전에 pull
    - 만약 다른 팀원과 협업을 진행 하고 있다면 pull먼저 진행하는 것을 권장합니다.<br>
      pull없이 push했다가 변경내용이 뒤섞일 수 있습니다
>```
>  git pull
>```
>```
>  git push
>```
- #### (선택사항) 4. git 로그 확인
    - pull push가 잘 되었는지 확인 합니다.
>```
>  git log
>```

# git 명령어 한번에 보기
### 저장소 복제/다운로드(clone)
>```
>git clone <https:.. URL>
>```
>```
>git clone /로컬/저장소/경로
>```
>```
>git clone 사용자명@호스트:/원격/저장소/경로
>```

### 스테이징에 추가
> - 모든 파일 or 폴더
>```
>git add *
>```
> - 선택 파일
>```
>git add <파일명> or 폴더
>```

### 커밋된 파일 내용 조회
>```
>git status
>```

### commit
>   - 간결한 메세지를 입력하는 경우
>```
>git commit -m "메세지 입력"
>```
>   - 디테일한 메세지를 입력하는 경우
>     - commit 후 작성 창에서 자세히 입력
>```
>git commit
>```
>   - 스테이징 추가 과정과 커밋을 동시에 하는 경우
>```
>git commit -am "메세지 입력"
>```

### branch
>   - 브랜치 목록 조회
>```
>git branch
>```
>   - 새 브랜치 생성
>```
>git branch <브랜치명>
>```
>   - 브랜치 생성 후 생성된 브랜치로 이동
>```
>git checkout -b <브랜치명>
>```
>  - 해당 브랜치로 이동
>```
>git checkout <브랜치명>
>```
>   - 코드가 변경되지 않은 상태의 브랜치로 이동
>```
>git checkout -f <브랜치명>
>```
>  - 브랜치명 수정
>```
>git branch -m <기존 브랜치명> <새 브랜치명>
>```
>  - 브랜치 삭제
>```
>git branch -d <브랜치명>
>```

### 원격 저장소 연결
> - 원격 저장소 조회
>   - 추가된 원격 저장소가 없으면 아무것도 없음
>   - 추가된 원격 저장소가 있으면 추가된 원격 저장소 URL 있음
>```
> git remote -v
>```
> - 원격 저장소 추가
>   - 원격 저장소에 로컬 브랜치 병합
> ```
> git remote add origin https://github.com/....
>```
> - 원격 저장소 수정
> ```
> git remote set-url origin https://github.com/....
>```
>- 원격 저장소 삭제
> ```
> git remote remove origin
>```

> - 원격 저장소 수정
> ```
> git remote set-url origin https://github.com/....
>```

### 원격 저장소에 브랜치 등록
- #### 원격 저장소에 어떠한 파일도 없는 경우 바로 push
- #### 원격 저장소에 파일 하나라도 있으면 pull로 받고 pull로 받으면 main 브랜치로 병합되기떄문에 push할 필요 없음
>   - 원격에 저장된 git 프로젝트의 현재 상태를 다운받고 + 현재 위치한 브랜치로 병합
>```
>git pull <리모트명> <브랜치명>
>```
>- 보편적으로 리모트명을 origin으로 명명합니다. <br>
>  다른 리모트명으로 바꿔도 상관은 없습니다.
>```
>git pull origin main
>```
>- 만든 브랜치를 원격 서버에 전송 or 새 브랜치를 원격 저장소로 push
>```
>git push -u <remote명> <브랜치이름>
>```
>- 보편적으로 리모트명을 origin으로 명명합니다. <br>
>  다른 리모트명으로 바꿔도 상관은 없습니다.
>```
>git push -u origin main
>```
> OR
>```
>git push --set-upstream origin main
>```

### merge
>   - 현재 브랜치에 다른 브랜치의 수정사항 병합
>```
>git merge <다른 브랜치명>
>```

### git 기록 조회
>   - 변경 내용 merge 전에 바뀐 내용을 비교할 수 있음
>```
>git diff <브랜치명> <다른 브랜치명>	
>```
>   - 현재 위치한 브랜치 커밋 내용 확인 및 식별자 부여됨
>```
>git log
>```

