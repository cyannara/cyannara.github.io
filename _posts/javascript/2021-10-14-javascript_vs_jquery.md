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
| 요소선택       | document.getElementById("div")                  | $("#div")	                                        |
|                |         .getElementsByTagName("div")            | $("div")                                           |
|                |         .getElementsByName("div")               | $("[name='div']")                                  |
|                |         .getElementsByClassName("div")          | $(".div")                                          |
|                |         .querySelector("css slector")           |                                                    |
|                |         .querySelectorAll("css slector")        |                                                    |
| html 요소 생성 | 변수 = document.createElement("option")         | $newTag = $("\<option\>")                          |  
| html 요소 추가 | 부모태그.append( node or text ...)              | $부모.append($newTag)                             | 
|                |        .prepend(), .appendChild()              |      .prepend($newTag)                             | 
|                |        .insertAdjacentElement(position, element) |                                                  |
|                |        .insertAdjacentHTML(position, text)     |                                                   |
|                |        .insertAdjacentText(position, text)     |                                                   |
|                | 형제.after(), before()                         |  $형제.after(), before()                           |
| html 내용 변경 | 태그.innerHTML = '수정할내용'                   | $태그.html("수정할내용")                           |
| html 요소 삭제 | 부모태그.removeChild(태그)                      |                                                    |
|                | 태그.remove()                                   | $태그.remove()                                     |
| html 속성 변경 | 태그.setAttribute('속성', '값')                 | $태그.attr('속성','값')                            |
|                | 태그.속성명 ='값'                               |      .prop('속성','값')                            |
|                | 태그.removeAttribute('속성')                    |                                                    |
| input 값       | 태그.value                                      | $태그.val()                                        |
| css 변경       | 태그.style.속성 = 'xxx'                         | $태그.css('속성','값')                             |
|                | 태그.style.display = 'none'   또는 'block'      |      .hide(),  show()                              |
| class 변경     | 태그.classList.add() / remove() / togger()      | $태그.addClass() / removeClass() / toggleClass()   |
|                |     .contains("클래스명")                       |      .hasClass("클래스명")                         |
|                |     .className = "클래스명"                     |      .attr("class", "클래스명")                    |
| data속성       | 태그.setAttribute("data-속성", "값")            | $태그.data("속성", "값")                           |
|                | 태그.dataset.속성 = "값"                        |                                                    |
| event 추가     | 태그.addEventListener("type", handler)          | $태그.bind(),    on(),  one()                      |
| event 삭제     | 태그.removeEventListener("type")                |      .unbind(),  off()                             |
| traverse-부모  | 태그.parentElement , closest()                  | $태그.parent(),   closest()                        |
|          자식  | childNodes, children, firstElementChild, lastElementChild |       children(),  first(),  last()                |
|                |                                                 |       find("css선택자")                            |
|          형제  | nextElementSibling, previousElementSibling      | $태그.prev(),  next()                              |
|                |                                                 |      .prevAll(), nextAll(),  siblings()            |
|          필터  |                                                 | eq(index), gt(), lt(), odd(), even()               |
| 반복문         | forEach()                                       | each()                                             |
| ajax           | XMLHttpRequest 객체                             |                                                    |
|                | fetch()                                         | $.ajax(),  $.post(),  $.get(),  $.getJson()        |
|                |                                                 | $("div").load(url)                                 |

## dom 객체와 jQuery 객체 변환

```javascript
//dom 객체
var btn = document.getElementById("btn1");
btn.style.backgroundColor = 'red'

//jquery 객체
var $btn = $("#btn1");
$btn.css("backgroundColor","blue")

//dom => jquery   : $()로 감쌈
$(btn).css("backgroundColor","blue")

//jquery => dom   : get(0) 함수
$btn[0].style.backgroundColor = 'red'
$btn.get(0).style.backgroundColor = 'red'

$("div").eq(0)    // jquery
$("div")[0]       // dom
$("div").get(0)   // dom

//each 반복문 안에서 객체 타입
$("div").each(function(idx, item){   
  item            // dom 객체
  $(item)         // jQuery 객체
  $(this)         // jQuery 객체
})

//each 반복중단
$.each(arr, function(idx, item){
  return;         // continue
  return false;   // beak
})
```

## fetch 함수와 $.ajax() 함수 비교

### query string
-  "변수명=값&변수명=값"
-  form-urlencoded(생략가능)

```javascript

 // get 방식
 fetch(url + "?var=value").then();
 $.ajax(url + "?var=value").done();

// post,put 방식
   fetch(url, {method:'post', body: "fvar=value&svar=value" }).then()	
  $.ajax(url, {method:'post', data: "fvar=value&svar=value" }).done()
  $.ajax(url, {method:'post', data: {"fvar":"value", "svar":"value" }  }).done()
```

### json string 
- "{"필드명":"값"}"
- application/json 
- get 방식은 지원 안 함

<pre>  
       post,put		      fetch(url,{method:'post', 
                                         headers : { "content-type" : "application/json"},
                                         body:'{"var":"value"}' }).then()	
 
			      $.ajax(url,{method:'post', 
                                          contentType" : "application/json", 
                                           data:'{"var":"value"}' }).done()

                                           data:JSON.stringify({var:"value"})  }).done()

                               axios  :  default 가 json 형식

</pre>

### sync     VS  asynchronus (동기와 비동기 차이점)
<pre>
   blocking VS  nonblocking

  sync : 순차적으로
  async : 콜백함수     -->  async ~ await
  cors : ajax 같은 도메인에서만 요청 
</pre>
  
## AJAX 실습


1. to do
2. petShop
3. users
4. emp


## jQuery 위젯
1. DataTable
2. fullcalendar
3. chart
4. jqgrid
