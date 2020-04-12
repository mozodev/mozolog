---
title: 지킬 검색엔진최적화
date: 2016-04-03
---

예전에는 페이스북 오픈그래프, 트위터 카드 메타태그를 출력하기 위해 _includes 에 social_share.html 이런 식으로 사용했다. 이제는 깃헙 페이지에서 [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag)라는 젬을 사용할 수 있어서 시도해보기로 했다.

[깃헙 페이지 의존성](https://pages.github.com/versions/)


설명
https://github.com/jekyll/jekyll-seo-tag/blob/master/README.md



https://help.github.com/articles/configuring-jekyll/

기본 설정
```
 github: [metadata]
 kramdown:
   input: GFM
   hard_wrap: false
 gems:
   - jekyll-coffeescript
   - jekyll-paginate
```

