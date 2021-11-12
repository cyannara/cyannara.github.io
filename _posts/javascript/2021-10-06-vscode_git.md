---
title: "vscode_git"
date: 2021-10-14
categories: javascript  
---

# github 연동

## 1. github repository clone
F1 > 'git clone' 입력 > 'Git: Clone' 메뉴 선택 -> GitHub에서 복제 -> 리포지토리 선택 -> 로컬에 저장될 위치 지정

## 2. add stage
![add](/img/vs_git_01.png)  

## 3. commit
![commit](/img/vs_git_02.png)  

## 4. push
![push](/img/vs_git_03.png)  


# 터미널에서 github연동  
```
>git clone https://github.com/{name}/{repository}
>git remote set-url origin https://{name}@github.com/{name}/{repository}
> git push
```

# 참고사이트  
* [Working with GitHub in VS Code](https://code.visualstudio.com/docs/editor/github){:target="_blank"} 