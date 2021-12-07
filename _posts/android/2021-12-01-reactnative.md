---
title: "react native"
date: 2021-12-01
categories: android  
---

## 개발환경 구축
1. Chocolatey(옵션)
2. node.js 설치
3. python 설치 : 빌드 시스템
4. JDK 설치
5. 안드로이드 스튜디오 설치
   * `SDK` 설치
   * `AVD` 설정
   * `ANDROID_HOME` 환경변수 추가 : 'C:\Users\admin\AppData\Local\Android\Sdk'
   * `path`에 platform-tools 실행경로 추가 : C:\Users\admin\AppData\Local\Android\Sdk\platform-tools
6. npm을 이용하여 react-native-cli 설치  

```javascript
# node --version                    //설치된 프로그램 버전확인
# python --version
# java -version                     
# npm install -g react-native-cli   //react-native-cli 설치
# npx react-native init ReactApp    //프로젝트 생성
# cd ReactApp
# npm run android                   //실행하기 전에 안드로이드 에뮬레이터 실행
```


