# 인덱스

[인덱스 설명](../인덱스.md)

## 대수 확장성

대수 확장성은 트리의 깊이가 노드 수에 비해 느리게 성장하는 것을 말합니다.

## MySQL에서 인덱스 만들기

### 클러스터형 인덱스

- 기본키(PK) 생성
- `unique not null` 옵션을 사용

### 세컨더리 인덱스

세컨더리 인덱스는 보조 인덱스로 여러 개의 필드 값을 기반으로 쿼리를 많이 보낼 때 생성하는 인덱스입니다.

`create index` 명령어를 이용합니다.</br>
(하나의 인덱스를 만든다면 클러스터형 인덱스를 만드는 것이 효율적이다.)

## MongoDB에서 인덱스 만들기

- 도큐먼트를 만들면 자동으로 ObjectID가 생성되고 해당 키가 기본 키로 동작
- 세컨더리 키도 부가적으로 설정하여 기본 키와 세컨더리 키를 같이 쓰는 복합 인덱스로 설정할 수 있음

## 인덱스 최적화 기법

### 인덱스의 비용

- 탐색 두 번 수행
- 테이블이 수정되었을 때 index도 수정
- B-Tree의 높이를 균형 조절하는 비용이 발생,  데이터를 효율적으로 조회할 수 있도록 분산시키는 비용이 발생

그렇기 때문에 인덱스는 모든 것을 선언하는 것이 아닌 꼭 필요한 것에 사용해야 한다.

### 테스트

`explain`을 통하여 실행계획을 통한 성능측정, 테스팅이 가능합니다.

### 복합 인덱스

복합 인덱스는 여러 개의 컬럼을 조합하여 인덱스를 생성하는 방식입니다.

여러 컬럼을 기반으로 조회할 때 사용하게 됩니다. 복합 인덱스는 생성 순서가 성능에 영향을 주기 때문에 동일, 정렬, 다중 값, 카디널리티 순서로 생성해야 합니다.

> **Note**
> 
> 다중 값은 `<`, `>`을 이용하여 범위 탐색을 하는 것을 말합니다.
> 
> 카디널리티는 유니크한 정도를 말합니다.</br>
> Ex: 이름(카디널리티 낮음) < 이메일 (카디널리티 높음)
