---
title: "springboot"
date: 2022-08-25
categories: spring  
tags: [springboot]
toc: true
---

##  로컬, 개발, 서버 각 환경에 맞는 스프링 프로파일 분리

1. dev, 
1. application-dev.properties : 스프링부트에서 활성 프로파일의 기본값은 dev이다
```properties
spring.profiles.active=dev
```
2. .gitignore에 추가

```java
java -jar (어플리케이션 파일명).jar    //application.properties 적용됨
java -jar -Dspring.profiles.active=dev (어플리케이션 파일명).jar  //application-dev.properties 파일이 적용됨
```

## Springboot 외부 경로의 리소스 또는 업로드 파일 접근
```java
import java.util.concurrent.TimeUnit;
import org.springframework.http.CacheControl;
import org.springframework.web.servlet.config.annotation.ResourceHandlerRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

public class ResourceConfiguration implements WebMvcConfigurer {

    @Override
    public void addResourceHandlers(final ResourceHandlerRegistry registry) {
	
        registry.addResourceHandler("/img/**")
        .addResourceLocations("file:///d:/upload_img/")      
        
        // 접근 파일 캐싱 시간 
	.setCacheControl(CacheControl.maxAge(1, TimeUnit.MINUTES));
    }
}
```