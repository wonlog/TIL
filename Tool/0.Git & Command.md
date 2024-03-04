## Todo
- [X] 깃 명령어 정리하기
- [ ] 커밋메세지 규칙 정리하기
      최초 프로젝트 업로드 시에는 "Upload Initial Project"로 사용하자  

<hr/>

## Git
버전 관리 시스템. 소스 관리 툴  

## 커밋  
편집된 파일을 저장하는 것과 마찬가지로 커밋은 분기에서 하나 이상의 파일에 변경 내용을 기록한다.
Git은 각 커밋에 다음을 식별하는 SHA 또는 해시라는 고유 ID를 할당한다.  
- 특정 변경 내용
- 변경된 시점
- 변경 내용을 만든 사람

#### 커밋 메세지 구조  
> type(타입) : title(제목)  
body(본문, 생략 가능)  
Resolves : #issueNo, ...(해결한 이슈 , 생략 가능)  
See also : #issueNo, ...(참고 이슈, 생략 가능)  
![image](https://github.com/wonlog/TIL/assets/149459170/f70b8e53-7f72-470e-bd7f-bb6fca0a610e)


#### 커밋 메세지 규칙  
> 1. 제목과 본문을 빈 행으로 구분한다.
> 2. 제목은 50글자 이내로 제한한다.
> 3. 제목의 첫 글자는 대문자로 작성한다.
> 4. 제목 끝에는 마침표를 넣지 않는다.
> 5. 제목은 명령문으로 사용하며 과거형을 사용하지 않는다.
> 6. 본문의 각 행은 72자 내로 제한한다.
> 7. 어떻게 보다는 무엇과 왜를 설명한다.
![image](https://github.com/wonlog/TIL/assets/149459170/cabbe9f7-ff08-4630-8f4c-b2b96614e5d0)


#### 커밋 메세지 타입  
> 자주 사용: feat, fix
![image](https://github.com/wonlog/TIL/assets/149459170/04e2acae-6db0-40b5-83e1-3da23ffe4510)
![image](https://github.com/wonlog/TIL/assets/149459170/0ef8a053-ac7b-4052-8c33-8b45fed88478)

#### 커밋 메세지를 GitHub 이슈와 연결  
> 커밋 메세지에 "#[Issue Number]"를 입력하게 될 경우 자동으로 이슈에 커밋 내용을 추가하게 된다.

#### 커밋과 함께 이슈를 close 할 수 있는 Keyword
- close
- closes
- closed
- fix
- fixes
- fixed
- resolve
- resolves
- resolved

## 명령어
< > 로 표시한 것은 상황에 따라 달라질 수 있는 이름임을 인지한다.

`$ git init`  
새로운 저장소 만들기: 폴더를 만들고, 폴더 경로 아래 명령을 실행하면 새로운 git 저장소가 만들어진다.

`$ git remote add origin <https://github.com/wonlog/Lecture.git>`  
로컬 저장소와 원격 저장소 연결하기

`$ git remote -v`  
현재 설정된 원격 저장소를 확인

`$ git remote remove origin`  
기존의 원격저장소 제거

`$ git add <파일 이름>`  
변경된 특정 파일 추가하기

`$ git add <폴더 이름>`  
변경된 특정 폴더 추가하기

`$ git add .`  
변경사항 모두 추가하기

`$ git commit -m "확정된 내역에 대한 설명 메세지"`  
변경 내용이 HEAD에 반영되었지만, 원격 저장소에 반영이 되지 않았다. -> push

`$ git push origin <main(브랜치)>`  
변경 내용을 원격 저장소에 반영하기

`$ git branch`  
현재 브랜치 확인하기

`$ git checkout <main>`  
main 브랜치로 체크아웃

`$ git branch -m <upload>`  
main 브랜치를 upload로 이름을 변경

`$ git push -u origin <upload>`  
변경된 브랜치를 원격 저장소에 푸시

`$ git branch -d <main>`  
로컬 저장소에서 main 브랜치를 삭제

`$ git push origin --delete <main>`  
원격 저장소에서 main 브랜치를 삭제

`$ git push -u origin <upload:main>0`  
원격 저장소에 upload 브랜치가 없다면, upload 브랜치를 원격 저장소의 main 브랜치로 변경  

**로컬에서 master 브랜치를 main 브랜치로 변경하고, 이 변경사항을 원격 저장소에 강제로 푸시하는 과정**
`$ git checkout master`  
현재 작업중인 브랜치를 `master`로 변경합니다.  

`$ git branch main master -f`  
`master`브랜치의 현재 상태를 기반으로 `main` 브랜치를 생성하거나 업데이트한다. `-f` 또는 `--force` 옵션은 이미 `main` 브랜치가 존재하는 경우, 이를 강제로 덮어쓰라는 의미이다.  
즉, `master`의 현재 상태를 `main`에 복사하되, `main`이 있으면 그 내용을 `master`의 현재 상태로 강제 업데이트한다는 것이다.

`$ git checkout main`  
작업 중인 브랜치를 `main`으로 변경한다.  

`$ git push origin main -f`  
로컬의 `main` 브랜치를 원격 저장소(`origin`)에 푸시한다.


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
> [git - 간편 안내서](https://rogerdudler.github.io/git-guide/index.ko.html)
> [좋은 Git Commit Message 작성 가이드라인_티스토리](https://jane-aeiou.tistory.com/93)
> [git branch main master -f/출처: https://jeongkyun-it.tistory.com/128 [나의 과거일지:티스토리]
