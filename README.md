
## Project1 - 서로 다른 Subnet 간 서버 접근
- **목표**: Public Subnet에 위치한 점프 호스트(MobaXterm)를 통해 외부 연결이 차단된 Private Subnet 내 서버에 안전하게 접근하는 환경 구축

##해결 방법
1. **네트워크 격리**: 외부 인터넷과 단절된 Private Subnet에 floating IP를 부여하지 않은 instance 생성
2. **점프 호스트 활용**: Public Subnet의 서버에만 Floating IP를 부여하여 외부 진입점으로 설정
3. **SSH Tunneling/Routing**: 내부 라우팅 설정을 통해 Public -> Private Subnet 간의 SSH(Port 22) 통신 허용

##실습<br>
<img width="400" height="150" alt="private에 접근" src="https://github.com/user-attachments/assets/522b015c-c571-473e-98b7-47811615ff79" />

-

-   Public 서버에서 `ssh` 명령어로 Private 서버(10.0.2.x)에 접속 성공한 터미널 화면
- **[파일: 실습2 - 14p]**: 인스턴스 리스트에서 Floating IP가 하나만 할당된 전체 현황 화면
