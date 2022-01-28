# Spring Basic 

## EJB
- EJB 를 많이 사용하였지만 복잡하고 어렵고 느린 문제점
- EJB에 맞는 인터페이스, EJB에 의존성 문 -> 코드 더러워짐

### EJB 대체
- 하이버네이트 : 현재의 JPA 
- 스프링 : 로드 존슨에 의해 책으로 처음 시작 및 설계 -> 유겐 휠러에 의해 상당수 개발 및 발전
  - BeanFactory, ApplicationContext, POJO, 제어의 역전, 의존관계 주입 등
- 스프링 부트 : 스프링의 세팅이 너무 오래 걸림 -> 2014년 스프링 부트 1.0출시 


## 스프링 구성요소
`spring.io`참고
- 필수 : 스프링 프레임워크, 스프링 부트
- 선택 : 
  - 스프링 데이터
  - 스프링 세션
  - 스프링 시큐리티
  - 스프링 Rest Docs
  - 스프링 배치
  - 스프링 클라우드
  
### 스프링 부트
- 스프링을 편리하게 사용할 수 있도록 지원, 실무에서 대부분의 프로젝트는 깔고 들어간다 생각
- 단독으로 실행할 수 있는 스프링 애플리케이션을 쉽게 생성
- Tomcat 같은 웹 서버 내장
- 손쉬운 빌드 구성을 위한 starter 종속성 제공 -> 의존 모듈 설치 용이
- 스프링과 3rd party 라이브러리 자동 구성
- 메트릭, 상태확인, 외부 구성 같은 프로덕션 준비 기능 제공 -> 메트릭: 모니터링
- 관례에 의한 간결한 설정 

### 스프링 정의?
- 스프링 DI 컨테이너 기술

### 스프링 왜??
- 핵심, 컨셉은 자바 언어 기반의 프레임워크
- 객체지향 언어
- 스프링은 좋은 객체 지향 애플리케이션을 개발할 수 있게 도와주는 프레임워크
- EJB : 사용 시 상속받는 부분에 대해서 더렵고 의존되는 코드 -> 객체지향의 좋은 장점 어려움 -> EJB 스타일에 의존

## 객체지향 프로그래밍
`객체`들의 `모임`으로 파악하고자 하는 것. 각각의 `객체`는 `메시지`를 주고받고, 데이터를 처리할 수 있다.

### 다형성
#### 운전자-자동차
- 자동차의 종류가 바뀌어도 운전자는 운전을 할 수 있는 것은 변하지 않음
- 클라이언트의 영향을 끼치지 않고 새로운 기능을 제공할 수 있다. -> 클라이언트를 바꾸지 않아도 된다.
- 역할과 구현으로 구분

#### 공연무대
- 로미오와 줄리엣 역할을 다른 배우로 대체가 가능해야 한다.

#### 장점
- 클라이언트는 인터페이스만 알면 된다.
- 클라이언트는 구현 대상의 내부구조를 몰라도 된다.
- 내부 구조가 변경되어도 영향을 받지 않는다.
- 구현 대상 자체를 변경해도 영향을 받지 않는다.

#### 구조
역할 : 인터페이스
구현 : 인터페이스를 구현한 클래스, 구현 객체
객체 설계시 역할(인터페이스)를 먼저 부여, 그 역할을 수행하는 구현 객체 만들기

#### 자바 언어의 다형성
- 오버라이딩 
- 다형성으로 인터페이스를 구현한 객체를 실행 시점에 유연하게 변경
- 클라이언트를 변경하지 않고, 서버의 구현 기능을 유연하게 변경할 수 있어야 한다.

#### 다형성 장점
- 유연하고, 변경 용이
- 확장 가능한 설계
- 클라이언트 영향 X
- 인터페이스를 안정적으로 잘 설계해야 한다.

#### 다형성 한계
- 인터페이스 자체가 변하면, 클라이언트, 서버 모두 큰 변경 발생
- 인터페이스를 안정적으로 잘 설계하는 것이 중요

### 스프링과 객체지향
- 다형성
- 제어의 역전(IoC), 의존관계 주입(DI)은 다형성을 활용해서 역할과 구현을 편리하게 다룰수 있도록 지원 

## SOLID
로버트 마틴이 설계

### SRP 단일 책임 원칙
- 한 클래스는 하나의 책임만.
- 책임을 나누는 중요한 기준은 `변경` : 변경이 있을 때 파급효과가 적게

### OCP 개방-폐쇄 원칙 `중요`
- `확장`에는 `열려` 있으나 `변경`에는 `닫혀` 있어야 한다.
- 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능 구현
- 객체를 생성하고, 연관관계를 맺어주는 별도의 조립, 설정자가 필요

### LSP 리스코프 치환 원칙
- 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.

### ISP 인터페이스 분리 원칙
- 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.
- ex) 
  - 자동차 인터페이스 : 운전 인터페이스, 정비 인터페이스로 분리
  - 사용자 클라이언트 : 운전자 클라이언트, 정비사 클라이언트로 분리

### DIP 의존관계 역전 원칙 `중요`
- 추상화에 의존해야지, 구체화에 의존하면 안된다.
- 클라이언트는 구체적인 클래스보다 인터페이스를 바라봐야 한다. 의존해야한다는 뜻
- 역할에 의존해야 한다.

## 객체지향 설계와 스프링
OCP, DIP 원칙을 지키기 위해 스프링 프레임워크 만들게 된다. (DI 컨테이너)

### 단점
인터페이스 도입 시에 추상화라는 비용이 듬
- 기능을 확장할 가능성이 안보이면 구체 클래스를 쓰는 것 -> 나중에 리팩토링을 통해 인터페이스 구현

## Ioc
- 프로그램에 대한 제어 흐름에 대한 권한은 모두 AppConfig가 가지고 있다.
- 프로그램의 제어 흐름을 직접 제어하는 것이 아닌 외부에서 관리하는 것.

## DI
- 의존 관계는 "정적인 클래스 의존관계와 실행 시점에 결정되는 동적인 객체(인스턴스) 의존 관계" 둘을 분리해서 생각

## 싱글톤 패턴
- 객체의 인스턴스가 오직 1개만 생성되는 패턴을 의미

## 진도율
- 90%