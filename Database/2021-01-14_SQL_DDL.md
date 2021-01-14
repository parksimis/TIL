# SQL을 이용한 데이터 정의

## 1. 테이블 생성

### - `CREATE TABLE`

* 기초 문법

  ```sql
  CREATE TABLE 테이블_이름 (
  		속성_이름 데이터 타입 [NOT NULL] [DEFAULT 기본_값] -- 테이블을 구성하는 각 속성의 이름, 데이터 타입, 기본 제약사항 정의
  		[PRIMARY KEY (속성_리스트)] -- 기본키 정의
  		[UNIQUE (속성_리스트)] -- 대체키 정의
  		[FOREIGN KEY (속성_리스트) REFERENCES 테이블_이름(속성_리스트)] -- 외래키 정의
  		[ON DELETE 옵션] [ON UPDATE 옵션] 
  		[CONSTRAINT 이름] [CHECK(조건)]) -- 데이터 무결성을 위한 제약조건 작성
  ```

  * 속성의 정의
    * 테이블을 구성하는 각 속성의 데이터 타입을 선택한 다음 NULL 값 허용 여부와 기본 값 필요 여부를 결정
    * NULL / NOT NULL
      * 아무것도 지정하지 않으면 default로 NULL 허용
    * PRIMARY KEY
      * 이 속성을 통해 각 테이블에 기본 키를 설정 가능
    * UNIQUE
      * 대체키 정의 옵션
    * FOREIGN KEY (속성_리스트) REFRENCE 테이블__이름(속성_리스트)
      * 외래키를 정의 가능
  * 제약 조건
    * 데이터의 무결성을 지키기 위한 제한된 조건
    * 특정 데이터를 입력할 때 무조건적으로 입력되는 것이 아닌, 어떠한 조건을 만족했을 때 입력되도록 제약
    * MariaDB가 제공하는 6가지 제약 조건
      * PRIMARY KEY 제약 조건
      * FOREIGN KEY 제약 조건
      * UNIQUE 제약 조건
      * CHECK 제약 조건
      * DEFAULT 정의
      * NULL 값 허용

#### 1) PRIMARY KEY 제약 조건

* 테이블에 존재하는 많은 행의 데이터를 구분할 수 있는 식별자를 '기본키'라고 부른다.

* 기본 키에 입력되는 값은 중복될 수 없으며, NULL 값이 입력될 수 없다. 
* 기본 키로 생성되는 것은 자동으로 클러스터형 인덱스가 생성된다.
* 대부분의 테이블은 기본 키를 가져야 한다. 기본 키가 없어도 테이블의 구성이 가능하지만, 실무적으로는 대부분의 테이블에는 기본 키를 설정해줘야 한다.

#### 2) FOREIGN KEY 제약 조건

* 두 테이블 간의 관계를 선언함으로써, 데이터의 무결성을 보장해주는 역할을 수행함.
* 외래키 관계를 설정하면, 하나의 테이블이 다른 테이블에 의존하게 된다.
* 외래키 테이블에 데이터를 입력할 때는 꼭 기준 테이블에 참조해서 입력하므로, 기준 테이블에 이미 데이터가 존재해야 한다.
* 기준 테이블의 열 이름과 외래키 테이블의 열 이름이 동일해도 되고, 아니어도 상관없다.

#### 3) UNIQUE 제약 조건

* 중복되지 않는 유일한 값을 입력해야 하는 조건.
* PRIMARY KEY와 거의 비슷하지만, 차이점은 UNIQUE는 NULL 값을 허용한다는 점이다.
  * NULL은 여러 개가 입력되어도 상관없음.

#### 4) CHECK 제약 조건

* 입력되는 데이터를 점검하는 기능을 함.
* 키에 마이너스 값이 들어올 수 없게 한다던지와 같은 여러 가지 조건을 지정한다.

#### 5) DEFAULT 정의

* 값을 입력하지 않았을 때, 자동으로 입력되는 기본값을 정의하는 방법
  * 예를 들어, 출생연도를 입력하지 않으면 -1을 입력하고, 주소를 특별히 입력하지 않았다면 '서울'이 입력되도록 하는 것.

#### 6) NULL 값 허용

* NULL 값을 허용하려면, NULL을, 허용하지 않으려면 NOT NULL을 사용한다.
  * PK가 설정된 열에는 NULL 값이 있을 수 없으므로, 생략하면 자동으로 NOT NULL로 인식됨
* NULL 값은 '아무 것도 없다.'라는 뜻이다. **공백(' ')이나 0과 같은 값과는 다르다.**



### - 실습

* 실제 데이터베이스를 만들고,  테이블을 만들어보는 실습을 진행
* **개체(데이터베이스, 테이블, 열) 이름은 영문을 사용해야 한다.** 행 데이터의 값에만 한글을 사용하도록 하자. 개체의 이름을 한글로 하는 경우 호환성과 같은 문제 발생 여지가 있으므로 영문을 사용하는 것이 좋다.
  * **아래 실습의 경우 가독성을 위해 한글로 개체명을 작성하였다.**

