---
title: "vscode github 연동"
date: 2021-10-06
categories: javascript  
---

## vscode에서 github연동
### 1. github repository clone(GitHub에서 복제)
F1  => 'git clone' 입력  => 'Git: Clone' 메뉴 선택   => 리포지토리 선택  => 로컬에 저장될 위치 지정

### 2. add stage
![add](/img/vs_git_01.png){:target="_blank"}  

### 3. commit
![commit](/img/vs_git_02.png){:target="_blank"}  

### 4. push
![push](/img/vs_git_03.png){:target="_blank"}  


## 터미널에서 github연동  
```js
> git clone https://github.com/{name}/{repository}
> git remote set-url origin https://{name}@github.com/{name}/{repository}
> git push
```

## pull request
1. `fork`를 통해 원본 레포지토리를 가져와 내 레포지토리를 만든다.
2. `clone`을 통해 fork한 내 레포지토리를 로컬에 가져온다.
3. 로컬에서 작업 후 `add` -> `commit` -> `push`를 통해 내 레포지토리에 작업내용을 업로드한다.
4. `Pull Request`를 통해 내 작업내용을 원본 레포지토리에 반영해달라고 요청한다.

## 참고사이트  
* [Working with GitHub in VS Code](https://code.visualstudio.com/docs/editor/github){:target="_blank"} 