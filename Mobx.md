# Mobx

#### 우선 React 란?

- Javaxcript Web Front-End Rendering 라이브러리 중 하나이다.

- 보통의 싱글페이지 앱 프레임워크(대부분의 기능 포함)가 아니라 View를 Rendering하는 것이 주 기능이며 기타 기능들은 라이브러리를 추가적으로 사용해야 한다.

#### Component

- React에서 데이터를 화면에 렌더링하는 가장 기본이 되는 단위

- 클래스형과 함수형이 있고 목적에 따라 구분 사용

- React는 작은 단위부터 큰 단위의 컴포넌트 조합으로 구성

- 컴포넌트를 분리하여 개발, 적절히 조합하여 하나의 Page를 구성한다

#### State

컴포넌트에서 변경 가능한 데이터

#### Props

자식 컴포넌트가 부모로부터 Parameter를 받아 오늘 값으로 변경 불가!

#### Store

- 글로벌 영역에서 애플리케이션의 State와 **비즈니스 로직을 가지고 있는 주체

** 일반적으로 데이터베이스와 사용자 인터페이스 사이의 정보 교환을 처리하는 알고리즘을 설명하는데 사용

** 업무에 필요한 데이터 처리를 수행하는 응용프로그램의 일부

** 하나의 프로젝트나 프로그램 중 업무와 관련된 처리를 하는 일부분을 뜻 하는데 웹의 구현 중에서 사용자가 원하는 자료의 가공 부분을 의미 한다. 미처리 영역에서 사용자가 원하는데로 다시 업무를 처리하는 과정

- State를 글로벌한 영역에서 관리한다

- => State 관리 라이브러리 사용의 목적이 된다

#### Redux

- Flux 개념을 바탕으로 한 React에서 현재 가장 많이 사용되는 State 관리 라이브러리

- Component와 State를 연결

#### Mobx

- Redux와 또 다른 State관리 라이브러리

- 객체지향의 느낌이 강하다

- 번잡한 **보일러플레이트 코드들을 데코레이터 제공으로 깔끔하게 해결

** 최소한의 변경으로 재사용할 수 있는 것

** 적은 수정만으로 여러 곳에 활용 가능한 코드

** 각종 문서에서 반복적으로 인용되는 문서의 한 부분

** 반복되지만 자주 쓰이는 형태를 자동화한다는게 핵심이다.

- mobx는 리덕스와 다르게 관심사에 따라서 여러개의 스토어를 만들고 필요에 따라 컴포넌트 위에 프로바이더를 만들어서 사용할 수 있다.

#### Observable (Mobx가 동작하는 가장 기본 개념이 된다)

- observer 함수 자체가 클래스 컴포넌트를 리턴하는 higher order component로  클래스를 위한 함수이다

  ==> hook과의 호환을 위해 mobx-react-lite 존재

- Mobx에서 랜더링 대상이 되는 state(상태, 값)를 관찰 대상(observabel value)라고 칭하며 @observable 데코레이터로 지정한 스테이트는 관찰대상으로 지정되고 그 스테이트는 값이 변경될 때 마다 랜더링 된다

- 관찰받고 있는 state = 리액트 안에서 사용되는 글로벌 상태를 직접 변경하며 어떻게 상태가 변했는지 파악하는 요소

#### 불변성 

- React에서 렌더링을 할 때 판단하는 방법 = State가 변경 되었을 때

- 변경전/후 state를 서로 비료할 때 복잡도가 높은 경우 자식 **property까지 비교하는 것 보다 효율적인 방법으로 state의  레퍼런스가 변경되었을 때 변경된 것으로 간주하고 렌더링을 한다.

** 어떤 값을 나타낸다 그런데 이 값이 다른 값과 연관을 갖을때 명시

** 예로 문자열에는 length라는 property가 있는데 이때는 문자열 안에 있는 문자의 양을 정수로 나타낸 값을 담고 있다

- 기존 State 값을 직접 변경 X -> 기존 State값을 바탕으로 변경되어 새로 생성된 객체의 레퍼런스를 setState 메서드를 통하여 변경

  ==> 불변성을 유지한다 라고 표현

## Mobx의 장점

### 객체 지향적 

도메인 모델로 분리됨 -> 집중된 비즈니스 로직은 적절히 분산, 도메인 간의 상호작용은 message를 주고받는 형태로 구현 가능

