---
title:  "[Blog] 블로그 만들기"
excerpt: "블로그 시작 과정"

categories:
  - Etc
tags:
  - Blog
  - Jekyll
  - Github

# last_modified_at: 
---

## Github Pages

[Github Pages 설명](https://pages.github.com/) → 웹 호스팅

### Static webSite

클라이언트가 서버에 페이지를 요청(URL)하면, **서버에 미리 저장된 문서(HTML, 이미지 등)**를 그대로 클라이언트에게 전달 하는 방식.  
구성 = User Interface : HTML, CSS, JS 등등

### Dynamic website

클라이언트가 서버에 페이지를 요청(URL)하면, **서버는 클라이언트의 요청(변수)을 처리**하여 HTML 문서를 생성하고 이를 전달 하는 방식.  
구성 = User Interface, Sever Side : 서버측 스크립트(PHP 등), DB 등

### Static Site Generator

[Jekyll](https://jekyllrb-ko.github.io/) 사용  
Jekyll은 Ruby로 작성

## Ruby?

>루비는 마츠모토 유키히로가 개발한 동적 객체 지향 스크립트 프로그래밍 언어. 루비는 순수 객체 지향 언어이기 때문에, 정수나 문자열 등을 포함한 데이터 형식 등 모든 것이 객체  
>클래스 정의, 가비지 컬렉션, 강력한 정규 표현식 처리, 다중 스레드, 예외 처리, 반복, 클로저, Mixin, 연산자 오버로드 등의 기능

### 루비 기초 용어

#### `Gem`

루비 프로젝트에 포함시킬 수 있는 코드. 기능들을 패키지화해서 다른 사람들이나 프로젝트에 공유

#### `Gemfile`

사이트에 필요한 젬들의 목록

```ruby
# 예시
source "https://rubygems.org"

gem "jekyll"
gem "minimal-mistakes-jekyll"
gem 'wdm'
gem 'tzinfo'
gem "tzinfo-data"
gem "webrick"
```

#### `Bundler`

필요한 `gem`과 그 `gem`의 버전을 설치하고, 추적하는 것으로 일관성 있는 Ruby 프로젝트를 제공하는 도구  
`$ Gem install bundler`로 bundler 설치 가능  
`$ bundle install`로 `Gemfile`에 있는 Gem들을 한번에 설치  
Jekyll 프로젝트 생성할 때마다 아니라 한 번만 설치

#### 세부사항

`Gemfile` 사용시 `$ bundle install`로 `gemfile`의 젬들 설치 후 `$ bundle exec jekyll serve`로 사이트 빌드 => `Gemfile`에 설정된 버전 젬들 사용

`Gemfile` 사용 안할 시 `$ Jekyll serve`로 사이트 빌드

## Jekyll on Windows

Jekyll 설치

1. Ruby 설치 : [Ruby installer for Windows](https://rubyinstaller.org/downloads/)
2. 터미널에 `$ Ruby -v` 로 환경변수 설정 확인
3. `$ Gem install jekyll bundler` jekyll 와 bundler 설치
4. `$ Jekyll -v` 로 Jekyll 설치 확인

## 테마 고르기 및 사이트 배포

1. 테마 github Fork
2. Fork 된 Repositories 이름 `/\<USERNAME>\.github.io` 으로 변경
3. _config.yml 의 url `"https://\<USERNAME>\.github.io"` 수정
4. `https://\<USERNAME>\.github.io` 접속
5. 작업 및 포스팅 후 `$ git push` 통해 사이트 배포

## 로컬 블로그

### 사용이유
  
사이트의 변경사항등을 배포하지 않고 즉각적으로 확인 가능

### 생성 방법

1. 필요한  `gem`들 `gemfile`에 작성 후 터미널로 프로젝트 폴더에서 `$ bundle install`로 설치

    ```ruby
    # gemfile 목록 예시
    source "https://rubygems.org"

    gem "jekyll"
    gem "minimal-mistakes-jekyll"
    gem 'wdm'
    gem 'tzinfo'
    gem "tzinfo-data"
    gem "webrick"
    ```

2. 터미널로 프로젝트 폴더에서 `$ bundle exec jekyll serve`

    ```ruby
    $ bundle exec jekyll serve

    # 출력 화면
    
    Configuration file:(Project folder)/_config.yml
                Source:(Project folder)
           Destination: (Project folder)/_site
    Incremental build: disabled. Enable with --incremental
          Generating...
                        done in 3.658 seconds.
    Auto-regeneration: enabled for '(Project folder)'
        Server address: http://127.0.0.1:4000//
      Server running... press ctrl-c to stop.
    ```

3. [로컬 블로그](http://localhost:4000/) 생성 완료
