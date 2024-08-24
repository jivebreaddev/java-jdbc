# 만들면서 배우는 스프링
[Next Step - 과정 소개](https://edu.nextstep.camp/c/4YUvqn9V)

## JDBC 라이브러리 구현하기

### 학습목표
- JDBC 라이브러리를 구현하는 경험을 함으로써 중복을 제거하는 연습을 한다.
- Transaction 적용을 위해 알아야할 개념을 이해한다.

### 시작 가이드
1. 이전 미션에서 진행한 코드를 사용하고 싶다면, 마이그레이션 작업을 진행합니다.
    - 학습 테스트는 강의 시간에 풀어봅시다.
2. LMS의 1단계 미션부터 진행합니다.

## 준비 사항
- 강의 시작 전에 docker를 설치해주세요.

## 학습 테스트
1. [ConnectionPool](study/src/test/java/connectionpool)
2. [Transaction](study/src/test/java/transaction)



## 1단계 요구사항


1. [x] UserDaoTest를 이용해서 리팩터링 진행
2. [x] JdbcTemplate을 구현한다.  
   - RowMapper 구현  (과거에 MetaEntity에 값 넣었던것이랑 동일)
   - JdbcTemplate의 메서드들 생성
     - queryForObejct
     - query
3. [x] 위의 기능들을 테스트로 검증한다.










## 3단계 요구사항


1. [] Transaction 경계 설정하기
   - 한 트랜잭션으로 묶으려면, 동일한 Connection 객체를 사용한다.



기능 정리
- Transaction 이란 논리적 기능을 수행하기 위한 작업 단위로 Commit 혹은 Rollback으로 상태가 완료된다.
- 이를 위해, Connection이라는 객체를 동일하게 유지해야하는데, 이때, TransactionalManager의 리소스 동기화 역할이 필요하다.
- 비즈니스 로직 레벨(Service)에서 TransactoinalManager 없이는, 데이터 접근 로직(Connection 객체)가 섞이게 된다.
-   https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/datasource/DataSourceTransactionManager.html


4단계의 resource 

https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/transaction/support/TransactionSynchronizationManager.html


## 4단계 요구사항

1. [] Transaction 동기화를 위한 Transactional Synchronization 적용하기
2. [] 트랜잭션 서비스 추상화 하기
3. [] 트랜잭션 테스트가 실제로 통과하는지 확인하기
   - [] 실제로 쓰레드 여러개 띄어서 트랜잭션 독립적인지 확인


키워드 정리
- 로컬 트랜잭션
- 글로벌 트랜잭션
- JTA 

