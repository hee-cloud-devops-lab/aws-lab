- 분산 어플리케이션 추적 도구
- **개발자를 위한 일종의 애플리케이션 분석 및 디버깅 서비스**로, 애플리케이션의 구성을 **시각화한 맵으로 표현**해주는 서비스
- 애플리케이션에 전송된 요청을 추적하고, 서비스 맵을 생성한다.
- 전송된 요청에 대한 응답을 분석해 오류를 자동으로 출력한다.
- 애플리케이션에서 생기는 에러를 추적하는 서비스이며, AWS 환경에서 어느 리소스가 문제의 원인인지 추적할 수 있다.
  
![image](https://github.com/user-attachments/assets/04b12781-0b4e-429d-a2b7-a53e4e68911f)

![image](https://github.com/user-attachments/assets/16595553-fa26-4bc5-9b66-e20ae772479f)


## X-Ray SDK

- 애플리케이션에서 X-Ray 서비스를 사용해 세그먼트 데이터를 작성하고 X-Ray Daemon에 전송하기 위한 클래스와 메소드를 제공한다.

## X-Ray Daemon

- 애플리케이션에서 데이터를 수집해 버퍼링 후에 X-Ray API에 정기적으로 전송하는 역할의 소프트웨어이다.
- 백그라운드 프로세스로써 유저는 따로 직접 관리하지 않는다.

## 참고 자료

- [https://medium.com/@zeroweb.tech/aws-x-ray-적용기-4e1c270c62fa](https://medium.com/@zeroweb.tech/aws-x-ray-%EC%A0%81%EC%9A%A9%EA%B8%B0-4e1c270c62fa)
- https://waspro.tistory.com/661
- https://isc9511.tistory.com/159
- https://jibinary.tistory.com/334#google_vignette
