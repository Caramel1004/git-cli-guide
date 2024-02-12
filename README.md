## 효율적인 코드 관리 == git 관리
로컬 서버로 개발 할때는 vscode에서 github에 commit push pull등 GUI로 처리하는 경우가 많았는데<br>
AWS EC2로 웹 플랫폼을 배포하면서 ubuntu OS 환경에서 git명령어를 수월하게 사용하기 위해 git의 명령어를 정리 했습니다.<br>

# GIT 명령어
- git init: 새로운 저장소 생성
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
