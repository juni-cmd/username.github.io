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

---
layout: splash
title: "안녕하세요, 채준입니다"
subtitle: "전기·전자/제어공학 실습과 프로젝트를 정리합니다."
intro: 
  - excerpt: "3초 안에 관심 끌기 ✅ — 아래 프로젝트 카드로 바로 보실 수 있어요."
feature_row:
  - image_path: /assets/img/proj1.jpg
    title: "동기기 무부하 포화곡선 실험"
    excerpt: "측정 데이터로 공극선 도출 및 비교 · Python 시각화"
    url: "/projects/#exp-synchronous"
    btn_label: "자세히 보기"
    btn_class: "btn--primary"
  - image_path: /assets/img/proj2.jpg
    title: "근궤적 & 계단응답 시각화"
    excerpt: "14개 전달함수 루트궤적/응답 자동화 코드"
    url: "/projects/#ctrl-rootlocus"
    btn_label: "코드 보기"
    btn_class: "btn--primary"
  - image_path: /assets/img/proj3.jpg
    title: "전력공학 노트"
    excerpt: "진상/지상, 고조파, 역률 보상 정리"
    url: "/blog/"
    btn_label: "노트 읽기"
    btn_class: "btn--primary"
---

{% include feature_row id="intro" type="center" %}
{% include feature_row %}

---
title: "About"
permalink: /about/
---

### 소개
- 전공: 전기·전자공학 (제어/전력 실습 다수)
- 관심: 제어시스템 시각화, 전력 품질, 현장형 직무

### 기술 스택
- **언어**: Python, MATLAB
- **도구**: Jupyter, GitHub, LTspice, Multisim
- **웹**: GitHub Pages (Jekyll)

### 목표
- 실험 데이터 → 시각화 → 해석까지 **End-to-End** 역량 강화
- 현장 실무에 바로 적용 가능한 포트폴리오 구축

---
title: "Projects"
permalink: /projects/
---

## 실험 · 프로젝트 모음

### 1) 동기기 무부하 포화곡선 실험  {#exp-synchronous}
- **역할**: 실험 세팅, 데이터 취득, 공극선 도출
- **사용기술**: Python(Matplotlib), Excel
- **성과**: 공극선과 실험곡선 비교·오차 분석 → 보고서 A 등급
- **자료**: 이미지/그래프, 측정 테이블
- **링크**: [블로그 해설](/blog/2025-05-06-eg-oc-curve/)

---

### 2) 근궤적 및 단위 계단응답 시각화  {#ctrl-rootlocus}
- **역할**: 14개 전달함수 루트궤적/응답 자동화 코드화
- **사용기술**: Python(control), MATLAB
- **성과**: 파라미터별 민감도 확인, 안정성 해석 템플릿 제작
- **코드**: `notebooks/rootlocus.ipynb` (추가 예정)

---

### 3) 전력공학 요약 노트
- **주제**: 진상/지상, 고조파(3·5고조파), 역률보상
- **형태**: 그림/표 위주 요약, 계산 예제 포함

---
title: "Contact"
permalink: /contact/
---

- 이메일: <YOUR_EMAIL@example.com>  
- GitHub: <https://github.com/USERNAME>

이력서(PDF)는 아래에서 받으실 수 있어요.  
- [이력서 다운로드](/assets/resume/resume.pdf)

---
layout: home
title: "Blog"
permalink: /blog/
---

---
title: "동기기 무부하 포화곡선: 공극선 도출 노트"
categories: [Electrical Machines]
tags: [Synchronous, Open-Circuit, Magnetization]
---

실험 데이터로 **무부하 포화곡선**을 얻고, 선형 구간을 이용해 **공극선**을 도출했습니다.  
- 데이터 정리: 표준화, 온도 보정  
- 그래프: 실험곡선 vs 공극선 비교 (기울기, 절편)  
- 해석: 포화 구간 진입 지점, 오차 논의

name: Build and Deploy Jekyll
on:
  push:
    branches: [ "main" ]
  workflow_dispatch:
permissions:
  contents: read
  pages: write
  id-token: write
concurrency:
  group: "pages"
  cancel-in-progress: true
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/jekyll-build-pages@v1
        with:
          source: ./
          destination: ./_site
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./_site
  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4

assets/
  img/
    profile.jpg        # 프로필 사진 (임시로 아무 이미지나)
    proj1.jpg
    proj2.jpg
    proj3.jpg
  resume/
    resume.pdf         # 이력서 PDF (없으면 임시 빈 파일)
