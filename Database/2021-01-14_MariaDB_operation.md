# MariaDB 전체 운영 실습

## 1. 정보시스템 구축 절차 요약

* 분석, 설계, 구현, 시험, 유지보수의 5가지 단계

  **1) 분석**

* 구현하고자 하는 프로젝트의 가장 첫 번째 단계
* 시스템 분석 또는 요구사항 분석이라고 부름
* 현재 우리가 '무엇(What)'을 할 것인지를 결정함. (사용자 인터뷰, 업무조사) 
* 프로젝트의 첫 단추를 끼우는 단계이므로, 많은 시간 동안 심혈을 기울여야 함.(많은 문서가 작성됨)

  **2) 설계**

* 시스템 설계, 프로그램 설계라는 용어로 부름
* 우리가 구축하고자 하는 시스템을 '어떻게(How)' 할 것인지 결정
* 대부분 프로젝트에서 이 분석과 설계의 과정이 전체 공정의 50% 이상을 차지함.

  **3) 구현**

* 시스템 설계가 끝나면 그 결과 문서들을 프로그래머에게 넘겨주고, 이를 토대로 프로그래머가 실제로 구현하는 단계

  **4) 시험**

  **5)유지보수**



## 2. 데이터베이스 모델링과 필수 용어

* 분석과 설계 중 가장 중요한 과정 중의 하나가 '데이터베이스 모델링'이다.
  * 데이터베이스 모델링 : 현실세계에서 사용되는 데이터를 DB에 어떻게 옮겨 놓을 것인가를 결정하는 과정
  * 저장할 정보를 Table이라는 형식에 맞춰 저장

* **주요 용어**
  * **데이터(Data)** : 단편적인 정보, 정보는 있으나 아직 체계화되지 못한 상태
  * **테이블(Table)** : 회원이나 제품의 데이터를 입력하기 위해, 표 형태로 표현한 것.
  * **데이터베이스(DataBase, DB)** : 테이블이 저장되는 저장소
  * **데이터베이스 관리 시스템(Database Management System, DBMS) **
    * 데이터베이스를 관리하는 시스템 또는 소프트웨어 현재는 MariaDB를 사용
  * **열(Column, Field)** : 각 테이블은 열로 구성됨
  * **열 이름** : 각 열을 구분하기 위한 이름. 열 이름은 각 테이블 내에서는 **중복되지 않고**, **고유해야 함**
  * **데이터 형식** : 열의 데이터 형식을 말함. **테이블을 생성할 때 열 이름과 함께 지정해줘야 함**
  * **행(Row, Record) ** : 실질적인 데이터를 말함. 
  * **기본 키 열**  
    * 각 행을 구분하는 유일한 열을 말함. 기본키 열은 중복되어서는 안되며, NULL 값이 존재해서도 안됨.
    * 또한, 각 테이블에는 기본 키가 하나만 지정되어 있어야 한다.
  * **외래 키 필드**
    * 두 테이블 간의 관계를 맺어주는 키를 말한다. 
  * **SQL** : 사람과 DBMS가 소통하기 위한 언어



## 3. MariaDB를 이용한 데이터베이스 구축 절차

#### 설치가 잘 되었는지를 확인하고, 전체적인 개요를 알기 위해서 DB 생성 및 여러 작업 실시

#### 1) 데이터베이스 생성

* 인터넷 쇼핑몰 구축을 위한 '쇼핑몰(shopdb)' 데이터베이스 생성

* 수업시간에는HeidiSQL을 통한 GUI 화면의 쿼리 탭에서 실행하지만, 배우는 내용들을매일 복습하면서 MySQL Client를 통해 CLI로 만들도록 함.

  * `CREATE DATABASE DB명 ;`
  * 주어진 DB 이름을 가지는 Database를 만듦.
  * `SHOW DATABASES ; `
  * 데이터베이스를 확인할 수 있다.
  * `USE DB명 ; `
    * 주어진 DB 이름을 사용

  ```mysql
  -- 만들기 전
  MariaDB [(none)]> show databases;
  +--------------------+
  | Database           |
  +--------------------+
  | employees          |
  | information_schema |
  | mysql              |
  | performance_schema |
  | test               |
  +--------------------+
  5 rows in set (0.001 sec)
  
  -- CREATE DATABASE `DB명` ; 으로 DATABASE를 만들 수 있다.
  
  MariaDB [(none)]> CREATE DATABASE `shopdb`;
  Query OK, 1 row affected (0.001 sec)
  
  -- 만들고 난 후 shopdb라는 DATABASE가 만들어진 것을 알 수 있다.
  MariaDB [(none)]> SHOW DATABASES;
  +--------------------+
  | Database           |
  +--------------------+
  | employees          |
  | information_schema |
  | mysql              |
  | performance_schema |
  | shopdb             |
  | test               |
  +--------------------+
  6 rows in set (0.001 sec)
  
  -- shopdb로 사용할 DB를 선택
  MariaDB [shopdb]> USE shopdb;
  Database changed
  ```

#### 2) 테이블 생성

* `CREATE TABLE` : 테이블을 생성하는 SQL 명령어 이후 다시 정리
* `SHOW TABLES ; ` : 현재 DB에 정의된 TABLE을 보여주는 명령어

##### 2-1) 회원 테이블(memberTBL) 생성

