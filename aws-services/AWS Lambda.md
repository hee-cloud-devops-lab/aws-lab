# AWS Lambda

- 서버리스 컴퓨팅 서비스
- 서버를 프로비저닝 또는 관리하지 않고도 실제로 모든 유형의 애플리케이션과 백엔드 서비스에 대한 코드를 실행할 수 있는 이벤트 중심의 서버리스 컴퓨팅 서비스
- 코드는 람다 함수로 구성되며, 사용자는 람다에 원하는 함수를 작성하고 필요 시 함수를 사용할 수 있다.
- 이벤트에 의해 자동으로 트리거되는 코드 실행 환경을 제공한다.
    - 예를 들어, S3 버킷에 파일이 업로드 되거나 DynamoDB에 새로운 레코드가 추가될 때 코드가 실행된다.
    - 이는 이벤트 기반 아키텍처를 가능하게 하며, 다양한 AWS 서비스와의 통합을 통해 강력한 백엔드 솔루션을 구축할 수있게 된다.

### 서버리스 컴퓨팅

- 서버의 설정과 관리 없이 백엔드 서비스를 운영할 수 있게 해주는 클라우드 컴퓨팅 모델
- 사용자는 코드 작성에만 집중하고, 나머지 인프라 관리는 AWS가 담당하게 된다.
- 클라우드 제공 업체가 서버 인프라에 대한 관리 등을 대신 처리해주기 때문에 개발자는 서버 관리에서 자유로워지며 실제로 구현해야 할 기능에만 더 집중할 수 있게 된다.

## 작동 원리

![image](https://github.com/user-attachments/assets/bfc5569d-10ef-47ee-a1e9-5837b4e93c81)

### 람다 함수

- 함수는 람다에서 코드를 실행하기 위해 호출할 수 있는 리소스이다.
- 함수에는 함수에 전달하는 이벤트 또는 다른 AWS 서비스에서 보낸 이벤트를 처리하는 코드가 포함된다.

### 이벤트 트리거(이벤트 소스)

- AWS Lambda는 이벤트를 처리하기 위해 함수 인스턴스를 실행한다.
    - 함수는 람다 API를 사용해 직접 호출할 수 있으며, AWS 서비스 및 리소스를 설정해 함수를 호출할 수도 있다.
- HTTP 요청, 데이터 상태 번역, 파일 업로드 등 다양한 이벤트에 의해 트리거된다.

### 람다 작동 방식

- 함수를 생성하고, 해당 함수를 사용하는 프로그래밍 언어와 같은 기본 정보를 서비스에 추가한다.
- 람다 편집기에서 코드를 작성하거나 소스 코드를 zip 파일로 업로드한다.
- 람다 코드가 업로드되면 서비스가 모든 용량 확장, 패치 및 인프라 관리를 처리한다.

## 참고 자료

- https://www.smileshark.kr/post/all-about-aws-lambda-the-complete-beginners-guide-1
