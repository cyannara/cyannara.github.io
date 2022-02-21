---
title: "vscode github 연동"
date: 2021-10-06
categories: javascript  
---

## GitHub에서 복제(clone)

1. github에서 리포지토리 생성

2. github repository clone
F1  => 'git clone' 입력  => 'Git: Clone' 메뉴 선택   => 리포지토리 선택  => 로컬에 저장될 위치 지정

3. add stage
![add](/img/javascript/vs_git_01.png){:target="_blank"}  

4. commit
![commit](/img/javascript/vs_git_02.png){:target="_blank"}  

5. push
![push](/img/javascript/vs_git_03.png){:target="_blank"}  

## 터미널에서 github clone 연동  

```js
> git clone https://github.com/{name}/{repository}
> git remote set-url origin https://{name}@github.com/{name}/{repository}
> git push
```

## 로컬 폴더를 github로 올리기

1. 로컬폴더를 git init로 초기화
F1  => 'git init' 입력  => 로컬 폴더 선택
![add](/img/javascript/vs_git_04.png){:target="_blank"}  

2. [Source controll]에서 add -> commit

3. [Source controll] 에서 publish

## pull request

1. `fork`를 통해 원본 레포지토리를 가져와 내 레포지토리를 만든다.
2. `clone`을 통해 fork한 내 레포지토리를 로컬에 가져온다.
3. 로컬에서 작업 후 `add` -> `commit` -> `push`를 통해 내 레포지토리에 작업내용을 업로드한다.
4. `Pull Request`를 통해 내 작업내용을 원본 레포지토리에 반영해달라고 요청한다.

## 참고사이트  

* [Working with GitHub in VS Code](https://code.visualstudio.com/docs/editor/github){:target="_blank"} 