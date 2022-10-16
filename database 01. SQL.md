# 01. SQL

Category: DB
Date: October 4, 2022
Git: No

---

## 1. Database

### 1.1. Intro

- 데이터베이스의 등장
    - 파일을 이용한 데이터 관리
        - 장점
            - 운영체제에 관계 없이 어디에서나 쉽게 사용 가능
            - 이메일이나 메신저를 이용해 간편하게 전송 가능
        - 단점
            - 성능과 보안에서 한계가 명확
            - 대용량 데이터를 다루기에 적합하지 않음
            - 데이터를 구조적으로 정리하기 어려움
            - 확장이 불가능한 구조
    - 스프레드 시트를 이용한 데이터 관리
        - 컬럼을 통해 데이터의 유형을 지정하고 레코드를 통해 구체적인 데이터 값 포함
        - 스프레드 시트 자체를 데이터베이스라고 부를 수는 없지만 데이터베이스로 가는 길목 정도로 볼 수 있음
    - 데이터베이스
        - 스프레드 시트와 달리 프로그래밍 언어를 사용해 작동시킬 수 있음
        - 많은 형태가 있지만 실제 가장 많이 쓰이는 유형은 RDB(Relational Database)라고 부르는 관계형 데이터베이스
        - RDB는 스프레드 시트에 작성하는 것처럼 각각의 데이터를 테이블에 기입
        - 스프레드 시트 파일 모음을 관계형 RDB로 생각할 수 있음
- 데이터베이스란?
    - 체계화된 데이터의 모임
    - 여러 사람이 공유하고 사용할 목적으로 통합 관리되는 정보의 집합
    - 검색, 구조화 같은 작업을 보다 쉽게 하기 위해 조직화된 데이터를 수집하는 저장 시스템
        - 내용을 고도로 구조화함으로써 검색과 갱신 효율화
        - 자료 파일을 조직적으로 통합하여 자료 항목의 중복을 없애고 구조화하여 기억시켜 놓은 자료의 집합체
    - 데이터베이스 조작 프로그램 = DBMS (Database Management System)
        - Oracle, MySQL, SQLite 등
        - DBMS에서 데이터베이스를 조작하기 위해 사용하는 언어 → SQL
    - 웹 개발에서 대부분의 데이터베이스는 관계형 데이터베이스 관리 시스템을 사용하여 SQL로 데이터와 프로그래밍 구성

### 1.2. RDB

- RDB란?
    - Relational Database (관계형 데이터베이스)
    - 데이터를 테이블, 행, 열 등으로 나누어 구조화하는 방식
    - 자료를 여러 테이블로 나누어 관리하고, 이 테이블간 관계를 설정해 여러 데이터를 쉽게 조작할 수 있다는 장점
    - SQL 사용하여 데이터를 조회하고 조작
- RDB 기본 구조
    - 종류
        - 스키마
        - 테이블
            - 필드
            - 레코드
            - 기본 키
    - 스키마 (Schema)
        - 테이블의 구조
        - 데이터베이스에서 자료의 구조, 표현 방법, 관계 등 전반적인 명세를 기술한 것
    - 테이블 (Table)
        - 필드와 레코드를 사용해 조직된 데이터 요소들의 집합
            - 필드 : 속성, 컬럼
            - 레코드 : 튜플, 행
        - 관계(Relation)라고도 부름
    - 필드 (Field)
        - 속성 혹은 컬럼
        - 각 필드에는 고유한 데이터 형식(타입)이 지정됨
    - 레코드 (Record)
        - 튜플 혹은 행
        - 테이블의 데이터는 레코드에 저장됨
    - 기본 키 (PK, Primary Key)
        - 각 레코드의 고유한 값
            - 각각의 데이터를 구분할 수 있는 고윳값
        - 기술적으로 다른 항목과 절대로 중복될 수 없는 단일 값(unique)
        - 데이터베이스 관리 및 테이블
