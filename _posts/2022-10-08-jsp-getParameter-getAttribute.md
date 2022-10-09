---
layout: single
title: JSP. getParameter, getAttribute
categories: web
---

## getParameter(name)

- 웹 브라우저(클라이언트)에서 전송받은 request 값을 읽어오는, 말 그대로 html의 데이터를 추출하는 데 사용됩니다.
- 파라미터의 이름(name)과 일치하는 HTML form 요소 입력값을 가져옴.
- setParameter는 없습니다.
- 반환 타입은 String.

```jsp
//form.jsp

//form 형식
<form name=test method=post action=getParameter.jsp>
  <input type=text size=10 name=username>
  <input type=submit value="보내기">
</form>

//jsp:param
<jsp:forward page="getParameter.jsp">
  <jsp:param name="username" value="tom" />
</jsp:forward>
```

```jsp
//getParameter.jsp

이름: <%=request.getParameter("username")%>

//출력 결과(form 형식)
//이름: 입력한 username
//출력 결과(jsp:param)
//이름: tom
```

## getAttribute(name)

- 이전 다른 JSP 또는 Servlet 페이지에 설정된 매개 변수를 가져오는 데 사용됩니다.
- 모든 객체를 담을 수 있고, 클래스 객체를 받을 수 있습니다.
- 해당 내장 객체의 속성 이름이 name인 속성값을 가져옵니다.
- 하지만 setAttribute를 통해 값을 설정해주지 않으면 null 값을 돌려받습니다.
- 반환 타입은 Object.
  Object 타입으로 반환하기 때문에 형 변환(casting)을 해주기도 합니다.

```jsp
//setAttribute.jsp

<% request.setAttribute("username","tom"); %>
<jsp:forward page="getAttribute.jsp"/>

//Servlet.java

//doGet, doPost 내부
request.setAttribute("username","Ann");
```

```jsp
//getAttribute.jsp

이름: <%=request.getAttribute("username")%>

//출력 결과(setAttribute.jsp)
//이름: tom
//출력 결과(Servlet.java)
//이름: Ann
```

### getParameter 와 getAttribute의 차이점

- getParameter는 String 타입을 getAttribute는 Object 타입을 반환합니다.
- getParameter는 웹 브라우저(클라이언트)에서 전송받은 request 영역의 값을 가져옵니다.
- getAttribute는 setAttribute를 통해 값을 받아옵니다.

###### 참고사이트

[JSP getParameter, getAttribute](https://nancording.tistory.com/55)  
[getAttribute ()와 getParameter ()의 차이점](https://blog.naver.com/PostView.nhn?blogId=kjh6688000&logNo=221380920936&parentCategoryNo=&categoryNo=20&viewDate=&isShowPopularPosts=true&from=search)
