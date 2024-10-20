# AWS EventBridge

- EDA(Event Driven Architecture)를 구성하는데 도움이 되는 AWS의 서버리스 서비스
- SaaS 서비스, 개인 어플리케이션, AWS 서비스에서 보내는 이벤트(데이터)를 받아 원하는 SNS나 Lambda와 같은 타겟으로 보내는 역할을 한다.

## EventBridge 구성요소

![image](https://github.com/user-attachments/assets/71006ea4-3b12-48a4-b944-b8ed78f76d80)


### Event

- 이벤트 소스에서부터 오는 이벤트
- AWS 서비스를 예로 들면, EC2의 상태가 변경된다든지, Auto Scaling Group에 인스턴스가 추가될 때 Event가 발생한다.

### Event Rule

- Event가 발생한 경우, **Event Rule과 매칭되는 이벤트만 Event Rule에 연결된 Event Target으로 라우팅된다.**
    - EDA에서 보면 구독할 수 있는 대상이라 볼 수 있다.
- 만약 Auto Scaling Group의 인스턴스가 추가되어 이벤트가 발생되었다고 하면, 해당 이벤트의 패턴과 매칭되는 Event Rule은 모두 이 이벤트를 통과시킨다.
    - 이 이벤트의 패턴은 Event Pattern이라 부르고, 이 패턴을 만족하는 이벤트는 이벤트 패턴을 가지는 모든 Rule의 Target에 라우팅된다.

### Event Target

- Event Rule의 필터링을 통과한 이벤트가 도착하는 대상이다.
- 하나의 Event Rule에 여러개의 Event Target 등록이 가능하다.
    - 즉, 해당 Event Rule의 이벤트 패턴을 만족하는 이벤트를 구독한다는 개념으로 생각할 수 있다.

### Event Bus

- 이벤트를 받는 역할을 한다.
- Event Rule 생성 시, 하나의 Event Bus에 연결해야 한다.
    - 이 Event Bus로 들어오는 이벤트만 Event Rule에서 필터링을 하게 된다.
- AWS 계정마다 기본적으로 생성하는 Event Bus가 있는데, 이것을 Default Event Bus라 부르고, AWS 서비스로부터 생성된 이벤트는 모두 이 이벤트 버스로 들어온다.

## CloudWatch Events와의 차이점

- EventBridge 등장 전, CloudWatch Events가 비슷한 역할을 담당하고 있었다.
- 하지만 CloudWatch Events는 AWS가 생성한 이벤트만 사용이 가능하지만, EventBridge는 AWS 서비스뿐만 아니라 SaaS나 개인 어플리케이션으로부터 생성된 이벤트도 사용이 가능하다.

## 참고 자료

- https://velog.io/@techy-yunong/AWS-EventBridge-concept