- RDB의 장점
    - 데이터를 직관적으로 표현 가능
    - 관련한 데이터에 쉽게 접근 가능
    - 대량의 데이터도 효율적으로 관리 가능
- RDMBS
    - Relational Database Management System (관계형 데이터베이스 관리 시스템)
    - 관계형 데이터베이스를 만들고 업데이트하고 관리하는 데 사용하는 프로그램
    - ex. SQLite, MySQL, PostgreSQL, Microsoft SQL Server, Oracle Database 등
- SQLite
    - 응용 프로그램에 파일 형식으로 넣어 사용하는 비교적 가벼운 데이터베이스
    - 안드로이드, iOS, macOS에 기본적으로 탑재되어 있으며 임베디드 소프트웨어에서도 많이 활용됨
    - 오픈 소스 프로젝트이기 때문에 자유롭게 사용 가능
    - 단점
        - 대규모 동시 처리 작업에는 적합하지 않음
        - 다른 RDBMS에서 지원하는 SQL 기능을 지원하지 않을 수 있음
    - 장점 (학습하는 이유)
        - 어떤 환경에서나 실행 가능한 호환성
        - 데이터 타입이 비교적 적고 강하지 않기 때문에 유연한 학습 환경 제공
        - Django Framework의 기본 데이터베이스

## 2. SQL

- SQL이란?
    - Structured Query Language
    - RDBMS의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어
    - RDBMS에서의 데이터베이스 스키마 생성 및 수정, 테이블에서의 자료 검색 및 관리 가능
    - 데이터베이스 객체에 대한 처리를 관리하거나 접근 권한을 설정하여 허가된 사용자만 RDBMS를 관리할 수 있도록 할 수 있음
    - 많은 데이터베이스 관련 프로그램들이 SQL을 표준으로 채택
    - SQL은 데이터베이스와 상호작용하는 방법 → SQL을 배우면서 데이터베이스의 동작원리를 익힐 수 있음

### 2.1. SQL Commands

- SQL Commands 종류
    - 명령어는 특성에 따라 세 가지 그룹으로 분류
        1. DDL (Data Definition Language)
        2. DML (Data Manipulation Language)
        3. DCL (Data Control Language)
        
        | 분류 | 개념 | SQL 키워드 |
        | --- | --- | --- |
        | DDL - 데이터 정의 언어 | 관계형 데이터베이스 구조(테이블, 스키마)를 정의(생성, 수정 및 삭제)하기 위한 명령어 | CREATE, DROP, ALTER |
        | DML - 데이터 조작 언어 | 데이터를 조작(추가, 조회, 변경, 삭제)하기 위한 명령어 | INSERT, SELECT, UPDATE, DELETE |
        | DCL - 데이터 제어 언어 | 데이터의 보안, 수행제어, 사용자 권한 부여 등을 정의하기 위한 명령어 | GRANT, REVOKE, COMMIT, ROLLBACK |
    - SQLite는 파일로 관리되는 DB이기 때문에 SQL을 이용한 접근 제한이 아닌 운영 체제의 파일 접근 권한으로만 제어 가능 → SQLite에는 권한 설정을 담당하는 `GRANT`(권한 부여)와 `REVOKE`(권한 회수)는 지원하지 않아 DCL 부분은 학습 생략

### 2.2. SQL Syntax

- SQL Syntax
    - 모든 SQL문(statement)은 `SELECT`, `INSERT`, `UPDATE` 등과 같은 키워드로 시작하고, 하나의 statement는 세미콜론으로 끝남
        - 세미콜론은 각 SQL문을 구분하는 표준 방법
    - SQL 키워드는 대소문자를 구분하지 않음
        - `SELECT`와 `select`는 SQL문에서 동일한 의미이나 대문자로 작성하는 것을 권장
- [참고] Statement & Clause
    - Statement (문)
        - 독립적으로 실행할 수 있는 완전한 코드 조각
        - statement는 clause로 구성됨
    - Clause (절)
        - statement의 하위 단위
    - 예시
        
        ```sql
        SELECT column_name FROM table_name;
        ```
        
        - SELECT statement라 부름
        - 이 statement는 2개의 clause로 구성됨
            - `SELECT column_name`
            - `FROM table_name`

