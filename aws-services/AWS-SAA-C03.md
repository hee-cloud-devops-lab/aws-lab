# S3 Transfer Acceleration

> 세계 각국의 어떤 Region에서 다른 Region의 S3에 빠르게 전송하고 싶을 때 사용한다.
> 
- 유저가 S3 버킷으로 데이터를 전송할 때 최적화된 네트워크 경로를 통해 전송할 수 있는 기능
- 멀리 떨어진 곳에서 S3 버킷에 데이터를 전송할 경우, 최적화된 네트워크 경로로 빠르게 전송할 수 있다.

## Use case

- 세계 각국에서 한 곳의 Region의 S3에 파일을 전송할 경우
- 대륙간에 정기적으로 대용량의 데이터를 전송하는 경우

## 참고 자료

- https://jibinary.tistory.com/321

# AWS Snowball

- 오프라인 전송 서비스
- 별도의 하드웨어 장비를 통해 IDC에서 장비로 데이터를 전송한 이후, AWS에서 장비를 수거해 S3로 이관한다.

## Snowball Edge 옵션

1. Snowball Edge Storage Optimized (데이터 전송용)
2. Snowball Edge Storage Optimized (EC2 컴퓨팅 기능 포함)
3. Snowball Edge Compute Optimized
4. GPU로 Snowball Edge Compute Optimized

## 참고 자료