### 서버 개발자들에게 친숙한 아키텍쳐

Java Spring Framework와 유사한 아키텍쳐 지향

### Decorator

데코레이터를 제공

-> redux 사용 시 컴포넌트와 스테이트를 연결하기 위한 mapStateToProps와 Redux action 연결을 위한 mapDispatchToProps등의 보이러플레이트 코드가 사라지고 데코레이터가 처리하여 깔끔한 코드가 생성된다

### 캡슐화

- Mobs Configuration 설정으로 State를 오직 메소드를 통하여 변경할 수 있도록 Private하게 관리할 수 있다.

- Mobx는 Configuration에서 옵션 한줄로 state의 변경은 해당 클래스의 메소드를 통해서만 변경할 수 있도록 할 수 있고, 도메인 모델간의 message를 통한 상호작용 코드 패턴을 유지해 나갈 수 있도록 해준다.

### 불변성 유지를 위한 노력이 불필요

State의 불변성을 유지하기 위해 번잡한 코드나 **ImmutableJS 같은 라이브러리를 따로 사용할 필요가 없다

** 불변 객체 : 객체지향 프로그래밍에 있어서 불변객체는 생성 후 그 상태를 바꿀 수 없는 객체를 말한다.

( 불변성을 유지하면서 state를 변경하는 코드는 Object가  Depth가 깊어지게 되면 코드의 가독성이 매우 떨어진다 그래서 ImmutableJS 라이브러리를 사용하게 되는데 리덕스와 함꼐 사용시 불편하다 )

 

## State관리 라이브러리 사용 목적

### 다중 계층 컴포넌트에서 데이터와 메소드 접근의 복잡성 해결

여러 컴포넌트가 조합되어 페이지가 구성되면 컴포넌트간 상호작용( State, Props )와 메소드의 접근이 까다롭다 ( 부모 자식의 관계로 scope가 이루어져 있기 때문 )

-> State를 Global한 Store영역에서 관리하는 방법 사용

### 컴포넌트에 집중된 비즈니스 로직의 분리

State관리 라이브러리를 사용하여 Component는 Controller에 해당하는 역할을 주로 하게 두고 나머지 로직은 적절히 분리하여 아키텍쳐를 구성할 수 있게 된다.



##  본격적인 Mobx

Mobx는 Redux와 비슷한 종류의 State관리 라이브러리다.

리덕스와 다르게 간결하고 깔끔함 구조를 갖는다.



### Mobx의 기본 개념 및 특징

기본 동작 개념 .ex) 배달리스트 가져오기

DeliveryStore의 FindAllDeliveries 호출

-> 서버로부터 가져온 데이터 선언부인 deliveries state에 할당

->  DeliveryComponent에서 deliveries 렌더링

기타 Mobx Store와 React 컴포넌트를 연결하는 방법은 @inject 데코레이더로 이루어 진다. 

이외 여러가지 기능을 하는 데코레이더 들이 제공된다.

### Mobx의 아키텍쳐

Mobx는 렌더링 할 State를 관찰 대상으로 지정

state를 변경하면 리액트 컴포넌트 렌더 메소드에 의해 렌더링 되는 아키텍쳐를 기본 골격으로 한다

Store / Model Class / Repository Class

#### Store = Service

java Spring Service와 비슷한 역할

but, 백엔드의 service 에서는 다수의 요청자에 의해 요청되기 때문에 특별한 상황이 아니라면 상태를 가지고 있지 않지만 **Mobx Strore는 observable한 state를 가지고 있다.**

Store는 싱글톤으로 유지해야 한다

#### Repository = Repository

Mobx Repository는 Ajax로 데이터를 가져오는 부분이다.

데이터를 가져오는 부분도 레이어를 나누어 구성하길 권장

( 비즈니스 로직 분리의 이점 및 test코드 작성시 **Mocking이 용이)

** 실제 값으로 테스트가 어려우니 가짜 값을 사용할 수 있게 해줌

#### Model = Entity or Dto

Spring의 Entity/Dto와 유사

미리 필드들을 선어하지 않아도 Object.assign 을 사용해서 동적으로 추가가 가능하다.

extendObservable은 Mobx가 제공하는 api로  Object.assign처럼 포로퍼티와 값을 Target 오브젝트에 합쳐주며 관찰 가능한 프로퍼티로 만들어 추가한다