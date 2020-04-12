---
title: Github pages 소개
date: 2015-03-16
---

## <i class="openwebicons openwebicons-git"></i> [GIT 깃](http://git-scm.com)?

리누스 토발즈가 linux kernel 소스 관리를 위해 만든 분산형 소스 버전 관리 프로그램입니다.

## <span class="mega-octicon really-more-mega octicon-mark-github"></span> [GITHUB 깃헙](http://github.com)? 코드 공유와 협업의 바다

GIT을 활용해서 모든 사람들과 코드를 공유하고 협업할 수 있는 플랫폼을 제공하는 서비스입니다. 회사가 운영하는 서비스이지만 오픈소스 프로젝트의 경우 코드 저장소와 대부분의 기능을 무료로 제공합니다. 사설 저장소를 사용하려면 유료 플랜에 가입해야 하고 기업에게 인프라로 서비스를 제공하기도 합니다. 

어쨌든 거의 매일 알게 모르게 사용하는 중요하고 고마운 코드들이 여기에 있고 수많은 개발자들이 열린 자세로 대화하며 협업하는 거대한 코드의 바다라고 할 수 있습니다.

## <span class="mega-octicon really-more-mega octicon-octoface"></span> [GITHUB PAGES 깃헙 페이지](http://pages.github.com)? 정적 웹사이트 호스팅

> Websites for you and your projects.   
> 당신과 당신의 프로젝트를 위한 웹사이트!   
> 깃헙 페이지는 깃헙 웹사이트를 통해서 공개하고 깃헙이 호스팅하는 웹페이지입니다. 

<!--break-->

오픈소스 프로젝트는 가벼운 문서화부터, 간단한 웹사이트, 조그만 라이브러리, 바이너리, 심각하게 거대한 프로그램까지 정말 다양합니다. 그런데 무슨 일을 하든 홍보하려면 웹사이트는 기본이죠. 오픈소스 프로젝트도 예외가 아닙니다. 코드가 아무리 뛰어나면 뭐합니까 알리지 못하면... 음 아주 뛰어나면 다들 찾아서 쓰겠지만... 코드를 쓰는 사람뿐만 아니라 누구에게나 알리려면 일종의 번역이 필요한 셈이죠.

