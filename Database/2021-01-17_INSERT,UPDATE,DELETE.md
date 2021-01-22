# 데이터 변경을 위한 SQL 문

## 1. 데이터 삽입 : INSERT

* 테이블에 데이터를 삽입하는 명령어이다.

* 기본 형식

  ```sql
  INSERT [INTO] 테이블[(열1, 열2, ...)] VALUES (값1, 값2, ...)
  ```

  * 테이블 이름 다음에 나오는 열은 생략이 가능하다.
    * 하지만, 생략할 경우 VALUES 다음에 나오는 값들의 순서 및 개수가 테이블이 정의된 열 순서 및 개수와 동일해야 한다.(모든 필드에 생성했던 순서대로 value가 저장됨)

### - 적용 예시

1. 판매 데이터베이스의 고객 테이블에 고객아이디(strawberry), 고객이름(최유경), 나이(30), 등급(vip), 직업(공무원), 적립금(100) 인 새로운 고객의 정보를 삽입하라

```mysql
-- 변경 전 테이블 확인
MariaDB [판매]> SELECT * FROM 고객 ;
+------------+----------+------+--------+--------+--------+
| 고객아이디 | 고객이름 | 나이 | 등급   | 직업   | 적립금 |
+------------+----------+------+--------+--------+--------+
| apple      | 정소화   |   20 | gold   | 학생   |   1000 |
| banana     | 김선우   |   25 | vip    | 간호사 |   2500 |
| carrot     | 고명석   |   28 | gold   | 교사   |   4500 |
| melon      | 성원용   |   35 | gold   | 회사원 |   5000 |
| orange     | 김용욱   |   22 | silver | 학생   |      0 |
| peach      | 오형준   | NULL | silver | 의사   |    300 |
| pear       | 채광주   |   31 | silver | 회사원 |    500 |
+------------+----------+------+--------+--------+--------+
7 rows in set (0.000 sec)

-- 데이터 삽입
MariaDB [판매]> INSERT INTO 고객(고객아이디, 고객이름, 나이, 등급, 직업, 적립금)
    -> VALUES ('strawberry', '최유경', 30, 'vip', '공무원', 100)
    -> ;
Query OK, 1 row affected (0.002 sec)

-- 변경 후 데이터 확인
MariaDB [판매]> SELECT * FROM 고객 ;
+------------+----------+------+--------+--------+--------+
| 고객아이디 | 고객이름 | 나이 | 등급   | 직업   | 적립금 |
+------------+----------+------+--------+--------+--------+
| apple      | 정소화   |   20 | gold   | 학생   |   1000 |
| banana     | 김선우   |   25 | vip    | 간호사 |   2500 |
| carrot     | 고명석   |   28 | gold   | 교사   |   4500 |
| melon      | 성원용   |   35 | gold   | 회사원 |   5000 |
| orange     | 김용욱   |   22 | silver | 학생   |      0 |
| peach      | 오형준   | NULL | silver | 의사   |    300 |
| pear       | 채광주   |   31 | silver | 회사원 |    500 |
| strawberry | 최유경   |   30 | vip    | 공무원 |    100 |
+------------+----------+------+--------+--------+--------+
8 rows in set (0.000 sec)
```



