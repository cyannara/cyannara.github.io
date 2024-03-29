---
title: "python web"
date: 2021-12-17
categories: python
tags: [python]
toc: true
---

## pip

* 파이썬으로 작성된 패키지 소프트웨어를 설치,관리하는 패키지 관리 시스템(npm, maven과 유사)
* 패키지 저장소 검색 : [pypi(Python Package Index)](https://pypi.org/){:target='_blank'}

```python
pip -V  또는 pip --version        # 버전확인
pip help
pip list                          # 설치된 패키지 목록 
pip install 패키지명              
pip uninstall 패키지명
```

## 크롤링으로 사이트 정보 수집

1. 크롤링(crawling)

* 소프트웨어 따위가 웹을 돌아다니며 유용한 정보를 찾아 특정 데이터베이스로 수집해 오는 작업. 또는 그러한 기술.
* 웹페이지에서 필요한 데이터 추출
* BeautifulSoup 모듈 : html, xml. json 등 파일의 구분을 분석하는 모듈
* requests 라이브러리

2. BeautifulSoup

* [document](https://www.crummy.com/software/BeautifulSoup/bs4/doc/){:target='_blank'}
* [실습예제-기상청날씨조회](https://dojang.io/mod/page/view.php?id=2458){:target='_blank'}
* html을 parse tree로 변환
* tag soup(구조가 맞지않는 html문서)에서 유래
* find(), find_all()
* select_one(), select()   #querySelector와 동일하게 css 선택자를 이용하여 태그검색
  * find는 tag를 웹의 구조 안에서 파악하는 것이 목적:syntax이다. 반면 select는 tag가 갖는 속성을 기준으로 역할에 따라 태그를 정의하는 것:semantics이 목적이다

```python
# 모듈을 읽어 들입니다.
from bs4 import BeautifulSoup

htmlDoc =  "<div>상품소개<p class='item' id='p1'> python </p></div>"

# BeautifulSoup을 사용해 웹 페이지를 분석합니다.
soup = BeautifulSoup(htmlDoc , "html.parser") 

# 태그 찾기
tag = soup.find('div').find('p')      #  tag = soup.select_one('div > a')

print(tag.name)   #태그이름 
print(tag.text)   #태그내용
print(tag.string) 
print(tag.attrs)  #태그속성
```

```python
# 모듈을 읽어 들입니다.
from urllib import request
from bs4 import BeautifulSoup

# urlopen() 함수로 기상청의 전국 날씨를 읽습니다.
target = request.urlopen("http://www.kma.go.kr/weather/forecast/mid-term-rss3.jsp?stnId=108")

# BeautifulSoup을 사용해 웹 페이지를 분석합니다.
soup = BeautifulSoup(target, "xml") 

# location 태그를 찾습니다.
for location in soup.select("location"):
    # 내부의 city, wf, tmn, tmx 태그를 찾아 출력합니다.
    print("도시:", location.select_one("city").string)
    print("날씨:", location.select_one("wf").string)
    print("최저기온:", location.select_one("tmn").string)
    print("최고기온:", location.select_one("tmx").string)
    print()
```

## Flask를 활용한 API 서버구축

* [document](https://flask.palletsprojects.com/en/2.0.x/){:target='_blank'}
* 서버의 Application단을 구현 한다기 보단 API Server의 역할을 한다.
* Docker나 Kubernetes를 이용해 여러 개의 컨테이너를 이용하여 스케쥴링이 용이

```python
# save this as app.py
from flask import Flask, escape, request, render_template

app = Flask(__name__)

@app.route('/')
def hello():
    name = request.args.get("name", "World")
    return f'Hello, {escape(name)}!'

@app.route('/main')
def main(name=None):
    return render_template('main.html', name=name)    
```