#### 1) 판매 데이터베이스 생성

* `CREATE DATABASE`를 사용해 '판매' 데이터베이스를 생성한다.

  ```mysql
  -- 1-1) 판매 데이터베이스 생성
  
  MariaDB [none]> CREATE DATABASE `판매`;
  Query OK, 1 row affected (0.001 sec)
  
  -- DATABASE 보기
  MariaDB [none]> SHOW DATABASES;
  +--------------------+
  | Database           |
  +--------------------+
  | employees          |
  | information_schema |
  | mysql              |
  | performance_schema |
  | shopdb             |
  | test               |
  | 판매               |
  +--------------------+
  7 rows in set (0.001 sec)
  
  -- 판매 데이터로 이동
  MariaDB [none]> USE 판매
  Database changed
  MariaDB [판매]>
  ```

#### 2) 고객 TABLE 생성

* 속성

  * 고객 아이디(PK) : varchar(20)
  * 고객 이름 : varchar(10)
  * 나이 : int
  * 등급 : varchar(10)
  * 직업 : varchar(20)
  * 적립금 : int, DEFAULT 0

* 위의 조건을 만족하는 고객 TABLE을 생성

  ```mysql
  -- 1-2) 고객 TABLE 만들기
  MariaDB [판매]> CREATE TABLE 고객 (
      -> 고객아이디 varchar(20) NOT NULL,
      -> 고객이름 varchar(10) NOT NULL,
      -> 나이 int,
      -> 등급 varchar(10) NOT NULL,
      -> 직업 varchar(20),
      -> 적립금 int DEFAULT 0,
      -> PRIMARY KEY(고객아이디)
      -> );
  Query OK, 0 rows affected (0.014 sec)
  
  -- TABLE 확인
  MariaDB [판매]> SHOW TABLES;
  +----------------+
  | Tables_in_판매 |
  +----------------+
  | 고객           |
  +----------------+
  1 row in set (0.000 sec)
  ```

#### 3) 제품 TABLE 생성

* 속성

  * 제품번호(PK) : char(3) 
  * 제품명 : varchar(20)
  * 재고량 : int
  * 단가 : int
  * 제조업체 : varchar(20)

* 제약조건

  * 재고량은 항상 0이상이고, 10,000개 이하여야 한다.

* 위의 조건에 맞는 제품 TABLE을 생성

  ```mysql
  -- 1-3) 제품 TABLE 생성
  MariaDB [판매]> CREATE TABLE 제품 (
      -> 제품번호 char(3) NOT NULL,
      -> 제품명 varchar(20),
      -> 재고량 int,
      -> 단가 int,
      -> 제조업체 varchar(20),
      -> PRIMARY KEY (제품번호),
      -> CHECK (재고량 >= 0 AND 재고량 <= 10000)
      -> );
  Query OK, 0 rows affected (0.014 sec)
  
  -- TABLE 확인
  MariaDB [판매]> SHOW TABLES;
  +----------------+
  | Tables_in_판매 |
  +----------------+
  | 고객           |
  | 제품           |
  +----------------+
  2 rows in set (0.000 sec)
  ```

#### 4) 주문 TABLE 생성

* 속성

  * 주문번호(PK) : char(3)
  * 주문고객(FK) : varchar(20)
  * 주문제품(FK) : char(3)
  * 수량 : int
  * 배송지 : varchar(30)
  * 주문일자 : date

* 제약조건

  * 주문고객 속성이 고객 테이블의 고객 아이디 속성을 참조하는 외래키
  * 주문제품 속성이 제품 테이블의 제품번호 속성을 참조하는 외래키

* 위의 조건을 만족하는 주문 TABLE 생성

  ```mysql
  -- 주문 TABLE 생성
  MariaDB [판매]> CREATE TABLE 주문(
      -> 주문번호 char(3) NOT NULL,
      -> 주문고객 varchar(20),
      -> 주문제품 char(3),
      -> 수량 int,
      -> 배송지 varchar(30),
      -> 주문일자 date,
      -> PRIMARY KEY(주문번호),
      -> FOREIGN KEY(주문고객) REFERENCES 고객(고객아이디),
      -> FOREIGN KEY(주문제품) REFERENCES 제품(제품번호)
      -> );
  Query OK, 0 rows affected (0.014 sec)
  
  -- TABLE 확인
  MariaDB [판매]> SHOW TABLES;
  +----------------+
  | Tables_in_판매 |
  +----------------+
  | 고객           |
  | 제품           |
  | 주문           |
  +----------------+
  3 rows in set (0.000 sec)
  ```

#### 5) 배송업체 TABLE 생성

* 속성

  * 업체번호(PK) : char(3)
  * 업체명 : varchar(20)
  * 주소 : varchar(100)
  * 전화번호 : varchar(20)

