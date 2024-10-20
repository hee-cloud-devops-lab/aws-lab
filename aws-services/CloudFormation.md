# AWS CloudFormation

- IaC 기반의 구성 조정 도구로, AWS 리소스를 자동으로 생성하는 서비스이다.
- 사용하려는 AWS 리소스를 파일로 작성하면, CloudFormation이 이를 분석해 AWS 리소스를 생성한다.
    - 이렇게 생성된 리소스를 스택이라고 한다.
- 템플릿은 JSON이나 YAML 형식으로 만들 수 있다.

## 템플릿 예시

```yaml
Parameters:

  # 파라미터 이름(ec2 암호화 키페어)
  KeyName:
    # 파라미터 설명
    Description: Name of an existing EC2 KeyPair to enable SSH access to the web server
    # 파라미터 타입
    Type: AWS::EC2::KeyPair::KeyName
    # 오류메시지
    ConstraintDescription: must be the name of an existing EC2 KeyPair.

  InstanceType:
    Description: WebServer EC2 instance type
    Type: String
    # 디폴트 값
    Default: t2.micro
    # 선택 가능한 값들 지정
    AllowedValues:
    - t2.micro
    - t2.small
    ConstraintDescription: must be a valid EC2 instance type.

  SSHLocation:
    Description: Lockdown SSH access to the bastion host (default can be accessed
      from anywhere)
    Type: String
    MinLength: '9'
    MaxLength: '18'
    Default: 0.0.0.0/0
    # 정규표현식도 사용 가능
    AllowedPattern: "(\\d{1,3})\\.(\\d{1,3})\\.(\\d{1,3})\\.(\\d{1,3})/(\\d{1,2})"
    ConstraintDescription: must be a valid CIDR range of the form x.x.x.x/x.
```

## 참고 자료

- [https://medium.com/pplink/aws-cloudformation으로-인프라-자동화-시작하기-9fe13cdf08c9](https://medium.com/pplink/aws-cloudformation%EC%9C%BC%EB%A1%9C-%EC%9D%B8%ED%94%84%EB%9D%BC-%EC%9E%90%EB%8F%99%ED%99%94-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-9fe13cdf08c9)
