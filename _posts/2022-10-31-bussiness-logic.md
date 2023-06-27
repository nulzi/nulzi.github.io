---
layout: single
title: Bussiness logic
categories: dev
---

## 배경

## Bussiness logic


###### 참고 사이트
[비즈니스 로직, 도메인 로직이 도대체 뭐지?](https://velog.io/@eddy_song/domain-logic)  

소프트웨어 공학에서 도메인, 비즈니스라는 말은, '소프트웨어가 풀고자하는 현실 세상의 문제'를 가리킨다.
소프트웨어가 존재하는 이유, 목적
은행 앱이라면, 금융 및 은행 업무가 도메인
SNS라면 동영상 촬영, 감상, 댓글 및 공유

대표적으로 데이터베이스에 연결하고, 백엔드 서버와 통신하고, 사용자와 인터랙션하는 코드들이 필요하다.
이런 것들은 도메인 로직과 구분지어 어플리케이션 서비스 로직

구분하는 하나의 척도는, 바로 '비즈니스 의사결정'이다.
[What is domain logic?](https://enterprisecraftsmanship.com/posts/what-is-domain-logic/)  
The problem space Domain, Problem Domain, and Core Domain
The solution space Business Logic, Business Rules, Domain Logic, and Domain Knowledge
Subdomain is the problem, the distinct area of your domain which can be easily isolated from other areas,
Bounded Context is the solution to that problem

Your domain model is responsible for generating business-critical decisions
all other parts of your code base just interpret those decisions or provide input needed to make them

Domain logic (aka business logic, business rules, and domain knowledge) is the logic that makes business-critical decisions.

All other types of logic orchestrate the decisions made by the domain model and transform them into side-effects: save them to the data store, show to the user, or pass to 3rd-party services.

It’s important to separate domain logic from other types of logic as it helps keep the overall code base simpler.