* 위의 조건을 만족하는 배송업체 TABLE 생성

  ```mysql
  -- 1-5) 배송업체 TABLE 생성
  MariaDB [판매]> CREATE TABLE 배송업체(
      -> 업체번호 char(3) NOT NULL,
      -> 업체명 varchar(20),
      -> 주소 varchar(100),
      -> 전화번호 varchar(20),
      -> PRIMARY KEY (업체번호)
      -> );
  Query OK, 0 rows affected (0.014 sec)
  
  -- TABLE 확인
  MariaDB [판매]> SHOW TABLES;
  +----------------+
  | Tables_in_판매 |
  +----------------+
  | 고객           |
  | 배송업체       |
  | 제품           |
  | 주문           |
  +----------------+
  4 rows in set (0.000 sec)
  ```

  

## 2. 테이블 수정

### - `ALTER TABLE`

#### 1) 테이블에 속성 추가

* 기본 문법

  ```sql
  ALTER TABLE 테이블명 ADD 추가할 칼럼명 데이터 유형;
  ```

#### 2) 테이블 속성 삭제

* 기본 문법

  ```sql
  ALTER TABLE 테이블명 DROP COLUMN 속성명;
  ```

#### 3) 테이블에 제약조건 추가

* 기본 문법

  ```sql
  ALTER TABLE 테이블명 ADD CONSTRAINT 제약조건이름 CHECK(조건) ;
  ```

### - 실습

#### 1) 테이블 속성 추가

* 고객 테이블에 가입 날짜 속성을 추가해보기

  ```mysql
  -- 고객 테이블에 가입 날짜 속성 추가
  MariaDB [판매]> ALTER TABLE 고객 ADD 가입날짜 DATE ;
  
  -- 컬럼 이름 보기
  MariaDB [판매]> SELECT COLUMN_NAME
      -> FROM INFORMATION_SCHEMA.COLUMNS
      -> WHERE TABLE_NAME = '고객';
  +-------------+
  | COLUMN_NAME |
  +-------------+
  | 고객아이디  |
  | 고객이름    |
  | 나이        |
  | 등급        |
  | 직업        |
  | 적립금      |
  | 가입날짜    |
  +-------------+
  7 rows in set (0.001 sec)
  ```

#### 2) 테이블 속성 삭제

* 위에서 생성한 가입날짜 속성 삭제

  ```mysql
  -- 고객 테이블의 가입날짜 속성 삭제
  MariaDB [판매]> ALTER TABLE 고객 DROP COLUMN 가입날짜;
  
  -- 컬럼 이름 보기
  MariaDB [판매]> SELECT COLUMN_NAME
      -> FROM INFORMATION_SCHEMA.COLUMNS
      -> WHERE TABLE_NAME = '고객';
  +-------------+
  | COLUMN_NAME |
  +-------------+
  | 고객아이디  |
  | 고객이름    |
  | 나이        |
  | 등급        |
  | 직업        |
  | 적립금      |
  +-------------+
  6 rows in set (0.001 sec)
  ```

#### 3) 테이블에 제약 조건 추가

* MySQL 10 이하 버전에서는 실행 안됨

* 고객 테이블에 나이가 20세 이상인 회원만 가입되도록 제약조건을 추가

  ```mysql
  -- 테이블에 제약 조건 추가
  MariaDB [판매]> ALTER TABLE 고객 ADD CONSTRAINT CHK_AGE CHECK(나이 >= 20);
  
  -- 제약 조건 확인
  MariaDB [판매]> SELECT * FROM information_schema.table_constraints WHERE CONSTRAINT_SCHEMA = '판매';
  +--------------------+-------------------+-----------------+--------------+------------+-----------------+
  | CONSTRAINT_CATALOG | CONSTRAINT_SCHEMA | CONSTRAINT_NAME | TABLE_SCHEMA | TABLE_NAME | CONSTRAINT_TYPE |
  +--------------------+-------------------+-----------------+--------------+------------+-----------------+
  | def                | 판매              | PRIMARY         | 판매         | 고객       | PRIMARY KEY     |
  | def                | 판매              | CHK_AGE         | 판매         | 고객       | CHECK           |
  | def                | 판매              | PRIMARY         | 판매         | 배송업체   | PRIMARY KEY     |
  | def                | 판매              | PRIMARY         | 판매         | 제품       | PRIMARY KEY     |
  | def                | 판매              | CONSTRAINT_1    | 판매         | 제품       | CHECK           |
  | def                | 판매              | PRIMARY         | 판매         | 주문       | PRIMARY KEY     |
  | def                | 판매              | 주문_ibfk_1     | 판매         | 주문       | FOREIGN KEY     |
  | def                | 판매              | 주문_ibfk_2     | 판매         | 주문       | FOREIGN KEY     |
  +--------------------+-------------------+-----------------+--------------+------------+-----------------+
  8 rows in set (0.060 sec)
  ```

  