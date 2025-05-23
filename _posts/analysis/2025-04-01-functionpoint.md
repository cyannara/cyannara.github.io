---
title: "function point"
date: 2025-04-01
categories: common  
tags: [function]
toc: true
---

## Function Point
 - Function Point는 프로젝트 규모를 정량적으로 평가
 - 기능 유형(ILF, EIF, EI, EO, EQ)별 개수를 세고, 복잡도를 설정하여 가중치 적용
 - referer : https://blog.naver.com/whwo161/221074363226

### 기능점수 산정방법 분류
1. 정규 기능 점수법(정규법 또는 정통법) 
    - 설계 단계 이후에 사용하며 기능의 유형별 복잡도를 적용한 기능점수 산정 
    - 데이터 기능 및 DET, RET 수 도출 / 트랜잭션 기능 및 DET, FTR 식별
    - 기능별 복잡도 매트릭(Low, Average, High)	
2. 간이 기능 점수법(간이법) - 기획, 발주 단계에서 사용하며 평균 복잡도를 적용하여 기능점수 산정
    - 예산수립, 제안서 견적 및 계약 SW 사업대가 산정
    - 데이터 기능, 트랜잭션 기능
    - 평균 복잡도


### 소프트웨어 기능 분류
데이터 기능  
 - 내부 논리 파일(ILF, Internal Logical File)
 - 외부 연계 파일(EIF, External Interface File)  

트랜잭션 기능  
 - 외부 입력(EI, External Input)
 - 외부 출력(EO, External Output)
 - 외부 조회(EQ, External inQuiry)


내부 논리 파일(ILF)  
  - 대학 종합정보시스템 - 학생 기본 정보, 학생 성적 정보 등의 데이터 사용자가 등록/수정/삭제/조회를 하기 위한 대상  
  - 기능 점수 측정 대상으로 애플리케이션 내부에서 파일로 유지  
  - 데이터베이스 테이블, 시스템 내부 파일, 클래스    

외부 연계 파일(EIF)
  - 학생들의 등록금을 은행에서 관리하는 경우 은행 데이터베이스의 학생 등록금 정보  
  - 측정 대상 애플리케이션에서는 참조만 하고 다른 애플리케이션에서 유지되는 파일  

외부 출력(EO, External Output) 
  - 데이터를 변환, 계산, 집계, 정렬 후 출력
  - 파일 다운로드, 통계 보고서, 차트 생성 등
  - 인기 게시글 목록(최근 1주일 조회수 순)

외부 조회(EQ, External inQuiry)
  - 데이터 변경 없이 그대로 출력
  - 게시글 목록 조회, 상품 상세보기

### 평균 복잡도 가중치

`SW사업 대가산정 가이드`에서 평균 복잡도 가중치를 미리 정해놓고 제시하고 있다  

|유형|내부논리파일|외부연계파일|외부입력|외부출력|외부조회|
|:-|:-|:-|:-|:-|:-|
|가중치|7.5|5.4|4.0|5.2|3.9|

### 기능별 복잡도 매트릭스

 
 |    | 낮음| 보통 | 높음 |
 |:-- | :-- | :-- |  :-- |
 |외부 입력 (EI)| 3 | 4 |6 |
 |외부 조회 (EQ)|  3 | 4 |6 |
 |외부 출력 (EO)| 4 | 5| 7 |
 |외부 연계 파일 (EIF)| 5 | 7 | 10 |
 |내부 논리 파일 (ILF)| 7 | 10 | 15 |


### 기능점수표를 이용한 개발 비용 산출 예시


|기능 유형|	기능 설명|	개수	|평균 FP 가중치|	점수|
 |:-- | :-- | :-- |  :-- | :-- |
|ILF|	게시글 데이터 (제목, 내용, 작성자, 댓글 등)	|1|	10	|10|
|ILF|	회원 정보 (이름, 이메일, 비밀번호)|	1|	10|	10|
|EIF	|외부 로그인 API (SSO 연동)|	1|	7	|7|
|EI|	게시글 작성|	1|	4|	4|
|EI|	댓글 작성|	1|	4|	4|
|EI|	회원 가입|	1	|4|	4|
|EO|	게시글 목록 조회|	1	|5|	5|
|EO|	게시글 상세 조회|	1|	5|	5|
|EO|	댓글 목록 조회|	1|	5|	5|
|EQ|	게시글 검색	|1	|4	|4|
|EQ|	게시글 필터링	|1	|4|	4|

총합	-	-	-	62 FP



1 Function Point당 7시간 소요 (평균)  
 개발비: 1인 1시간당 5만원  

 총개발비용 = 57 * 7 * 5만  =  1,995만  