- [https://medium.com/@nuatmochoi/aws-snowball-대용량-데이터-이관-ac9d26615b4c](https://medium.com/@nuatmochoi/aws-snowball-%EB%8C%80%EC%9A%A9%EB%9F%89-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9D%B4%EA%B4%80-ac9d26615b4c)

# AWS S3 Cross-Region Replication

## Replication

- 특정 버킷에서 다른 버킷으로 비동기 방식의 복제를 지원하는 기능
- 버킷 복제는 서로 다른 AWS 계정 간에도 사용할 수 있다.

## Cross-Region Replication

- 특정 리전에 S3 버킷이 있는 경우, 다른 리전의 S3 버킷에 복제하는 것을 의미한다.
- 소스 버킷과 타겟 버킷 모두 버전 관리 기능이 활성화되어야 한다.
- 여러 Region에 분포되어 성능이나 기능 상 유리할 때 사용한다.

## 참고 자료

- https://gngsn.tistory.com/245

# Amazon Elastic Block Store(Amazon EBS)

- AWS 클라우드의 EC2 인스턴스에 사용할 영구 블록 스토리지 볼륨을 제공하고, 각 EBS 볼륨은 가용 영역 내에 자동으로 복제되어 구성요소 장애로부터 보호해주고, 고가용성 및 내구성을 제공한다.
- 데이터를 블록 단위로 저장하는 스토리지 방식이며, SAN(Storage Area Network) 또는 클라우드 기반 스토리지 환경에서 사용되는 기술이다.
- EC2가 메모리, 그래픽 카드 등 하드디스크를 제외한 컴퓨터의 모든 부분이라면, EBS는 하드웨어라고 생각하면 된다.
- EBS를 사용하면, EC2 인스턴스를 중지하거나 종료시켜도 EBS에 저장된 데이터는 보존된다.

## 참고 자료

- https://velog.io/@ghldjfldj/AWS-EBSAMISG
- https://jibinary.tistory.com/150

# AWS RedShift

- AWS에서 제공하는 클라우드 기반의 완전 관리형 데이터 웨어하우스 서비스이다.
- PetaByte 규모의 데이터까지 처리할 수 있다.
- PostgreSQL을 기반으로 두고 있어, 표준 SQL을 이용하는 데이터 처리를 지원하며 이를 통해 BI를 얻을 수 있다.

## 참고 자료

- https://velog.io/@ssongji/AWS-RedShift
- https://bomwo.cc/posts/Datawarehouse/

# Amazon Athena

- 표준 SQL을 사용해 Amazon S3에 저장된 데이터를 간편하게 분석할 수 있는 대화식 쿼리 서비스

## 참고 자료

- https://docs.aws.amazon.com/ko_kr/athena/latest/ug/what-is.html
- https://btcd.tistory.com/341

# Amazon CloudWatch Logs

- EC2, Route53, AWS CloudTrail 및 기타 소스에서 사용자 지정 로그 파일을 모니터링하고 저장 및 액세스할 수 있다.

## 참고 자료

- [https://velog.io/@jihwankim94/AWS-Cloudwatch-Log-란](https://velog.io/@jihwankim94/AWS-Cloudwatch-Log-%EB%9E%80)

# Amazon EMR

- 빅데이터 환경 및 애플리케이션을 간단하게 구축하고 운영할 수 있다.

## EMR 구조

![image](https://github.com/user-attachments/assets/bc59681d-59f2-4544-9736-77231f29e192)


- Master Node: 클러스터 전체를 관리하는 노드
- Core Node: 연산 처리를 실행하는 노드
- Task Node: 코어 노드와 같이 연산처리를 하며, 파일 시스템을 갖지 않는 연산처리 전용의 노드이다.

## **HDFS와 EMRFS**

EMR은 파일 시스템으로 HDFS와 EMRFS를 사용할 수 있다.

- **HDFS**: Hadoop Distributed File System
    - Hadoop의 파일 시스템이다.
    - EMR에서 마스터노드와 코어노드에서 사용 가능.
    - EMR 클러스터가 종료되면 HDFS의 데이터는 사라진다.
        
        ![image](https://github.com/user-attachments/assets/d45ee8a2-6620-4321-a945-4e74da3e08d7)

        
- **EMRFS**: EMR File System
    - **Amazon S3**를 EMR 클러스터에서 파일 시스템으로 사용할 수 있도록 하는 기능.
    - 데이터를 영원히 보관하여 EMR 클러스터가 종료되어도 데이터는 사리 지지 않는다.
    - S3가 갖는 기능(데이터 암호화등)도 같이 사용가능.
        
        ![image](https://github.com/user-attachments/assets/d2da3efc-0b77-44c0-a7e9-6b52280900b7)

        

## 참고 자료

- [https://velog.io/@busybean3/Amazon-EMR의-기능을-알아보자](https://velog.io/@busybean3/Amazon-EMR%EC%9D%98-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)
- https://jibinary.tistory.com/253

# AWS Glue

- 완전 관리형 ETL 서비스로, 간단하게 여러 데이터 스토어 및 스트림 간에 원하는 데이터를 분류, 정리, 보강, 이동한다.

## 참고 자료

- [https://velog.io/@ginee_park/AWS-Glue란](https://velog.io/@ginee_park/AWS-Glue%EB%9E%80)

# AWS Organizations

- 여러 계정을 조직에 통합하고 중앙에서 관리할 수 있는 계정 관리 서비스
- 계정 관리 및 통합 결제 기능을 지원하며, 기업의 예산, 보안 및 규정 준수 요구 사항 준수에 도움을 줄 수 있다.

## 조건 키

- 특정 조건에 따라 접근 제어를 수행하기 위해 Policy의 Condition 요소 내에서 사용된다.
- 조건 키를 사용하면 Policy의 허가나 거부를 구체적인 조건으로 세밀하게 제어해 접근 권한을 상세히 관리할 수 있다.

### **글로벌 조건 키 예시**

- **aws:PrincipalOrgID**: Organization 전체
    - AWS Organizations에 속한 전체 **계정의 접근**을 제어하는 데 사용됩니다.
    - 예시) **특정 조직(Organizations) ID를 가진 계정만** 특정 리소스에 접근할 수 있도록 설정
- **aws:PrincipalOrgPaths**: Organization의 특정 OU
    - 조직 유닛(OU)의 계층을 지정하여 특정 부서나 그룹에 대한 세밀한 접근을 제어
    - 예시) **특정 OU에 속한 계정들만** 특정 리소스에 접근할 수 있도록 설정
- **aws:PrincipalTag**:
    - Tag에 기반하여 접근을 제어한다.
    - 예시) 특정 태그가 적용된 사용자나 역할만 리소스에 접근할 수 있도록 설정

**Organizations 전체가 대상**이라면 aws:PrincipalOrgID를 적용해야한다.

**특정 OU가 대상**이라면 aws:PrincipalOrgPaths를 적용해야한다.

## 참고 자료

- [https://velog.io/@xlwdn98767/AWS-Organizations란](https://velog.io/@xlwdn98767/AWS-Organizations%EB%9E%80)

# AWS CloudTrail

- **AWS 계정**의 운영 및 위험 감사, 거버넌스 및 규정 준수를 활성화하는 데 도움이 되는 서비스
    - 클라우드 인프라에서 이루어지는 것들을 로깅하는 서비스이다.
- 사용자, 역할 또는 AWS 서비스가 수행하는 작업은 CloudTrail에 이벤트로 기록된다.
- AWS 계정에서도 사용할 수 있는데, 활동이 AWS 계정에서 이루어지면 해당 활동이 CloudTrail 이벤트에 기록된다.
- API 호출 내역도 기록 가능

## 참고 자료

- https://metaverse-cloud.tistory.com/204
- [https://velog.io/@juhyeon1114/AWS-CloudTrail-알아보기](https://velog.io/@juhyeon1114/AWS-CloudTrail-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0)
- https://peterica.tistory.com/346

# Amazon API Gateway

- 애플리케이션이 백엔드 서비스의 데이터, 비즈니스 로직 또는 기능에 액세스할 수 있는 정문 역할을 한다.
- 실시간 양방향 통신 애플리케이션이 가능하도록 하는 RESTful API 및 WebSocket API를 작성할 수 있다.
- API 게이트웨이를 등록하면, 모든 클라이언트는 각 서비스의 엔드포인트 대신 API Gateway로 요청을 전달하기 때문에 관리가 용이해진다.

## 참고 자료

- https://aws.amazon.com/ko/api-gateway/
- [https://inpa.tistory.com/entry/AWS-📚-API-Gateway-개념-기본-사용법-정리](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-API-Gateway-%EA%B0%9C%EB%85%90-%EA%B8%B0%EB%B3%B8-%EC%82%AC%EC%9A%A9%EB%B2%95-%EC%A0%95%EB%A6%AC)

# Amazon EFS (Elastic File System)

![image](https://github.com/user-attachments/assets/927a68f5-3df3-4f11-b75c-420fa4720e6a)


- AWS 클라우드 서비스와 온프레미스 리소스에서 사용할 수 있는 간단하고 확장 가능하며 탄력적인 파일 스토리지를 제공하는 서비스
- EC2 Linux 인스턴스에 마운트된 NFS를 통해 VPC에서 필요한 파일에 접근하거나 AWS Direct Connect로 연결된 **온프레미스 서버의 파일에 접근할 수 있다.**
- 쉽게 생각해서 EFS는 회사의 온프레미스 환경의 NFS, NAS 폴더와 비슷한 서비스라고 이해하면 된다.
    - 그래서 수천대의 EC2 인스턴스간 파일 시스템 공유 가능하며, 병렬 접근이 가능하도록 설계되어 있어, **두 개 이상의 EC2로부터 하나의 공유된 스토리지 공간이 필요할 때 EFS를 채택하면 된다.**

## 참고 자료

- [https://inpa.tistory.com/entry/AWS-📚-EFS-개념-원리-사용-세팅-💯-정리](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-EFS-%EA%B0%9C%EB%85%90-%EC%9B%90%EB%A6%AC-%EC%82%AC%EC%9A%A9-%EC%84%B8%ED%8C%85-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)

# AWS CLI (Command Line Interface)

- AWS 서비스와 상호작용할 수 있는 오픈소스 도구
- Powershell이나 터미널에서도 AWS에서 제공하는 명령어 기능을 실행할 수 있다.

## 참고 자료

- https://potato-yong.tistory.com/94

# AWS Storage Gateway

- 온프레미스 소프트웨어 어플라이언스를 클라우드 기반 스토리지에 연결해 **온프레미스 IT 환경과 AWS 스토리지 인프라 클라우드에 데이터를 저장해 데이터 보안을 유지하는데 도움이 되는 확장 가능하면서 비용 효율적인 스토리지를 구현**할 수 있다.

## 유형

### File Gateway

![image](https://github.com/user-attachments/assets/5194aadf-af1c-4133-a0d2-f86312ff72d9)


- Amazon S3 파일 게이트웨이는 Amazon S3로의 파일 인터페이스를 지원하고 서비스와 가상 소프트웨어 어플라이언스를 결합한다.
- 이 조합을 사용하면 NFS와 SMB 같은 업계 표준 파일 프로토콜을 사용해 Amazon S3에서 객체를 저장하고 검색할 수 있다.
- S3에 저장된 파일, 파일과 연결된 객체의 메타데이터도 저장한다.
- 객체가 S3 버킷으로 전송되면 버전 관리, 수명 주기 관리, 교차 리전 복제와 같은 S3의 기능을 사용해 파일/객체를 관리할 수 있다.

**사용 사례**

- 온프레미스 애플리케이션을 클라우드로 마이그레이션하는 경우
- 저렴한 비용으로 클라우드에서 온프레미스 데이터를 백업하는 경우

### Volume Gateway

- 온프레미스 애플리케이션 서버에서 iSCSI 장치로 탑재할 수 있도록 클라우드 기반 스토리지 볼륨을 제공한다.

### 테이프 게이트웨이

- 클라우드 기반 가상 테이프 스토리지를 제공한다.
- 하이퍼바이저에서 실행되는 VM으로 온프레미스 환경에 배포된다.

## 참고 자료

- [https://blog.bespinglobal.com/post/aws-storage-gateway-이해하기/](https://blog.bespinglobal.com/post/aws-storage-gateway-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0/)

# AWS Direct Connect

- Data Center, 사무실 환경과 같은 장소에서 AWS와 전용 네트워크 연결을 제공하는 전용선 서비스이다.
- 회사 내부 네트워크 혹은 기존 데이터 센터 환경의 온프레미스 IT 자원과 AWS 클라우드 자원을 전용 회선으로 연결해 하이브리드 환경을 구축할 수 있는 서비스
- **실제 전용선**을 AWS와 연결하기 때문에 일관성 있는 서비스 품질을 보장받을 수 있다.
- 사용자는 인터넷을 경유하지 않고 AWS 네트워크(VPC)와 사용자 네트워크를 직접 연결할 수 있다.

## 참고 자료

- https://btcd.tistory.com/328
- https://dev.classmethod.jp/articles/what-is-the-aws-dx-kr/
- https://white-polarbear.tistory.com/135
- https://aws-hyoh.tistory.com/107

# Amazon Kinesis

- 실시간 스트리밍 데이터를 수집, 처리, 분석해 적시에 인사이트를 확보하고 새로운 정보에 신속하게 대응할 수 있다.
- 기계 학습, 분석 및 기타 애플리케이션을 위해 비디오, 오디오, 애플리케이션 로그, 웹 사이트 클릭 스트림과 같은 실시간 데이터를 수집한다.
- 모든 데이터가 수집된 후에야 처리를 시작하는 것이 아니라 데이터가 수신되는 대로 처리 및 분석, 즉시 대응이 가능하다.

## 참고 자료

- [https://aws.amazon.com/ko/pm/kinesis/?gclid=Cj0KCQiA19e8BhCVARIsALpFMgFQOWvaZ53ycHOqxOFAH0E7bEEWPei240R1GDy72ZGwCaPE25WTPWcaAnWQEALw_wcB&trk=5860e0a8-c230-4101-ba35-cdf15ec7e186&sc_channel=ps&ef_id=Cj0KCQiA19e8BhCVARIsALpFMgFQOWvaZ53ycHOqxOFAH0E7bEEWPei240R1GDy72ZGwCaPE25WTPWcaAnWQEALw_wcB:G:s&s_kwcid=AL!4422!3!651510601839!e!!g!!amazon kinesis!19828229715!148480174513](https://aws.amazon.com/ko/pm/kinesis/?gclid=Cj0KCQiA19e8BhCVARIsALpFMgFQOWvaZ53ycHOqxOFAH0E7bEEWPei240R1GDy72ZGwCaPE25WTPWcaAnWQEALw_wcB&trk=5860e0a8-c230-4101-ba35-cdf15ec7e186&sc_channel=ps&ef_id=Cj0KCQiA19e8BhCVARIsALpFMgFQOWvaZ53ycHOqxOFAH0E7bEEWPei240R1GDy72ZGwCaPE25WTPWcaAnWQEALw_wcB:G:s&s_kwcid=AL!4422!3!651510601839!e!!g!!amazon%20kinesis!19828229715!148480174513)

# Amazon Simple Notification Service (Amazon SNS)

- 완전 관리형 pub/sub 서비스
- SNS를 사용해 AWS 내부의 서비스나 외부의 시스템에 메시지를 보낼 수 있다.
- Decoupling 아키텍처로서 유용하다.

## 참고 자료

- https://jibinary.tistory.com/201

# Amazon Simple Queue Service (Amazon SQS)

- 서버끼리 사용할 수 있는 메시지 큐를 제공하는 서비스
- 해야할 일을 나중에 처리하거나, 다른 시스템이 처리할 수 있도록 하기 위한 비동기 메시징 서비스

## 대기열 종류

### 표준 대기열

- 메시지의 순서 보장을 하지 않으며 메시지가 한 번 이상 전달될 수 있다. (초당 무제한 호출)

### FIFO 대기열

- 선입선출 전달과 메시지 정확히 한 번 전달(초당 최대 3천건 호출)

### Dead-Letter Queue

- 소비자에게 배달되지 못한 메시지를 캡쳐해 저장하여 애플리케이션의 복원 및 내구성 보장

## 참고 자료

- [https://velog.io/@holicme7/AWS-SQS-란](https://velog.io/@holicme7/AWS-SQS-%EB%9E%80)

# Amazon EventBridge(Amazon CloudWatch Events)

- EDA(Event Driven Architecture)를 구성하는데 도움을 주는 AWS의 서버리스 서비스
- 다양한 소스의 데이터와 애플리케이션을 연결하는데 사용할 수 있는 서버리스 이벤트 서비스
- AWS 서비스 뿐만 아니라 SaaS 서비스, 개인 어플리케이션에서 보내는 이벤트를 받아, 원하는 SNS나 람다와 같은 타겟으로 보내주는 역할을 한다.

## 참고 자료

- https://velog.io/@techy-yunong/AWS-EventBridge-concept

# SQS vs SNS vs EventBridge

- https://junuuu.tistory.com/697

# AWS DataSync

![image](https://github.com/user-attachments/assets/35581278-c8bc-4964-8768-3e47833aa7b1)


- 온프레미스 혹은 AWS 클라우드의 스토리지 서버에서 AWS의 또 다른 스토리지 서비스로 데이터를 동기화하는 서비스

## 참고 자료

- https://engmisankim.tistory.com/42
- https://jibinary.tistory.com/326

# Amazon S3 Glacier Deep Archive

- S3의 스토리지 클래스 중 하나로, 매우 저렴한 비용으로 장기간 데이터 보관이 필요한 경우 사용된다.
- 데이터를 안정적으로 보관하고 검색할 수 있는 서비스로, 보통 장기간 보관이 필요한 데이터, 아카이브, 백업 등에 사용된다.
- 특히, 데이터를 주기적으로 검색하지 않고 긴 기간동안 보관할 경우 저렴한 비용으로 이용할 수 있다.

## 참고 자료

- [https://velog.io/@leesh0567/S3-Standard-란](https://velog.io/@leesh0567/S3-Standard-%EB%9E%80)
- https://bluese05.tistory.com/35

# Amazon FSx

- 완전 관리형 파일 시스템 서비스
- 세계적으로 유명한 써드파티 파일 시스템을 AWS에서 사용할 수 있도록 하는 서비스
- 기존 온프레미스 환경에서 AWS 클라우드로 파일 서버를 이동하고자 할 때 사용한다.
- EFS가 리눅스 방식이라면, FSx는 윈도우 방식

## 참고 자료

- https://jibinary.tistory.com/281
- https://jibinary.tistory.com/328

# AWS S3 Glacier

## 스토리지 클래스

### Amazon S3 Glacier Instant Retrieval

- 분기당 한 번 액세스되고 밀리초 단위의 검색이 필요한 수명이 긴 데이터에 대해 가장 저렴한 스토리지 제공

### Amazon S3 Glacier Flexible Retrieval

- 연간 1~2회 액세스하고 비동기식으로 검색되는 데이터에 대해 저렴한 비용의 스토리지 제공
- 즉각적인 액세스가 필요하지 않지만 백업 또는 재해복구 사용 사례와 같이 대규모 데이터 집합을 무료로 검색할 수 있는 유연성이 필요한 아카이브 데이터에 대해 이상적인 스토리지 클래스이다.

### Amazon S3 Glacier Deep Archive

- 최저 비용의 스토리지 제공
- 연 1회 미만으로 액세스되고 비동기식으로 검색되는 수명이 긴 아카이브 데이터에 대해 저렴한 비용의 스토리지를 제공한다.

## 참고 자료

- https://kimjingo.tistory.com/193#toc4

# Amazon Aurora Database

- MySQL 및 PostgreSQL과 호환되는 완전 관리형 관계형 데이터베이스 엔진으로, RDS의 일부이다.
- RDS 기반 유지 관리는 전체적으로 동일하지만, 스토리지에서 큰 차이점을 보인다.
- DB용량이 늘어날수록 Aurora 클러스터 볼륨이 자동 확장되며, 클러스터의 볼륨 크기는 최대 128TiB까지 증가할 수 있다.

## 참고 자료

- [https://support.bespinglobal.com/ko/support/solutions/articles/73000544784--aws-amazon-aurora-와-amazon-rds-의-주요-기능-차이-및-데이터-마이그레이션-방법](https://support.bespinglobal.com/ko/support/solutions/articles/73000544784--aws-amazon-aurora-%EC%99%80-amazon-rds-%EC%9D%98-%EC%A3%BC%EC%9A%94-%EA%B8%B0%EB%8A%A5-%EC%B0%A8%EC%9D%B4-%EB%B0%8F-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%A7%88%EC%9D%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EC%85%98-%EB%B0%A9%EB%B2%95)
- https://notemusic.tistory.com/69

# AWS Secrets Manager

- DB 자격증명, 온프레미스 리소스 자격증명과 같은 중요한 정보를 관리하고 보호하는데 도움이 된다.
- RDS는 Secretes Manager와의 통합을 제공하고, 마스터 데이터베이스 자격 증명을 관리한다.

## 유형

- 데이터베이스 자격 증명
- API 키
- OAuth 토큰
- SSH 키
- TLS/SSL 인증서 및 개인키
- 일반 텍스트 또는 JSON 형식의 기타 민감 정보

## 참고 자료

- https://somaz.tistory.com/183
- https://www.megazone.com/awstechblog_230224/

# AWS System Manager Parameter Store

- 데이터베이스 접속 정보, 외부 API 서비스를 이용하기 위한 비밀 액세스 키를 소스코드보다 안전하게 관리하는 방법

## 참고 자료

- https://dublin-java.tistory.com/66
- [https://velog.io/@el0902/파라미터-스토어-AWS-Systems-Manager-Parameter-Store](https://velog.io/@el0902/%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%8A%A4%ED%86%A0%EC%96%B4-AWS-Systems-Manager-Parameter-Store)

# AWS Parameter Store vs Secrets Manager

- [https://rainbound.tistory.com/entry/AWS-Parameter-Store-와-AWS-Secrets-Manager-공통점과-차이점](https://rainbound.tistory.com/entry/AWS-Parameter-Store-%EC%99%80-AWS-Secrets-Manager-%EA%B3%B5%ED%86%B5%EC%A0%90%EA%B3%BC-%EC%B0%A8%EC%9D%B4%EC%A0%90)

# AWS Key Management Service(AWS KMS)

- 데이터를 암호화할 때 사용되는 암호화 key를 안전하게 관리하는데 목적을 둔 서비스

## Key 관리 서비스 종류

### AWS Managed Key

- AWS 서비스들이 KMS를 통해 Key를 서비스받는 것
- 내부적으로 자동으로 일어나며 사용자가 직접적으로 제어 불가능하다.

### Customer Managed Key (CMK)

- 사용자가 직접 key를 생성하고 관리하는 것
- CMK에 대한 제어는 IAM을 통해 권한을 부여받아 제어 가능하다.

### Custom Key Store

- CloudHSM을 활용한 Key 관리 형태

## 참고 자료

- https://bluese05.tistory.com/71

# ALB - Application Load Balancer

- AWS에서 제공하는 로드 밸런서 중 하나로, OSI 7인 애플리케이션 계층에서 동작하는 로드밸런서이다.
- 트래픽을 균형있게 나누어준다 하여 로드밸런서라고 불린다.

## 기능

- 어플리케이션의 트래픽을 여러 가용 영역으로 분산한다.
- 리스너를 통해 RL, 호스트, 헤더, 메소드 등을 기반으로 요청의 규칙을 구성하여 처리할 수 있다.
- 트래픽 부하에 따라 자동으로 스케일업,스케일 다운을 수행한다.
- 하나 이상 타겟 그룹에 라우팅할 수 있으며 가중치 설정이 가능하다.
- SSL Offloading(SSL Termination)을 지원한다.
- 디폴트 로드밸런싱 알고리즘은 라운드 로빈이며, 최소 미해결 요청 라우팅 알고리즘을 지원한다.
- 교차 영역 로드밸런싱을 통해 Availability Zone의 모든 타켓 그룹에 고르게 트래픽을 분산한다.

## 참고 자료

- https://yainii.tistory.com/47

# Amazon CloudFront

- AWS CDN 서비스
    - CDN이란 클라이언트의 콘텐츠 요청으로 서버에서 받아온 콘텐츠를 캐싱하고, 이후 같은 요청이 왔을 때 그 캐싱해둔 것을 제공하는 서비스이다.
    - 물리적으로 거리가 먼 곳에서도 빠르게 요청을 처리할 수 있고, 서버의 부하를 낮출 수 있다.

## 정적/동적 콘텐츠 처리

![image](https://github.com/user-attachments/assets/3804637a-32ba-4be8-9e6e-1d779fbe0a32)


### 정적 콘텐츠

- 정적 콘텐츠에서는 서버(EC2)가 필요하지 않은 이미지 등이 포함된다.
- 미리 캐싱해둔 뒤, 모든 사용자에게 동일하게 전달해줘도 무방한 데이터에 사용할 수 있다.

### 동적 콘텐츠

- 서버가 필요한 콘텐츠를 의미한다.
    - 서버가 무언가 해줘야하는 데이터
    - DB에서 끌어오는 로그인 자료나 실시간으로 새롭게 추가되는 게시판 등이 있다.
- 이러한 자료들을 정적 캐싱한다면 TTL 시간 동안 사용자는 새롭게 추가/수정된 데이터를 볼 수 없게 된다.

## 참고 자료

- https://bosungtea9416.tistory.com/entry/AWS-CloudFront

# AWS Global Accelerator

![image](https://github.com/user-attachments/assets/73322643-d630-4e3a-8469-6af38c6acc9d)

- AWS의 글로벌 네트워크 인프라를 통해 사용자 트래픽을 전송해 인터넷 사용자의 성능을 최대 60%까지 개선하는 네트워킹 서비스
- **사용자와 가장 가까운 위치의 사용 가능한 정상 엔드포인트로 트래픽을 자동으로 재라우팅한다.**
- 자동 라우팅 최적화 기능은 인터넷이 혼잡할 때 패킷 손실, 지터 및 지연 시간을 일관적으로 낮게 유지한다.

## 참고 자료

- https://velog.io/@khyup0629/AWS-Global-Accelerator
- https://jibinary.tistory.com/227

# EC2 spot instance

- 온디맨드(사용한 만큼 요금을 부과하는 EC2)에 비해 70~90% 정도의 가격으로 EC2 인스턴스를 이용할 수 있게 해주는 기능이다.
- 가격은 수요와 공급에 따라 변화한다.

## 참고 자료

- https://data-engineer-tech.tistory.com/21
- [https://velog.io/@c17an/예약-인스턴스와-스팟-인스턴스로-EC2-비용-절감하기](https://velog.io/@c17an/%EC%98%88%EC%95%BD-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%EC%99%80-%EC%8A%A4%ED%8C%9F-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%EB%A1%9C-EC2-%EB%B9%84%EC%9A%A9-%EC%A0%88%EA%B0%90%ED%95%98%EA%B8%B0)

# Amazon GuardDuty

- **여러가지 로그를 감시하고 기계학습으로 위협을 검출한다.**
- 유저의 조작이나 통신 등의 로그를 지속적으로 모니터링해서 수상한 서버와의 통신, 부정 액세스 등 악의적인 동작을 기계 학습을 가지고 검출한다.

## 참고 자료

- https://blog.naver.com/classmethodkr/223087629888
- https://dev.classmethod.jp/articles/amazon-guardduty-explained-korean/

# AWS VPC Traffic Mirroring

- ENI 유형의 네트워크 패킷을 복사하는데 사용할 수 있는 VPC의 기능 중 하나이다.
- EC2 패킷을 NLB 또는 다른 EC2에 미러링해 와이어샤크 등의 도구로 패킷을 분석하고 모니터링할 수 있다.

## 참고 자료

- https://h-susu.tistory.com/8
- https://chan-it-note.tistory.com/140

# AWS Network Firewall

- 외부 액세스 포인트와 사용자 퍼블릭 서브넷 사이에 위치
- 상태 저장 및 상태 비저장 규칙 그룹을 통해 트래픽을 필터링/검사하는 서비스
- 오픈소스 IPS인 Suricata를 기반으로 구성되었다.
- 인터넷 게이트웨이를 통해 들어오고 나가는 트래픽을 필터링해 인스턴스를 보호한다.

## 참고 자료

- https://engmisankim.tistory.com/47
- https://minjoos.tistory.com/9

# Firewall Manager

- 여러 AWS 계정과 리전에서 방화벽 규칙을 중앙에서 관리할 수 있도록 하는 보안 서비스
- 실제 트래픽 차단이나 필터링과 같은 구체적인 방어 기능은 다른 서비스에서 수행한다.

## 참고 자료

- https://jibinary.tistory.com/394

# Amazon QuickSight

- 특정 데이터에 대한 시각화 대시보드를 생성하고 다른 사용자와 공유할 수 있다.

## 참고 자료

- https://velog.io/@parkksss/Amazon-QuickSight

# AWS Athena

- 표준 SQL을 사용해 S3에 저장된 데이터를 간편하게 분석할 수 있는 대화식 쿼리 서비스
- 서버리스이기 때문에 관리할 인프라가 없고, 실행한 쿼리에 대해서만 비용을 지불하면 된다.

## 참고 자료

- https://btcd.tistory.com/341

# AWS IAM

- https://somaz.tistory.com/181

# S3 Event Notification

- 객체의 생성, 삭제, 복원, 복제 등의 모든 이벤트 알림을 만들어 다른 AWS 수신 서비스로 보낼 수 있다.

## 참고 자료

- https://gngsn.tistory.com/245

# Inspection VPC

- Network Firewall **중앙 집중형 배포 모델은 검사를 수행하는 firewall이 한 곳(중앙)에 있다는 의미이다.**
- 따라서 검사를 수행하기 위한 **검사 전용 VPC**가 따로 존재한다.
    - 이 VPC를 Inspection VPC라고 부른다.
- Inspection VPC는 Firewall endpoint가 있는 검사 전용 VPC이다.
- Inspection VPC는 **Transit Gateway Subnet**과 **Firewall subnet**으로 구성된다.
    - Transit Gateway Subnet은 외부에서 Inspection VPC로 들어오는 트래픽을 Firewall endpoint로 연결해주는 역할을 한다.
    - 또한 Firewall에서 검사를 받고 나가는 트래픽이 Transit Gateway로 다시 전송되어 외부와 연결된다.
    - Transit Gateway는 네트워크 허브 역할을 한다.

## 참고 자료

- https://minjoos.tistory.com/12

# Gateway Load Balancer

- 방화벽, 침입 탐지 및 방지 시스템, 심층 패킷 검사 시스템과 같은 가상 어플라이언스를 배포, 확장 및 관리할 수 있다.
- Gateway Load Balancer는 OSI 3번째 레이어인 네트워크 계층에서 동작한다.
- 온프레미스에서 사용되는 네트워크 장비 혹은 보안 장비 등의 OS Image를 AWS EC2에 올려 장비의 고유 기능을 AWS에서 활용할 수 있다.
    - 즉, AWS에 3rd party Solution을 생성해 활용하는 것을 의미한다.
- 모든 포트에서 모든 IP 패킷을 수신하고, 수신자 규칙에 지정된 대상 그룹으로 트래픽을 전달한다.
- 3rd party solution에 부하 분산과 헬스체크, 확장을 제공하기 위해 만든 로드밸런서

## 참고 자료

- [https://support.bespinglobal.com/ko/support/solutions/articles/73000544791--aws-aws-gateway-load-balancer-gwlb-의-작동-방식-및-구성-방법](https://support.bespinglobal.com/ko/support/solutions/articles/73000544791--aws-aws-gateway-load-balancer-gwlb-%EC%9D%98-%EC%9E%91%EB%8F%99-%EB%B0%A9%EC%8B%9D-%EB%B0%8F-%EA%B5%AC%EC%84%B1-%EB%B0%A9%EB%B2%95)
- https://aws-hyoh.tistory.com/216

# EBS Snapshot

- EBS를 저장하는 효율적인 방법
- 특정 시간에 EBS 볼륨 상태의 저장본을 의미한다.
- EBS 데이터 저장 상태에 대해 백업본을 찍어둔 개념으로 이해하면 된다.
- 그래서 필요 시 스냅샷을 통해 특정 시간의 저장 데이터에 대한 EBS 복구가 가능하다.

## 참고 자료

- [https://inpa.tistory.com/entry/AWS-📚-AMI-Snapshot-개념-백업-사용법-💯-정리](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-AMI-Snapshot-%EA%B0%9C%EB%85%90-%EB%B0%B1%EC%97%85-%EC%82%AC%EC%9A%A9%EB%B2%95-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)

# EBS Multi-Attach

- EBS 볼륨에 새로운 다중 연결 옵션을 구성하면 특정 볼륨을 여러 대의 EC2에 연결할 수 있다.
- 각 EBS 볼륨은 Multi-Attach 설정 시 해당 볼륨이 위치한 가용영역에서 최대 16개의 EC2에 연결할 수 있게 된다.

## 참고 자료

- https://library.gabia.com/contents/tech/8848/

# Instance Store 볼륨

- EBS 볼륨과 달리, 인스턴스 스토어 볼륨은 비지속성 스토리지이며, 인스턴스를 종료시키면 인스턴스 스토어에 저장된 데이터가 손실된다.
- 인스턴스 스토어 볼륨은 인스턴스 서버 호스팅 물리적으로 부착되는 SSD 저장장치이다.
- 단기적인 목적으로 인스턴스를 시작하는 배포 모델에 적합하며, 외부에서 데이터를 임포트해서 사용하므로 내부에 저장된 데이터는 삭제돼도 무방하다.

## 참고 자료

- https://kimjingo.tistory.com/185
- https://jibinary.tistory.com/150

# S3 Tier (스토리지 클래스)

## S3 Standard-Infrequent Access (S3 Stantard-IA)

- 자주 접근되지는 않으나 접근 시 빠른 접근이 요구되는 파일이 많을 시 사용한다.
- 일반 S3에 비해 비용은 저렴하지만 데이터를 불러올 때마다 추가 비용이 발생한다.

## S3 One Zone-Infrequent Access (S3 One Zone-IA)

- 기본적으로 IA와 같지만 하나의 AZ에만 데이터를 저장하는 클래스이다.
- 덜 중요하고 자주 사용되지 않는 데이터를 저장하는데 적합하다.

## S3 Intelligent-Tiering (지능형 계층화)

- 머신러닝을 통해서 자동으로 파일의 티어(클래스)를 변경하는 서비스
- 예를 들어 최근에 파일을 사람들이 자주 접근하면 스탠다드에 옮기고, 접근 빈도가 낮으면 IA로 옮기고, 다시 많이 찾으면 스탠다드에 옮기는 형식이다.
- 퍼포먼스 손해 오버헤드도 없으면서 관리비도 많이 들지 않는다.

## 참고 자료

- [https://inpa.tistory.com/entry/AWS-📚-S3-티어스토리지-클래스-수명주기-관리하기](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-S3-%ED%8B%B0%EC%96%B4%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80-%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%88%98%EB%AA%85%EC%A3%BC%EA%B8%B0-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0)

# Cost Explorer

- 시간에 따른 AWS 비용 및 사용량의 시각화, 이해 및 관리
- 시간에 따른 AWS 비용과 사용량을 시각화, 이해 및 관리할 수 있는 손쉬운 인터페이스를 제공한다.
- 최대 12개월 이전의 데이터를 확인
- qhrhtj

## 참고 자료

- https://aws.amazon.com/ko/aws-cost-management/aws-cost-explorer/
- https://brunch.co.kr/@topasvga/3615

# AWS Cost and Usage Reports

- 시간 단위로 AWS에서 사용하는 모든 리소스에 대한 비용 및 사용량 데이터
- 매월 조직 규모에 따라 수백만에서 수십억개의 데이터로 표현된다.

## 참고 자료

- https://tech.kakaopay.com/post/cloud-cost-visualization/

- **예산을 관리하고 초과 방지를 원한다면 → AWS Budgets**
- **비용 분석 및 최적화를 원한다면 → AWS Cost Explorer**
- **청구서 및 결제 관리를 원한다면 → AWS Billing Dashboard**
- **정교한 비용 분석이 필요하다면 → AWS Cost and Usage Reports (CUR)**

# Amazon DynamoDB Accelerator(DAX)

- DynamoDB를 위한 가용성이 뛰어난 완전관리형 인메모리 캐시로서, 초당 요청수가 몇백만개인 경우에도 몇 밀리초에서 몇 마이크로초까지 최대 10배의 성능을 제공한다.
- 개발자가 캐시 무효화, 클러스터 관리 또는 데이터 집단을 관리할 필요 없이 DAX가 DynamoDB 테이블에 인메모리 가속화를 추가하는데 필요한 모든 작업을 수행한다.

## 참고 자료

- https://mattmk.tistory.com/14

# AWS Trusted Advisor

- 사용중인 AWS 계정의 리소스를 분석하고 개선할 수 있는 사항을 제안해주는 서비스
- 비용 최적화, 보안, 서비스 제한, 성능, 장애조치 등의 조언을 준다.

## 참고 자료

- https://jibinary.tistory.com/132
- https://sh-t.tistory.com/119

# Amazon Inspector

- 소프트웨어 취약성과 의도하지 않은 네트워크 노출이 있는지 검사한다.
- 소프트웨어 취약점이나 네트워크 문제가 발견되면 Amazon Inspector에서 검색 결과를 생성해준다.
- Inspector는 [Amazon EC2 인스턴스](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html), [Amazon ECR의 컨테이너 이미지](https://docs.aws.amazon.com/AmazonECR/latest/userguide/what-is-ecr.html) 및 [Lambda 함수](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)를 검색하고 스캔한다.

## 참고 자료

- https://jflip.tistory.com/67
- https://docs.aws.amazon.com/ko_kr/inspector/latest/user/what-is-inspector.html

# AWS Config

- AWS 리소스의 설정을 관리하고 기록 및 평가하는 서비스
- 보안에 관련된 설정을 제대로 지키고 있는지 모니터링 해주는 서비스
- AWS Config를 활성화하면 아래와 같은 다양한 AWS 리소스의 설정 상태를 감사(audit)할 수 있다.
    - Security Group의 설정이 변경되었을 때
    - 새로운 S3 버킷이 생성되었을 때
    - S3의 버전 관리(versioning)가 활성화되어 있는지 확인
    - S3 버킷에 대해 public으로 쓰기 액세스가 허용되지 않았는지 확인

## 참고 자료

- https://velog.io/@rjsgml126/config

# CloudWatch

- AWS 리소스와 AWS에서 실시간으로 실행중인 애플리케이션을 모니터링하는 서비스
- 지표를 감시해 알림을 보내거나 임계값을 위반한 경우, 모니터링 중인 리소스를 자동으로 변경하는 경보를 생성할 수 있다.
    - 예를 들어, 경보는 인스턴스 중지, 오토 스케일링 및 SNS 작업 시작, 종료 등으로 구성할 수 있다.

## 참고 자료

- https://nearhome.tistory.com/134

# AWS Single Sign-On (SSO)

- 1회 사용자 인증으로 다수의 애플리케이션 및 웹사이트에 대한 사용자 로그인을 허용하는 인증 솔루션
- AWS에서 제공하는 완전관리형의 단일 로그인 서비스로, 사용자가 여러 AWS 계정 및 비즈니스 애플리케이션에 대해 단일 로그인으로 액세스할 수 있도록 지원한다.
- 간편한 사용자 관리, 보안 강화, 인증의 중앙화를 통해 AWS 리소스 및 외부 애플리케이션에 대한 액세스를 효과적으로 관리한다.
- 사용자 애플리케이션이 아니라 AWS 계정을 이걸로 관리함

## 참고 자료

- https://aws.amazon.com/ko/what-is/sso/
- [https://velog.io/@leesh0567/AWS-Single-Sign-OnAWS-SSO-이란](https://velog.io/@leesh0567/AWS-Single-Sign-OnAWS-SSO-%EC%9D%B4%EB%9E%80)
- https://www.smileshark.kr/post/hidden-holes-in-iam-account-management-enhancing-account-security-with-aws-sso

# AWS Directory Service

- AWS 환경에서 AD(Active Directory)를 사용하기 위한 서비스이다.

## AD (Active Directory)

- 마이크로소프트가 개발한 서비스로, 주로 기업이나 조직에서 사용된다.
- 회사 직원들의 컴퓨터 계정 정보를 관리하는 데이터베이스와 같다.

## AD의 구조

- https://blog.naver.com/ddor77/60031485575

| 옵션 | 설명 | 장점 | 단점 | 적합성 |
| --- | --- | --- | --- | --- |
| **A. One-Way Trust** | 온프레미스 AD → AWS | 간단한 설정 | AWS에서 온프레미스 AD 자원 접근 불가 | ❌ |
| **B. Two-Way Trust (정답)** | 양방향 신뢰 | 완전한 AD 통합, AWS SSO 연동 | 설정 복잡성 증가 | ✅ |
| **C. AWS Directory Service만 사용** | AWS 내 AD 구축 | 간편한 설정 | 온프레미스 AD 연동 불가 | ❌ |
| **D. 온프레미스 IdP 배포** | 자체 인증 시스템 구축 | 유연한 통합 가능 | 관리 오버헤드 및 운영 비용 | ❌ |


## 참고 자료

- https://jibinary.tistory.com/185
- https://ossian.tistory.com/48

CloudFront는 Edge Locations를 사용하여 콘텐츠를 캐시하는 반면 Global Accelerator는 Edge Locations를 사용하여 가장 가까운 지역 엔드포인트로 가는 최적의 경로를 찾습니다. CloudFront는 HTTP 프로토콜을 처리하도록 설계된 반면 Global Accelerator는 HTTP와 TCP 및 UDP와 같은 비 HTTP 프로토콜 모두에 가장 잘 사용됩니다. 그래서 A가 더 나은 답이라고 생각합니다.

# AWS Fargate

- 별도로 인스턴스를 생성/관리하지 않고 완전한 매니지드 서비스의 형태로 도커 컨테이너를 실행시킬 수 있는 아마존의 서버리스 컨테이너 상품
- 단독으로 사용할 수 없으며, ECS나 EKS와 같은 컨테이너 오케스트레이션 서비스와 결합해 사용한다.

## 참고 자료

- https://jsonobject.tistory.com/536
- https://www.smileshark.kr/post/aws-container-service-ecs-eks-fargate-comparison
- https://m.blog.naver.com/classmethodkr/222782686010

# Kinesis Data Firehose

- 데이터를 이동시키는 서비스
- 운영 환경에서 수많은 데이터를 회사는 지연 시간을 최소화하며 저장해야 한다.
- S3에 데이터를 그냥 연결해서 보내는 것은 많은 리소스를 사용할 뿐 아니라 보안에도 취약하다.
- 미리 정의된 목적지에 데이터를 안전하게 전달하는 것이다.
- 람다를 이용해 가공하는 작업도 가능하다.

## 참고 자료

- [https://velog.io/@rlarudgns970/AWS-Kinesis-Data-Firehose란](https://velog.io/@rlarudgns970/AWS-Kinesis-Data-Firehose%EB%9E%80)
- https://jaeyeong951.medium.com/aws-kinesis-data-stream-vs-data-firehose-10102d949741

# Kinesis Data Stream

- 실시간으로 데이터를 받아들일 수 있는 입구이자 저장소
- 한 시스템이 실시간으로 데이터 스트림에 데이터를 전송하면, 해당 데이터 스트림을 listening하고 있던 다른 한 시스템이 해당 데이터를 받아서 처리한다.

## 참고 자료

- https://jaeyeong951.medium.com/aws-kinesis-data-stream-vs-data-firehose-10102d949741

# Elastic Load Balancer (ELB)

- Amazon EC2 인스턴스, 컨테이너 및 IP 주소와 같은 여러 대상에 대해 수신 애플리케이션 또는 네트워크 트래픽을 여러 가용 영역에 배포한다.
- 단순 부하 분산을 넘어 HTTP Header를 조작하여 전달 대상을 정하거나 고정 페이지를 반환하며, ACM의 SSL 인증서를 탑재해 EC2 부하를 줄이고, WAF를 앞에 내세워 보안 기능을 강화하거나 하는 등 다양한 기능을 할 수 있다.
- ELB의 종류로는 ALB, NLB, GLB, CLB가 있다

## 참고 자료

- https://aws-hyoh.tistory.com/128
- https://incheol-jung.gitbook.io/docs/q-and-a/infra/alb-nlb-elb

# AWS shield, shield Advanced

- 네트워크 및 전송 계층(3계층 및 4계층)과 애플리케이션 계층(7계층)에서 AWS 리소스에 대한 분산 서비스 거부 공격(DDoS) 으로부터 보호한다.
- AWS Shield은(는) 알려진 다양한 DDoS 공격 벡터와 제로데이 공격 벡터로부터 보호합니다. Shield 탐지 및 완화 기능은 탐지 당시 서비스에 해당 위협이 명시적으로 알려지지 않았더라도 위협에 대한 적용 범위를 제공하도록 설계되었습니다.
- Shield Standard는 AWS 사용 시 추가 비용 없이 자동으로 제공됩니다. 공격으로부터 더 높은 수준의 보호를 위해 AWS Shield Advanced을(를) 구독할 수 있습니다.

## 참고 자료

- https://docs.aws.amazon.com/ko_kr/waf/latest/developerguide/ddos-overview.html

# SSE-S3, SSE-KMS

> S3 객체 암호화 기능
> 
- 서버측 S3 암호화 방식이다.

## SSE-S3

- AWS 회사 자체에서 관리되는 key를 이용해 암호화

## SSE-KMS

- KMS를 이용해 암호화

## 참고 자료

- [https://inpa.tistory.com/entry/AWS-📚-S3-객체-암호화-기능-종류-및-사용하기](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-S3-%EA%B0%9D%EC%B2%B4-%EC%95%94%ED%98%B8%ED%99%94-%EA%B8%B0%EB%8A%A5-%EC%A2%85%EB%A5%98-%EB%B0%8F-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)

# AWS Well-Architected Framework

- https://wa.aws.amazon.com/index.ko.html

# AWS Systems Manager Session Manager

- **IAM 정책을 사용하여 관리형 노드에 대한 중앙 집중식 액세스 제어**
    
    관리자가 한 곳에서 관리형 노드에 대한 액세스 권한을 부여하고 취소할 수 있습니다. AWS Identity and Access Management(IAM) 정책만 사용하는 경우에는 Session Manager를 사용할 수 있는 조직 내 개별 사용자 또는 그룹과 이들이 액세스할 수 있는 관리형 노드를 제어할 수 있습니다.
    
- **인바운드 포트를 열 필요가 없고 Bastion Host 또는 SSH 키를 관리할 필요가 없음**
    
    관리형 노드에 인바운드 PowerShell 포트와 원격 PowerShell 포트를 열어 두면 관리형 노드에서 개체가 권한이 없거나 악의적인 명령을 실행할 위험이 매우 높아집니다. Session Manager에서는 이러한 인바운드 포트를 닫도록 하고, SSH 키 및 인증서, Bastion Host 및 점프박스를 관리할 필요가 없도록 해 보안 태세를 강화하도록 합니다.
    
- **클릭 한 번으로 콘솔 및 CLI에서 관리형 노드에 액세스**
    
    AWS Systems Manager 콘솔 또는 Amazon EC2 콘솔을 사용하여 한 번의 클릭으로 세션을 시작할 수 있습니다. AWS CLI를 사용하여 단일 명령 또는 일련의 명령을 실행하는 세션을 시작할 수도 있습니다. 관리형 노드에 대한 권한이 SSH 키 또는 기타 메커니즘을 대신 IAM 정책을 통해 제공되기 때문에 연결 시간이 크게 줄어듭니다.
    
- [**하이브리드 및 멀티클라우드](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/operating-systems-and-machine-types.html#supported-machine-types) 환경의 Amazon EC2 인스턴스와 비 EC2 관리형 노드에 모두 연결**
    
    [하이브리드 및 멀티클라우드](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/operating-systems-and-machine-types.html#supported-machine-types) 환경의 Amazon Elastic Compute Cloud(Amazon EC2) 인스턴스와 비 EC2 관리형 노드에 모두 연결할 수 있습니다.
    
    Session Manager를 사용하여 비EC2 노드에 연결하려면 먼저 고급 인스턴스 티어를 활성화해야 합니다. **고급 인스턴스 티어를 사용하는 데는 요금이 부과됩니다.** 그러나 Session Manager를 사용하여 EC2 인스턴스에 연결하는 데는 추가 요금이 부과되지 않습니다. 자세한 내용은 [인스턴스 티어 구성](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/fleet-manager-configure-instance-tiers.html)을 참조하세요.
    
- **포트 전달**
    
    원격 관리형 노드 내부의 포트를 클라이언트의 로컬 포트로 리디렉션합니다. 그런 다음 로컬 포트에 연결하고 노드 내부에서 실행 중인 서버 애플리케이션에 액세스합니다.
    
- **Windows, Linux 및 macOS에 대한 크로스 플랫폼 지원**
    
    Session Manager에서는 단일 도구의 Windows, Linux 및 macOS에 대한 지원을 제공합니다. 예를 들면, Windows Server 관리형 노드의 Linux 및 macOS 관리형 노드 또는 RDP 연결에 SSH 클라이언트를 사용할 필요가 없습니다.
    
- **세션 활동 로그**
    
    조직의 작업 또는 보안 요구 사항을 충족하기 위해 관리형 노드에 대한 연결과 해당 인스턴스에서 실행된 명령에 대한 기록을 제공해야 할 수 있습니다. 또한 조직의 사용자가 세션 활동을 시작 또는 종료할 때 알림을 받을 수도 있습니다.
    
    로깅 기능은 다음 AWS 서비스와의 통합을 통해 제공됩니다.
    
    - **AWS CloudTrail** - AWS CloudTrail에서는 AWS 계정에서 수행된 Session Manager API 호출에 대한 정보를 캡처해 지정한 Amazon Simple Storage Service(Amazon S3) 버킷에 저장되는 로그 파일에 기록합니다. 계정에 대한 모든 CloudTrail 로그를 저장하는 데 버킷 하나가 사용됩니다. 자세한 내용은 [AWS CloudTrail을 사용하여 AWS Systems Manager API 호출 로깅](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/monitoring-cloudtrail-logs.html) 단원을 참조하십시오.
    - **Amazon Simple Storage Service** - 디버깅 및 문제 해결을 위해 선택한 Amazon S3 버킷에 세션 로그 데이터를 저장하도록 선택할 수 있습니다. 로그 데이터는 AWS KMS key를 사용하여 암호화를 적용하거나 적용하지 않은 상태로 Amazon S3 버킷으로 전송할 수 있습니다. 자세한 내용은 [Amazon S3를 사용하여 세션 데이터 로깅(콘솔)](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/session-manager-logging-s3.html) 단원을 참조하십시오.
    - **Amazon CloudWatch Logs** - CloudWatch Logs를 사용하면 다양한 AWS 서비스의 로그 파일을 모니터링, 저장 및 액세스할 수 있습니다. 디버깅 및 문제 해결을 위해 CloudWatch Logs 로그 그룹으로 세션 로그 데이터를 전송할 수 있습니다. 로그 데이터는 KMS 키를 사용하여 AWS KMS 암호화를 적용하거나 적용하지 않은 상태로 로그 그룹으로 스트리밍할 수 있습니다. 자세한 내용은 [Amazon CloudWatch Logs를 사용하여 세션 데이터 로깅(콘솔)](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/session-manager-logging-cloudwatch-logs.html) 단원을 참조하십시오.
    - **Amazon EventBridge** 및 **Amazon Simple Notification Service** - EventBridge를 사용하면 지정한 AWS 리소스에 변경 사항이 발생할 때 이를 감지하는 규칙을 설정할 수 있습니다. 조직 내 사용자가 세션을 시작 또는 중지하면 이를 감지하는 규칙을 생성하면 Amazon SNS를 통해 해당 이벤트에 대한 알림(예: 문자 메시지 또는 이메일 메시지)을 받을 수 있습니다. 또한 다른 응답을 시작하도록 CloudWatch 이벤트를 구성할 수도 있습니다. 자세한 내용은 [Amazon EventBridge를 사용하여 세션 활동 모니터링(콘솔)](https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/session-manager-auditing.html#session-manager-auditing-eventbridge-events) 단원을 참조하십시오.

## 참고 자료

- https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/session-manager.html
- [https://tech.cloudmt.co.kr/2022/09/29/aws-systems-manager의-session-manager를-이용하여-프라이빗-환경의-서버-접근통제-구현/](https://tech.cloudmt.co.kr/2022/09/29/aws-systems-manager%EC%9D%98-session-manager%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%98%EC%97%AC-%ED%94%84%EB%9D%BC%EC%9D%B4%EB%B9%97-%ED%99%98%EA%B2%BD%EC%9D%98-%EC%84%9C%EB%B2%84-%EC%A0%91%EA%B7%BC%ED%86%B5%EC%A0%9C-%EA%B5%AC%ED%98%84/)

# Site-to-Site VPN

![image](https://github.com/user-attachments/assets/c72d7e9b-1a68-49b0-991d-a958b5a43608)


- IPSec 암호화 프로토콜을 사용해 클라우드 환경과 온프레미스 환경을 연결해주는 서비스

## 참고 자료

- [https://bosungtea9416.tistory.com/entry/AWS-Site-to-Site-VPN-구성하기](https://bosungtea9416.tistory.com/entry/AWS-Site-to-Site-VPN-%EA%B5%AC%EC%84%B1%ED%95%98%EA%B8%B0)
- https://blog.bespinglobal.com/post/aws-site-to-site-vpn-with-openswam/

# Direct Connect vs Site-to-Site VPN

https://dev.classmethod.jp/articles/what-is-differnce-aws-dx-ans-vpn-kr/

# Amazon Appflow

- 다양한 형태의 서비스에서 수집한 데이터를 AWS 환경에 담아 가공하기 위한 솔루션
- SaaS 애플리케이션과 S3, RedShift와 같은 서비스 간에 데이터를 안전하게 전송할 수 있는 서비스

## 참고 자료

- https://kinggrmoon.tistory.com/56

# VPC Endpoint

- VPC와 AWS 서비스 사이의 통신을 비공개로 연결할 수 있도록 도와주는 서비스
- Public IP 주소가 필요하지 않다.
- VPC와 기타 서비스 간의 트래픽은 AWS 네트워크를 벗어나지 않는다.
- VPC Endpoint가 없다면 EC2 인스턴스에서 S3로 액세스 할 때, EC2는 NAT와 Internet Gateway를 통해 외부로 나가 S3에 접속한다.

## 참고 자료

- https://bosungtea9416.tistory.com/entry/AWS-VPC-Endpoint-Gateway-Endpoint-Interface-Endpoint

# AWS Management Console

- AWS 클라우드 리소스와 서비스를 관리하기 위한 웹 화면
- 로그인했을 때 맨 처음 뜨는 화면 생각하면 된다.

## 참고 자료

- https://na-um.tistory.com/18

# AWS VPN

- 온프레미스, 원격 사무실 및 AWS 네트워크 사이에서 보안 연결을 설정한다.
- AWS VPN은 AWS site-to-site VPN 및 AWS Client VPN이라는 두 가지 서비스로 구성된다.

## 참고 자료

- https://btcd.tistory.com/46

# S3 MFA Delete

- AWS S3 버킷에서 수행하는 중요한 작업을 추가적으로 보호하는 기능이다.
- MFA는 사용자가 코드를 입력하는 방식을 통해 본인 인증을 추가적으로 요구하는 보안 메커니즘이다.
- 중요 작업 수행 전 코드를 입력해야한다.

## 참고 자료

- https://velog.io/@gun_123/Amazon-S3-Security-S3-MFA-Delete

# Amazon Macie

- S3 버킷에서 데이터를 검색할 때 사용하는 기능
- 기계학습 및 패턴 정규식 일치를 사용해 개인정보나 민감한 데이터를 검색, 모니터링, 보호하는 서비스
    - 민감한 개인정보나 데이터 식별 가능
- 버킷과 객체에 대한 메타데이터 주기적으로 자동 검색
- 버킷 상태 시각화

## 참고 자료

- https://sh-t.tistory.com/113
- [https://www.hakawati.co.kr/entry/Amazon-Macie-12-구축편](https://www.hakawati.co.kr/entry/Amazon-Macie-12-%EA%B5%AC%EC%B6%95%ED%8E%B8)

# AWS Systems Manager Patch Manager

Systems Manager(SSM)은 여러 AWS 리소스를 그룹화하여 그룹 내 리소스의 운영 데이터를 일원화하고 운영 작업을 자동화할 수 있는 운영 관리 서비스이다.

Systems Manager는 역할별로 여러 기능으로 구성되어 있다.

1. **Patch Manager** OS 패치 적용을 자동화하는 기능
2. **Session Manager** 관리 콘솔에서 EC2 인스턴스로 안전하게 로그인할 수 있는 기능

## Patch Manager

- OS 패치 정보를 스캔해 업데이트하고 패치 자동화

## 참고 자료

- https://jibinary.tistory.com/371

# S3 Object Lock

- 객체에 대해 업데이트 와 삭제를 못하게 방지

## 참고 자료

- https://jibinary.tistory.com/354

# Amazon Rekognition

- 기계학습을 통해 이미지 인식 및 비디오 분석 자동화

## 참고 자료

- https://aws.amazon.com/ko/rekognition/

# Amazon Comprehend

- 기계 학습을 활용해 문서 내의 텍스트에서 유용한 인사이트를 도출하고 이해

## 참고 자료

- https://aws.amazon.com/ko/comprehend/

# Amazon SageMaker

- 머신러닝 클라우드 플랫폼
- 모든 개발자 및 Data Scientist들이 **ML**(Machine Learning) 모델을 빠르게 구축, 훈련 및 배포할 수 있도록 하는 **모듈식**의 **완전 관리형** 서비스

## 참고 자료

- https://labs.brandi.co.kr/2018/05/17/ohyj.html
- https://velog.io/@bbkyoo/SageMaker
