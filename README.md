
## Project1 - 서로 다른 Subnet 간 서버 접근

  <img width="500" height="300" alt="서로다른subnet1" src="https://github.com/user-attachments/assets/4829f415-382d-47da-a90e-1796bcba4b71" />
  <br>- **목표**: Public Subnet에 위치한 점프 호스트(MobaXterm)를 통해 외부 연결이 차단된 Private Subnet 내 서버에 안전하게 접근하는 환경 구축<br>
<br><br>


@해결 방법
1. **네트워크 격리**: 외부 인터넷과 단절된 Private Subnet에 floating IP를 부여하지 않은 instance 생성
2. **점프 호스트 활용**: Public Subnet의 서버에만 Floating IP를 부여하여 외부 진입점으로 설정
3. **SSH Tunneling/Routing**: 내부 라우팅 설정을 통해 Public -> Private Subnet 간의 SSH(Port 22) 통신 허용
<br>
@실행<br>
 (1) 전체 인스턴스 목록<br><br>
<img width="500" height="250" alt="1" src="https://github.com/user-attachments/assets/b8eda718-ec24-4e5f-a335-b6dfc79c28b7" /><br>
 - 인프라 구성: 외부 접속용 Bastion 서버와 내부망 전용 서버 분리 <br><br><br>

 (2) Private 서버의 보안 그룹 설정<br><br>
<img width="500" height="250" alt="2" src="https://github.com/user-attachments/assets/2bca64e4-ef63-44ab-858d-6220b8bb636b" />
 - 전체 허용(0.0.0.0/0)이 아니라 지정된 통로(10.0.1.0/24)로만 들어오게 설정<br><br><br>

 (3) MobaXterm 접속 과정<br><br>
 <img width="500" height="400" alt="3-1" src="https://github.com/user-attachments/assets/32394a2b-7714-4b0c-b1c0-8ef1ed21a5a0" /><br>
  - 보안을 위해 .pem 파일의 권한이 과도하게 열려 있을 경우 SSH 접속이 차단되는 현상 확인(Permission denied)<br><br>
<img width="400" height="150" alt="3-2" src="https://github.com/user-attachments/assets/efd3bfb6-ddd6-4756-b6d7-e7eaac80840d" /><br>
 - 리눅스 파일 시스템 권한 관리를 통해 키페어 파일을 소유자 읽기 전용(chmod 400)으로 변경하여 보안 무결성 확보<br><br>
<img width="400" height="150" alt="3-3" src="https://github.com/user-attachments/assets/5e7e2018-3b72-48cf-957b-309444c2b4a4" /><br>
 - Private 서버(10.0.2.86) 접속 성공<br>



 
 (4) Public 서버에서 `ip addr` 명령어로 Private 서버(10.0.2.86)에 접속 성공 확인<br><br>
<img width="400" height="150" alt="4" src="https://github.com/user-attachments/assets/ae5b4f1b-0a7b-4bfd-9470-7c3a15d160f7" />
