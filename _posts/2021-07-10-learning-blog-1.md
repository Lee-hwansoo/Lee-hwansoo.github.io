---
title:  "[Blog] 블로그 기본 설정, 커스텀"
excerpt: "블로그 시작 과정"

categories:
  - Etc
tags:
  - Blog
  - Jekyll
  - Github

last_modified_at: 2022-02-19
---

2022-02-19 📌 업데이트를 수시로 진행
{: .text-center .notice--info}

## _config.yml 설정

```yml
minimal_mistakes_skin    : "dark" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# Site Settings
locale                   : "ko-KR"
title                    : "STORAGE"
subtitle                 : "Daily Learning 🏆"
name                     : "Lee Hwan Soo"
description              : "Blog"
url                      : "https://Lee-hwansoo.github.io"
breadcrumbs            : true # true, false (default)
atom_feed:
  path                   : 
  hide                   : true
search                   : true # true, false (default)
search_full_content      : true # true, false (default)

# Site Autor

author:
  name             : "Lee Hwan Soo"
  avatar           : "/assets/images/avatar.jpg"
  bio              : "Growing Developer 🍀"
  location         : "Seoul, Korea"
  links:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/Lee-hwansoo"

# Site Footer

footer:
  links:
  - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/Lee-hwansoo"

# Outputting

permalink: /:categories/:title/
paginate: 4 # amount of posts to show
paginate_path: /page:num/
timezone: Asia/Seoul

# Defaults

defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: false
      show_date: true
      comments: # true
      share: false
      related: true
      toc: true
      toc_sticky: true
      toc_label: "목차"
      toc_icon: "align-left"
      sidebar_main: true

  # _pages
  - scope:
      path: ""
      type: pages
    values:
      layout: single
      author_profile: true
      read_time: false
      show_date: true
      comments: # true
      share: false
      related: true
      toc: true
      toc_sticky: true
      toc_label: "목차"
      toc_icon: "align-left"
      sidebar_main: true

```

## 시간 형식 변경

📝_includes/page_date.html

```html
<!-- default -->
{% raw %}{% assign date_format = site.date_format | default: "%B %-d, %Y" %}

<!-- 변경 후 -->
{% assign date_format = site.date_format | default: " %Y.%m.%d" %}{% endraw %}
```

📝_includes/page_meta.html

```html
<!-- default -->
{% raw %}{% assign date_format = site.date_format | default: "%B %-d, %Y" %}

<!-- 변경 후 -->
{% assign date_format = site.date_format | default: " %Y.%m.%d" %}{% endraw %}
```

## 기본 폴더 및 페이지 생성
  
📁_posts 생성  
📁/assets/images 생성  
📁_pages 생성
  
📝_pages/404.md

```md
---
title: "Page Not Found"
excerpt: "Page not found. Your pixels are in another canvas."
sitemap: false
permalink: /404.html
---

Sorry, but the page you were trying to view does not exist.
```

📝_pages/category-archive.md

```md
---
title: "Posts by Category"
layout: categories
permalink: /categories/
author_profile: true
---
```

📝_pages/tag-archive.md

```md
---
title: "Posts by Tag"
permalink: /tags/
layout: tags
author_profile: true
---
```

## 스킨 설정

📝_sass/minimal-mistakes/skins/_dark.scss

```scss
/* Colors */
$background-color: #252a34 !default;
$text-color: #eaeaea !default;
$primary-color: #00adb5 !default;
$border-color: mix(#fff, $background-color, 20%) !default;
$code-background-color: mix(#000, $primary-color, 40%) !default;
$code-background-color-dark: mix(#000, $background-color, 20%) !default;
$form-background-color: mix(#000, $background-color, 15%) !default;
$footer-background-color: mix(#000, $background-color, 30%) !default;
$link-color: mix($primary-color, $text-color, 40%) !default;
$link-color-hover: mix(#fff, $link-color, 25%) !default;
$link-color-visited: mix(#000, $link-color, 25%) !default;
$masthead-link-color: $text-color !default;
$masthead-link-color-hover: mix(#000, $text-color, 20%) !default;
$navicon-link-color-hover: mix(#000, $background-color, 30%) !default;

.author__urls.social-icons i,
.author__urls.social-icons .svg-inline--fa,
.page__footer-follow .social-icons i,
.page__footer-follow .social-icons .svg-inline--fa  {
  color: inherit;
}

.ais-search-box .ais-search-box--input {
  background-color: $form-background-color;
}
```

## navigation 설정

⚙️_data/navigation.yml

```yml
main:
  - title: "Home"
    url: /
  - title: "Category"
    url: /categories/
```

## 영역및 글자 설정

### 본문영역 크기

