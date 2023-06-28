---
title:  "[Blog] Github 블로그 MathJax 추가"
excerpt: "블로그 시작 과정"

categories:
  - Etc
tags:
  - Blog
  - Jekyll
  - Github
  - MathJax

# last_modified_at:
---

## MathJax ?

MathML, LaTeX 및 ASCIIMathML 마크 업을 사용하여 웹 브라우저에 수학 표기법을 표시하는 크로스 브라우저 JavaScript 라이브러리

## 마크다운 엔진 변경

⚙️_config.yml 수정

```yml
# Conversion
markdown: kramdown
highlighter: rouge
lsi: false
excerpt_separator: "\n\n"
incremental: false
```

## html 생성

📁_includes에 📄mathjax_support.html 생성

```html
<script>
MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']]
  }
};
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js">
</script>
```

## html 내용 추가

📄_layouts/default.html에 내용 추가

\<head>태그 사이에 내용 추가

```html
{% raw %}{% if page.use_math %}
  {% include mathjax_support.html %}
{% endif %}{% endraw %}
```

## YAML front-matter 설정

포스트의 front-matter에 use_math: true 사용
