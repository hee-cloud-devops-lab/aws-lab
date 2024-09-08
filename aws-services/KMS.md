# Key Management Service

- 데이터를 암호화할 때 사용되는 암호화 Key를 안전하게 관리하는데 목적을 둔 서비스

## KMS Key 관리 서비스

- AWS managed key
    - AWS 서비스들이 KMS를 통해 Key를 서비스 받는 것
    - 내부적으로 자동으로 일어나게 되며, 사용자가 직접적으로 제어가 불가능하다.
- Customer managed key (CMK)
    - 사용자가 직접 Key를 생성하고 관리하는 것
    - CMK에 대한 제어는 IAM을 통해 권한을 부여받아 제어가 가능하다.
- Customer key stores
    - AWS에서 제공하는 또다른 Key 관리형 서비스인 CloudHSM을 활용한 Key 관리형태
    - CloudHSM이 조금 더 강력한 형태의 보안 안전성을 제공한다.

## 참고 자료

- https://bluese05.tistory.com/71
- https://velog.io/@odh0112/AWS-KMS