📝_sass/minimial-mistakes/_variables.scss

```scss
$right-sidebar-width-narrow: 200px !default; // default 200px
$right-sidebar-width: 200px !default; // default 300px
$right-sidebar-width-wide: 300px !default; // default 400px
```

### 글자 크기

📝_sass/minimal-mistakes/_reset.scss

```scss
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 15px;          // default 16px

  @include breakpoint($medium) {
    font-size: 17px;        // default 18px
  }

  @include breakpoint($large) {
    font-size: 17px;        // default 20px
  }

  @include breakpoint($x-large) {
    font-size: 19px;        // default 22px
  }

```

### 본문 글 간격 조절

📝_sass/minimal-mistakes/_base.scss  

```scss
body {
  margin: 0;
  padding: 0;
  color: $text-color;
  font-family: $global-font-family;
  line-height: 1.8;
}
```

### 하이퍼링크 밑줄 제거

📝_sass/minimal-mistakes/_base.scss  

```scss
a { /*devinlife : a link 하이퍼링크 밑줄 없애기*/  
text-decoration: none;

  &:focus {
    @extend %tab-focus;
  }

  &:visited {
    color: $link-color-visited;
  }

  &:hover {
    color: $link-color-hover;
    outline: 0;
  }
```

### 인용과 코드 강조 변경

📝_sass/minimal-mistakes/_base.scss

```scss
/* blockquotes */

blockquote {
  margin: 2em 1em 2em 0;
  padding-left: 1em;
  padding-right: 1em;
  // font-style: italic;
  border-left: 0.25em solid $primary-color;

  cite {
    font-style: italic;

    &:before {
      content: "\2014";
      padding-right: 5px;
    }
  }
}


/* code */

tt,
code,
kbd,
samp,
pre {
  font-family:  $global-font-family;
}

pre {
  overflow-x: auto; /* add scrollbars to wide code blocks*/
}

p > code,
a > code,
li > code,
figcaption > code,
td > code {
  padding-top: 0.1rem;
  padding-bottom: 0.1rem;
  font-size: 0.95em;
  background: $code-background-color;
  border-radius: $border-radius;

  &:before,
  &:after {
    letter-spacing: -0.2em;
    content: "\00a0"; /* non-breaking space*/
  }
}
```

### 사이드바 크기 조정

📝_sass/minimal-mistakes/_sidebar.scss

```scss
.sidebar {
  p,
  li {
    font-family: $sans-serif;
    font-size: $type-size-6;
    line-height: 1.3;
  }
}

.sidebar .author__name {
  font-family: $sans-serif;
  font-size: $type-size-4;
}

.author__bio {
  margin: 0;

  @include breakpoint($large) {
    margin-top: 10px;
    margin-bottom: 20px;
  }

  p {
  margin-top: 1.6px;
  margin-bottom: 3px;
  }
}
```

### 네비게이션 글자 크기 조절

📝_sass/minimal-mistakes/_navigation.scss

```scss
.nav__list {
    a {
      // padding: 0.25em 0;
      }
}

.nav__list .nav__items {
  margin: 0;
  font-size: 1.25rem;

  a {
    color: inherit;
    line-height: 1.8;
    font-size: 14px;
  }

.nav__sub-title {
  display: block;
  margin: 0.5rem 0;
  padding: 0.25rem 0;
  font-family: $sans-serif-narrow;
  font-size: 15px;
  font-weight: bold;
  text-transform: uppercase;
  border-bottom: 1px solid $border-color;
}
```

### toc 관련 설정

📝_sass/minimal-mistakes/_navigation.scss

```scss
.toc__menu {
    &:hover {
      color: mix(#000, $primary-color, 30%);
    }
 }
```

## 하단 footer 변경

📝_includes/footer.html

```html
<div class="page__footer-copyright">&copy; {{ site.time | date: '%Y' }} {{ site.name | default: site.title }}</div>
```

## 같은 카테고리 내에서의 이전글, 다음글 이동

📝_includes/post_pagination.html

