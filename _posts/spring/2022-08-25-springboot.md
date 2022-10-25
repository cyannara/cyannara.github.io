
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