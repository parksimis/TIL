```bash

# 새 가상환경 만들기(이름 test)
conda create -n test


# 명령어에 대한 사용 도움말 출력
man chmod

# 현재 디렉터리 내의 파일과 디렉터리 목록 출력 : ls
## 일반적으로 다른 사람들에게 보여줄 수 있는 파일 보여줌
ls
$ ls
KNN_실습_1.ipynb

# 모든 파일(히든 파일까지 모두 보여줌) : ls -a
$ ls -a
.   .bash_logout  .cache    .gnupg  .mongorc.js  .ssh
..  .bashrc       .dbshell  .local  .profile     KNN_실습_1.ipynb

# 항목의 유형 반환 : ls -F
$ ls -F
AB테스트/  KNN_실습_1.ipynb

## 자세히 보여줌 
## 파일 권한 설정 내용 | 소유주 | 소유주 그룹 | 날짜 | 이름
## -	 |	rw-		|	r--			| r--			|
##일반 파일| 소유자권한 |  소유자그룹권한 | 일반사용자권한   |
## d(=디렉터리)	rwx	r-x	r-x 
### r : 읽기	 w : 쓰기	 - : 실행('-'은 불가)
### rwx : 읽, 쓰, 실 모두 가능
$ ls -l
total 60
drwxr-xr-x 2 lab06 multi  4096 Apr  9 11:16 AB테스트
-rw-r--r-- 1 lab06 multi 56490 Apr  9 10:46 KNN_실습_1.ipynb

# 디렉터리 이동 : cd
## 절대 경로명과 상대경로명 모두 사용 가능
## 절대 경로 : /home/tutor
$ cd /home
/home$

# 변경되었는지 확인
/home$ ls
lab05  lab06  lab07  lab08  techbrew  tutor  ubuntu

## 상대경로 : 현재 디렉터리에 대한 상대경로
:~$ cd ../
/home$

# 변경되었는지 확인
/home$ ls
lab05  lab06  lab07  lab08  techbrew  tutor  ubuntu


## 현재 작업 디렉터리 확인
~$ pwd
/home/lab06
/home$ ls
lab05  lab06  lab07  lab08  techbrew  tutor  ubuntu
## / : root 표현
## home : root와 시스템 계정을 제외한 모든 일반 사용자 계정 디렉터리를 포함하고 있음

# 서브 디렉터리 생성하기(사용자 계정 디렉터리 밑의 서브 디렉터리 생성) : mkdir
~$ mkdir ubuntu
~$ ls
AB테스트  KNN_실습_1.ipynb  ubuntu

## ubuntu 파일 안에 test 파일 만들기
~$ mkdir ./ubuntu/test
~$ cd ubuntu/
~/ubuntu$ ls
test

## 한번에 다 만들기는 불가능 -> 옵션 추가해야함
~$ mkdir ./test2/test1/test
mkdir: cannot create directory ‘./test2/test1/test’: No such file or directory

## -p 옵션
~$ mkdir -p  ./test2/test1/test
~$ ls
AB테스트  KNN_실습_1.ipynb  test2  ubuntu


# 디렉터리 제거(제거하고자 하는 디렉터리들이 비어있어야 함)
~$ rmdir test2
rmdir: failed to remove 'test2': Directory not empty

# test2 안에 폴더가 있으므로 삭제 불가
~$ cd test2/
~/test2$ ls
test1

## 지우려면 하나하나씩 지워야함
~/test2/test1$ rmdir test
~/test2/test1$ cd ../
~/test2$ rmdir test1
~/test2$ cd ../
~$ rmdir test2
~$ ls

# 파일 삭제 명령어 : rm
## 옵션
## 		-i : 삭제 전에 사용자에게 물어볼 것
##		-f : 확인 없이 삭제
##		-r : 디렉터리인 경우 적용해줘야함

~$ rm -r ubuntu/
~$ ls
AB테스트  KNN_실습_1.ipynb

# 파일 만들기 : touch
~$ touch abc
~$ ls
AB테스트  KNN_실습_1.ipynb  abc

# 파일 복사 : cp
# cp 원본파일 새로운파일명
# 같은 폴더 안에서 파일 복사
~$ cp abc abc_copy
~$ ls
AB테스트  KNN_실습_1.ipynb  abc  abc_copy

# cp 원본파일 디렉터리명
## 원본파일 복사해 디렉터리에다가 넣음
~$ mkdir cp_test
~$ cp abc cp_test
~$ cd cp_test
~/cp_test$ ls
abc

# cp -r 디렉터리1 디렉터리2
~$ cp -r cp_test cp_test1
~$ ls
AB테스트  KNN_실습_1.ipynb  abc  abc_copy  cp_test  cp_test1
# cp_test1 확인
~$ cd cp_test1
~/cp_test1$ ls
abc


# 파일 이름 바꾸기 / 이동하기 : mv
# 1) 파일 이름 바꾸기
## mv 원본파일 새파일명 
## 홈 디렉터리의 ab 파일을 test.csv로 변경
~$ ls
AB테스트  KNN_실습_1.ipynb  abc  abc_copy  cp_test  cp_test1
~$ mv abc test.csv
~$ ls
AB테스트  KNN_실습_1.ipynb  abc_copy  cp_test  cp_test1  test.csv

## 2) 파일 이동하기
## test.csv를 cp_test로 옮기기
~$ mv test.csv cp_test
(base) lab06@ip-172-31-11-131:~$ ls
AB테스트  KNN_실습_1.ipynb  abc_copy  cp_test  cp_test1
# cp_test 폴더 확인
~$ cd cp_test
(base) lab06@ip-172-31-11-131:~/cp_test$ ls
abc  test.csv

# 빈 파일 생성 : touch
~$ touch test
~$ ls
AB테스트  KNN_실습_1.ipynb  abc_copy  cp_test  cp_test1  test

# 파일 내용 확인하기 : cat
# cat 파일명
~$ vim test
# vim 편집기로 HI 작성
~$ cat test
HI

```

