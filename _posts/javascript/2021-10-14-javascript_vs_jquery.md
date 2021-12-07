---
title: "javascript vs jquery"
date: 2021-10-14
categories: javascript  
---

## 자바스크립트 기능
1. DOM api
2. AJAX
3. validation

## DOM api

|  분류          | 자바스크립트                                |  jquery                                            |
| :------------: | :------------------------------------------ | :------------------------------------------------- |
| 요소선택	     | document.getElementById("div")              | $("#div")	                                        |
|                |         .getElementsByTagName("div")        | $("div")                                           |
|                |         .getElementsByName("div")           | $("[name='div']")                                  |
|                |         .getElementsByClassName("div")      | $(".div")                                          |
| html 요소 추가 | 변수 = document.createElement("option")     | $newTag = $("\<option\>")                          |  
|                | 부모태그.appendChild(변수)                  | $부모태그.append($newTag)                          |
| html 요소 변경 | 태그.innerHTML = '수정할내용'               | $태그.html("수정할내용")                           |
| input 값       | .value                                      | val()                                              |
| html 요소 삭제 | 부모태그.removeChild(태그)                  |                                                    |
|                | 태그.remove()                               | $태그.remove()                                     |
| html 속성 변경 | 태그.setAttribute('속성', '값')             | $태그.attr('속성','값')                            |
|                | 태그.속성명 ='값'                           | prop('속성','값')                                  |
|                | 태그.removeAttribute('속성')                |                                                    |
| css 변경       | 태그.style.속성 = 'xxx'                     | $태그.css('속성','값')                             |
|                |                                             |    .hide(),  show(),  width()                      |
| class 변경     | 태그.classlist.add() / remove() / togger()  | $태그.addClass() / removeClass() / toggleClass()   |
|                |                                             |                                                    |
|                |                                             |                                                    |
|                |                                             |                                                    |
|                |                                             |                                                    |
|                |                                             |                                                    |
|                |                                             |                                                    |

## AJAX
1. to do list
2. 