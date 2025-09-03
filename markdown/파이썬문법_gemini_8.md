
-----

### 🐍 파트 6: 데이터베이스

#### **1. SQLite**

📌 **설명**
SQLite는 2000년에 리처드 힙이 C언어로 개발한 파일 기반의 DBMS입니다.   
저메모리와 빠른 처리 속도가 특징이며,별도의 DB 서버 없이도 사용 가능한 내장형 SQL 엔진입니다. 
안드로이드나 아이폰과 같은 스마트폰에 내장된 DB로도 사용됩니다

💡 **주요 특징**

  *   **공식 사이트:** [http://sqlite.org](http://sqlite.org) 
  *   **특징:** 파일 기반 DBMS, 저메모리, 빠른 처리 속도, 오픈소스
  *   **지원하지 않는 기능:** RIGHT/FULL OUTER JOIN, 완전한 ALTER TABLE/TRIGGER 지원, VIEW 쓰기, GRANT/REVOKE 등

🧑‍💻 **SQLite 사용 예제**

  * **테이블 생성**
      `create_table()` 함수를 사용하여 `my_books.db` 데이터베이스에 `books` 테이블을 생성하는 예제입니다

<!-- end list -->

```python
import sqlite3

def create_table():
    conn = sqlite3.connect('my_books.db')
    cursor = conn.cursor()
    cursor.execute('''create table if not exists books(
        title text, published_date text, publisher text, pages integer, recommend integer
    )''')
    conn.commit()
    conn.close()

create_table()
```

  * **데이터 입력**
      `insert_books()` 함수를 사용하여 `books` 테이블에 데이터를 삽입하는 예제입니다

<!-- end list -->

```python
import sqlite3

def insert_books():
    conn = sqlite3.connect("my_books.db")
    cursor = conn.cursor()
    cursor.execute("insert into books values('Java','2019-05-20','길벗',500,10)")
    sql = 'insert into books values(?,?,?,?,?)'
    cursor.execute(sql, ('Python','201001','한빛',584,20))
    items = [
        ('빅데이터','2014-07-02','삼성',296,11),
        ('안드로이드','2010-02-02','영진',526,20),
        ('Spring','2013-12-02','삼성',248,15)
    ]
    cursor.executemany(sql, items)
    conn.commit()
    conn.close()

insert_books()
```

  * **데이터 출력**

      *   **전체 데이터 출력:** `fetchall()`을 사용해 모든 데이터를 가져옵니다
      *   **일부 데이터 출력:** `fetchmany()`를 사용해 지정된 개수만큼 데이터를 가져옵니다
      *   **하나의 데이터 출력:** `fetchone()`을 사용해 하나의 데이터를 가져옵니다
      *   **조건 및 정렬:** `WHERE`와 `ORDER BY`를 사용해 조건을 지정하고 정렬하여 데이터를 검색합니다

  * **데이터 수정 및 삭제**

      *   **수정:** `UPDATE` 문을 사용해 데이터를 수정합니다
      * 
      *   **삭제:** `DELETE` 문을 사용해 데이터를 삭제합니다

-----

#### **2. Oracle**

📌 **설명**
  파이썬에서 Oracle 데이터베이스에 연결하기 위해서는 `cx_Oracle` 라이브러리를 설치해야 합니다

🧑‍💻 **Oracle 사용 예제**

  * **테이블 생성**
      `PRODUCT` 테이블을 생성하는 예제입니다

<!-- end list -->

```sql
CREATE TABLE PRODUCT(
    product_id number,
    product_name varchar2(50),
    price number default 0,
    description clob,
    picture_url varchar2(500),
    primary key(product_id)
);
```

  * **데이터 삽입**
      `insert_product()` 함수를 사용해 한 개의 레코드를 삽입하거나 `insert_many()` 함수를 사용해 여러 레코드를 삽입할 수 있습니다[cite: 1272, 1273, 1289].

  * **데이터 조회**
    `all_product()` 함수를 사용해 `product` 테이블의 모든 레코드를 조회합니다.   특히, `CLOB` 필드는 `read()` 메서드를 통해 읽습니다[cite: 1282, 1283].   `select_one()` 함수를 사용해 레코드의 개수와 같이 한 개의 레코드를 조회할 수 있습니다[cite: 1302].

  * **데이터 수정 및 삭제**

      *   **수정:** `update()` 함수는 `UPDATE` 문을 사용하여 특정 `product_id`에 해당하는 가격을 수정합니다
      *   **삭제:** `delete_product()` 함수는 `DELETE` 문을 사용하여 레코드를 삭제합니다

-----

#### **3. MySQL**

📌 **설명**
  파이썬에서 MySQL 데이터베이스에 연결하기 위해서는 `PyMySQL` 라이브러리를 설치해야 합니다

🧑‍💻 **MySQL 사용 예제**

  * **테이블 생성**
      `pydb` 데이터베이스를 생성하고, `book` 테이블을 생성하는 예제입니다

<!-- end list -->

```sql
create database pydb;
use pydb;
CREATE TABLE book (
    id INT NOT NULL AUTO_INCREMENT,
    title VARCHAR(200),
    pub VARCHAR(45),
    pages INT,
    author VARCHAR(100),
    PRIMARY KEY (id)
);
```

  * **DB 연결**
      `pymysql.connect()` 함수를 사용하여 데이터베이스에 연결합니다

<!-- end list -->

```python
import pymysql

conn = pymysql.connect(
    host='localhost',
    user='pgm',
    password='1234',
    db='pydb',
    charset='utf8'
)
```

  * **데이터 삽입**
      `insert_book()` 함수를 사용해 하나의 레코드를 삽입하거나, `insert_book_list()` 함수를 사용해
  * 여러 레코드를 삽입할 수 있습니다

  * **데이터 조회**
      `select_all()` 함수를 사용해 `book` 테이블의 모든 레코드를 조회합니다

  * **데이터 수정 및 삭제**

      *   **수정:** `update_book()` 함수를 사용해 `UPDATE` 문으로 데이터를 수정합니다
      * 
      *   **삭제:** `delete_book()` 함수를 사용해 `DELETE` 문으로 데이터를 삭제합니다

-----