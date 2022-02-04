# MySql
# 목차
* [MySql 시작하기](#MySql-시작하기)
* [데이터베이스 관리 명령어](#데이터베이스-관리-명령어)
* [테이블 관리 명령어](#테이블-관리-명령어)
* [데이터 관리 명령어](#데이터-관리-명령어)
* [백업과 복구](#백업과-복구)

# MySql 시작하기
* 맥 기준으로 `MySql`을 설치하는 방법에는 2가지가 있는데 
* `homebrew`를 통해 설치하는 방법과
* MySql 홈페이지에서 `dmg` 파일을 다운받아 설치하는 방법이 있다. <br><br>

* 나는 여기서 `homebrew`를 통해 설치하는 방법을 택했다.
* `homebrew`는 맥에서 쓸 수 있는 터미널 버전 앱스토어 같은 느낌으로 개발에 필요한 각종 소프트웨어들을 명령어 한 줄로 간편하게 설치할 수 있다. 

## MySql 설치
* `homebrew`가 설치되어 있다는 전제하에 `homebrew` 터미널을 열어 명령어 입력을 통한 설치를 진행할 것인데, 먼저 홈 브루를 최신 버전으로 업데이트 시켜주고 시작하자.
```
brew update
```

* 업데이트가 완료되면 아래 명령어를 입력하면 MySql이 설치된다. 
```
brew install mysql
```

* 설치가 완료된 후 
```
brew list
```
* 를 입력하면 홈 브루를 통해 설치된 프로그램들이 나열되는데 그 중에 mysql이 있으면 설치가 잘 된 것임

## MySql 실행
* 아까 설치할 때 썼던 터미널창에서 명령어 입력을 통해 `MySql`을 실행할 수 있는데 역시 2가지 방법이 있다.
```
brew services start mysql 혹은
mysql.server start
```
* 둘 중 하나를 입력해서 `MySql`서버를 시작할 수 있다.
* 네트워크 연결 허용하겠냐는 창이 뜨면 허용하겠다고 하면 된다.

## MySql 초기 설정
* 서버가 시작되었다고 바로 쓸 수 있는 것은 아니고 간단한 설정을 해 주어야 한다.
``` 
mysql_secure_installation
```
* 위 명령어를 입력하면 `MySql` 초기 세팅을 시작할 수 있다.<br><br>

* "Would you like to setup VALIDATE PASSWORD component?
* Press y|Y for Yes, any other key for No"
* 비밀번호를 복잡하게 설정하겠느냐는 것인데 아직 초보 단계니까 `No`를 입력해서 '1234'와 같은 쉬운 비밀번호를 설정한다. (`Yes`를 입력하면 복잡한 비밀번호 설정)
* 새 비밀번호를 입력하라는 메시지가 나오면 입력하고 엔터 누르면 된다.<br><br>

* "Remove anonymous users? (Press y|Y for Yes. any other key for No)"
* 사용자 설정을 묻는 것인데 `Yes`를 선택했다. 
* Yes - 접속하는 경우 "mysql -uroot"처럼 -u 옵션 필요
* No - 접속하는 경우 "mysql"처럼 -u 옵션 불필요<br><br>

* "Disallow root login remotely? (Press y|Y for Yes, any other key for No)"
* 다른 IP에서 root 아이디로 원격 접속이 가능한지 묻는 것인데 `Yes`는 불가능, `No`는 가능
* 나는 `Yes`로 선택했다.<br><br>

* "Remove test database and access to it? (Press y|Y for Yes, any other key for No)"
* 테스트 데이터베이스를 삭제할건지 말건지 묻는 것인데 나는 `Yes`로 선택했다.<br><br>

* "Reload privilege tables now? (Press y|Y for Yes, any other key for No)"
* 변경된 권한을 테이블에 적용하는 설정에 대한 질문인데 이 질문은 무조건 `Yes`로 선택하는 것이 좋다고 한다.<br><br>

* 여기까지 하면 모든 초기 설정이 완료된다.

## MySql 접속
```
mysql -u root -p
```
* 위 명령어를 입력하면 root 아이디로 로그인할 수 있다.
* 비밀번호 입력창이 나오면 비밀번호를 입력 후(보이지 않지만 그냥 치면 됨) 엔터를 누르면 로그인이 완료된다.
* 정상적으로 로그인 되면 쉘이 `mysql>`로 바뀐다. 

```
mysql> status;
```
* 위 명령어를 입력하면 현재 설정을 확인할 수 있다. 

## MySql 종료
```
mysql> exit
```
* 위 명령어를 입력하면 `Bye`라는 메시지와 함께 `mysql`에서 빠져나올 수 있다.

```
brew services stop mysql 혹은
mysql.server stop
```
* 둘 중 하나를 입력하면 `MySql` 서버가 종료된다.
************************************

# 데이터베이스 관리 명령어
## 데이터베이스 목록 조회
```sql
show databases;
```
<br><br>

## 데이터베이스 생성
```sql
create database [DB명];
ex) create database jspdb;
```
<br><br>

## 데이터베이스 삭제
```sql
drop database [DB명];
ex) drop database jspdb;
```
<br><br>

## 데이터베이스 선택
```sql
use [DB명];
ec) use jspdb;
```
*********************************

# 테이블 관리 명령어
## 테이블 조회
```sql
show tables;
```
<br><br>

## 테이블 생성
```sql
create table [테이블명] (
    필드명1 데이터타입1 제약조건,
    필드명2 데이터타입2 제약조건,
    필드명3 데이터타입3 제약조건,
    필드명4 데이터타입4 제약조건
);

ex)
create table test (
    idx int,
    d_num double,
    name varchar(10)
);
```
* 꼭 줄을 바꾸지 않고 한 줄로 써도 괜찮지만 가독성을 위해 위처럼 줄을 바꿔서 쓴다.

### ☑️ 오라클과 MySql의 자료형 명칭 차이
* 문자형
    * 오라클 : varchar2
    * MySql : varchar

* 정수형
    * 오라클 : number
    * MySql : int
<br><br>

## 테이블 삭제
```sql
drop table [테이블명];
drop test;
```
<br><br>

## 테이블 구조확인
```sql
desc [테이블명];
desc test;
```
<br><br>

### 컨트롤 + 쉬프트 + C 여러번 누르기 : 잘못 입력했을 때 빠져나오기
*********************************

# 데이터 관리 명령어
* {} 안 내용은 생략 가능

## 데이터 삽입
```sql
insert into [테이블명] {(필드명1, 필드명2, ...)}
values(데이터1, 데이터2, ...);

ex)
insert into test
values(1, 'Kim');
```

* 필드명 생략시 데이터를 컬럼의 순서대로 모두 입력해야 함
<br><br>

## 데이터 검색
```sql
select [필드명, *] from [테이블명] {where 조건문};

ex) select * from test;
```
<br><br>

## 데이터 삭제
```sql
delete from [테이블명] {where 조건문};

ex) delete from test;
```

* 보통 테이블 통째로 지우지 않고 where 조건에 해당하는 것들을 지움

### ☑️ primary key, PK<br>
+-------+-------------+------+-----+---------+-------+<br>
| Field | Type        | Null | Key | Default | Extra |<br>
+-------+-------------+------+-----+---------+-------+<br>
| idx   | int         | NO   | PRI | NULL    |       |<br>
| name  | varchar(10) | YES  |     | NULL    |       |<br>
+-------+-------------+------+-----+---------+-------+<br><br>

* 그 테이블을 구분할 수 있는 고유한 값
* 어떤 컬럼을 PK로 지정하면 그 컬럼에는 고유한 값이 무조건 들어가야 한다.(null값 삽입 불가!)

### ☑️ 제약조건
* 어떤 컬럼에 특정 조건을 만족하는 값만 삽입될 수 있도록 하는 조건

#### UNIQUE 제약조건
* ERROR 1062 (23000): Duplicate entry '1' for key 'test4.PRIMARY'
* (idx 필드의 값이 PK를 사용하기 때문에 데이터 중복 불가)

#### Not Null 제약조건
* ERROR 1364 (HY000): Field 'idx' doesn't have a default value
* (idx 필드의 값이 PK 제약조건을 사용하기 때문에 Null 값을 사용할 수 없음)

### ☑️ auto_increment
```sql
create table test(
    idx int auto_inrement primary key,
    name varchar(10)
);
```

* 테이블을 만들 때 컬럼의 속성으로 넣어주면 한 줄씩 늘어날 때마다 그 컬럼의 번호가 자동으로 1씩 증가되어서 삽입된다. 
* 그래서 테이블에 데이터를 삽입할 때 PK로 지정한 컬럼 값으로 null을 넣어도 자동으로 증가된 숫자가 들어간다.
* 하지만 연속된 숫자를 가진 필드들 가운데 한 필드를 지워도 중간에 빈 값을 채우지 않고 마지막으로 증가되었던 숫자부터 계속 증가된다.(1~5번 중에 3번을 지우면 3번을 다시 채우고 6번으로 가는 것이 아니라 그냥 6번부터 시작한다)

### ☑️ datetime, timestamp, date
```sql
create table test(
    idx int auto_inrement primary key,
    datetime datetime,
    timestamp timestamp,
    date date
);
```

* 모두 날짜와 시간을 저장할 수 있는 속성인데 저장 범위가 약간 다르다.<br><br>
+-----+---------------------+---------------------+------------+<br>
| idx | datetime            | timestamp           | date       |<br>
+-----+---------------------+---------------------+------------+<br>
|   1 | 2022-02-03 11:17:00 | 2022-02-03 11:17:00 | 2022-02-03 |<br>
+-----+---------------------+---------------------+------------+<br><br>

## 오류 확인 명령어
```sql
show warnings;
show errors;
```

## 테이블명 명명 규칙
* `SQL` 예약어랑 겹칠수도 있기 때문에 보통 풀네임 단독으로는 잘 안 쓰고 `tbl_member`처럼 뒤에 단어를 좀 더 붙여주거나 약자로 쓴다.

## where 조건절 데이터 검색
```sql
select * from tbl_member where idx >= 3;
```

* idx 필드값이 3 이상인 데이터를 모두 조회<br><br>

```sql
select * from tbl_member where gender = 'W' and age < 20;
select * from tbl_member where gender = 'W' && age < 20;
```

* 성별이 'W'이고 나이가 20살 미만인 사람의 정보만 조회<br><br>

```sql
select * from tbl_member where age <= 20 or gender = 'M';
select * from tbl_member where age <= 20 || gender = 'M';
```

* 나이가 20살 이하이거나 성별이 'M'인 사람의 정보를 조회

## 데이터 수정
```sql
update [테이블명] set 필드명1 = 데이터1, 필드명2 = 데이터2, ... {where 조건절};

ex) update test set name = 'Kim' where idx = 3 and age >= 20;
```

* `update` 구문에는 `from`을 쓰지 않는다!
*********************************

# 백업과 복구
### 백업
```sql
mysqldump -u [아이디] -p [DB명] >파일명.sql    전체 백업
mysqldump -u [아이디] -p [DB명] [테이블명] >파일명.sql     해당 테이블만 백업

ex) mysqldump -u root -p jspdb >test.sql
```

* 비밀번호 입력 후 users desktop % 이 상태에서 커서가 깜박이고 있으면 다 된 것임
<br><br>

### 복구
```sql
mysql -u [아이디] -p [DB명] <파일명.sql

ex) mysql -u root -p jspdb <test.sql
```

* 비밀번호 입력하면 DB가 복구됨
