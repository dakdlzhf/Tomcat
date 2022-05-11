### :heavy_exclamation_mark:  톰캣 서비스시 주의!

* 한번에 하나의 프로젝트만 실행 할수 있도록 설정해준다.

  

### :ballot_box_with_check:   이클립스 톰캣서버  연동



* Windows -Preferences

  * Server - Runtime Environment
    * Add
      * 서버이름 (기본이름 사용) /압충해제한 톰캣폴더 선택 Jre 선택 후 Apply and Close

* Dynamic Web Project 생성

  * 프로젝트 이름작성

  * 실행 환경(Target Runtime) 확인

  * Next - Next

  * web.xml 파일 생성 체크 후 Finish

    

* 프로젝트를 생성후 서버를 동작시킬때

  * 프로젝트 우클릭 Run on Server !
    *  프로젝트 파일전체 를 가져다가 이클립스가 톰캣을 동작시키면서 거기다가 올려주면 서비스가 된다.

### web.xml

* WEB-INF 폴더 에 web.xml 이 안보일경우

  * 프로젝트를 만들때 check 항목을 놓친경우일뿐 큰문제는 되지않는다

  * web.xml 파일을 만들고싶을경우 프로젝트 우클릭   

    Java EE Tools  -> Generate Deployment Descriptor Stub

* web.xml 

  * web.xml 파일은 이름 과 값 이런식으로 값을 성정할때 xml이라는 형식을 활용한다 .
  * 여기서 설정값들을 바꿔주면 톰캣 의 동작에 영향을 준다.
  * web.xml 파일은 꼭있어야하는 필수!
  * WEB-INF 폴더에 들어있는 web.xml 은 잘 건드리지말자

### Context Path

* 웹에서 서비스할때 최상위에 해동되는 경로를 일컫는다.

### :small_orange_diamond: 정적 서비스 (Web Server)

* HTML , CSS , JS 로 만든 웹페이지 를 브라우저에서 서버에게

​      원하는 HTML 을 요청하면 해당 파일을 찾아서 브라우저에게

​	  응답 한다 ( requerst / response )

* HTTP 라는 프로토콜을 기반으로 동작
* 단순히 HTML 파일을 찾아서 응답!

### :small_blue_diamond:동적 서비스 (Web Application Server)

* 동적으로 처리된 결과에 맞게 서비스된다.

* JSP 파일의 내용을 처리하고 HTML 파일로 만든다.

* JSP , ASP , PHP 같은 언어가 필요하다.

  

### :star2:프로젝트( Dynamic Web Project ) 구조와 동적서비스 개념



* src 폴더는 Java 코드가 들어갈 곳이다.

* WebApp or WebContent 는 base 폴더이다 (웹 관련한  자원들이 위치한다.)

  * 클라이언트에게 서비스하고자하는 기본 폴더라고 보면된다
    * Context Path ( 최상위 경로) 는 localhost:8080/ 일수도, localhost/프로젝트명/ 까지가 최상위경로 일수도있다.
    * 브라우저에서 Context Path 라는 정보를 통해서 요청을하면  WebApp or WebContent 로 연계된다. (base 폴더에 있는 파일을 요청한다 고 생각하면된다.)

  * HTML , CSS , JS , JSP 파일등 이미지나,정적파일도 base 폴더에 위치한다.

### :rocket:JSP 특징

* JSP는 서버 측 동적서비스를위한  웹 프로그래밍 언어 중 하나이다.

* 서블릿 기술의 확장이다.

* 빠른 개발이 가능하며 유지 보수가 용이하고, 코드의 양도 줄일수 있다.

  

### :computer:  JSP 파일의 처리

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>JSP 예제</title>
</head>
<body>
<%
	int total = 0;
	for(int i = 1; i < 10; i++){
		total += i;
	}
%>
	1부터 10까지의 합 : <%= total %>
</body>
</html>
```

* <%  자바 실행문 %>  스크립트릿 태그 

  * 자바 코드로 이루워진 로직 부분을 작성할수있다.

  * JSP 페이지가 요청될 때마다 수행되어야하는 자바코드를 톰캣이 요청을 받아서 처리해준다.

    

* <%= 자바코드 %> 표현문 태그

  * 웹 브라우저에서 출력할 부분 표현
  * 표현문 태그에 숫자,문자,boolean 등 기본 데이터 타입과 자바 객체 타입도 사용이가능하다
  * 스크립트릿 코드 안에 out이라는 내장객체를 통해 브라우저에 출력가능하다.

* 브라우저를통해 클라이언트가 요청하여 톰캣이 JSP 파일처리 결과를  HTML 코드를 브라우저에준다.  

  * 브라우저 화면에 표시되는것은 HTML 코드의 기반으로 값을 표현해줄뿐 JSP 코드를 보여주진않는다
    * 동적페이지로 만든것이지만 결과는 정적인페이지를 브라우저에 보여준다.