2. 고객아이디(tomato), 고객이름(정은심), 나이(36), 등급(gold), 적립금(100)인 사람을 고객테이블에 삽입하라

   * 직업 속성의 값이 없는 경우 속성리스트에서 제거하거나 해당하는 위치에 NULL 값을 표시해줘야한다.

   ```mysql
   -- 1) 속성리스트에서 제거
   MariaDB [판매]> INSERT
       -> INTO 고객(고객아이디, 고객이름, 나이, 등급, 적립금)
       -> VALUES ('tomato', '정은심', 36, 'gold', 100);
   Query OK, 1 row affected (0.002 sec)
   
   -- 2) 해당 위치에 NULL값 입력
   INSERT 
   INTO 고객(고객아이디, 고객이름, 나이, 등급, 적립금)
   VALUES ('tomato', '정은심', 36, 'gold', NULL, 100);
   
   -- 1), 2) 모두 아래와 같이 동일한 결과를 반환한다.
   MariaDB [판매]> SELECT * FROM 고객 ;
   +------------+----------+------+--------+--------+--------+
   | 고객아이디 | 고객이름 | 나이 | 등급   | 직업   | 적립금 |
   +------------+----------+------+--------+--------+--------+
   | apple      | 정소화   |   20 | gold   | 학생   |   1000 |
   | banana     | 김선우   |   25 | vip    | 간호사 |   2500 |
   | carrot     | 고명석   |   28 | gold   | 교사   |   4500 |
   | melon      | 성원용   |   35 | gold   | 회사원 |   5000 |
   | orange     | 김용욱   |   22 | silver | 학생   |      0 |
   | peach      | 오형준   | NULL | silver | 의사   |    300 |
   | pear       | 채광주   |   31 | silver | 회사원 |    500 |
   | strawberry | 최유경   |   30 | vip    | 공무원 |    100 |
   | tomato     | 정은심   |   36 | gold   | NULL   |    100 |
   +------------+----------+------+--------+--------+--------+
   9 rows in set (0.000 sec)
   ```



## 2. 데이터 수정 : UPDATE

* 기존에 입력되어 있는 값을 변경하기 위해서는 UPDATE를 사용한다.

* 기본 형식

  ```sql
  UPDATE 테이블이름
  	SET 열1=값1, 열2=값2, ...
  	WHERE 조건;
  ```

  * **<u>WHERE 절은 생략이 가능하지만, 생략하면 테이블 전체의 행이 변경된다.</u>**

### - 적용 예시

1. 제품 테이블에서 제품번호가 p03인 제품의 재고량을 3000으로 수정하라.

```mysql
-- 변경 전 p03의 제품 확인
MariaDB [판매]> SELECT *
    -> FROM 제품
    -> WHERE 제품번호 = 'p03';
+----------+----------+--------+------+----------+
| 제품번호 | 제품명   | 재고량 | 단가 | 제조업체 |
+----------+----------+--------+------+----------+
| p03      | 쿵떡파이 |   3600 | 2600 | 한빛제과 |
+----------+----------+--------+------+----------+
1 row in set (0.000 sec)

-- 값 변경
MariaDB [판매]> UPDATE 제품
    -> SET 재고량=3000
    -> WHERE 제품번호 = 'p03';
Query OK, 1 row affected (0.002 sec)
Rows matched: 1  Changed: 1  Warnings: 0

-- 변경 후 p03 제품 확인
MariaDB [판매]> SELECT *
    -> FROM 제품
    -> WHERE 제품번호 = 'p03';
+----------+----------+--------+------+----------+
| 제품번호 | 제품명   | 재고량 | 단가 | 제조업체 |
+----------+----------+--------+------+----------+
| p03      | 쿵떡파이 |   3000 | 2600 | 한빛제과 |
+----------+----------+--------+------+----------+
1 row in set (0.000 sec)
```



2. 제품 테이블에 모든 제품의 단가를 10% 인상하라
   * UPDATE 시 새로 저장되는 값에 수식을 적용할 수 있다.

