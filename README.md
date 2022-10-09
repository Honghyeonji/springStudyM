## springStudyM
### 모각코 개인 스터디용 레퍼지토리

   해당 레퍼지토리에 올라올 스터디 파일들은 전부 인프런의 "스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술" 이라는 강의를 듣고 공부한 것이다.

올해 들어서 백엔드에 관심이 많아졌다. 그래서 최근에 시작한 프로젝트는 전부 백을 맡게 됐는데 백을 맡겠다고 했지만 사실 나도 아예 처음 배우는 거고 이전에 django로 백을 맡아서 했던 프로젝트에서는 별의별 실수를 다 했었기에 이번엔 제발 민폐끼치지 말자 하는 마음가짐으로 시작한다.. 그래도 django는 나름 에전에도 공부해봤고 프로젝트에서도 사용해봤지만 굳이 spring을 더 배우는 것은 일단 나한테 맞는 프레임워크를 찾고 싶은 것도 있었고 내가 python보다는 java를 더 좋아하기 때문인 것도 있다. 하지만 최근엔 java, python, c 중에선 java를 제일 안 사용했기 때문에 좀 걱정된다..
아무튼 모각코를 통해서 반강제적으로라도 spring공부를 하게 되었으니 이왕 하는 김에 제대로 공부해서 프로젝트도 성공적으로 끝내고 나도 다른 사람들처럼 기록하면서 사는 습관을 좀 들여야겠다. 제발

-------------------
### 1주차 목표
-------------------
+ spring boot starter을 이용한 프로젝트 환경 설정
+ view 환경 설정 및 작동 원리 
-------------------
### 1주차 활동
-------------------
### 프로젝트 환경 설정

+ 언어 : java 11
+ 개발 툴 : intelliJ

spring가 프로젝트 환경 설정의 AZ를 다 하며 개발자가 설정을 신경써야할 게 너무 많은 반면 spring boot는 spring boot starter을 사용해서 개발자가 개발하고자 하는 설정에 맞춰 초기 프로젝트 설정을 다 맞춰주기 때문에 spring boot starter을 이용해서 환경 설정을 한 후 프로젝트를 진행하고 그 파일을 github파일로 다시 옮겼다.

사족을 덧붙이자면 자바를 처음 배울 때 다른 개발 툴을 이용해서 한 것이 아니라 이경용 교수님 수업을 들었어서 aws 클라우드와 프로그래머스에서만 코드를 짰었다.
다들 이클립스만 써서 많이 들어왔기에 이클립스가 더 친숙하게 느껴진 것도 있었고 개발툴이라곤 vscode와 androidstudio만 썼어서 다른 개발툴을 사용하면 불편할까 했는데 intelliJ가 androidstudio랑 똑같아서 개발 툴에 바로 적응할 수 있었다!

