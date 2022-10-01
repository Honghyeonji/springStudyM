### springStudyM
#### 모각코 개인 스터디용 레퍼지토리

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
#### 프로젝트 환경 설정

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

#### view 환경 설정

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


#### 1주차 마무리
회의도 있고, 생각보다 노트북으로 설정하는 것이 오래 걸려서 많은 진도를 못나갔다.
다음번에는 스프링 DB 접근 기술의 반까지 나가는 것이 목표이다.


