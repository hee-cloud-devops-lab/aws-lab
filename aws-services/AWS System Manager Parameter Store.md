# AWS System Manager Parameter store

- 외부에 노출되면 안되는 값들을 관리하는 서비스
    - 다양한 AWS 서비스에서 공통적으로 해당 값을 참조할 수 있다.
- 구성 데이터 관리 및 암호 관리를 위한 안전한 계층적 스토리지를 제공한다.

## Parameter

- 텍스트 블록, 이름 목록, 암호, 라이선스 키 같이 파라미터 스토어에 저장되는 모든 데이터

### 유형

- String: 일반적인 문자열
- StringList: 쉼표로 구분된 값 목록
- SecureString: 안전한 방식으로 저장되고 참조되어야 하는 모든 민감한 데이터

## 참고 자료

- https://dublin-java.tistory.com/66
- [https://velog.io/@el0902/파라미터-스토어-AWS-Systems-Manager-Parameter-Store](https://velog.io/@el0902/%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%8A%A4%ED%86%A0%EC%96%B4-AWS-Systems-Manager-Parameter-Store)