아무튼 환경 설정 하고 로컬에서 돌려봤는데 노트북을 혹사시켰어서 잘 돌아갈까 했는데 다행히도 잘 실행된다..~~
![캡처_2022_09_30_02_21_45_110](https://user-images.githubusercontent.com/66579773/193100520-edf754bc-3207-4718-90e6-10b16a2cd66c.png)

강사분이 설명해주시는 작동원리는
``` Java
@SpringBootApplication
public class StudySpringApplication {
	public static void main(String[] args) {
		SpringApplication.run(StudySpringApplication.class, args);
	}
}
```
main을 실행시키면 SpringApplication.run에 StudySpringApplicaion 클래스를 넣어주면 이 클래스가 SpringBootApllication이 어노테이션 되어있어서 SpringBootAplication이 실행이 된다.
우리가 springbootstarter로 설정할 때 라이브러리를 web으로 하였는데 이 안에 톰캣이라는 웹서버가 내장되어있다. SpringBootAplication이 실행될 때 프로그램이 톰캣을 자체적으로 실행 시키면서 springboot가 같이 올라온다고 한다.

그리고 intelliJ에서 라이브러리도 자세하게 확인했는데 라이브러리 구조가 대강 이렇다.
```
+ spring-boot-starter-web
  + spring-boot-starter-tomcat : 웹서버, 톰캣 (8080)
  + spring-webmvc : 스프링 웹 MVC
+ spring-boot-starter-thymeleaf : 타임리프 템플릿 엔진 (View)
+ spring-boot-starter : spring boot + spring core + logging 
(이 라이브러리를 쓰면 하위의 하위에 있는 spring-core라이브러리까지 다 땡겨와서 쓰기 때문에 springboot관련된 설정들은 다 저절로 셋팅이 된다.)
  + spring-boot
    + spring-core
  + spring-boot-starter-logging
    + logback
    + slf4j
```

### view 환경 설정

그리고 spring boot에서는 welcome page라는 기능이 있다.
"resources/static/index.html" 경로로 index파일을 만들어두면 이 index파일이 웰컴 페이지가 되는 것이다.
그래서 따로 "java/study.studyspring/StudySpringApplication"에다가 코드를 추가 안 해줘도 실행하고 localhost:8080에 들어가면 index.html파일이 보인다.
https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-welcome-page
(이 사이트 참고하면 springboot가 제공하는 기본 기능들을 검색해서 찾아볼 수 있다.)

또 thymeleaf라는 템플릿 엔진을 이용해서도 view page를 만들 수 있는데 개발자가 자기 맘대로 page 템플릿을 만들어서 사용하는 것이다. 
(localhost:8080/ 이후 경로를 매핑할 수 있다.)

thymeleaf를 쓰러면 Controller패키지를 만들어서 controller 클래스를 만들어야한다.
그래서 main\java\study.studyspring 경로에다가 controller 패키지를 만들고 강의대로 HelloController 자바파일을 만들어 주었다.
코드를 살펴보자면
``` Java
@Controller //Controller 클래스를 만드려면 @Controller로 어노테이션 해주어야한다.
public class HelloController {
    @GetMapping("hello") // localhost:8080/hello 요청이 들어오면 이 메소드를 실행시켜주는 것이다.
    public String hello(Model model){
        model.addAttribute("data", "hello!!"); // hello페이지에서 data key값을 사용하면 hello!! value값이 나온다.
        return "hello";
    }
}
```
로 설명은 주석으로 달았다.

또한 resources파일에다가 templates 폴더를 따로 만들어 템플릿을 이용한 hello.html 파일도 따로 만들어준다. 
코드를 조금만 보면
``` HTML
<html xmlns:th="http://www.thymeleaf.org">
```
로 html선언할 때 th라는 코드로 thymeleaf템플릿을 사용할 것이라는 선언도 같이 해준다.

``` HTML
<p th:text="'안녕하세요. ' + ${data}" >안녕하세요. 손님</p>
```
th:text= 로 이미 안녕하세요 data를 써줬기 때문에 안녕하세요. 손님을 무시하고 thymeleaf로 만들어두었던 value값을 가져온다.

작동원리는 이런식이다.
![캡처_2022_10_02_01_18_52_966](https://user-images.githubusercontent.com/66579773/193418623-38080acc-bb06-45f6-a8e7-a58d4c34feb9.png)


### 1주차 마무리
회의도 있고, 생각보다 노트북으로 설정하는 것이 오래 걸려서 많은 진도를 못나갔다.
다음번에는 스프링 DB 접근 기술의 반까지 나가는 것이 목표이다.


-------------------------
### 2주차 목표
--------------------------
+ 인프런 강의 중 스프링 웹 개발 기초 공부
--------------------------
### 2주차 활동
--------------------------
### 정적 컨텐츠
springboot에서 정적 컨텐츠란 앞서 단순한 index.html 파일을 만든 것 처럼 html파일 코드를 직접 짜서 스프링 웹 브라우저를 구축하는 것이 정적컨텐츠이다.
springboot는 정적 컨텐츠 기능을 기본으로 제공해준다.
static폴더가 있는데 그 폴더에다가 만들면 된다. (public, resources 폴더도 가능)
index.html파일을 만들어보기도 했고 api를 주로 쓸거라서 굳이 실습까지 따라해 볼 필요는 없다고 생각해 실습은 안 했다.

이런식으로 작동된다.
![캡처_2022_10_09_19_43_23_699](https://user-images.githubusercontent.com/66579773/194756883-0563714b-3373-42cb-980e-6bdff3a698ee.png)


### MVC와 템플릿 엔진
MVC와 템플릿 엔진은 소위 jsp,csp코드를 짜서 html 동적이게 구축하는 동적컨텐츠이다.
MVC는 Model, View, Controller를 뜻한다.

과거에는 view와 controller가 분리되어있지 않았는데 view에서 모든 걸 다 했는데(model1방식) 현재에는 MVC을 나눠서 개발한다.
현재 방식에서 view는 단순히 웹브라우저 화면을 그리는 용도로 사용된다.
controller랑 model은 비즈니스 로직이나 내부처리에 집중된다.

이 파트 실습에서는 controller와 view 코드를 새로 짰다.
controller는 이전에 hellocontroller코드에서 추가해주었다.
``` Java
@GetMapping("hello-mvc")
public String helloMvc(@RequestParam(value="name",required = false) String name, Model model) {
    model.addAttribute("name", name);
    return "hello-template";
}
```
이 코드에서 RequestParam는 외부에서 name파라미터를 가져온다는 뜻이다. 서버 경로에다가 name=(단어)를 써주면 되는 것이다.

서버를 돌리고 로컬호스트 경로에다가 /hello-mvc?name=spring 를 추가해서 써주면 hello! spring 이라고 뜬다.

만약 hello-mvc만 쓰면 name 파라미터를 안 넣어줘서 에러가 뜬다.
뜨게 해주려면 RequestParam()안에 value = "name", required = false 이렇게 코드를 추가해주면 된다.

작동원리는 이렇다.
![캡처_2022_10_09_19_43_31_694](https://user-images.githubusercontent.com/66579773/194757130-51996a4d-b716-4ddb-a7a4-82c2afc004e6.png)


### API
json이라는 데이터 구조 포맷으로 클라이언트에게 데이터를 전달해준다. (서버끼리 통신할 때 씀)
api와 mvc를 구분하는 방식은 템플릿을 html로 내려 화면으로 보이게 해주는 가, 아니면 api방식으로 데이터를 바로 내리는 가 이다.

아무튼 서버 경로를 만들어서 호출하고 작동하는 건 똑같기 때문에 hellocontroller안에 코드를 또 추가해주었다.
``` Java
@GetMapping("hello-string")
@ResponseBody
public String helloString(@RequestParam("name") String name) {
    return "hello " + name;
}
```
@ResponseBody의 의미는 http 통신 프로토콜의 응답 바디부에 helloString이라는 데이터를 직접 넣어주겠다는 뜻이다.
그래서 viewResolver가 없어서 view를 안써줘도 된다.

서버 경로로 /hello-stirng?name=spring을 써주면 웹브라우저는 똑같이 hello spring으로 나오지만

**/hello-mvc?name=spring 페이지 소스**
![캡처_2022_10_09_21_16_18_694](https://user-images.githubusercontent.com/66579773/194757284-17b1bab1-63e0-4eee-ada0-d4d754096f26.png)

**/hello-string?name=spring 페이지 소스**
![캡처_2022_10_09_21_16_30_135](https://user-images.githubusercontent.com/66579773/194757340-c284e161-e4ce-4ea7-85b6-af8180b7b93d.png)

이렇게 페이지 소스보기로 코드를 확인해보면 html코드로 돌아가는 게 아니라는 걸 알 수 있다.

하지만 위 코드는 문자를 보여주는 코드이다. 만약 데이터를 보여주고 싶은 코드라면 json형태로 객체를 반환시켜 보여줘야하지 않나
똑같이 hellocontroller에다가 코드를 추가해준다.
``` Java
    @GetMapping("hello-api")
    @ResponseBody
    public Hello helloApi(@RequestParam("name") String name) {
        Hello hello = new Hello();
        hello.setName(name);
        return hello;
    }
    static class Hello {
        private String name;
        public String getName() {
            return name;
        }
        public void setName(String name) {
            this.name = name;
        }
    }
```
이 코드에서는 Hello라는 객체를 만들어서 그 안의 name이라는 변수에 name이라는 파라미터를 받아 넣어주고 Hello객체를 반환시켜 준다.

이 코드로 서버를 돌려 서버 경로로 hello-api?name=spring을 써주면 이렇게 뜬다.
![캡처_2022_10_09_21_22_21_312](https://user-images.githubusercontent.com/66579773/194757443-e61128fc-12ab-465e-bb66-9cc510d339c2.png)
문자 형태로 반환해준 게 아니라 json 객체 형태로 반환해줬기 때문에 name이라는 데이터 이름과 내용이 보이는 것이다.

정리하자면 작동원리는 이렇고
![캡처_2022_10_09_19_43_40_923](https://user-images.githubusercontent.com/66579773/194757452-ede50d6b-f181-4323-8c1d-9ca280123597.png)
@ResponseBody를 사용하면
+ HTTP의 바디에 문자 내용이나, data를 직접 반환해준다.
+ viewResolver 대신에 HttpMessageConverter이 동작한다.
+ 문자처리는 StringHttpMessageConverter가 객체처리는 MappingJackson2HttpMessageConverter가 동작한다.
+ 이외의 다른 처리도 HttpMessageConverter로 기본으로 등록되어 있다.

