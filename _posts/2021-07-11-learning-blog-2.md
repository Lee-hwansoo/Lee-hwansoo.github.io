---
title:  "[Blog] Jekyll 디렉터리 구조"
excerpt: "블로그 시작 과정"

categories:
  - Etc
tags:
  - Blog
  - Jekyll
  - Github

# last_modified_at: 
---

## jekyll 디렉터리 구조

```bash
jekyll
├── ⚙️_config.yml     
├── 📁_data
├── 📁_drafts
├── 📁_includes
├── 📁_layouts
├── 📁_posts
├── 📁_sass
├── 📁_site
├── 📝.jekyll-metadata
└── 📝index.html # 올바른 머리말을 가진 'index.md' 도 가능
```  

## _config.yml

환경설정 정보 저장

## _data

```bash
📁_data
   └── ⚙️members.yml
```

사이트에 사용할 데이터를 적절한 포맷으로 정리하여 보관하는 디렉토리  
이 디렉토리에 있는 (확장자와 포맷이 `.yml` 또는 `.yaml`, `.json`, `.csv`, `.tsv` 인) 모든 데이터 파일을 자동으로 읽어들여 `site.data` 로 사용

### members.yml

`site.data.members` 라고 입력하여 그 컨텐츠를 사용

## _drafts

```bash
📁_drafts
   ├── 📝begin-with-the-crazy-ideas.md
   └── 📝on-simplicity-in-technology.md
```

현재 작성중인 초안보관  
초안은 파일명 형식에 날짜 x

## _includes

```bash
📁_includes
   ├── 📝footer.html
   └── 📝header.html
```

재사용하기 위한 파일을 담는 디렉토리로서, 필요에 따라 포스트나 레이아웃에 쉽게 삽입 가능

## _layouts

```bash
📁_layouts
   ├── 📝default.html
   └── 📝post.html
```

포스트를 포장할 때 사용하는 템플릿  
`YAML` 머리말 블록에 레이아웃 설정

## _posts

```bash
📁_posts
   ├── 📝2007-10-29-why-every-programmer-should-play-nethack.md
   └── 📝2009-04-26-barcamp-boston-4-roundup.md
```

컨텐츠를 담는 디렉토리  
`YEAR-MONTH-DAY-title.MARKUP` 형식을 따름

## _sass

```bash
📁_sass
   ├── 📝_base.scss
   └── 📝_layout.scss
```

`main.scss`에 임포트할 수 있는 sass조각들을 담든 디렉토리  
`main.css` 로 가공되어 사이트에서 사용하는 스타일들을 정의

## _site

Jekyll 변환 작업을 마친 뒤 생성된 사이트가 저장되는 기본 경로  
보통 `.gitignore`에 추가해 사용

## .jekyll-metadata

Jekyll은 이 파일을 참고하여, 마지막으로 빌드한 이후에 한번도 수정되지 않은 파일은 어떤 것인지, 다음 빌드 때 어떤 파일을 다시 생성해야 하는지 판단  
보통 `.gitignore`에 추가해 사용

## 기타

📝index.html or 📝index.md 및 다른 📝html,md 파일들은 Jekyll 은 머리말 섹션을 가진 모든 파일을 찾아 변환 작업을 수행

---

참고

[Jekyll 공식 홈페이지](https://jekyllrb-ko.github.io/docs/)
