title: "Chaejun Portfolio"
description: "전기·전자/제어공학 학습 & 프로젝트 포트폴리오"
url: "https://USERNAME.github.io"   # USERNAME을 깃허브 아이디로 변경
locale: "ko-KR"

# Minimal Mistakes 원격 테마 사용
remote_theme: "mmistakes/minimal-mistakes@4.26.2"

# 기본 설정
markdown: kramdown
theme: null
timezone: Asia/Seoul

# 네비게이션
defaults:
  - scope:
      path: ""
    values:
      layout: single
      author_profile: true

plugins:
  - jekyll-feed
  - jekyll-seo-tag
  - jekyll-include-cache

# 사이드바 프로필
author:
  name: "채준"
  avatar: "/assets/img/profile.jpg"
  bio: "전기·전자공학 전공 | 제어·전력 실험과 시각화 좋아함"
  links:
    - label: "GitHub"
      icon: "fab fa-github"
      url: "https://github.com/USERNAME"
    - label: "Email"
      icon: "fas fa-envelope"
      url: "mailto:YOUR_EMAIL@example.com"

# 내비게이션(상단 메뉴)
nav:
  - title: "Home"
    url: /
  - title: "About"
    url: /about/
  - title: "Projects"
    url: /projects/
  - title: "Blog"
    url: /blog/
  - title: "Contact"
    url: /contact/

# 블로그 설정(선택)
paginate: 5
paginate_path: /blog/page:num/

# 깔끔한 목록/표시
minimal_mistakes_skin: "air"
