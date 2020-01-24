---
title: Jekyll을 이용해서 Github 사이트 만들기
tags: Jekyll
comments: ture
---

## 목록
> 1. 개인 블로그를 만들게된 이유
> 2. 블로그를 만들기 위해 사용한 기능
> 3. 간략한 과정
> 4. 오류 및 팁
> 5. 기간
> 6. 참고 사이트

---

### 개인 블로그를 만들게된 이유
 >  HTML, CSS, JS를 공부하고 개인 홈페이지를 만들었는데 Jekyll로 사이트를 만들면 편하고 좋은 사이트를 만들 수 있다고 해서 도전.
<hr/>
### 개인 블로그를 만들기 위해서 사용한 기능
> 1. Jekyll
  - 사이트를 구성하는 모든 것을 만듬.
  + 일정 형식에 맞추어 작성한 글을 이미 짜여진 HTML, CSS, JC을 사용하여 자동으로 변환해주기 때문에 일일이 페이지를 만들 필요가 없음.
  하지만 Jekyll은 컨셉부터 다릅니다. 아주 생소한 메커니즘을 갖고 있습니다. 파일 기반의 데이터를 정적인 리소스로 빌드해서 서비스하죠. 게시글마다 md 파일이나 html 파일을 생성합니다. 글을 작성하고 배포하기 위한 빌드를 진행하면 응답할 html 화면을 만들고, 파일로 저장해 준비합니다. 이 상태에서 유저가 특정 화면을 요청하면 미리 생성한 html 파일을 찾아 꺼내주기만 하면 되죠. 다시 말해, 데이터베이스를 조회하고 HTML 양식으로 응답값을 만드는 과정이 생략되는 것입니다. [참고2: jekyll의 메커니즘을 이해하고 커스터마이징하기](https://dreamgonfly.github.io/2018/01/27/jekyll-remote-theme.html)
	- 오픈 소스를 찾아서 빌드하는 경우 쉽게 만들 수 있음.
 2. Github
+ 웹호스팅 및 오픈 소스를 구하기 위한 사이트.
 - 오픈 소스 사용법은 Repositories(=이하 레포) 안에 자세히 설명되어 있음으로 다른 블로그와 병행해서 참고하되 레포 안에 설명이 우선적임.  
<hr/>
###  간략한 과정
> 1. Jekyll 설치하기 (Ryby,Rybygam)
   + [RubyInstaller](https://jekyllrb-ko.github.io/docs/windows/)에서 RubyInstaller를 통한 설치
  2. Jekyll 테마 고르기 (오픈 소스)
   + <http://jekyllthemes.org/> <https://jekyllthemes.io/free>
  3. Github의 레포를 사이트로 만들기(웹호스팅)
<hr/>
###  오류 및 팁

> + Github의 레포를 컴파일하고 나서 대락 1분 후에 사이트에 반영된다.
  + Jekyll은 '[markdow](https://gist.github.com/ihoneymon/652be052a0727ad59601)'의 간단한 문법체계로 쓰여진다.
  + Jeklly -serve 명령에 의해서 기본 홈피가 실행되어야 한다.(자신의 깃허브 아이디를 넣어서 적용해야 한다.)
<hr/>
###  기간
> #### 20.01.06~01.07
<hr/>
### 참고 사이트

1. [쉽고 빠르게 수준 급의 GitHub 블로그 만들기-jekyll remote theme으로](https://dreamgonfly.github.io/2018/01/27/jekyll-remote-theme.html)
2. [jekyll의 메커니즘을 이해하고 커스터마이징하기](http://labs.brandi.co.kr/2019/04/15/chunbs.html)

---
