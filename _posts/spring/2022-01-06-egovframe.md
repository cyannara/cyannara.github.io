---
title: "eGovFrame"
date: 2022-1-6
categories: spring  
tags: [egov]
toc: true
---

## Template Project

* error 원인 : FORMAT_DATE
D:\eGovFrameDev-4.0.0-64bit\workspace\potal\src\main\resources\egovframework\mapper\let\uss\olp\qri\EgovQustnrRespondInfo_SQL_oracle.xml 파일에서 DATE_FORMAT() 함수를 TO_CHAR()로 수정

* 접속계정 :  user1/1 , admin/1

## egov project 설정하기

### 1. DB 사용자 계정 생성
```sql
  create user com identified by com01;
  grant resource, connect, create view to com;
```
### 2. eGovFrame 프로젝트 생성
1. "file" 메뉴 -> "new" 메뉴 -> eGovFrame Web Project 실행
2. Project name 입력
3. target runtime 항목은 tomcat 9.0 선택
4. "Dynamic Web Module version" 은 3.1 선택
5. grop Id, Artifact Id 입력

### 3. 공통컴포넌트 추가
1. file -> new -> eGovFrame Commom Component
2. [역할/권한관리], [공통코드], [메뉴관리], [프로그램관리] 선택
3. "Select Table Creation Type" 에서 "사용자 DB에 생성" 선택
4. "Select DB"에서 datasource 선택
5. "Connection Test" 버튼 클릭하여 연결 확인("Connection succeeded" 메시지)
6. "Create Table" 버튼 클릭하여 관련 테이블 생성
7. "finish" 버튼 클릭하면 소스파일 다운받음.

### 4. DB 연결정보 수정
1. resources\egovframework\egovProps\global.properties 파일 변경
2. "Globals.OsType" 을 "WINDOWS" 변경
3. "Globals.DbType" 을 "oracle"로 변경
4. "Globals.oracle.Url"에서 sid  변경

### 5. error page disable
1. web.xml 에서 404, 500 에러 설정 주석처리
2. egov-com-servlet.xml 파일에서 SimpleMappingExceptionResolver 주석처리 (컨트롤러 에러)
3. src\main\resources\egovframework\spring\com\context-aspect.xml 파일에서 aop-config 설정 전체를 주석처리(서비스 에러)

### 6. component-scan 위치 추가
1. resources\egovframework\spring\com\context-common.xml 파일에서 "mes" 패키지 추가
2. webapp\WEB-INF\config\egovframework\springmvc\egov-com-servlet.xml 파일에서 "mes" 패키지 추가  

```xml
  <context:component-scan base-package="egovframework mes">
```

### 7. Mybatis 설정 변경
* typeAlias 경로 추가 : resources\egovframework\mapper\config\mapper-config.xml  
```xml
  <package name="mes"/> 
```
* resources\egovframework\spring\com\context-mapper.xml파일에서 mapperLocations 위치 추가  
```xml
<list>
	<value>classpath:/egovframework/mapper/com/**/*_${Globals.DbType}.xml</value>
	<value>classpath:/mes/**/*.xml</value>
</list>
```
* MapperScannerConfigurer 빈 등록하고 basePackage 속성 설정  
```xml
<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <property name="basePackage" value="mes.**.dao" />
</bean>
```

### 8. @responseBody 사용할 수 있게 MessageConveter 등록
> eGov는 "jsonView"를 사용하고 있음
1. egov\src\main\webapp\WEB-INF\config\egovframework\springmvc\egov-com-servlet.xml 파일에 추가
2. 기존에 있는 "RequestMappingHandlerAdapter" 빈 설정에 "messageConverters" 속성 추가함.

```xml
<bean class="org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerAdapter">
	<property name="webBindingInitializer">
		<bean class="egovframework.com.cmm.web.EgovBindingInitializer" />
	</property>
	<property name="messageConverters">
        <list>
            <bean class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter" />
            <bean class="org.springframework.http.converter.xml.Jaxb2RootElementHttpMessageConverter" />
        </list>
	</property>
</bean>
```

### 9. 테스트
* USER/공통12 로 로그인

### 10. 파일업로드
    1. Sequence diagram

### 11. [메뉴관리, 프로그램관리, 권한관리](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:com:v3.10:sym:메뉴관리){target=_blank}
* 프로그램, 메뉴 등록 : 메뉴관리리스트 -> 일괄등록 -> 엑셀파일선택
* 롤별 메뉴 생성 : 메뉴생성관리 -> 메뉴생성, 사이트맵생성
* 롤별 메뉴 조회

### 12. egovFrameTemplate
    1. table 생성
    2. CRUD Program 실행
    3. 스키마와 테이블 선택
    4. 파일(vo, dao, mapper, service, impl, controller, jsp)이 생성될 위치 지정
    5. vo에서 날짜 타입이 있으면 java.sql.Date -> java.util.Date로 변경

    
## (jenkins) maven build 에러 발생시 조치
* 원인 : encoding 에러 
    * 조치방법 : pom.xml 에 <encoding>UTF-8</encoding> 설정 추가

* 원인 : Blocked mirror for repositories error 발생 
    * 조치방법 : C:\dev\apache-maven-3.8.4\conf\setting.xml 파일에 mirror 설정 추가

```xml
	<mirror>
      <id>jaspersoft-third-party</id>
      <mirrorOf>jaspersoft-third-party</mirrorOf>
      <name>jaspersoft-third-party</name>
      <url>http://jaspersoft.jfrog.io/jaspersoft/third-party-ce-artifacts/</url>
	  <blocked>false</blocked>
    </mirror>
	<mirror>
      <id>egovframe</id>
      <mirrorOf>egovframe</mirrorOf>
      <name>egovframe</name>
      <url>http://maven.egovframe.go.kr/maven/</url>
	  <blocked>false</blocked>
    </mirror>
	<mirror>
      <id>egovframe_old1</id>
      <mirrorOf>egovframe_old1</mirrorOf>
      <name>egovframe_old1</name>
      <url>http://maven.egovframe.kr:8080/maven/</url>
	  <blocked>false</blocked>
    </mirror>	
	<mirror>
      <id>egovframe_old2</id>
      <mirrorOf>egovframe_old2</mirrorOf>
      <name>egovframe_old2</name>
      <url>http://www.egovframe.go.kr/maven/</url>
	  <blocked>false</blocked>
    </mirror>
```
