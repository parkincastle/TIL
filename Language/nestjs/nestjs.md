# NestJS 란?
<br>

<div align = "center">
    <img src = "../../img/nestjs.png" width = "75%" height = "50%">
</div>

<br>
NestJS는 node.js의 프레임워크 중 하나로 서버 측 애플리케이션 을 구축할 수 있다.
<br>

NestJS는 기본적으로 Typescript를 지원하며 애플리케이션을 작성하는 것도 가능하다.
뿐만 아니라 **OOP(Object Oriented Programming)**, **FPR(Functional Reactive Programming)**, **FP(Functional Programming)** 등을 지원한다.

<br><br>

# NestJS의 장점
## 효율성
<br>

NestJS는 **typescript의 적극적인 도입, DI(Iependency Injestion), Ioc(Inversion of control), Module을 통한 구조화**등의 기술 덕분에
규모가 있는 프로젝트에서의 생산적인 개발이 가능하다.

<br><br>

## 안정적
<br>

NestJs는 **typescript를 적극적으로 도입**합으로서 서버 애플리케이션 개발 시 발생할 수 있는 **오류들을 사전에 방지**할 수 있도록 했다. 또한 모듈로 감싸는 형태로 개발하기 때문에 모듈별로 테스트 코드를 쉽게 작성할 수 있도록 구현되어 있다.

<br><br>

## 확장성
<br>

NestJs는 module을 통해 **확장이 용이하도록 설계**되어 있댜. 실제로 사용해보면 module을 통해 코드적으로, 논리적으로 구분한다는 장점을 크게 느끼실 수 있다
그리고 NestJS는 **기본적으로 마니크로서비스 아키텍처 개발 스타일을 제공**한다.

<br><br>

## 구조
<br>

controller, service, module클래스들은 각각 역할을 가지고 있다.
middelware, guard, filter등의 클래스들 또한 다 그들의 역할을 가지고 있다.
IoC와 DI 같은 디자인 패턴을 도입해서 그것들에 맞추지 않으면 개발하기 힘든 구조이다. 하지만 그런 제한이 개발의 통일성을 가지고 온다

# NestJS의 단점

아키텍처의 구조가 어느 젇도 정해져 있다 보니 **러닝 커브(습득하는데 드는시간)가 있는 편**이다. 아직은 한국에서는 많이 사용되고 있지 않아서 문서가 많이 없지만 공식문서가 잘 되어 있고 영어 문서는 점점 늘어나는 추세이기 때문에 시간이 해결해 줄 것이다.
