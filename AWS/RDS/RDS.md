## RDS

### 생성

AWS > RDS > 데이터베이스 > 데이터 베이스 생성

#### 설정

- 템플릿
  - 프리 티어
- 설정
  - DB 클러스터 식별자
  - 마스터 사용자 이름
  - 퍼블릭 엑세스
  - VPC 보안 그룹

### 접속

호스트 부분은 생성한 RDS의 엔드 포인트를 사용

```shell
mysql -h my-rds.cro8ko4igy9t.ap-northeast-2.rds.amazonaws.com -u dan -p
```

접속이 불가한 경우 보안그룹 > 인바운드 규칙 > 유형, 소스, IP 설정 확인

### 모니터링

Cloud watch를 이용해 확인

### 백업

RDS에서 스냅샷을 생성하고 스냅샷을 이용한 복원이 가능하다. RDS 인스턴스를 삭제해도 스냅샷으로 복원이 가능하다.

### 삭제

1. 인스턴스 선택 > 삭제
2. 스냅샷 삭제
