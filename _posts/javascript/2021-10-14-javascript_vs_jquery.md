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

|  분류          | 자바스크립트                                    |  jquery                                            |
| :------------  | :---------------------------------------------- | :------------------------------------------------- |
| 요소선택	     | document.getElementById("div")                  | $("#div")	                                        |
|                |         .getElementsByTagName("div")            | $("div")                                           |
|                |         .getElementsByName("div")               | $("[name='div']")                                  |
|                |         .getElementsByClassName("div")          | $(".div")                                          |
| html 요소 추가 | 변수 = document.createElement("option")         | $newTag = $("\<option\>")                          |  
|                | 부모태그.appendChild(변수)                      | $부모태그.append($newTag)                          |
| html 내용 변경 | 태그.innerHTML = '수정할내용'                   | $태그.html("수정할내용")                           |
| html 요소 삭제 | 부모태그.removeChild(태그)                      |                                                    |
|                | 태그.remove()                                   | $태그.remove()                                     |
| html 속성 변경 | 태그.setAttribute('속성', '값')                 | $태그.attr('속성','값')                            |
|                | 태그.속성명 ='값'                               |      .prop('속성','값')                            |
|                | 태그.removeAttribute('속성')                    |                                                    |
| input 값       | .value                                          | $태그.val()                                        |
| css 변경       | 태그.style.속성 = 'xxx'                         | $태그.css('속성','값')                             |
|                |                                                 |      .hide(),  show(),  width()                    |
| data속성       | 태그.setAttribute("data-속섬", "값")            | $태그.data("속성", "값")                           |
| class 변경     | 태그.classlist.add() / remove() / togger()      | $태그.addClass() / removeClass() / toggleClass()   |
|                |     .contains()                                 |                                                    |
| event          | 태그.addEventListener("type", handler)          | $태그.bind()   ,  on() , one()                     |
|                | 태그.removeEventListener("type")                |      .unbind() ,  off()                            |
| traverse-부모  | 태그.parentElement , closest()                  | $태그.parent(),  closest()                         |
|          자식  | childNodes, firstElementChild, lastElementChild |       children()  first()  last()                  |
|                |                                                 |       find("css선택자")                            |
|          형제  | nextElementSibling, previousElementSibling      | $태그.prev()/next()/prevAll()/nextAll()/siblings() |
|          필터  |                                                 | eq(), odd(), even()                                |
| 반복문         | forEach()                                       | each()                                             |

## AJAX
1. to do list
2. 

 firstElementChild,lastElementChild