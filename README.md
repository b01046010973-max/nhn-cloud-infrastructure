# nhn-cloud-infrastructure
# NHN Cloud 인프라 구축 프로젝트

보안과 효율적인 자원 관리를 목표로 한 클라우드 인프라 설계 실습

## 문제
- 외부의 무분별한 접근 차단 및 필수 서비스(SSH, Web)의 안전한 노출
- 한정된 Public IP 자원의 효율적 배분

## 해결
- **네트워크 분리**: VPC 내 Public/Private Subnet 구분 설계
- **통신 제어**: Internet Gateway 및 라우팅 테이블 직접 설정
- **보안 최적화**: Security Group을 통한 화이트리스트 기반 트래픽 제어

## 결과
- Floating IP 활용으로 보안성이 강화된 인스턴스 환경 구축
- 클라우드 네트워크 트래픽 흐름에 대한 실질적 이해도 확보
