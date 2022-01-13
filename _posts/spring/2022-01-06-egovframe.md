---
title: "eGovFrame"
date: 2022-1-6
categories: spring  
tags: [egov]
toc: true
---

## eGovFrame 프로젝트 
1. DB 사용자 계정 생성
```sql
  create user com identified by com01;
  grant resource, connect to com;
```
2. eGovFrame 프로젝트 생성
    1. file -> new -> eGovFrame Web Project
    1. Project name 입력
    2. target runtime : tomcat 9.0 선택
    3. dynamic web Module version 3.1 선택
    4. grop Id, Artifact Id 입력

3. file -> new -> eGovFrame Commom Component
  1. [역할/권한관리], [공통코드], [메뉴관리], [프로그램관리] 선택
  2. datasource 선택
  3. test connection
  4. create table

4. global.properties 파일 변경
  1. OsType 을 windows로 변경
  2. dbType 을 oracle
  2. Globals.oracle.Url에서 sid 변경

5. error page disable
  1. web.xml 에서 404, 500 에러 설정 주석처리
  2. egov-com-servlet.xml 파일에서 SimpleMappingExceptionResolver 주석처리 (컨트롤러 에러)
  3. src\main\resources\egovframework\spring\com\context-aspect.xml 파일에서 aop-config 설정 전체를 주석처리(서비스 에러)

6. context-mapper.xml
  1. mapperLocations 위치 추가
  2. MapperScannerConfigurer 빈 등록하고 basePackage 속성 설정

7. egovFrameTemplate
  1. table 생성
  2. CRUD Program 실행
  3. 스키마와 테이블 선택
  4. 파일(vo, dao, mapper, service, impl, controller, jsp)이 생성될 위치 지정
  5. vo에서 날짜 타입이 있으면 java.sql.Date -> java.util.Date로 변경