어쨌든 이렇게 프로젝트 홍보를 위해 깃헙이 오픈소스 프로젝트에 대한 정적인 웹호스팅도 무료로 제공합니다. 쉽게 말하면 아파치나 엔진엑스같은 웹서버에 html, css, 이미지 등을 호스팅하게 해준다는 말이죠. 게다가 [fastly](http://www.fastly.com/customers/github/) [CDN](http://en.wikipedia.org/wiki/Content_delivery_networ)도 붙어 있어서 어디서나 페이지 로딩이 빠릅니다.

깃헙 페이지는 깃헙 인프라를 활용해서 오픈소스 프로젝트를 지원하는 서비스라고도 볼 수 있습니다. 깃헙은 사용자, 단체, 프로젝트, 위키나 이슈에 대한 정보를 api로 서비스하고 있고 곧 자신의 인프라를 노출하고 있는 것이죠 뿐만 아니라 댓글, 공동 작업, 메신저 등등 어떤 문제를 해결해주는 좋은 도구들이 많이 있고 마찬가지로 서로 연동하기 좋아진 상황입니다. 이런 상황을 활용해서 static 웹페이지가 아니라 보다 가볍게 동적인 웹서비스를 만들 수도 있을 것 같습니다.

### 깃헙 페이지 특징
- 사용자, 단체, 프로젝트 소개
- 블로그 쓰기
- 자신의 도메인 연결

### 깃헙 페이지 사용법
- [자동 생성기 사용하기](https://help.github.com/articles/creating-pages-with-the-automatic-generator/)
- [직접 프로젝트 페이지 만들기](https://help.github.com/articles/creating-project-pages-manually/)
- [지킬 사용하기](https://help.github.com/articles/using-jekyll-with-pages/)


## [Jekyll 지킬](http://jekyllrb.com): 정적 웹사이트 생성기

> Transform your plain text into static websites and blogs.   
> 작성한 원고를 정적인 웹사이트와 블로그로 만들어드려요.   

데이터베이스, 댓글 승인, 업데이트 이딴거 없이 그냥 콘텐츠만 작성하면 웹페이지로 표시해주는 루비로 작성한 프로젝트로 가장 유명한 [static site generator](https://www.staticgen.com)입니다.

> 왜 매번 사용자가 요청할 때마다 서버 자원을 사용하며 html을 빌드해야하는 걸까?

지킬은 이런 질문에 대한 대답 중 하나입니다. 원고를 변경하면 한 번 빌드해서 배포하는거죠. 사용자와의 복잡한 인터렉션이 필요없고 주로 일방적으로 콘텐츠를 서비스하는 경우 이런 접근은 여러 가지 이점을 갖게 됩니다. 

복잡한 인터렉션을 수행하는 웹서비스의 경우에는 적합하지 않지만 한 사람이 글을 쓰며 자주 수정하지 않고 여러사람이 보는 블로그나 회사 소개 등 정보를 알리기 위한 웹사이트라면 지킬과 같은 [static site generator](https://www.staticgen.com)가 적절한 기술 중 하나가 될 수 있습니다.

### 이점
- 빌드한 결과는 모두 정적인 파일로, 깃헙이 무료로 호스팅을 해줍니다. 
- 요청 시 마다 빌드가 아니라 바로 html, 게다가 cdn도 달아놔서 꽤나 빠릅니다. 
- 서버가 해킹당하는 등의 보안 걱정이 없습니다. 

### 단점
- 댓글, 회원가입, 신청, 폼 입력 등의 인터랙션은 음....
- 개발자는 나름 편할지 모르지만 코드를 모르는 사람은 음.... 
- 매번 또 메일 보내야함? 그냥 워드프레스처럼 글 쓰고 이미지 올릴 수만 있음 되는데?
- 깃헙 공격 당하거나 망하면 사이트 접근이 안되거나 없어지는?

### 지킬 사용 시 참고
- [깃헙 페이지 의존성](https://pages.github.com/versions/)
- [github-pages gem](https://rubygems.org/gems/github-pages)


### [Prose](http://prose.io/#about): 깃헙용 콘텐츠 편집기

> Prose는 [CMS가 없는 웹사이트](http://developmentseed.org/blog/2012/07/27/build-cms-free-websites/)에 
멋지고 간결한 컨텐츠 제작 환경을 제공해 줍니다.

> Prose는 [GitHub](http://github.com) 상의 컨텐츠를 관리하는 웹기반의 인터페이스를 제공해 줍니다. Prose를 이용하면 파일을 생성 수정 삭제하고 변경내용을 GitHub에 직접 저장할 수 있습니다. 
웹사이트를 [GitHub Pages](http://pages.github.com)에 무료로 호스팅하거나 직접 [GitHub webhook server](http://developmentseed.org/blog/2013/05/01/introducing-jekyll-hook/)를 셋업하기 바랍니다.

> Prose는 [Jekyll](http://jekyllrb.com/) 사이트와 [markdown content](http://daringfireball.net/projects/markdown/)에 대한 지원을 향상시켜 왔습니다. 
Prose는 Jekyll 사이트 내의 마크다운 글들을 찾아서 해당 사이트의 
전체 레이아웃 상에서 문법 하이라이팅, 툴바, 초안 미리보기를 제공해 줍니다. 

> 개발자는 Jekyll 사이트를 설정하여 이러한 장점과 컨텐트 편집을 
커스터마이징할 수 있는 많은 기능들을 사용할 수 있습니다. 
> - [prose.io#about](http://prose.io/#about)

워싱턴 DC에 있는 데이터 시각화 맵핑 [mapbox](http://mapbox.com) 서비스를 운영하는 [Development Seed](http://developmentseed.org)라는 회사가 개발하고 유지보수를 하고 있는 서비스입니다. 개인적으로 이 회사를 알게 된 계기는 예전에 상당히 활발하게 [Drupal 드루팔](http:drupal.org) 커뮤니티에 기여했기 때문입니다. 

간략하게 설명하면 자신의 깃헙 계정으로 로그인해서 쓰기 권한이 있는 저장소에 접근해서 워드프레스같은 CMS에서 편집하는 듯한 화면을 만들어 줍니다. 다만 위지윅이 아니라 [markdown 마크다운](http://daringfireball.net/projects/markdown/syntax) 에디터이기는 합니다. 깃헙에서 사용할 수 있는 [깃헙용 마크다운 github flavored markdown](https://guides.github.com/features/mastering-markdown/)를 참고하시면 좋습니다. 어쨌든 이런 서비스까지 함께 사용하면 코드를 모르는 사람도 충분히 글을 써서 웹사이트에 공개할 수 있습니다. 

## 마무리

오픈소스 문화가 번성하면서 다양한 사람들이 여러가지 문제를 해결해가는 협업 과정과 그 결과를 보고 그 자체가 너무 재밌기도 하고 인상적이어서 공유하고 싶어서 깃에서부터 깃헙, 깃헙 페이지, 지킬, 프로즈까지 장황하게 소개했습니다. 좀 더 구체적으로는 회사, 단체, 행사, 문서화 소개 페이지 등을 지킬과 깃헙 페이지를 활용해서 만들면 IT분야의 적정기술처럼 여러가지 면에서 참 좋을 것 같습니다.

이런 과정은 단순히 개발자들만의 문화가 아니고 코드 바깥의 메트릭스 세상의 변화와 궤를 같이 하고 있다고 생각합니다. 저는 앞으로도 재밌게 기술과 정보와 마음을 공유하며 여러 가지 문제를 해결하고 좀 더 나은 세상을 만들어나가는 이런 즐겁고 유괘한 경험을 계속해나고 싶습니다.

개인적으로 지킬과 깃헙 페이지가 썩 마음에 들고 이미 여러 웹사이트를 이렇게 만들면서 느낀 재미와 문제 해결법에 대해서 앞으로 틈틈이 포스팅하겠습니다.

