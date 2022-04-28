# 마이크로서비스 아키텍처(Microservices Architecture, MSA)
* `마이크로서비스`는 하나의 큰 애플리케이션을 여러 개의 다른 역할을 수행하는 애플리케이션으로 분리하였을 때 각 애플리케이션을 말하며, 마이크로서비스를 분리하여 여러 개의 작은 애플리케이션으로 쪼개어 변경과 조합이 가능하도록 만든 아키텍처를 `마이크로서비스 아키텍처`라 한다.
* 대규모 소프트웨어 프로젝트를 마이크로 단위의 모듈로 분리하여 결합도를 낮추고(loosley-coupled) `API`를 통해 통신한다.
* 이렇게 만들면 기존에 개발했던 부분을 수정하거나 새로운 기능을 추가할 때 그 기능이 실패해도 전체 어플리케이션에 미치는 영향을 최소화 할 수 있다. 

## 모놀리틱(Monolithic) 아키텍처

<p align="center"><img src="https://miro.medium.com/max/1280/0*1WjIRAQHhL-UR7WL.png" width="600"></p>
* 사진 출처 : [https://giljae.medium.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-microservices-architecture-%EC%9D%98-%EC%9E%A5%EC%A0%90%EA%B3%BC-%EB%8B%A8%EC%A0%90-7c45615cfe1a](https://giljae.medium.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-microservices-architecture-%EC%9D%98-%EC%9E%A5%EC%A0%90%EA%B3%BC-%EB%8B%A8%EC%A0%90-7c45615cfe1a)

* 만약 `JAVA`를 사용하여 웹 어플리케이션을 개발한다면 
    * 사용자에게 보여줄 `view` 페이지를 구성
    * 요청된 `URI`에 따라 각 `view` 페이지를 연결해 줄 `컨트롤러`
    * 도메인 정의 및 `DAO` 설계
    * `컨트롤러`와 `DAO`간의 결합도를 낮추기 위해 서비스 계층 구성
* 등 각 계층간 결합도를 낮추기 위한 설계를 하지만 최종 배포시에는 하나의 `war` 파일로 배포하게 된다. 즉 모두가 하나로 합쳐지게 되고 이는 유연한 리펙토링을 어렵게 만든다.
* 서비스의 규모가 작고 개발자의 수도 적다면 큰 문제가 되지 않지만 개발자의 수가 늘어나고 서비스의 규모가 커지면 간단한 기능을 추가할 때에도 수정할 코드가 많아지고 그 수정이 영향을 미치는 부분도 많아졌기 때문에 간단한 변화에도 대규모 통합 테스트가 필요해진다. 이를 `모놀리틱(Monolithic)` 아키텍처라 한다.
* 모놀리틱 아키텍처의 특성은 새로운 프레임워크를 사용할 필요가 생겨도 쉽사리 바꾸지 못한다는 점을 만들어 낸다. 왜냐하면 전체 어플리케이션이 하나로 묶여 있다면 그 동안 작성한 코드들을 새로운 언어 또는 프레임워크로 바꿔야 하는데 개발된 코드의 양이 많으면 많을수록 엄두가 안 날 것이다.

## 마이크로서비스(Microservice) 아키텍처

<p align="center"><img src="https://miro.medium.com/max/1214/0*6c95Zet-KhecGRKK.png" width="600"></p>
* 사진 출처 : [https://giljae.medium.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-microservices-architecture-%EC%9D%98-%EC%9E%A5%EC%A0%90%EA%B3%BC-%EB%8B%A8%EC%A0%90-7c45615cfe1a](https://giljae.medium.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-microservices-architecture-%EC%9D%98-%EC%9E%A5%EC%A0%90%EA%B3%BC-%EB%8B%A8%EC%A0%90-7c45615cfe1a)

* 하지만 마이크로서비스 아키텍처는 서비스가 개별적으로 독립적인 단위의 어플리케이션이기 때문에 변경이 용이하고  그 변경이 다른 어플리케이션에 미치는 영향도 적다.
* 또한 개별 서비스 단위의 배포가 가능하기 때문에 하루에도 여러 번의 배포가 가능하다. 최근에 진행했던 `JAVA & JSP` 프로젝트를 `AWS EC2`로 배포할 때 `war` 파일로 배포했기 때문에 배포 후 조그만 수정사항이 생겨도 `war` 파일을 다시 익스포트해야 했기 때문에 좀 불편했다. 프로젝트를 마이크로서비스 아키텍처로 설계하게 되면 그런 수고를 덜 수 있어 좀 더 유연하고 빠른 개발이 가능해 보인다.
* 하지만 그만큼 개발이 어렵다는 단점이 있다. 마이크로서비스 아키텍처를 적용해 개발하게 되면 `view` 페이지 하나에서 보여지는 여러 컨텐츠 중 특정 컨텐츠 하나만 제공하는 어플리케이션 단위로 쪼개어서 페이지 로드 시 각 어플리케이션에서 받아오게 된다. 이론적으로는 쉬워 보이지만 실제 구현시에는 각각 마이크로서비스의 호스트 정보 및 통신 프로토콜에 대해 처리해 주어야 하기 때문이라고 한다.
* 관련글 : [마이크로서비스 아키텍처. 그것이 뭣이 중헌디?](http://guruble.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4microservice-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EA%B7%B8%EA%B2%83%EC%9D%B4-%EB%AD%A3%EC%9D%B4-%EC%A4%91%ED%97%8C%EB%94%94/)<br><br><br>

# 결론
* 마이크로서비스 아키텍처의 장점들을 보면 무조건 마이크로서비스 아키텍처를 쓰는 것이 좋아보인다. 하지만 아직 서비스의 규모가 작고 마이크로서비스 아키텍처를 적용했을 때 모놀리틱 아키텍처에 비해 오히려 일이 더 늘어나고 생산성이 더 떨어진다면 마이크로서비스보다는 모놀리틱 아키텍처를 적용해 개발하는 것이 더 좋을 수 있다는 결론을 얻을 수 있었다. 나보다 더 전문가이신 분들이 쓴 글에서 깊은 인사이트를 얻을 수 있었기에 공부에 참고했던 링크를 남긴다.<br><br><br>

# 참고
* [마이크로서비스 아키텍처. 그것이 뭣이 중헌디?](http://guruble.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4microservice-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-%EA%B7%B8%EA%B2%83%EC%9D%B4-%EB%AD%A3%EC%9D%B4-%EC%A4%91%ED%97%8C%EB%94%94/)
* [Do Not Use MSA - 마이크로서비스 아키텍처가 꼭 필요한가요?](https://www.samsungsds.com/kr/insights/msa.html)
* [마이크로서비스 아키텍처(Microservices Architecture)의 장점과 단점](https://giljae.medium.com/%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%95%84%ED%82%A4%ED%85%8D%EC%B2%98-microservices-architecture-%EC%9D%98-%EC%9E%A5%EC%A0%90%EA%B3%BC-%EB%8B%A8%EC%A0%90-7c45615cfe1a)
