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

## 참고사이트  
* [Working with GitHub in VS Code](https://code.visualstudio.com/docs/editor/github){:target="_blank"} 