```html
{% raw %}<!-- default-->
{% if page.previous or page.next %}
  <nav class="pagination">
    {% if page.previous %}
      <a href="{{ page.previous.url | relative_url }}" class="pagination--pager" title="{{ page.previous.title | markdownify | strip_html }}">{{ site.data.ui-text[site.locale].pagination_previous | default: "Previous" }}</a>
    {% else %}
      <a href="#" class="pagination--pager disabled">{{ site.data.ui-text[site.locale].pagination_previous | default: "Previous" }}</a>
    {% endif %}
    {% if page.next %}
      <a href="{{ page.next.url | relative_url }}" class="pagination--pager" title="{{ page.next.title | markdownify | strip_html }}">{{ site.data.ui-text[site.locale].pagination_next | default: "Next" }}</a>
    {% else %}
      <a href="#" class="pagination--pager disabled">{{ site.data.ui-text[site.locale].pagination_next | default: "Next" }}</a>
    {% endif %}
  </nav>
{% endif %}

<!-- 같은 카테고리에서의 이동 -->
{% assign cat = page.categories[0] %}
{% assign cat_list = site.categories[cat] %}
{% for post in cat_list %}
  {% if post.url == page.url %}
   {% assign prevIndex = forloop.index0 | minus: 1 %}
   {% assign nextIndex = forloop.index0 | plus: 1 %}
   {% if forloop.first == false %}
     {% assign next_post = cat_list[prevIndex] %}
   {% endif %}
   {% if forloop.last == false %}
     {% assign prev_post = cat_list[nextIndex] %}
   {% endif %}
   {% break %}
  {% endif %}
{% endfor %}

{% if prev_post or next_post %}
  <nav class="pagination">
    {% if prev_post %}
      <a href="{{ prev_post.url }}" class="pagination--pager">{{ site.data.ui-text[site.locale].pagination_previous | default: "Previous" }}</a>
    {% else %}
      <a href="#" class="pagination--pager disabled">{{ site.data.ui-text[site.locale].pagination_previous | default: "Previous" }}</a>
    {% endif %}
    {% if next_post %}
      <a href="{{ next_post.url }}" class="pagination--pager">{{ site.data.ui-text[site.locale].pagination_next | default: "Next" }}</a>
    {% else %}
      <a href="#" class="pagination--pager disabled">{{ site.data.ui-text[site.locale].pagination_next | default: "Next" }}</a>
    {% endif %}
  </nav>
{% endif %}

<!-- 같은 카테고리에서의 이동 응용 -->
{% assign cat = page.categories[0] %}
{% assign cat_list = site.categories[cat] %}
{% for post in cat_list %}
  {% if post.url == page.url %}
   {% assign prevIndex = forloop.index0 | minus: 1 %}
   {% assign nextIndex = forloop.index0 | plus: 1 %}
   {% if forloop.first == false %}
     {% assign next_post = cat_list[prevIndex] %}
   {% endif %}
   {% if forloop.last == false %}
     {% assign prev_post = cat_list[nextIndex] %}
   {% endif %}
   {% break %}
  {% endif %}
{% endfor %}

{% if prev_post or next_post %}
  <nav class="pagination_prev_next">
    {% if prev_post %}
      <a href="{{ prev_post.url }}" class="pagination_prev_next--pager"><span class="prev_next">이전 글  &nbsp</span>{{ prev_post.title }}</a>
    {% else %}
      <a href="#" class="pagination_prev_next--pager disabled">첫 번째 글입니다</a>
    {% endif %}
    {% if next_post %}
      <a href="{{ next_post.url }}" class="pagination_prev_next--pager"><span class="prev_next">다음 글  &nbsp  </span>{{ next_post.title }}</a>
    {% else %}
      <a href="#" class="pagination_prev_next--pager disabled">가장 최근 글입니다</a>
    {% endif %}
  </nav>
{% endif %}{% endraw %}
```

메인 페이지에서의 페이지 넘김 또한 `pagination` class로 관리  
게시글에서의 이전 글, 다음 글 관리를 따로하기위해 `pagination_prev_next` calss 생성

📝_sass/minimal-mistakes/_navigation.scss

```scss
//가로로 긴 막대 2개로 게시글에서의 이전 글, 다음 글
.pagination_prev_next {
  @include clearfix();
  float: left;
  width: 100%;
  margin-top: 1em;

  /* next/previous buttons */
  &--pager {
    margin-top: 0em;
    padding-top: 0em;
    display: block;
    padding: 1em 2em;
    //float: left;
    width: 100%;
    //font-family: $sans-serif;
    font-size: $type-size-5;
    font-weight: bold;
    text-align: center;
    text-decoration: none;
    color: $muted-text-color;
    border: 1px solid mix(#000, $border-color, 25%);
    border-radius: $border-radius;
    
    //.prev_next {
      //font-family: $monospace;
      //color:#ffd861; }
    }
}
```

## 사이드 카테고리 만들기

1. 같은 카테고리를 모아 놓는 페이지 생성

   1. 📁_pages/categories 폴더 생성

   2. 📝같은 카테고리 페이지 생성

      ```md
      ---
      title: "Blog" <!-- 카테고리 모음페이지 제목 -->
      layout: archive
      permalink: categories/blog <!-- 페이지 주소 -->
      author_profile: true
      sidebar_main: true <!-- 사이드 바와 연결 -->
      ---
      {% raw %}
      <!-- 카테고리 등록한 것들 검색 -->
      {% assign posts = site.categories.Blog %}
      {% for post in posts %}
      {% include archive-single.html type=page.entries_layout %} {% endfor %}
      {% endraw %}
      ```

