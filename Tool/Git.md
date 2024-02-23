# Git
버전 관리 시스템. 소스 관리 툴

# GitHub
`$ git init`
새로운 저장소 만들기
: 폴더를 만들고, 폴더 경로 아래 명령을 실행하면 새로운 git 저장소가 만들어진다.

`$ git remote add origin https://github.com/wonlog/Lecture.git`
로컬 저장소와 원격 저장소 연결하기

`$ git add <파일 이름>`
변경된 파일 추가하기

`$ git add .`
변경사항 모두 추가하기

`$ git commit -m "확정된 내역에 대한 설명 메세지"`
변경 내용이 HEAD에 반영되었지만, 원격 저장소에 반영이 되지 않았다. -> push

`git push origin main(혹은 원하는 브랜치명)`
변경 내용을 원격 저장소에 반영하기

## reference
> https://rogerdudler.github.io/git-guide/index.ko.html