```mysql
-- 변경 전 확인
MariaDB [판매]> SELECT * FROM 제품;
+----------+------------+--------+------+----------+
| 제품번호 | 제품명     | 재고량 | 단가 | 제조업체 |
+----------+------------+--------+------+----------+
| p01      | 그냥만두   |   5000 | 4500 | 대한식품 |
| p02      | 매운쫄면   |   2500 | 5500 | 민국푸드 |
| p03      | 쿵떡파이   |   3000 | 2600 | 한빛제과 |
| p04      | 맛난초콜릿 |   1250 | 2500 | 한빛제과 |
| p05      | 얼큰라면   |   2200 | 1200 | 대한식품 |
| p06      | 통통우동   |   1000 | 1550 | 민국푸드 |
| p07      | 달콤비스킷 |   1650 | 1500 | 한빛제과 |
+----------+------------+--------+------+----------+
7 rows in set (0.000 sec)

-- 수식을 활용한 UPDATE
MariaDB [판매]> UPDATE 제품
    -> SET 단가 =  단가 * 1.1;
Query OK, 7 rows affected (0.002 sec)
Rows matched: 7  Changed: 7  Warnings: 0

-- 변경 후 확인
MariaDB [판매]> SELECT * FROM 제품;
+----------+------------+--------+------+----------+
| 제품번호 | 제품명     | 재고량 | 단가 | 제조업체 |
+----------+------------+--------+------+----------+
| p01      | 그냥만두   |   5000 | 4950 | 대한식품 |
| p02      | 매운쫄면   |   2500 | 6050 | 민국푸드 |
| p03      | 쿵떡파이   |   3000 | 2860 | 한빛제과 |
| p04      | 맛난초콜릿 |   1250 | 2750 | 한빛제과 |
| p05      | 얼큰라면   |   2200 | 1320 | 대한식품 |
| p06      | 통통우동   |   1000 | 1705 | 민국푸드 |
| p07      | 달콤비스킷 |   1650 | 1650 | 한빛제과 |
+----------+------------+--------+------+----------+
7 rows in set (0.000 sec)
```



## 3. 데이터 삭제 : DELETE FROM

* 테이블에 저장된 데이터를 삭제할 때 사용. DELETE는 행 단위로 삭제한다.

* 기본 형식

  ```sql
  DELETE FROM 테이블이름 WHERE 조건;
  ```

  * 만약 WHERE 문이 생략되면 전체 데이터를 삭제한다.

### - 적용 예시

1. 주문 테이블에서 주문일자가 2019년 5월 22일인 주문 내역을 삭제하라.

   ```mysql
   -- 삭제 전 확인
   MariaDB [판매]> SELECT * FROM 주문;
   +----------+----------+----------+------+-----------------+------------+
   | 주문번호 | 주문고객 | 주문제품 | 수량 | 배송지          | 주문일자   |
   +----------+----------+----------+------+-----------------+------------+
   | o01      | apple    | p03      |   10 | 서울시 마포구   | 2019-01-01 |
   | o02      | melon    | p01      |    5 | 인천시 계양구   | 2019-01-10 |
   | o03      | banana   | p06      |   45 | 경기도 부천시   | 2019-01-11 |
   | o04      | carrot   | p02      |    8 | 부산시 금정구   | 2019-02-01 |
   | o05      | melon    | p06      |   36 | 경기도 용인시   | 2019-02-20 |
   | o06      | banana   | p01      |   19 | 충청북도 보은군 | 2019-03-02 |
   | o07      | apple    | p03      |   22 | 서울시 영등포구 | 2019-03-15 |
   | o08      | pear     | p02      |   50 | 강원도 춘천시   | 2019-04-10 |
   | o09      | banana   | p04      |   15 | 전라남도 목포시 | 2019-04-11 |
   | o10      | carrot   | p03      |   20 | 경기도 안양시   | 2019-05-22 |
   +----------+----------+----------+------+-----------------+------------+
   10 rows in set (0.000 sec)
   
   -- 삭제
   MariaDB [판매]> DELETE
       -> FROM 주문
       -> WHERE 주문일자 = '2019-05-22'
       -> ;
   Query OK, 1 row affected (0.001 sec)
   
   
   -- 삭제 후 확인
   MariaDB [판매]> SELECT * FROM 주문;
   +----------+----------+----------+------+-----------------+------------+
   | 주문번호 | 주문고객 | 주문제품 | 수량 | 배송지          | 주문일자   |
   +----------+----------+----------+------+-----------------+------------+
   | o01      | apple    | p03      |   10 | 서울시 마포구   | 2019-01-01 |
   | o02      | melon    | p01      |    5 | 인천시 계양구   | 2019-01-10 |
   | o03      | banana   | p06      |   45 | 경기도 부천시   | 2019-01-11 |
   | o04      | carrot   | p02      |    8 | 부산시 금정구   | 2019-02-01 |
   | o05      | melon    | p06      |   36 | 경기도 용인시   | 2019-02-20 |
   | o06      | banana   | p01      |   19 | 충청북도 보은군 | 2019-03-02 |
   | o07      | apple    | p03      |   22 | 서울시 영등포구 | 2019-03-15 |
   | o08      | pear     | p02      |   50 | 강원도 춘천시   | 2019-04-10 |
   | o09      | banana   | p04      |   15 | 전라남도 목포시 | 2019-04-11 |
   +----------+----------+----------+------+-----------------+------------+
   9 rows in set (0.000 sec)
   ```



