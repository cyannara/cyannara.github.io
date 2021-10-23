---
title: "JPA"
date: 2019-7-10 08:26:28 -0400
categories: spring  
tags: [jpa]
---

# JPA와 hibernate, Spring Data JPA와 관계
* JPA  
 Java Persistence API의 약자로, 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스이다. JPA는 단순히 명세이기 때문에 구현이 없다.   
 JPA의 핵심이 되는 EntityManager 구성은 다음과 같다
  * JPA의 핵심이 되는 EntityManager
  * public void persist(Object entity);
  * public <T> T merge(T entity);
  * public void remove(Object entity);
  * public <T> T find(Class<T> entityClass, Object primaryKey);
* [hibernate](http://hibernate.org/orm/documentation/5.4/)    
JPA라는 명세의 구현체로  Hibernate의 작동 방식이 마음에 들지 않는다면 언제든지 DataNucleus, EclipseLink 등 다른 JPA 구현체를 사용해도 된다.  
 

* [Spring Data JPA](https://docs.spring.io/spring-data/jpa/docs/2.4.7/reference/html/#reference)   
JPA를 쓰기 편하게 만들어놓은 모듈이다. Spring에서 제공하는 모듈 중 하나로, 개발자가 JPA를 더 쉽고 편하게 사용할 수 있도록 도와준다. 이는 JPA를 한 단계 추상화시킨 Repository라는 인터페이스를 제공함으로써 이루어진다. 

![](https://suhwan.dev/images/jpa_hibernate_repository/overall_design.png)

## 1. springboot 프로젝트 시작  
<a href="https://spring.io/quickstart">start</a>  


```java
package com.example.demo.controller;


```
https://spring.io/quickstart

> 참고사이트
> 참고입니다.
 
**강조** 입니다.  

---

# 