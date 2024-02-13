## 📚효율적인 App 버전 관리 == ⚙ git 관리
로컬 서버로 개발 할때는 vscode에서 github에 commit push pull등 GUI로 처리하는 경우가 많았는데<br>
AWS EC2로 웹 플랫폼을 배포하면서 ubuntu OS 환경에서 git명령어를 수월하게 사용하기 위해 git의 명령어를 정리 했습니다.<br><br><br>

# GIT 초기 설정 및 확인

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
>```
>git config --list
>```
---

# git 원격 저장소를 로컬 브랜치에 병합하여 연결

### - git 서버에 원격 저장소 생성
1. 내 github에 접속 후 맨 상단에 repositories 클릭
2. 상단 맨 오른쪽에 초록색 New 버튼 클릭
3. (선택 사항)README.md를 생성

### - 로컬 서버에서 git에 업로드 할 소스 코드 폴더에 로컬 저장소 생성

> #### 1. 터미널에서 업로드 할 소스코드 폴더로 이동
>    - vscode or intellij로 해당 소스코드 폴더를 열었다면 <br>
>    터미널에 이미 해당 폴더에 위치해 있습니다.
>    - iTerm2 OR Terminal OR gitbash를 이용한다면 해당 폴더로 이동 해야 합니다.<br>
>    아래 명령로 해당 폴더로 이동 합니다.
>    
>```
>cd ~/desktop/...
>```

> #### 2. 새로운 저장소 생성
>```
>git init
>```
#### 3 . 로컬 서버에서 변경되거나 추가된 파일 스테이징에 추가
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

> #### 4. 로컬 서버에서 스테이징된 변경 사항들을 원격 저장소에 커밋
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

> #### 5. 최초 브랜치 생성
> - 보통 기본 브랜치명은 main 권장
>   - tmi로 원래는 기본 브랜치명으로 master라는 용어를 많이 사용 되어 왔고 <br>
>   브랜치를 추가할때 slave라는 용어가 보편적으로 많이 사용되어 왔지만 <br> 이는 인종차별적 의미가 있어
>   사용을 지양하고 있습니다.
>```
>git branch -M main
>```
### - 원격 저장소를 로컬 브랜치에 병합
> #### 6. git 원격 저장소 연결
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

> #### 7. git 원격 저장소에 초기 소스코드 업로드
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
> #### 1. 원격 저장소 복제
>   - 원하는 폴더로 이동 후 그 폴더에 클론 하면 됩니다.
>```
>  git clone <원격 저장소 URL>
>```
> - 예시
> ```
>  git clone https://github.com/Caramel1004/git-cli.git
> ```


- git clone <https:.. URL>: 저장소 복제/다운로드(clone)
- git clone /로컬/저장소/경로
- git clone 사용자명@호스트:/원격/저장소/경로
- git add <파일명>: <추가 및 확정(commit)>aaa
- git add *
- git commit -m "커밋 메시지"	커밋 생성
(실제 변경사항 확정)
- git status	파일 상태 확인
- git branch	브랜치 목록
- git branch <브랜치이름>	새 브랜치 생성 (local로 만듦)
- git checkout -b <브랜치이름>	브랜치 생성 & 이동
- git checkout master	master branch로 되돌아 옴
- git branch -d <브랜치이름>	브랜치 삭제
- git push origin <브랜치이름>	만든 브랜치를 원격 서버에 전송
- git push -u < remote > <브랜치이름>	새 브랜치를 원격 저장소로 push
- git pull < remote > <브랜치이름>	원격에 저장된 git 프로젝트의 현재 상태를 다운받고 + 현재 위치한 브랜치로 병합
- <변경 사항 발행(push)>	git push origin master	변경사항 원격 서버에 업로드
- git push < remote > <브랜치이름>	커밋을 원격 서버에 업로드
- git push -u < remote > <브랜치이름>	커밋을 원격 서버에 업로드
- git remote add origin <등록된 원격 서버 주소>	클라우드 주소 등록 및 발행
- (git에게 새로운 원격 서버 주소 알림)
- git remote remove <등록된 클라우드 주소>	클라우드 주소 삭제
- <갱신 및 병합(merge)>	$ git pull	원격 저장소의 변경 내용이 현재 디렉토리에 가져와지고(fetch) 병합(merge)됨
- git merge <다른 브랜치이름>	현재 브랜치에 다른 브랜치의 수정사항 병합
- git add <파일명>	각 파일을 병합할 수 있음
- git diff <브랜치이름><다른 브랜치이름>	변경 내용 merge 전에 바뀐 내용을 비교할 수 있음
- <태그tag 작업>	$ git log	현재 위치한 브랜치 커밋 내용 확인 및 식별자 부여됨
