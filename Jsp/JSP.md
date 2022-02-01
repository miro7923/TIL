# JSP
# 목차
* [JSP(Java Server Page)란?](#JSPJava-Server-Page란)
* [JSP의 특징](#JSP의-특징)
* [JSP 사용](#JSP-사용)
* [JSP 지시어(Directive)](#JSP-지시어Directive)
* [JSP 스크립트 요소](#JSP-스크립트-요소)
* [내장 객체](#내장-객체)
* [액션 태그](#액션-태그)
* [영역 객체(Scope)와 속성(Attribute)](#영역-객체Scope와-속성Attribute)

# JSP(Java Server Page)란?
* `Java`를 이용하여 `동적인 웹 페이지`를 만들기 위해 Sun Microsystems사가 개발한 기술
*************************

# JSP의 특징
## 1. 강력한 이식성
* `자바기반`의 언어로 어떤 `JSP 컨테이너`에서도 사용이 가능하므로 한 번 작성한 코드를 별다른 수정 없이 다른 플랫폼으로 이식이 가능하다.
* `모듈화`와 `모듈의 재사용성`이 좋다.

## 2. 서버 자원의 효율적인 사용
* `스레드(Thread)` 기반의 아키텍처 사용으로 불필요한 자원 낭비를 감소시켰다.

## 3. 간편한 MVC 패턴(디자인 패턴)
* `MVC 패턴`을 `JSP(View)`와 `자바빈즈(Model)`, `서블릿(Controller)`을 이용해 쉽게 구현할 수 있다.

### 🔸 MVC 패턴
* 사용자에게 보여지는 화면인 `View` 부분과 실제 비즈니스 로직이 들어가는 `Model` 부분 그리고 `View`와 `Model`을 연결시켜주는 `Controller` 부분으로 구성
* 최근에 중대형 프로젝트에서 효과적이라 평가되어 많이 사용되고 있다.

### 🔸 디자인 패턴
* 프로젝트를 개발함에 있어서 특정한 문제가 주어졌을 때 그 문제를 해결하기 위한 방법을 설명해 놓은 일종의 지침
*********************************

# JSP 사용
* `HTML` 태그와 `Java` 코드를 함께 사용한다.

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
  <%
      // 스크립틀릿
  %>
</body>
</html>
```

* `HTML` `body` 태그 안에서 스크립틀릿을 쓴 다음에 스크립틀릿의 범위 내에 코드를 작성한다.

```html
<h2>자바코드로 테이블 생성</h2>
	<table border="1">
		<tr>
			<td>번호</td><td>이름</td>
		</tr>
		<%
			for (int i = 1; 6 > i; i++)
			{
				%>
				<tr>
					<td><%=i %></td><td>학생<%=i %></td>
				</tr>
				<%
			}
		%>
	</table>
```

* 위와 같이 자바 코드 사이에 `스크립틀릿`이 끝나는 표시(`%>`)를 하고 `HTML` 태그를 쓴 다음에 `<%= %>`를 이용해 자바 코드의 지역 변수를 출력하는 것이 가능하다.(신기...)

## 🔸 JSP 주석

```jsp
<%-- --%> (웹페이지 개발자 도구창에서 나타나지 않기 때문에 보안상 이것을 쓰는 것이 더 좋다)
// 자바 스타일도 사용 가능
```

********************************

# JSP 지시어(Directive)

```jsp
<%@ ... %>
```

* `JSP` 파일 내에서 `JSP`를 실행할 컨테이너에서 해당 페이지를 어떻게 처리할 것인가에 대한 설정 정보들을 지정해주는 데 사용
* `page` 지시어, `include` 지시어, `taglib` 지시어 3가지로 나누어진다.

## 1. page 지시어

```jsp
<%@ page 속성1="값1" 속성2="값2" 속성3="값3"... %>
```

* `JSP` 페이지에 대한 속성을 지정하는 지시어
* 속성에는 스크립트 언어, import할 패키지/클래스, 세션 사용 여부, 에러 페이지 등 12개의 설정 정보를 지정해 사용할 수 있다.

|속성|사용법|기본값|설명|
|---|---|---|---|
|language|language="java"|java|스크립트 요소에서 사용할 언어 설정|
|extends|extends="클래스명"|없음|상속받을 클래스를 설정|
|import|import="패키지.클래스명"|없음|import할 패키지.클래스 설정|
|session|session="true"|true|HttpSession 사용 여부를 설정|
|buffer|buffer="16kb"|8kb|JSP 페이지의 출력 버퍼 크기를 설정|
|autoFlush|autoFlush="true"|true|출력 버퍼가 다 찼을 경우 처리 방법을 설정|
|isThreadSafe|isThreadSafe="true"|true|다중 스레드의 동시 실행 여부를 설정|
|info|info="페이지 설명"|없음|페이지 설명|
|errorPage|errorPage="에러 페이지.jsp"|없음|에러 페이지로 사용할 페이지를 지정|
|contentType|contentType="text/html"|text/html;charset=ISO-8859-1|JSP 페이지가 생성할 문서의 타입을 지정|
|isErrorPage|isErrorPage="false"|false|현재 페이지를 에러 페이지로 지정|
|pageEncoding|pageEncoding="euc-kr"|ISO-8859-1|현재 페이지의 문자 인코딩 타입 설정| <br>

* 각각의 속성을 하나의 `page 지시어`에 한 번에 지정할 수도 있으며 여러 개의 `page 지시어`에 나누어 지정할 수도 있다.
* 하지만 `import` 속성을 제외한 나머지 속성은 하나의 페이지에서 오직 한 번씩만 지정할 수 있다.<br><br>

## 2. include 지시어

```jsp
<%@ include file="header.jsp" %>
```

* 특정한 `JSP` 파일 또는 `HTML` 파일을 해당 `JSP` 페이지에 삽입할 수 있도록 하는 기능을 제공한다.
* `include`되는 `JSP` 코드 자체가 해당 `JSP` 페이지에 복사되어 더해지므로 서블릿 컴파일 과정은 `include` 되는 페이지의 수가 아무리 많아도 단 한 번만 이루어지게 된다.
* 사용되는 공통 변수값들을 추가할 때 주로 사용한다.
* `include` 지시어는 중첩 사용이 가능하기 때문에 `include`되는 파일 안에서 또 다른 파일을 `include`하여도 문제없이 동작한다.<br><br>

## 3. taglib 지시어

```jsp
<%@ taglib url="http://taglib.com/sampleURI" prefix="samplePrefix" %>
```

* `JSTL(JSP Standard Tag Library)이나 커스텀 태그 등 태그 라이브러리를 `JSP`에서 사용할 때 접두사를 지정하기 위해 사용된다.
* `uri` 속성과 `prefix` 속성으로 이루어진다.

### 🔸 uri 속성
* 태그 라이브러리에서 정의한 태그와 속성 저보를 저장한 `TLD(Tag Library Descriptor)` 파일이 존재하는 위치 지정

### 🔸 prefix 속성
* 사용할 커스텀 태그의 네임 스페이스(Name Space)를 지정
**************************

# JSP 스크립트 요소
## 1. 선언문

```jsp
<%!
    // 멤버변수와 메서드 선언
%>
```

* 멤버변수와 메서드를 선언하기 위한 영역
* 클래스에서 멤버변수와 메서드를 선언한 것과 동일한 결과로 같은 `JSP` 페이지 어느 위치에서든 참조가 가능하다.

## 2. 스크립틀릿(Scriptlet)

```jsp
<% 문장1; %>
<%
    문장2; 문장3; 문장4; ...
%>
```

* `JSP` 코드를 작성하는 영역
* 서블릿 코드의 작성법이 다소 어려워서 이것을 보완하기 위해 만들어진 방식
* 스크립틀릿 영역에서 선언되는 변수들은 지역변수로 인식된다.
* `JSP` 파일이 실행되면 웹 컨테이너에 의해 `JSP` 파일이 파싱되어 서블릿 클래스로 변환된 자바 소스 파일과 클래스 자바 파일이 서버에 저장된다.

## 3. 표현식(Expression)

```jsp
<%=변수 %>
<%=리턴값이 있는 메소드 %>
<%=수식(변수 또는 리턴값이 있는 메소드를 포함할 수 있음) %>
```

* 선언문, 스크립틀릿에 생성한 변수, 메소드의 리턴값을 스크립틀릿 태그 외부에서 출력하기 위해 사용
* 하나의 표현식 태그 내의 구문 전체가 `print()` 메소드의 괄호 안에 통채로 들어가기 때문에 표현식 태그 내부에서는 `세미콜론(;)`을 사용해서는 안된다.
******************************

# 내장 객체
* `JSP` 페이지가 웹 컨테이너에 의해서 서블릿으로 변환할 때 웹 컨테이너가 자동으로 생성해 주는 객체(`클래스`, `import` 구분없이 사용 가능)<br><br>

javax.servlet 패키지 - 8개<br>

|내장 객체 변수명|설명|
|---|---|
|request|클라이언트의 `HTTP` 요청 정보를 저장한 객체(`HTTP`헤더 정보, 파라미터 등)|
|response|클라이언트 요청에 대한(`HTTP`) 응답 정보를 저장한 객체|
|session|클라이언트의 세션 정보를 저장한 객체|
|pageContext|페이지 실행에 필요한 컨텍스트 정보를 저장한 객체|
|out|응답 페이지 정보를 전송하기 위한 출력 스트림 객체|
|application|동일한 애플리케이션의 컨텍스트 정보를 저장한 객체|
|config|해당 페이지의 서블릿 설정 정보(초기화 정보)를 저장한 객체|
|page|해당 페이지 서블릿 객체(인스턴스)|<br><br>

java.lang 패키지 - 1개<br>
* exception : 예외 처리를 위한 객체

## 1. request 객체
* 사용자의 요청에 관한 정보를 얻기 위한 객체<br><br>

* 서버 도메인명 : ```request.getServerName();```
* 서버 포트번호 : ```request.getServerPort();```
* URL : ```request.getRequestURL();```
* URI : ```request.getRequestURI();```
* 클라이언트 호스트명 : ```request.getRemoteHost();```
* 클라이언트 IP주소 : ```request.getRemoteAddr();```
* 프로토콜 : ```request.getProtocol();```
* 페이지 요청(전송)방식 : ```request.getMethod();```
* 프로젝트 경로 : ```request.getContextPath();```
* 물리적 경로 : ```request.getRealPath("/");```
* http헤더 (user-agent): ```request.getHeader("user-agent");```
* http헤더 (accept-language) : ```request.getHeader("accept-language");```
* http헤더 (host) : ```request.getHeader("host");```
* http헤더 (connection) : ```request.getHeader("connection");```

* 전송을 통해 다른 페이지에서 전달받은 (이름 등의)정보를 얻을 때

```jsp
String name = request.getParameter("name");
```
<br>

* 정보들을 배열로 얻을 때

```jsp
String hobbies[] = request.getParameterValues("hobby");
```

### 🔸 URI
* URI는 특정 리소스를 식별하는 `통합 자원 식별자(Uniform Resource Identifier)`를 의미한다. 
* 웹 기술에서 사용하는 논리적 또는 물리적 리소스를 식별하는 고유한 문자열 시퀀스다.

### 🔸 URL
* URL은 흔히 웹 주소라고도 하며, 컴퓨터 네트워크 상에서 리소스가 어디 있는지 알려주기 위한 규약이다. URI의 서브셋이다.
* 한마디로 URI가 자원 자체에 대한 고유 식별자라면 URL은 자원이 실제로 존재하는 위치를 가리킨다. <br><br>
![uri-url](../img/uri-url.png)<br><br>

## 2. response 객체
* 클라이언트의 요청에 대한 `HTTP` 응답(HTTP Response)을 나타내는 객체<br><br>

* response.setHeader("헤더이름", 값);

```jsp
response.addHeader("Refresh", "3"); // 3초에 한번씩 새로고침
response.addHeader("Refresh", "3;url=http://www.naver.co.kr"); // 3초 후에 다음 페이지로 이동
```

* response.sendRedirect("주소"); // "주소"로 요청 재전송

```jsp
response.sendRedirect("http://www.naver.co.kr"); // 해당 페이지로 바로 이동
```

* ```response.setContentType("속성값"); 컨텐츠 타입 지정```
* ```response.addCookie("쿠키값"); 쿠키 추가```

## 3. session 객체
* 클라이언트의 정보가 유지되어야 할 필요가 있는 경우를 위해 가상 연결을 구현해주는 세션<br><br>

* 세션ID값 : ```session.getId();```
* 세션생성시간 정보(ms) : ```session.getCreationTime();```
* 최종 접속 시간(ms) : ```session.getLastAccessedTime();```
* 세션 유지시간(기본)(1800s,30m) : ```session.getMaxInactiveInterval();```<br>

## 4. application 객체
* 해당 웹 애플리케이션의 실행 환경을 제공하는 서버의 정보와 서버측 자원에 대한 정보를 얻어내거나 해당 애플리케이션의 이벤트 로그를 다루는 메소드들을 제공<br><br>

* 서버정보 : ```application.getServerInfo();```
* 서버의 물리적 경로 : ```application.getRealPath("/");```

## 5. out 객체
* 서블릿/JSP 컨테이너가 응답 페이지를 만들기 위해 사용하는 출력 스트림 객체
* 하지만 표현식을 사용해서 자바 코드의 변수 값들과 메소드의 리턴 값들을 출력할 수 있기 때문에 잘 사용되지 않는다.<br><br>

* 출력 : ```out.print("Hello");```
* 버퍼 사이즈 : ```<%=out.getBufferSize() %>byte<br>```
* 버퍼 사용후 : ```<%=out.getRemaining() %>byte<br>```
******************************

# 액션 태그

```jsp
<jsp:~ 형태로 시작하는 태그>
```

* `JSP` 페이지에서 `HTML` 태그 형태로 `JSP` 코드의 역할을 수행하는 것
* 스크립틀릿 등의 스크립트 요소(자바 코드)를 사용하지 않기 때문에 `JSP` 페이지의 내부적인 프로그램 로직을 사용자로부터 감출 수 있다.
* 즉, 사용자에게 보여지는 프레젠테이션 부분과 사용자의 요청을 처리하는 비즈니스 로직 부분(프로그램 부분)을 분리하는 것이 가능하다.
* 프로그램 재사용성을 높여주고 코드의 간결성을 향상시킨다.

## 🔸 <jsp:forward>

```jsp
<jsp:forward page="이동할 페이지(ex. forward.jsp)" />
<jsp:forward page="이동할 페이지"></jsp:forward>
```

* 액션 태그는 `XML` 문법을 이용하여 구현된 기능이므로 태그의 종료 끝에 반드시 종료 태그가 있어야 한다.
* `forward` 액션은 현재 페이지의 요청과 응답에 관한 처리권을 `page` 속성에 지정된 이동할 페이지로 영구적으로 넘기는 기능을 한다.

## 🔸 <jsp:include>

```jsp
<jsp:include page="이동할 페이지(ex. forward.jsp)" flush="false" />
<jsp:include page="이동할 페이지(ex. forward.jsp)" flush="false"></jsp:include>
```

* 특정 페이지를 `include` 한다.
* 각각의 페이지를 컴파일 후 해당 파일을 `include` 한다.
* top, bottom과 같은 동일 사용 페이지를 추가할 때 사용한다.

## 🔸 <jsp:param>

```jsp
<jsp:param name="파라미터 이름1" value="파라미터 값1" />
<jsp:param name="파라미터 이름2" value="파라미터 값2" />
```

* `forward`와 `include` 태그를 사용하여 이동할 페이지에 추가적으로 넘겨줄 파라미터가 있으면 `<jsp:param/>` 태그를 사용할 수 있다.
***********************

# 영역 객체(Scope)와 속성(Attribute)
* jsp 내장객체 중에서 특정 공간(Scope)에 정보를 저장하고, 저장된 정보(Attribute)를 공유할 수 있는 객체
* `JSP`에서는 `page`, `request`, `session`, `application` 4가지 영역으로 정의한다.<br><br>
![jspScope](../img/jspScope.png)<br><br>
************************