* 아래와 같은 속성을 갖는 회원 테이블을 생성한다.

  ```mysql
  -- 회원 TABLE 생성
  MariaDB [shopdb]> CREATE TABLE memberTBL (
      -> memberID char(8) NOT NULL,
      -> memberName char(5) NOT NULL,
      -> memberAddress char(20),
      -> PRIMARY KEY (memberID)
      -> );
  Query OK, 0 rows affected (0.015 sec)
  
  -- 생성 후 TABLE 보기
  MariaDB [shopdb]> SHOW TABLES;
  +------------------+
  | Tables_in_shopdb |
  +------------------+
  | membertbl        |
  +------------------+
  1 row in set (0.000 sec)
  ```

##### 2-2) 제품 테이블(productTBL) 생성

* 아래와 같은 속성을 갖는 제품 테이블을 생성한다.

  ```mysql
  -- 제품 테이블 생성
  MariaDB [shopdb]> CREATE TABLE productTBL(
      -> productName char(4) NOT NULL,
      -> cost int NOT NULL,
      -> makeDate date,
      -> company char(5),
      -> amount int NOT NULL,
      -> PRIMARY KEY (productName)
      -> );
  Query OK, 0 rows affected (0.013 sec)
  
  -- 생성 후 TABLE 보기
  MariaDB [shopdb]> SHOW TABLES;
  +------------------+
  | Tables_in_shopdb |
  +------------------+
  | membertbl        |
  | producttbl       |
  +------------------+
  2 rows in set (0.000 sec)
  ```

# 4. 트리거

* 테이블에 부착되어서, 테이블에 `INSERT`, `UPDATE`, `DELETE` 작업이 발생되면 실행되는 코드를 말한다. 

* 상세한 내용은 추후 알아보고, 간단한 사례를 통해 트리거의 용도를 확인

  * 예를 들어, '회원1'이 탈퇴하는 경우, 회원에서 탈퇴하면 간단히 회원 테이블에서 '회원1'의 정보를 지우면 된다.
  * 하지만, 나중에 탈퇴 회원의 정보를 알아야하는 경우에는?
    * 이 경우는 삭제하기 전에 다른 TABLE에 삭제 내용을 복사해 놓으면 됨. 하지만 이를 매번 수작업으로 해주기에는 현실적으로 힘들기 때문에, **Trigger**를 활용한다.
    * 트리거를 활용해, 회원 테이블에서 행 삭제가 일어나기 전에 미리 다른 곳에 삭제될 데이터를 **'자동으로'** 저장해주는 기능을 구현

* 직접 실습을 통해 트리거를 구현해보자

  1)  지워질 데이터를 보관할 테이블(deletedMemberTBL) 생성

  2) 트리거 생성(trg_deletedMemberTBL)

  3) 회원 테이블 확인

  4) 회원 테이블의 데이터를 삭제

  5) 회원 테이블 확인

  6) 삭제된 데이터가 '1)'의 테이블에 들어가있는지 확인 

  ```mysql
  -- Step 1) 지워질 데이터를 보관할 테이블 생성
  -- 회원아이디, 회원이름, 주소, 삭제날짜 속성 
  MariaDB [shopdb]> CREATE TABLE deleteMemberTBL (
      -> memberID char(8),
      -> memberName char(5),
      -> memberAddress char(20),
      -> deletedData date -- 삭제 날짜 기록
      -> );
      
  -- Step 2) 트리거 생성
  MariaDB [shopdb]> DELIMITER $$
  MariaDB [shopdb]> CREATE TRIGGER trg_deletedMemberTBL -- 트리거 이름
      -> AFTER DELETE -- 삭제 후에 작동하게 지정한다.
      -> ON memberTBL -- memberTBL에서 삭제가 일어나면 트리거 동작
      -> FOR EACH ROW -- 각각 행마다 적용시킴
      -> BEGIN
      -> -- OLD 테이블의 내용을 백업 테이블에 삽입
      -> INSERT INTO deletemembertbl
      -> VALUES(OLD.memberID, OLD.memberName, OLD.memberAddress, CURDATE() );
      -> END $$
  Query OK, 0 rows affected (0.004 sec)
  
  MariaDB [shopdb]> DELIMITER ;
  
  -- Step 3) 회원 테이블 확인
  MariaDB [shopdb]> SELECT * FROM memberTBL;
  +----------+------------+--------------------+
  | memberID | memberName | memberAddress      |
  +----------+------------+--------------------+
  | Dang     | 당탕이     | 경기도 부천시 중동 |
  +----------+------------+--------------------+
  1 row in set (0.000 sec)
  
  -- Step 4) '당탕이' 이름의 회원 삭제
  MariaDB [shopdb]> DELETE FROM memberTBL WHERE memberName = '당탕이';
  Query OK, 1 row affected (0.007 sec)
  
  -- Step 5) memberTBL 데이터 확인
  MariaDB [shopdb]> SELECT * FROM memberTBL;
  Empty set (0.000 sec)
  
  -- Step 6) deleteMemberTBL 테이블 확인
  MariaDB [shopdb]> SELECT * FROM deleteMemberTBL;
  +----------+------------+--------------------+-------------+
  | memberID | memberName | memberAddress      | deletedData |
  +----------+------------+--------------------+-------------+
  | Dang     | 당탕이     | 경기도 부천시 중동 | 2021-01-14  |
  +----------+------------+--------------------+-------------+
  1 row in set (0.000 sec)
  ```

  * 이처럼 지워지기 전에 deleteMemberTBL 테이블에 복사되어 들어가는 것을 알 수 있다. 간단한 사례이지만, 트리거의 개념을 어느 정도는 알 수 있는 사례인 것 같다.
  * 자세한 사항은 후에 다루도록 한다.