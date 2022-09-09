---
layout: single
title: What is AJAX?
---

![ajaxLogo](https://user-images.githubusercontent.com/74344132/189290276-ba0566a2-74ba-4d87-bf9d-6049b6ca2b36.png)

## AJAX가 뭔가요?
AJAX는 **Asynchronous JavaScript And XML**의 약자입니다.
그대로 해석하면 비동기 JavaScript와 XML입니다. 하지만 프로그래밍 언어는 아닙니다.
단지 웹 서버에게 데이터를 요청하기 위한 브라우저 내장 **XMLHttpResquest object**, 데이터를 보여주거나 사용하기 위한 **JavaScript와 HTML DOM**의 결합을 이용합니다.
AJAX는 웹 페이지가 뒤에서(behind the scenes) 웹 서버를 가지고 변경된 데이터에 의해 비동기적으로 업데이트되는 것을 허락합니다.
이 말은 전체 페이지의 새로고침(reloading) 없이 웹 페이지 일부분을 업데이트할 수 있다는 말 입니다.

### 장점
<ul>
  <li>새로고침 할 일이 없어 웹 애플리케이션을 만들 때 사용하면 좋다</li>
</ul>

### 예시 코드

#옛날 JS 방식
```html
<script>
  
  var ajax = new XMLHttpRequest();
  ajax.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200){
      console.log(ajax.responseText)
    }
  };
  ajax.open("GET", "any url", true);
  ajax.send();
  
</script>
```

#요즘 JS 방식
1. then 함수 사용
```html
<script>
  
  fetch('any url')
    .then((response) => {
      if (!response.ok) {
        throw new Error('400 or 500 error')
      }
      return response.json()
    })
    .then((result) => {
      consol.log(result)
    })
    .catch(() => {
      console.log('error')
    })
  
</script>
```

2. await 문법 사용
```html
<script>
  
  async function getData() {
    var response = await fetch('any url');
    if (!response.ok) {
      throw new Error('400 or 500 error');
    }
    var result = await response.json();
    console.log(result);
  }
  getData().catch(() => {
    console.log('error')
  });
  
</script>
```

#외부 라이브러리 방식($.ajax(), axios)
```html
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>

<script>
  
  axios.get('any url')
    .then((result) => {
      console.log(result.data)
    }).catch(() => {
      console.log('error')
    })
  
</script>
```

#### +α
CORS 관련 에러
예를 들면 naver에서 개발을 진해하다가 kakao에 AJAX 요청을 날릴 수가 없다.
집에서 개발할 때는 방해가 될 수 있으니
1. 헤더 세팅 Access-Control-Allow-Origin: *
> res.setHeader('Access-Control-Allow-origin', '*');
2. CORS 정책 관련 기능 off

자세한 내용은 <a href="https://nulzi.github.io/cors/">여기에</a>...
