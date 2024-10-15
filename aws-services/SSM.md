# AWS System Manager

- 하이브리드 클라우드 환경을 위한 end-to-end 관리 솔루션
- EC2 System Manager 혹은 Simple System Manager(SSM)으로도 알려져 있다.
- AWS의 리소스 및 온프레미스 서버의 자동 및 수동 작업을 관리한다.

## System Manager의 업무

1. 온프레미스와 EC2 인스턴스의 패키지 업그레이드
2. 설치 소프트웨어 목록 생성
3. 새 애플리케이션 설치
4. EBS 스냅샷을 이용한 AMI 이미지 생성
5. IAM 인스턴스 프로파일 부착
6. S3 버킷에 대한 퍼블릭 접근 차단

## 주요 기능

### 액션(Actions)

- 자동화(Automation) 액션
    - AWS 리소스에 대해 일괄적으로 작업을 수행할 수 있다.
        - 다수의 EC2 인스턴스 재시작, CloudFormation 스택 업데이트, AMI 패치 작업 등
    - 자동화 액션을 통해 개별 작업을 세분화된 방식으로 처리할 수 있으며, 일괄적으로 전체 자동화 업무를 처리하거나, 필요한 상황과 시점에 맞춰 단계별로 처리되도록 할 수 있다.
- 명령(Command) 액션
    - Linux 또는 Windows 인스턴스에 대한 작업 수행
- 정책(Policy) 액션
    - 관리중인 인스턴스로부터 목록 데이터를 수집하는 과정 정의

## 참고 자료

- https://kimjingo.tistory.com/187
- https://velog.io/@golddong98/aws-Systems-Manager
