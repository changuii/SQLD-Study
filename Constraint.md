# 제약조건 생성

ADD : 추가  
MODIFY : 수정
DROP : 삭제

`테이블 생성이 끝난 후 제약조건`  
ORACLE  
```sql
ALTER TABLE table_name
ADD CONSTRAINT constraint_name
constraint_type(column_name)
```  
SQL Server
```sql
ALTER TABLE table_name
ALTER COLUMN column_name
자료형 constraint_type
```

`테이블 생성과 함께`  
ORACLE
```sql
CONSTRAINT constraint_name constraint_type(column_name)
```  
SQL Server
ORACLE과 동일하게 사용 가능
```sql
constraint_type(column_name)
```

`외래키 제약조건`  
```sql
FOREIGN KEY (외래키 컬럼)
REFERENCE 연관 테이블 명(가져올 외래키)
ON DELETE 제약조건
```

1. CASCADE : Master에서 해당 행이 삭제되면 child도 같이 삭제된다. (참조 무결성 제공)
2. SET NULL : Master에서 해당 행이 삭제되면 child는 NULL값 입력된다.
3. DEAFAULT : Master에서 해당 행이 삭제되면 child는 DEFAULT값이 입력된다.
4. RESTRICT, NO ACTION : Master에서 해당 행이 child에서 참조하고 있다면 Master에 있는 행은 값을 수정 및 삭제하지 못한다. (참조 무결성과 일관성 제공)

`UNIQUE 제약조건`
해당 컬럼의 값을 해당 테이블에서 유일하게 제약조건을 설정한다.  
NULL값을 입력될 수 있다.  
PRIMARY KEY : UNIQUE + NOT NULL  

`CHECK 제약조건`  
컬럼값의 입력범위를 지정한다.  

테이블 생성 후 설정  
```sql
ALTER TABLE table_name
CONSTRAINT constraint_name
CHECK (column_name = 'YES' OR column_name = 'NO')
```

테이블 생성과 함께  
```sql
column_name CONSTRAINT constraint_name CHECK('YES', 'NO')
```

`AUTOMATIC, DEPENDENT 제약조건`  
AUTOMATIC : Master table에 PK가 없다면 MASTER PK 생성 후 child 생성
DEPENDENT : Master table에 PK가 존재할 때만 child 생성  
  



