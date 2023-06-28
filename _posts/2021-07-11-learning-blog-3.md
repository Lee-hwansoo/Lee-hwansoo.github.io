---
title:  "[Blog] minimal-mistakes 테마 디렉터리 구조"
excerpt: "블로그 시작 과정"

categories:
  - Etc
tags:
  - Blog
  - Jekyll
  - Github
  - minimal-mistakes

# last_modified_at: 
---

## 불필요한 파일들 삭제

- .editorconfig
- .gitattributes
- .github
- /docs
- /test
- CHANGELOG.md
- minimal-mistakes-jekyll.gemspec
- README.md
- screenshot-layouts.png
- screenshot.png

## 테마 구조

```bash
minimal-mistakes
├── 📁_data                  # data files for customizing the theme
├── 📁_includes
├── 📁_layouts
├── 📁_sass                  # SCSS partials
├── 📁assets
├── ⚙️_config.yml            # site configuration
├── 📝Gemfile                # gem file dependencies
├── 📝index.html             # paginated home page showing recent posts
└── 📝package.json           # NPM build scripts
```

## _data

```bash
📁_data                        # data files for customizing the theme
  ├── ⚙️navigation.yml         # main navigation links
  └── ⚙️ui-text.yml            # text used throughout the theme's UI
```

테마 커스텀을 위한 데이터 파일들이 있는 폴더  
`.yml`, `.yaml`, `.json`, `.csv`, `.tsv` 같은 파일들을 `site.data.(파일명)`로 사용

**⚙️navigation.yml**  
상단 메뉴바

**⚙️ui-text.yml**  
UI의 언어별 텍스트 설정

## _include

```bash
📁_includes
  ├── 📁analytics-providers    # snippets for analytics (Google and custom)
  ├── 📁comments-providers     # snippets for comments
  ├── 📁footer
  ├── 📁head
  ├── 📁search                 # snippets for search
  ├── 📄feature_row              # feature row helper
  ├── 📄gallery                  # image gallery helper
  ├── 📄group-by-array           # group by array helper for archives
  ├── 📄nav_list                 # navigation list helper
  ├── 📄toc                      # table of contents helper
  └── ...
```

많이 재사용 되는 html 파일들을 모아놓은 폴더  
Liquid 언어 태그로 폴더 내의 코드들을 쉽게 삽입해 재사용 가능  
ex) {% raw %}{% include example %}{% endraw %}로 _includes 폴더의 example 코드 삽입

**📁analytics-providers**  
analytics 플랫폼 종류  
google analytics 아닌 다른 analytics 사용시 `custom.html`에 analytics embed code 작성

```bash
📁analytics-providers                    
  ├── 📝google.html          # Google Standard Analytics를 사용할 때
  ├── 📝google-gtag.html     # Google Analytics Global Site Tag를 사용할 때
  ├── 📝google-universal.html # Google Universal Analytics를 사용할 때
  └── 📝custom.html           # 그 밖에 다른 analytics를 사용할 때
```

**📁comments-providers**  
comments 플랫폼 종류  
다른 댓글 플랫폼 사용시 `custom.html`에 analytics embed code 작성

```bash
📁comments-providers                   
  ├── 📝custom_scripts.html     
  ├── 📝custom.html
  ├── 📝discourse.html
  ├── 📝disqus.html
  ├── 📝facebook.html
  ├── 📝giscus.html
  ├── 📝scripts.html
  ├── 📝staticman_v2.html
  ├── 📝staticman.html
  └── 📝utterances.html
```

**📁footer**  
하단 고정부

```bash
📁footer
  └── 📝custom.html          # custom snippets to add to site footer
```

**📁head**  
상단 고정부

```bash
📁head
  └── 📝custom.html          # custom snippets to add to site head
```

**📁search**  
검색엔진

```bash
📁search                   
  ├── 📝aloglia-search-scripts.html # aloglia 검색 엔진
  ├── 📝google-search-scripts.html  # google 검색 엔진
  ├── 📝lunr-search-scripts.html    # lunr 검색 엔진
  └── 📝search_form.html            # 검색창 양식
```

