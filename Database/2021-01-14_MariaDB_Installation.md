# MariaDB 개요 및 설치

## 2. MariaDB

### 2.1 MariaDB

* [WIKI](https://ko.wikipedia.org/wiki/MariaDB)
* [MariaDB Hompage](https://mariadb.org/)
* MariaDB사에서 제작한 RDBMS 소프트웨어로, 오픈소스로 제공된다.
* MariaDB의 전신인 MySQL이 비상업용이나 교육용으로는 제한없이 사용해도 되지만, 2010년 오라클이 인수 이후 상용으로 사용하기 위해서는 상용 라이선스를 취득해야 하는 반면에, MariaDB는 어떤 환경에서도 제한없이 사용해도 된다는 특징이 있다.
* MariaDB는 MySQL과 호환성을 대부분 유지하므로, MySQL을 사용하던 환경에서도 MariaDB로 별 문제없이 변경된다.



### 2.2 MariaDB 설치

#### 1) 소프트웨어 요구사항

* 하드웨어적인 부분은 Windows가 설치되면 특별히 제한이 없지만, Windows 운영체제는 Windows 7 이후나 Window Server 2008 R2 이후 버전에만 설치 가능함.

#### 2) MariaDB 설치

* [Download Link](https://downloads.mariadb.org/mariadb/10.3.11/)
* 책과 같은 환경을 만들어주기 위해서 MariaDB 10.3.11 version을 설치

###### MariaDB 실행 파일이 있는 경로 Path 추가

* 1) Windows의 경우 [Windows PowerShell(관리자모드)]를 선택해서 관리자 권한으로 파워셀 실행

* 2) `cmd` 명령으로 명령프롬프트로 변경

* 3) 아래의 명령으로 Path 추가

  * `C:\Windows\system32>SETX PATH "C:\Program Files\MariaDB 10.3\bin;%PATH%" /M`

  ```powershell
  # Step 1) Powershell 관리자 모드로 실행
  # Step 2) cmd 명령으로 명령프롬프트로 변경
  PS C:\Windows\system32> .\cmd
  Microsoft Windows [Version 10.0.18363.1256]
  (c) 2019 Microsoft Corporation. All rights reserved.
  
  # Step 3) Path 추가
  C:\Windows\system32>SETX PATH "C:\Program Files\MariaDB 10.3\bin;%PATH%" /M
  
  성공: 지정한 값을 저장했습니다.
  ```

  * 위와 같은 결과가 나오면 성공

### 3) 샘플 데이터베이스 설치

* 책에서 제공하는 샘플 데이터베이스를 다운로드 받아서 설치

##### MariaDB 콘솔로 접근하는 방법

* 1) 파일을 다운로드 받아 원하는 위치에 압축 풀기
* 2) Windows Powershell(관리자 모드)로 실행
* 3) `cmd` 명령어로 명령 프롬프트 실행
* 4) `cd 파일 위치` 명령어로 압축 푼 위치로 이동
* 5) `mysql -u root -p`로 MariaDB 접속
* 6) `source employees.sql ;` 명령으로 샘플 데이터베이스를 MariaDB로 자동으로 가져오기
* 7) 데이터베이스 확인해보기(`show datases ;`)

```powershell
# Step 1) 원하는 폴더에 압축풀기
# Step 2) Powershell 관리자 모드로 실행
# Step 3) cmd 명령으로 명령프롬프트로 변경
PS C:\Windows\system32> .\cmd
Microsoft Windows [Version 10.0.18363.1256]
(c) 2019 Microsoft Corporation. All rights reserved.

# Step 4) C:\Windows\system32>cd C:\Users\qkrtj\DataScience\database\employees
C:\Users\qkrtj\DataScience\database\employees>

# Step 5) mysql -u root -p 명령으로 접속 후 비밀번호 입력
C:\Users\qkrtj\DataScience\database\employees>mysql -u root -p
Enter password: ****
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 10.3.11-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>

# Step 6) 샘플 데이터베이스를 MariaDB로 자동으로 가져오기

MariaDB [(none)]> source employees.sql ;
Query OK, 0 rows affected, 1 warning (0.000 sec)

Query OK, 1 row affected (0.001 sec)

Database changed
+-----------------------------+
| INFO                        |
+-----------------------------+
| CREATING DATABASE STRUCTURE |
+-----------------------------+
1 row in set (0.000 sec)

Query OK, 0 rows affected, 6 warnings (0.020 sec)

# 'Query OK' 메시지가 실행되다 아래의 내용이 나오면 끝
MariaDB [employees]> 

# Step 7) 데이터베이스 확인
MariaDB [employees]> show databases;
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
```



#### 4) 설치 후 확인 사항

##### - 설치 폴더 확인

| 폴더    | 역할                                                         |
| ------- | ------------------------------------------------------------ |
| bin     | MariaDB 서버 프로그램, 클라이언트 프로그램 및 유틸리티 프로그램 파일 |
| data    | 데이터베이스 및 로그 파일                                    |
| include | 응용프로그램을 개발할 때 필요한 헤더 파일                    |
| lib     | MariaDB 관련 라이브러리 파일                                 |
| share   | 기타 지원 파일, 각 언어별 오류 메시지 파일 등                |

* data 폴더는 데이터베이스 파일들과 로그 파일들이 들어있는 **중요한 폴더**이다. 
* 데이터베이스는 데이터베이스 이름과 동일하게 각 폴더별로 그 내부에 파일들이 저장되어 있음.