## 3. DDL

- 사전 준비
    - VScode SQLite 확장 프로그램 설치 (공용 노션 문서 ‘SQLite3 설치’ 참고)
    - 데이터베이스 mydb.sqlite3 파일 생성
    - DDL.sql 파일 생성
    - vscode 실행 후 DDL.sql 화면에서 마우스 우측 버튼 클릭 → Use Database 선택 → mydb.sqlite3 선택
- DDL
    - Data Definition Language
    - SQL 데이터 정의 언어를 사용하여 테이블 데이터베이스 개체를 만드는 방법 학습
    - DDL은 테이블 구조를 관리 : `CREATE`, `ALTER`, `DROP`

### 3.1. CREATE TABLE

- `CREATE TABLE`
    - create a new table in the database
    - 데이터베이스에 새 테이블을 만듦
        
        ```sql
        CREATE TABLE table_name (
        	column_1 data_type constraints,
        	column_2 data_type constraints,
        	column_3 data_type constraints
        );
        ```
        
- 실습
    - contacts 테이블 생성
        
        ```sql
        -- DDL.sql
        
        CREATE TABLE contacts (
        	name TEXT NOT NULL,
        	age INTEGER NOT NULL,
        	email TEXT NOT NULL UNIQUE
        );
        ```
        
    - Query 실행
        - 실행하고자 하는 명령문에 커서를 두고 마우스 우측 버튼 → Run Selected Query
        - 명령문을 모두 선택할 필요 없이 실행하고자 하는 명령문 안에 커서가 올라가 있으면 가능
    - 쿼리 실행 후 테이블 및 스키마 확인
        - id 컬럼은 우리가 직접 기본 키 역할의 컬럼을 정의하지 않으면 자동으로 rowid라는 컬럼으로 만들어짐

### 3.2. SQLite Date Types

- Data Types
    - 종류
        - NULL
        - INTEGER
        - REAL
        - TEXT
        - BLOB
    - NULL
        - NULL value
        - 정보가 없거나 알 수 없음을 의미 (missing information or unknown)
    - INTEGER
        - 정수
        - 크기에 따라 0, 1, 2, 3, 4, 6 또는 8바이트와 같은 가변 크기를 가짐
    - REAL
        - 실수
        - 8바이트 부동 소수점을 사용하는 10진수 값이 있는 실수
    - TEXT
        - 문자 데이터
    - BLOB (Binary Large Object)
        - 입력된 그대로 저장된 데이터 덩어리 (대용 타입 없음)
        - 바이너리 등 멀티미디어 타입
        - ex. 이미지 데이터
- [참고] Boolean type
    - SQLite에는 별도의 Boolean 타입이 없음
    - 대신 Boolean 값은 정수 0과 1로 저장됨
- [참고] Date & Time Datatype
    - SQLite에는 날짜 및 시간을 저장하기 위한 타입이 없음
    - 대신 SQLite의 built-in Date And Functions으로 TEXT, REAL 또는 INTEGER 값으로 저장할 수 있음
- [참고] Binary Data
    - 데이터의 저장과 처리를 목적으로 0과 1의 이진 형식으로 인코딩 된 파일
    - 기본적으로 컴퓨터의 모든 데이터는 binary data
        - 이를 필요에 따라 텍스트 타입으로 변형해서 사용
- SQLite Datatypes 결정 규칙
    - 값이 작은 따옴표나 큰 따옴표로 둘러 쌓이면 → TEXT
    - 값에 둘러싸는 따옴표가 없고, 소수점 또는 지수가 없으면 → INTEGER
    - 값에 따옴표가 없고, 소수점 또는 지수가 있으면 → REAL
    - 값이 따옴표 없이 NULL이면 → NULL
