# AWS EFS (Amazon Elastic File System)

- AWS 클라우드 서비스와 온프레미스 리소스에서 사용할 수 있는 간단하고 확장 가능하며 탄력적인 파일 스토리지를 제공하는 서비스
- 여러 서버가 있고, 각 서버끼리 동일한 파일을 공유해야 할 경우 사용한다.
- 대량의 동시 접속을 지원한다.
- 리눅스 인스턴스를 위한 확장성, 공유성이 높은 파일 스토리지로, EC2 Linux 인스턴스에 마운트된 NFS를 통해 VPC에서 필요한 파일에 접근하거나 AWS Direct Connect로 연결된 온프레미스 서버의 파일에 접근 가능하다.
- 따라서 수천대의 EC2 인스턴스간 파일 시스템 공유가 가능하며, 병렬 접근이 가능하도록 설계되어 있어, 두 개 이상의 EC2로부터 하나의 공유된 스토리지 공간이 필요할 때 EFS를 채택한다.
- 다수의 인스턴스에서 파일에 접근할 수 있는 전송 지연 문제가 적으며, 안전하고 내구성 높은 네트워크 파일 스토리지 서비스라고 할 수 있다.

## 참고 자료

- [https://inpa.tistory.com/entry/AWS-📚-EFS-개념-원리-사용-세팅-💯-정리](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-EFS-%EA%B0%9C%EB%85%90-%EC%9B%90%EB%A6%AC-%EC%82%AC%EC%9A%A9-%EC%84%B8%ED%8C%85-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC)
- https://jibinary.tistory.com/67
