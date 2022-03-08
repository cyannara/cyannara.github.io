---
title: "java vw javascript"
date: 2022-03-08
categories: javascript  
---

## Java와 비교

|  분류          | 자바                                            |  자바스크립트                                      |
| :------------  | :---------------------------------------------- | :------------------------------------------------- |
| datatype       | 리터럴: number, string, boolean, object         | 기본형: byte/short/int/long/float.double, char, boolean |
|                | 객체: String, Date, Object                      | 참조형: String, Date, Object                       |
|                |       Number, Boolean                           |       : (랩퍼클래스)Integer/Float/Double, Boolean  |
|                | null, undefiend                                 | null                                               |
|                | symbol                                          |                                                    |
| 변수선언(함수) | var                                             |                                                    |  
| 변수선언(블록) | let                                             |데이터타입 변수명                                   |  
| 상수           | const                                           |static final                                        |  


| html 요소 추가 | 부모태그.appendChild(변수)                      | $부모태그.append($newTag)                          |
|                | 부모태그.append(변수1, 변수2)                   |                                                    | 
| html 내용 변경 | 태그.innerHTML = '수정할내용'                   | $태그.html("수정할내용")                           |
| html 요소 삭제 | 부모태그.removeChild(태그)                      |                                                    |
|                | 태그.remove()                                   | $태그.remove()                                     |
| html 속성 변경 | 태그.setAttribute('속성', '값')                 | $태그.attr('속성','값')                            |
|                | 태그.속성명 ='값'                               |      .prop('속성','값')                            |
|                | 태그.removeAttribute('속성')                    |                                                    |
| input 값       | 태그.value                                      | $태그.val()                                        |
| css 변경       | 태그.style.속성 = 'xxx'                         | $태그.css('속성','값')                             |
|                | 태그.style.display = 'none'   또는 'block'      |      .hide(),  show()                              |
| class 변경     | 태그.classlist.add() / remove() / togger()      | $태그.addClass() / removeClass() / toggleClass()   |
|                |     .contains("클래스명")                       |      .hasClass("클래스명")                         |
| data속성       | 태그.setAttribute("data-속성", "값")            | $태그.data("속성", "값")                           |
| event 추가     | 태그.addEventListener("type", handler)          | $태그.bind()   ,  on() , one()                     |
| event 삭제     | 태그.removeEventListener("type")                |      .unbind() ,  off()                            |
| traverse-부모  | 태그.parentElement , closest()                  | $태그.parent(),   closest()                        |
|          자식  | childNodes, firstElementChild, lastElementChild |       children(),  first(),  last()                |
|                |                                                 |       find("css선택자")                            |
|          형제  | nextElementSibling, previousElementSibling      | $태그.prev(),  next()                              |
|                |                                                 |       .prevAll(), nextAll(),  siblings()           |
|          필터  |                                                 | eq(), odd(), even()                                |
| 반복문         | forEach()                                       | each()                                             |
| ajax           | XMLHttpRequest 객체,  fetch()                   | $.ajax(),  $.post(),  $.get(),  $.getJson()        |
|                |                                                 | $("div").load(url)                                 |