2. 정소화 고객이 주문한 주문내역을 모두 삭제

   ```mysql
   -- 삭제 전 확인
   MariaDB [판매]> SELECT * FROM 주문;
   +----------+----------+----------+------+-----------------+------------+
   | 주문번호 | 주문고객 | 주문제품 | 수량 | 배송지          | 주문일자   |
   +----------+----------+----------+------+-----------------+------------+
   | o01      | apple    | p03      |   10 | 서울시 마포구   | 2019-01-01 |
   | o02      | melon    | p01      |    5 | 인천시 계양구   | 2019-01-10 |
   | o03      | banana   | p06      |   45 | 경기도 부천시   | 2019-01-11 |
   | o04      | carrot   | p02      |    8 | 부산시 금정구   | 2019-02-01 |
   | o05      | melon    | p06      |   36 | 경기도 용인시   | 2019-02-20 |
   | o06      | banana   | p01      |   19 | 충청북도 보은군 | 2019-03-02 |
   | o07      | apple    | p03      |   22 | 서울시 영등포구 | 2019-03-15 |
   | o08      | pear     | p02      |   50 | 강원도 춘천시   | 2019-04-10 |
   | o09      | banana   | p04      |   15 | 전라남도 목포시 | 2019-04-11 |
   +----------+----------+----------+------+-----------------+------------+
   9 rows in set (0.000 sec)
   
   -- 삭제
   MariaDB [판매]> DELETE
       -> FROM 주문
       -> WHERE 주문고객 in (SELECT 고객아이디
       -> FROM 고객
       -> WHERE 고객이름 = '정소화')
       -> ;
   Query OK, 2 rows affected (0.001 sec)
   
   -- 삭제 후 확인
   MariaDB [판매]> SELECT * FROM 주문;
   +----------+----------+----------+------+-----------------+------------+
   | 주문번호 | 주문고객 | 주문제품 | 수량 | 배송지          | 주문일자   |
   +----------+----------+----------+------+-----------------+------------+
   | o02      | melon    | p01      |    5 | 인천시 계양구   | 2019-01-10 |
   | o03      | banana   | p06      |   45 | 경기도 부천시   | 2019-01-11 |
   | o04      | carrot   | p02      |    8 | 부산시 금정구   | 2019-02-01 |
   | o05      | melon    | p06      |   36 | 경기도 용인시   | 2019-02-20 |
   | o06      | banana   | p01      |   19 | 충청북도 보은군 | 2019-03-02 |
   | o08      | pear     | p02      |   50 | 강원도 춘천시   | 2019-04-10 |
   | o09      | banana   | p04      |   15 | 전라남도 목포시 | 2019-04-11 |
   +----------+----------+----------+------+-----------------+------------+
   7 rows in set (0.000 sec)
   ```

   