2. 1번 페이지들을 모아 사이드바 설정

   1. 1번 페이지들을 모으는 📝_includes/nav_list_categories 작성

      ```html
      <!--전체 글 수를 세기 위한 연산. sum 변수에 전체 글 수 저장-->
      {% raw %}
      {% assign sum = site.posts | size %}

      <nav class="nav__list">
        <input id="ac-toc" name="accordion-toc" type="checkbox" />
        <label for="ac-toc">카테고리 펼치기</label>
        <ul class="nav__items" id="category_tag_menu">
            <!--전체 글 수-->
            <li>
                  📂 전체 글 수 {{sum}}개 
            </li>
            <li>
              <!--span 태그로 카테고리들을 크게 분류 ex) C/C++/C#-->
              <span class="nav__sub-title">🗑️ etc</span>
                  <!--ul 태그로 같은 카테고리들 모아둔 페이지들 나열-->
                  <ul>
                      <!--Cpp 카테고리 글들을 모아둔 페이지인 /categories/cpp 주소의 글로 링크 연결-->
                      <!--category[1].size 로 해당 카테고리를 가진 글의 개수 표시--> 
                      {% for category in site.categories %}
                          {% if category[0] == "Blog" %}
                              <li><a href="/categories/blog" class="">📖 Blog ({{category[1].size}})</a></li>
                          {% endif %}
                      {% endfor %}
                  </ul>
           </li>
        </ul>
      </nav>{% endraw %}
      ```

   2. 📝_includes/sidebar.html 에 추가

      ```html
      <!-- div 사이에 추가 -->
      {% raw %}{% if page.sidebar_main %}
        {% include nav_list_categories %}
      {% endif %}{% endraw %}
      ```

   3. ⚙️_config.yml 에서 sidebar_main: true 값 사용

## 버튼 색상 변경

📝_sass/minimal-mistakes/_buttons.scss

```scss
.btn {
  $buttoncolors:
    (primary, $primary-color),
    (inverse, $link-color), // default #fff
}
```

## 스크롤바 커스터마이징

📝_sass/minimal-mistakes/_reset.scss

```scss
::-webkit-scrollbar{
  width: 13px; // 세로 스크롤의 너비
  height: 8px; // 가로 스크롤의 너비
  background-color: $footer-background-color; // 스크롤의 기본 배경색상
}
::-webkit-scrollbar-thumb{
  border-radius: 3px; // 스크롤바 곡률
  background-color: $primary-color; // 스크롤바 색상
}

::-webkit-scrollbar-track:horizontal{
  background-color: $primary-color; // 가로 스크롤바 색상
}
```

## 글 하단에 맨위로 이동 버튼

📝_includes/page_date.html

```html
{% raw %}{% assign date_format = site.date_format | default: " %Y.%m.%d" %}
{% if page.last_modified_at %}
  <p class="page__date"><strong><i class="fas fa-fw fa-calendar-alt" aria-hidden="true"></i> {{ site.data.ui-text[site.locale].date_label | default: "Updated:" }}</strong> <time datetime="{{ page.last_modified_at | date: "%Y-%m-%d" }}">{{ page.last_modified_at | date: date_format }}</time></p>
  <p>
    <a href="#page-title" class="back-to-top">맨 위로 이동 ↑</a>
  </p>
{% elsif page.date %}
  <p class="page__date"><strong><i class="fas fa-fw fa-calendar-alt" aria-hidden="true"></i> {{ site.data.ui-text[site.locale].date_label | default: "Updated:" }}</strong> <time datetime="{{ page.date | date_to_xmlschema }}">{{ page.date | date: date_format }}</time></p>
  <p>
    <a href="#page-title" class="back-to-top">맨 위로 이동 ↑</a>
  </p>
{% endif %}{% endraw %}
```

## 파비콘 설정

1. <https://favicon.io/emoji-favicons>에 들어가서 마음에 드는 이모지를 찾은 후 다운로드 or 다른 이미지 다운로드

2. png나 jpg 확장자의 이미지 파일을 <https://realfavicongenerator.net/>에 select your favicon image 버튼을 누른 후 업로드

3. 이 곳에 이미지 파일을 업로드

4. Favicon package 다운로드 후 프로제트 최상위 폴더에 압축해제

5. 맨 밑에 Generate your Favicons and HTML code

6. 해당 HTML 태그를 _includes/head/custom.html에 저장

7. git commit, git push하여 웹 서버에 반영
