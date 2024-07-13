---
title: "vscode github 연동"
date: 2021-10-06
categories: javascript
---

## GitHub에서 복제(clone)

1. git 설치하고 path 추가

2. [이름과 이메일을 설정](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup){:target="\_blank"}

```console
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
$ git config --list
```

3. github에서 리포지토리 생성

4. github repository clone
   F1 => 'git clone' 입력 => 'Git: Clone' 메뉴 선택 => 리포지토리 선택 => 로컬에 저장될 위치 지정

5. add stage  
   ![add](/img/javascript/vs_git_01.png){:target="\_blank"}

6. commit  
   ![commit](/img/javascript/vs_git_02.png){:target="\_blank"}

7. push  
   ![push](/img/javascript/vs_git_03.png){:target="\_blank"}

## 터미널에서 github clone 연동

```js
> git clone https://github.com/{name}/{repository}
> git remote set-url origin https://{name}@github.com/{name}/{repository}
> git push
```

## 로컬 폴더를 github로 올리기

1. 로컬폴더를 git init로 초기화
   F1 => 'git init' 입력 => 로컬 폴더 선택
   ![add](/img/javascript/vs_git_04.png){:target="\_blank"}

2. [Source controll]에서 add -> commit

3. [Source controll] 에서 publish

## pull request

1. `fork`를 통해 원본 레포지토리를 가져와 내 레포지토리를 만든다.
2. `clone`을 통해 fork한 내 레포지토리를 로컬에 가져온다.
3. 로컬에서 작업 후 `add` -> `commit` -> `push`를 통해 내 레포지토리에 작업내용을 업로드한다.
4. `Pull Request`를 통해 내 작업내용을 원본 레포지토리에 반영해달라고 요청한다.

## branch

### 원격 브랜치 업데이트

git remote update

### 원격 브랜치 목록

git branch -r

### 로컬 브랜치 목록

git branch -a

## 로컬저장소 브랜치 리스트

git branch -al

## 원격 브랜치 동기화

git fetch --all --prune

git purne

## Git pull이 안되는 경우

- fatal: refusing to merge unrelated histories <-- 공통된 커밋 포인트가 없다(commit history가 서로 관련이 없다)는 에러

git pull origin main **--allow-unrelated-histories**
--allow-unrelated-histories 옵션은 이미 존재하는 두 프로젝트의 기록(history)을 저장하는 드문 상황에 사용하는 것으로 강제로 pull한다

## pull 과정

- pull = fetch + merge FETCH_HEAD
- fetch 는 원격 저장소에 있는 내용을 가져옴. 원격 저장소의 내용를 확인만 함
- merge는 원격저장소와 로컬 저장소가 공통으로 가지고 있는 commit 지점이 존재해야하고 그지점부터 병합을 시도
- HEAD 는 로컬에서 가장 마지막에 행해진 commit 정보
- FETCH_HEAD는 원격 저장소의 최신 commit 이력

## 참고사이트

- [Working with GitHub in VS Code](https://code.visualstudio.com/docs/editor/github){:target="\_blank"}
