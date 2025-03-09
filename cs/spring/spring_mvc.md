## Spring MVC란?

- Spring MVC(Model-View-Controller)는 Spring Framework에서 제공하는 웹 애플리케이션 개발을 위한 아키텍처입니다.
- Model-View-Controller 패턴을 기반으로 웹 애플리케이션을 구조화하여 유지보수성과 확장성을 높이는 역할을 합니다.

<br/>

### Spring MVC 동작 흐름

Spring MVC는 **클라이언트 요청을 받아 컨트롤러에서 처리한 후, 적절한 뷰를 반환하는 방식**으로 동작합니다.

1. 클라이언트가 요청을 보냄
2. 디스패처 서블릿(DispatcherServlet)이 요청을 가로챔
3. 적절한 컨트롤러(Controller)로 요청을 전달
4. 컨트롤러는 요청을 처리하고 Model 데이터를 반환
5. ViewResolver가 적절한 뷰(View)를 선택
6. 뷰에서 응답을 생성하고 클라이언트에게 반환

📌 디스패처 서블릿(DispatcherServlet)이 중심 역할을 수행하며, 요청과 응답을 조율하는 역할을 함.

<br/>

### Spring MVC 핵심 구성 요소

| 구성 요소                                         | 설명                                         |
|-----------------------------------------------|--------------------------------------------|
| **DispatcherServlet**                         | Spring MVC의 핵심. 모든 요청을 받아 컨트롤러에 전달하고 뷰를 결정 |
| **Controller (@Controller, @RestController)** | 클라이언트 요청을 처리하는 핵심 로직                       |
| **Model**                                     | 비즈니스 로직의 데이터를 담는 객체                        |
| **View (JSP, Thymeleaf, JSON 등)**             | 클라이언트에게 보여지는 화면                            |
| **ViewResolver**                              | 컨트롤러가 반환한 View 이름을 적절한 화면으로 변환             |