- SQLite Datatypes 특징
    - SQLite는 다른 모든 SQL 데이터베이스 엔진(MySQL, PostgreSQL 등)의 정적이고 엄격한 타입(static, rigid typing)이 아닌 동적 타입 시스템(dynamic type system) 사용
        - 컬럼에 선언된 데이터 타입에 의해서가 아니라 컬럼에 저장된 값에 따라 데이터 타입이 결정됨
    - 테이블 생성 시 컬럼에 대해 특정 데이터 타입을 선언하지 않아도 됨
        - 예를 들어 동일한 컬럼에 정수 1을 넣을 경우 INTEGER로 타입이 지정되고, 문자 ‘1’을 넣을 경우는 TEXT 타입으로 지정됨
    - 이러한 SQLite의 동적 타입 시스템을 사용하면 기존의 엄격하게 타입이 지정된 데이터베이스에서는 불가능한 작업을 유연하게 수행할 수 있음
        - 정적 타입 시스템이 지정된 데이터베이스에서 작동하는 SQL문이 SQLite에서 동일한 방식으로 작동
        - 다만 이는 다른 데이터베이스와의 호환성 문제가 있기 때문에 테이블 생성 시 데이터 타입을 지정하는 것을 권장
    - 데이터 타입을 지정하게 되면 SQLite는 입력된 데이터의 타입을 지정된 데이터 타입으로 변환
        - TEXT 타입 컬럼에 정수 1을 저장할 경우 문자 타입의 ‘1’로 저장
        - 허용 가능한 타입 변환
            
            
            | Column Datatype | Types Allowed In That Column |
            | --- | --- |
            | INTEGER | INTEGER, REAL, TEXT, BLOB |
            | REAL | REAL, TEXT, BLOB |
            | TEXT | TEXT, BLOB |
            | BLOB | INTEGER, REAL, TEXT, BLOB |
- [참고] static, rigid typing 데이터베이스
    - statically, rigidly typed databases라고도 부름
    - 저장되는 값의 데이터 타입은 컬럼에 선언된 데이터 타입에 의해 결정
    - 동작 예시
        
        ```sql
        CREATE TABLE my_table (
        	a INTEGER NOT NULL,
        	b TEXT NOT NULL
        );
        ```
        
        - 만약 a 컬럼에 ‘123’, b 컬럼에 456 데이터를 삽입하려는 경우 삽입을 수행하기 전에 문자열 ‘123’을 정수 123으로 변환하고, 정수 456을 문자열 ‘456’으로 변환
- Type Affinity
    - 타입 선호도 : 특정 컬럼에 저장된 데이터에 권장되는 타입
    - 데이터 타입 작성 시 SQLite의 5가지 데이터 타입이 아닌 다른 데이터 타입을 선언한다면, 내부적으로 각 타입의 지정된 선호도에 따라 5가지 선호도로 인식됨
        1. INTEGER
        2. TEXT
        3. BLOB
        4. REAL
        5. NUMERIC
        
        | Example Typenames From The CREATE TABLES Statement | Resulting Affinity |
        | --- | --- |
        | INT, INTEGER, TINYINT, SMALLINT, MEDIUMINT, BIGINT, UNSIGNED, INT2, INT8 | INTEGER |
        | CHARACTER(20), VARCHAR(255), VARYING CHARACTER(255), NCHAR(55), NATIVE CHARACTER(70), NVARCHAR(100), TEXT, CLOB | TEXT |
        | BLOB (no datatype specified) | BLOB |
        | REAL, DOUBLE, DOUBLE PRECISION, FLOAT | REAL |
        | NUMERIC, DECIMAL(10, 5), BOOLEAN, DATE, DATETIME | NUMERIC |
    - 타입 선호도 존재 이유
        - 다른 데이터베이스 엔진 간의 호환성 최대화
        - 정적이고 엄격한 타입을 사용하는 데이터베이스의 SQL문을 SQLite에서도 작동하도록 하기 위함

### 3.3. Constraints

### 3.4. ALTER TABLE

### 3.5. DROP TABLE

## 4. DML