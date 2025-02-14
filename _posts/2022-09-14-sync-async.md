---
layout: single
title: Synchronous / Asynchronous Programming
categories: web
---

## Synchronous(동기)

### 먼저 현실에서 상상해보자
레스토랑이 있고 웨이터 **sync**가 있다. 만약 세트 메뉴를 주문 받으면 **sync**는 모든 메뉴가 나오길 기다립니다. 모든 메뉴가 전부 나오면 그제서야 서빙합니다.

### 프로그래밍에서
동기 프로그래밍은 다음 작업이 실행되기 전에 각 작업이 실행되어야 하는 Blocking I/O operation을 사용합니다.
동기 작업은 한 번에 하나씩 발생하기 때문에 데이터베이스 쿼리와 같이 긴 시간의 작업은 실행되는 동안 다른 모든 스레드를 차단합니다.
* 장점
  * 단순함(Simplicity): 코드 작성이 단순해져서 시간을 아낄 수 있고, 더 쉽게 테스트할 수 있습니다.
  * 마케팅 잠재력(Marketing Potential): 검색 엔진이 동기 아키텍처를 사용한 웹 페이지를 더 쉽게 크롤링할 수 있습니다. 따라서 검색이 많이 되어야 하는 사이트에 유용합니다.
* 단점
  * 속도(Speed): 다중 요청을 다루는 것에서 비동기 프로그래밍보다 느립니다.
  * 자원 집약(Resource Intensity): 다중 비동기 실행은 하나의 스레드에서 가능하지만, 동기에서는 안되기 때문에 많은 자원을 요구합니다.
  
### 활용
* 비디오 렌더링
* 수학적 계산
* 결제 시스템

## Asynchronous(비동기)

### 먼저 현실에서 상상해보자
레스토랑이 있고 비동기적으로 일을 하는 웨이터 **async**가 있다. 만약 세트 메뉴를 주문 받으면 **async**는 메인 메뉴가 나오기 전에 먼저 나오는 에피타이저부터 서빙합니다.
그리고 나온 메인 메뉴를 서빙합니다.

### 프로그래밍에서
비동기 프로그래밍은 다음 작업이 실행되기 전에 각 작업이 실행되어야 하는 Non-blocking I/O operation에 의존합니다.
이 말은 비동기 프로그램은 계층적이나 순차적인 순서로 작업을 실행하지 않고 동시에 독립적으로 다중 요청을 처리할 수 있다는 의미 입니다.
* 장점
  * 사용자 경험(User Experience): 프로그램이나 웹 페이지의 모든 스크립트를 한 번에 로드할 수 있어 응답성이 향상되고 페이지 로드 지연이 감소합니다.
  * 맞춤 제작(Customization): 비동기 프로그래밍은 발생하거나 프로그램을 중단시킬 수 있는 오류에 맞춰 **<a href="https://nulzi.github.io/callback/#callback-function-">callback 함수</a>** 작성을 요구합니다.
작성된 콜백 함수는 프로그래머에게 개인의 오류 메시지를 작성할 기회를 제공합니다.
  * 확장성(Scalability): 확장성은 수평 및 수직 두가지 방식이 있습니다. 서버를 추가하면 수평적 확장이 가능합니다.
수직적 확장은 **<a href="">async/await</a>, <a href="">Promise</a>** 이 두 개념을 이용하는 비동기 프로그램에서 한 서버가 처리할 수 있는 요청 수를 늘리는 것입니다.
* 단점
  * 복잡성(Complexity): 깊이 있는 지식이 필요하고 코드 자체가 복잡해질 수 있습니다.
  * 지연 시간(Latency): 처음 페이지 렌더링하는 데 시간이 걸릴 수 있습니다. 또한 비동기 요청이 많을 경우 서버에 과부하가 걸리고 느려질 수 있습니다.
  * 호환성(Compatibility): C++나 JavaScript에서는 많이 사용되지만 다른 언어에서는 사용하기 쉽지 않습니다.

### 활용
* I/O 작업
* 데이터 베이스의 쿼리
* 반복문이 많은 프로젝트
* 반응형 UI

##### 참고 사이트
* <span style="font-size: 17px;"><a href='https://www.trio.dev/blog/synchronous-and-asynchronous'>https://www.trio.dev/blog/synchronous-and-asynchronous</a></span>
* <span style="font-size: 17px;"><a href='https://nesoy.github.io/articles/2017-01/Synchronized'>https://nesoy.github.io/articles/2017-01/Synchronized</a></span>
* <span style="font-size: 17px;"><a href='https://www.mendix.com/blog/asynchronous-vs-synchronous-programming/#use-cases'>https://www.mendix.com/blog/asynchronous-vs-synchronous-programming/#use-cases</a></span>
