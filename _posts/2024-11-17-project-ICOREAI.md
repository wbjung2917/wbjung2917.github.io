---
layout: post
title: EGMR-AI(이거먹을래?)
subtitle: ICORE E&C Google Cloud 인공지능(AI) 전문인력 양성 교육 Project
author: 정우빈
categories: Project
tags: [JavaScript,Python,React,Express,PostgreDB]
---

## 프로젝트 추진배경
![background-chart](/assets/images/projects/egmrai/background-chart.PNG)
- 일상 생활에서 사람들은 점심메뉴를 많이 고민하고 그 고민의 양이 적지않다.
- 이처럼 점심 메뉴가 고민거리인 가장 큰 이유는 함께 먹는 인원이 있을 때에 취향차이 문제가 있다.

![main-features](/assets/images/projects/egmrai/main-features.PNG)
- 때문에 친구와 본인의 취향을 동시에 고려해 음식점을 추천해주는 챗봇이 있다면 그 효용이 높을 것이라 생각했다.

## 데이터 수집 및 크롤링
![crawling-data](/assets/images/projects/egmrai/crawling-data.PNG)
Python의 BeautifulSoup,Selenium 라이브러리를 활용해 위와 같은 데이터를 확보하였다.

### 당면한 문제
1. 데이터 양의 문제
    - 리뷰가 적은 음식점의 비율이 높았다. 이 적은 리뷰를 RAG에 활용할 경우 정확도가 좋은 추천을 주기 어려웠다. 

2. 비정형 데이터의 정확도 문제
    - 리뷰데이터가 비정형 데이터라서 단순 cosine similarity 비교로는 높은 정확도를 얻을 수 없었다.

## UI구성 및 구현

## AI-Chatbot 구현