**📄feature_row**  
여러개의 제목, 설명 달린 사진들 가로로 나열 되는 설정파일  
`feature_row`변수 선언 후  `{% raw %}{{% include feature_row %}}{% endraw %}` 로 사용

**📄gallery**  
사진들 가로로 나열 되는 설정파일  
`gallery`변수 선언 후  `{% raw %}{{% gallery %}}{% endraw %}` 로 사용

**📄group-by-array**  
`collection`과 `fileld`를 매개변수로 `group-names`와 `group-items`라는 전역 변수 설정

**📄nav_list**  
_data/navigation.yml(상단 메뉴바 리스트 설정) 표현

**📄toc**  
toc 설정

**📄figure**  
figure(싱글 이미지와 캡션 생성) 설정

**📄video**  
video 삽입 설정

**📝analytics.html**  
analytics 제공자에 따른 html 설정

**📝archive-single.html**  
아카이브 페이지에서 각각의 포스트가 보여지는 모습 설정

**📝author-profile-custom-links.html**  
author-profile.html에서 제공하지 않는 소셜 링크 사용시 작성

**📝author-profile.html**  
author profile 모습 html

**📝breadcrumbs.html**  
포스트 전체 경로 표시해주는 기능 구현 html

**📝browser-upgrade.html**  
IE 9 브라우저로 접속시 브라우저 업데이트 문구 표시

**📝category-list.html**  
post에 작성된 카테고리들을 리스트 표현 기능  
_layouts/single.html에서 include됨

**📝comment.html**  
댓글 한 개의 위치와 모양

**📝comments.html**  
댓글 여러개가 모인 블록  
댓글 플랫폼에 따라 다른 모양

**📝documents-collection.html**  
포스트나 페이지들이 그룹화된 페이지 정렬 및 설정  
`archive`는 자동 분류, `collection`은 사용자 정의 그룹화

**📝footer.html**  
하단부 설정

**📝head.html**  
상단부 설정

**📝masthead.html**  
상단 사이트 관련 설정

**📝page_date.html**  
글의 작성 시간과 수정 시간 표현

**📝page-hero_video.html**  
영상으로된 히어로 이미지(웹 페이지 상단에 위치한 큰 배너 이미지)

**📝page_hero.html**  
히어로 이미지 표시

**📝page_meta.html**  
페이지 메타데이터 표시

**📝page_taxonomy.html**  
글 분류를 위한 태그, 카테고리 리스트 표시

**📝paginator.html**  
페이징 기능

**📝post_paginator.html**  
글 안에서의 페이징 기능(이전글, 다음글)

**📝post-category.html**  
카테고리 archive들을 모은 archive 페이지

**📝post-tag.html**  
태그 archive들을 모은 archive 페이지

**📝scripts.html**  
자바 스크립트, 검색 엔진, 애널리틱스 등등의 소스 구성

**📝seo.html**  
검색 엔진 최적화

**📝sidebar.html**  
사이드바 구성

**📝skip-links.html**  
컨텐츠로 바로가기, 맨 위 아래로 바로가기 같은 스킵 기능

**📝social-share.html**  
공유 링크  
트위터, 링크드인, 페이스북 기본값

**📝tag-list.html**  
post에 작성된 태그들을 리스트 표현 기능  
_layouts/single.html에서 include됨

**📝toc.html**  
toc 기능 구현

## _layouts

```bash
📁_layouts
  ├── 📝archive-taxonomy.html   # tag/category archive for Jekyll Archives plugin
  ├── 📝archive.html            # archive base
  ├── 📝categories.html         # archive listing posts grouped by category
  ├── 📝category.html           # archive listing posts grouped by specific category
  ├── 📝collection.html         # archive listing documents in a specific collection
  ├── 📝compress.html           # compresses HTML in pure Liquid
  ├── 📝default.html            # base for all other layouts
  ├── 📝home.html               # home page
  ├── 📝posts.html              # archive listing posts grouped by year
  ├── 📝search.html             # search page
  ├── 📝single.html             # single document (post/page/etc)
  ├── 📝tag.html                # archive listing posts grouped by specific tag
  ├── 📝tags.html               # archive listing posts grouped by tags
  └── 📝splash.html             # splash page
```

