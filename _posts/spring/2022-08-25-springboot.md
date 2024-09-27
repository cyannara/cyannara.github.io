---
title: "springboot"
date: 2022-08-25
categories: spring  
tags: [springboot]
toc: true
---
## springboot 버전
<pre>
springboot    3.2.9   <==   3.2.0  <==  2.7.18
    spring    6.1.12  <==   5      <==  5
   mybatis    3.5.14  <==   3.0.3  <==  2.3.2
      java    21      <==   17     <==  11
</pre>

## springboot annotation
- @EnableAutoConfiguration
- @EnableWebMvc
- @SpringBootApplication
- @Configuration
- @PropertySource, @ConfigurationProperties, @Value
- @ComponentScan. @Component
- @Bean, @Required, @Singletone, @Lazy
- @Autowired, @Inject, @Qualifier, @Resource
- @PostCopnstuct, @PreConstruct, @PreDestory
- @RestController, @Controller, @Service, @Repository
- @CrossOrign
- @ExceptionHandler
- @ControllerAdvice, @RestControllerAdvice
- @RequestMapping, @GetMapping, @PostMapping, @PutMapping, @DeleteMapping, @PatchMapping
- @CookieValue
- @Valid, @InitBinder
- @PathVariable
- @RequestAttribute, @RequestHeader, @RequestParam, @RequestPart, @RequestBody
- @ModelAttribute, @SessionAttributes
- @ResponseBody, @ResponseStatus
- @Transactional
- @Cacheable, @CachePut, @CacheEvent, @CacheConfig

### AOP Anotation
- @Aspect
- @Pointcut
- @Before, @After, @Around, @AfterRetruning, @AfterThrowing

### JPA Annotation
- @Entity
- @Table
- @Id, @GeneratedValue
- @column
- @OneToMany
- @ManyToOne

### Java Bean Validation Annotation
- @NotBlank, @Null, @NotNull
- @NotEmpty
- @Email
- @Min, @Max
- @Digits, @Positive, @PositiveOrZero, @Negative, @NegativeOrZero
- @Future, @futureOrPresent, @Past, @PastOrPresent

### Swagger Annotation
- @Tag
- @Operation
- @Parameter
- @ApiResponse
- @Schema
- @ApiModelProperty


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

## security
```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityCustomizer;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public PasswordEncoder bcryptPassword() {
		return new BCryptPasswordEncoder();
	}
	
	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http.authorizeHttpRequests((requests) -> requests.antMatchers("/home", "/").permitAll().antMatchers("/admin/**")
				.hasAuthority("ROLE_ADMIN")
				//.anyRequest().authenticated()
				.anyRequest().permitAll()
				)
				.formLogin(login -> login.defaultSuccessUrl("/home").loginPage("/login").usernameParameter("userid")
						.permitAll())
				.logout().logoutUrl("/logout").logoutSuccessUrl("/home").permitAll()
		// .and()
		// .csrf().disable();
		;
		return http.build();
	}


	@Bean
	public WebSecurityCustomizer webSecurityCustomizer() {
		return (web) -> web.ignoring().antMatchers("/images/**", "/js/**", "/css/**");
	}
}
```

## junit error
[JUnit] The method andExpect(ResultMatcher) in the type ResultActions is not applicable for the arguments (RequestMatcher)

해결책 : content import 수정
org.springframework.test.web.client.match.MockRestRequestMatchers.content;
==>    org.springframework.test.web.servlet.result.MockMvcResultMatchers.content;
