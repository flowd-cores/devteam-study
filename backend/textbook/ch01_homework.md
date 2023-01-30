# 데이터베이스

## 관계형 데이터베이스

> 데이터를 정규화하여 저장하는 방식

1. 장점
    * 정규화를 통해 데이터의 중복성을 최소화하며 트랜잭션을 수행하는 것이 쉬움
    * 데이터의 원자성, 일관성, 격리 및 내구성을 유지하며 데이터 무결성을 높임
2. 단점
    * 객체-관계형 매핑이 복잡해질 수 있음
    * 유연성이 떨어짐
    * 수평적 확장이 어려움
    * 테이블에 다양한 가변성이 있는 데이터를 저장하기 어려움

### 종류

1. MySQL
    * Oracle 사에서 제작하고 유지보수 중인 오픈소스 데이터베이스
    * 데이터베이스 순위 2위 (https://db-engines.com/en/ranking)
    * 상업적으로 사용 시 상업용 라이센스(Enterprise Edition)를 취득해야만 사용 가능함
    * 오픈소스 라이브러리이나, 상용 라이센스 제품은 오픈소스가 아님
    * 커뮤니티 에디션(Community Edition)은 개인용으로 오픈소스임
2. MariaDB
    * 데이터베이스 순위 12위
    * Oracle 사에서 MySQL에 대해 영리 목적의 라이센스를 별도로 부여함에 따라 그에 대항하여 시작된 RDMBS
    * 최초 버전은 MySQL에서의 포크로 시작되었으나, 현재는 MySQL과 호환되지만 궤를 달리하고 있음
    * MySQL과 비교하여 현재 더 나은 기능과 속도, 안전성을 제공
    * Storage Engine
        - innoDB Engine
            + Transaction-Safe 엔진
            + IUD 속도가 빠름
            + Full-text 인덱싱 불가
            + MyISAM Engine에 비교하여 파일 용량이 1.5~2배 증가
        - MyISAM Engine
            + Non-Transaction-Safe 엔진
            + Select 속도 빠름
            + IUD 속도가 느림
            + Full-text 인덱싱 가능
        - Xtra Engine
            + innoDB 개량형 엔진
        - Memory Engine
            + 데이터를 메모리에 보관 (휘발성)
            + 매우 빠른 속도를 보이나, 정전 등에 취약함
        - Archive Engine
            + Column에 대해 Gzip을 이용하는 엔진
            + 주로 매우 작은 풋 프린트로 인덱스 없이 대량의 데이터를 저장하는데 사용
        - Aria Engine
            + MariaDB 버전 10.4 부터 모든 시스템 테이블은 이 Aria Engine으로 기본 지정됨
            + MyISAM보다 더 나은 캐싱을 제공하여 Group by 및 distinct 쿼리 속도가 향상

## 비관계형 데이터베이스 또는 분산 데이터 데이터베이스

> 융통성 있는 데이터 모델을 사용하여 데이터의 저장 및 검색을 위한 특화 데이터베이스

1. 장점
    * 클러스터에 새로운 프로세스 노드 형태로 수평적 확장이 가능
    * 샤딩 기술에 대해 적은 비용으로 고효율을 제공함
    * 통합된 검색 기능으로 고품질의 검색 결과를 제공
    * 다양한 가변성 데이터 저장이 쉬움
2. 단점
    * 자체적인 트랜잭션이 소극적이며, 애플리케이션 단계에서 설계해야 함
    * 데이터 중복이 발생될 수 있으며 중복된 데이터가 변경될 경우 모든 컬렉션(또는 도큐먼트)에서 수행해야 함
    * 스키마가 존재하지 않기 때문에 데이터 구조를 보장하지 않음

### 종류

1. MongoDB
    * JSON 형태의 동적 스키마형 문서를 사용함. (BSON이라 명칭함)
    * 자동 샤딩을 기본 제공함 > 장애 대처가 쉬우며, 적은 비용으로 확장이 가능함
    * 문서에 대한 검색이 빠름
        - string 부분 연산을 비교 - MySQL No Index : 1347sec , MongoDB No Index : 947sec
        - JOIN 연산 비교 - MySQL 9239sec , MongoDB : 1670sec
        - 단, 검색 시 양측 모두 소실량이 존재하며 MongoDB에서 더 많은 소실량을 보임
        - 자료출처 : https://soojle.gitbook.io/project/requirements/undefined-2/undefined-2-1/MySQL-vs-mongodb
2. Redis
    * 메모리 상주 데이터베이스
    * 매우 빠른 속도를 보이며, 휘발성의 형태를 띔
    * 오로지 Key-Value 형태로 저장이 가능하다.
    * 지원 데이터 형태 : 문자열, 리스트, 해시, 셋, 정렬된 셋




# 데이터베이스 ORM/ODM 패키지
1. Golang MySQL 드라이버 : https://github.com/go-sql-driver/mysql
    * 지원 DB : MySQL
2. Gorm : https://pkg.go.dev/gorm.io/gorm
    * 지원 DB : MySQL , PostgreSQL , SQLite , MSSQL
3. Xorm : https://xorm.io/
    * 지원 DB : MySQL , PostgreSQL , SQLite , MSSQL
4. Entgo : https://entgo.io/
    * 지원 DB : MySQL , PostgreSQL , SQLite
5. Golang Mongo 드라이브 : https://pkg.go.dev/go.mongodb.org/mongo-driver/mongo
6. Mgo : https://pkg.go.dev/gopkg.in/mgo.v2
    * 지원 DB : MongoDB
    * 2015년에 지원 종료
7. MGM : https://pkg.go.dev/github.com/kamva/mgm/v3
    * 지원 DB : MongoDB
8. Go-radis : https://github.com/redis/go-redis
    * 지원 DB : redis

   