페이지의 디자인과 전체적인 레이아웃을 모아놓은 폴더  
📁_include에 부분적인 html 들이 존재해 이를 사용  
포스트에서 머릿말 YAML헤더에 layout: 값으로 레이아웃을 선택

## _sass

```bash
📁_sass
  ├── 📁minimal-mistakes
  |     ├── 📁skins
  |     ├── 📁vendor
  |     ├── 📝_animation.scss
  |     ├── 📝_archive.scss
  |     ├── 📝_base.scss
  |     ├── 📝_button.scss
  |     ├── 📝_footer.scss
  |     ├── 📝_forms.scss
  |     ├── 📝_masthead.scss
  |     ├── 📝_mixin.scss
  |     ├── 📝_navigation.scss
  |     ├── 📝_notices.scss
  |     ├── 📝_page.scss
  |     ├── 📝_print.scss
  |     ├── 📝_reset.scss
  |     ├── 📝_search.scss
  |     ├── 📝_sidebar.scss
  |     ├── 📝_syntax.scss
  |     ├── 📝_tables.scss
  |     ├── 📝_utillities.scss
  |     └── 📝_variables.scss
  └── 📝minimal-mistakes.scss
```

`📝minimal-mistakes.scss`에 import 할 수 있는 scss 파일들 모은 폴더  
`📝minimal-mistakes.scss`는 `📁assets/css/main.scss`에 import 됨

**📁skins**  
minimal-mistakes 테마의 스킨들

```bash
📁skins
  ├── 📝_air.scss
  ├── 📝_aqua.scss
  ├── 📝_contrast.scss
  ├── 📝_dark.scss
  ├── 📝_default.scss
  ├── 📝_dirt.scss
  ├── 📝_mint.scss
  ├── 📝_neon.scss
  ├── 📝_plum.scss
  └── 📝_sunrise.scss
```

**📁vendor**  
`third-party` classes 나 libraries 폴더

```bash
📁vendor
  ├── 📁breakpoint
  ├── 📁magnific-popup
  └── 📁susy
```

library : `first-party` classes 나 libraries  
프로그램의 구성요소들 중에서 공통으로 사용될 수 있는 특정 기능들을 모듈화(비슷한 성격의 플러그인의 집합)  
Plugin : 어떤 특정한 하나의 문제를 해결하기 위한 컴포넌트

## assests

```bash
📁assets
  ├── 📁css
        └── 📝main.scss            # main stylesheet, loads SCSS partials from _sass
  ├── 📁images                  # image assets for posts/pages/collections/etc.
  └── 📁js
        ├── 📁lunr
        ├── 📁plugins              # jQuery plugins
        ├── 📁vendor               # vendor scripts
        ├── 📝_main.js             # plugin settings and other scripts to load after jQuery
        └── 📝main.min.js          # optimized and concatenated script file loaded before </body>
```

사이트 빌드를 돕는 파일들을 모은 폴더

## _config.yml

환경설정 정보 저장  
{% raw %}`{{site.xxx}}`{% endraw %}는 ⚙️_config.yml에서 정의된 변수  
{% raw %}`{{page.xxx}}`{% endraw %}는 포스트의 YAML 헤더에서 정의된 변수

## Gemfile

사이트에 필요한 젬들의 목록

## index.html

사이트의 홈페이지

## package.json

프로젝트 정보와 의존성(dependencies)을 관리하는 문서  
NPM build scripts

---

참고

[Jekyll 공식 홈페이지](https://jekyllrb-ko.github.io/docs/)  
[minimal-mistakes 공식 홈페이지](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)  
[공부하는 식빵 맘 블로그](https://ansohxxn.github.io/blog/jekyll-directory-structure/)
