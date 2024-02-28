## Git
버전 관리 시스템. 소스 관리 툴

## 명령어
`$ git init`
새로운 저장소 만들기
: 폴더를 만들고, 폴더 경로 아래 명령을 실행하면 새로운 git 저장소가 만들어진다.

`$ git remote add origin https://github.com/wonlog/Lecture.git`
로컬 저장소와 원격 저장소 연결하기

`$ git remote -v`
현재 설정된 원격 저장소를 확인

`$ git remote remove origin`
기존의 원격저장소 제거

`$ git add <파일 이름>`
변경된 파일 추가하기

`$ git add .`
변경사항 모두 추가하기

`$ git commit -m "확정된 내역에 대한 설명 메세지"`
변경 내용이 HEAD에 반영되었지만, 원격 저장소에 반영이 되지 않았다. -> push

`$ git push origin main(혹은 원하는 브랜치명)`
변경 내용을 원격 저장소에 반영하기

## 깃에 올리지 않아도 되는 파일/디렉터리:
- node_modules/
프로젝트의 의존성을 관리하는 디렉터리입니다. package.json과 package-lock.json 파일에 정의된 내용을 바탕으로 npm install 또는 yarn 명령어를 실행하여 각자의 환경에서 쉽게 재생성할 수 있습니다.
- .env
환경 변수를 저장하는 파일입니다. API 키나 비밀번호 같은 민감한 정보가 포함될 수 있으므로, 이를 공유 저장소에 업로드하는 것은 보안상 위험할 수 있습니다.
- build/
빌드 프로세스를 통해 생성된 정적 파일을 포함하는 디렉터리입니다. 이러한 파일들은 배포 과정에서 생성되므로 깃에 포함시킬 필요가 없습니다.
- .DS_Store, Thumbs.db
macOS의 .DS_Store나 Windows의 Thumbs.db 같은 운영 체제에서 생성하는 숨김 파일들은 프로젝트와 관련이 없으므로 업로드할 필요가 없습니다.
- .next/
Next.js 프로젝트의 경우, 빌드 시 생성되는 .next 디렉터리도 깃에 업로드하지 않아야 합니다.
## 깃에 올리는 파일/디렉터리:
- src/
소스 코드, 컴포넌트, 스타일 파일 등 프로젝트의 핵심이 되는 파일들입니다.
- public/
정적 파일(이미지, 로고 등)이 포함된 디렉터리입니다.
- package.json, package-lock.json 또는 yarn.lock
프로젝트의 의존성과 스크립트를 정의한 파일입니다. 이 파일들을 통해 다른 개발자가 필요한 패키지를 설치할 수 있습니다.
- README.md
프로젝트 설명, 설치 방법, 사용 예 등을 포함한 문서입니다.
- .gitignore
깃에 업로드하지 않을 파일이나 디렉터리 목록을 지정하는 파일입니다.

### reference
> https://rogerdudler.github.io/git-guide/index.ko.html
