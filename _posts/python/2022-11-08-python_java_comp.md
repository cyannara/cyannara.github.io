---
title: "python java"
date: 2022-11-08
categories: python
tags: [python]
---

## 파이썬과 자바 언어 비교  

| 구분           | 파이썬                           |  자바                                   |
| :------------  | :------------------------------- | :-------------------------------------- |
|                | 절차지향 + 객체지향 언어         | 객체지향 언어                           |
|                | 동적타이핑 언어                  | 정적타이핑 언어                         |
| 실행           | 인터프리터 방식                  | 컴파일러 방식                           |
| 변수선언       | a = 10                           | int a = 10                              |
|                | a = "hong"                       | a = "hong"   &gt;-- error               |
| 리스트         | emps = ["홍", "김"]              | List emps = Arrays.asList("홍", "김");  |
|                | emps = list()                    | List emps = new ArrayList()             |
|                | emps.append("apple")             | emps.add("apple")                       |
| 딕셔너리       | info = {'name':'hong','age':20}  | HashMap info = new HashMap();           |
|                |                                  | info.put("name","hong");                |
|                | info.addr = '대구'               | info.put("addr","대구")                 |
| 스트링         | name = str()                     | String name = new String()              |
|                | name = "hong"                    | String name = "hong"                    |
|                | print( name.upper() )            | System.out.print( name.toUpper() )      |
|                |                                  |                                         |
|                |                                  |                                         |

### 객체지향
- 클래스를 선언하고 클래스를 생성해야 사용가능
- 코드 재사용 할 수 있고, 유지보수가 쉽다
```java
public class HelloPrint {
	public static void main(String[] args) {
		System.out.println("Hello");
	}
}
```

### 절차지향  
- 클래스를 만들 필요없이 바로 코딩 가능. 
- 코드 재사용 불가. 유지보수가 어렵다.
```python
print("Hello");
```

### 정적타이핑언어
자바는 변수를 사용하기 위해 데이터 유형을 선언

### 동적타이핑언어
변수유형을 선언할 필요가 없는 동적 유형으로서 런타임 시에 값이 대입될 때 유형이 결정된다.

## 자바와 파이썬 
 ![자바와 파이썬 비교](/img/python/python_vs_java.png){:width="800px"}  


## 절차지향과 객체지향 비교
 ![절차지향과 객체지향 비교](/img/python/proc_vs_obj.png){:width="600px"}  