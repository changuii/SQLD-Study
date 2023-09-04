# 테이블 관련 구문


`테이블 명 변경`
```sql
RENAME table_name TO new_table_name;
ALTER TABLE table_name TO new_table_name;
```

`TRUNCATE`  
데이터만 삭제하고 테이블 구조, 속성, 인덱스, 제약조건 등은 그대로 유지  

DELETE 구문과의 차이점  
1. DDL 구문이다.
2. 속도 : DELETE는 행 별로 개별적으로 삭제하지만 TRUNCATE는 데이터 페이지 자체를 삭제하기 때문에 더 빠르다.
3. 로그 : DELETE는 로그를 생성하지만 TRUNCATE는 생성하지 않는다.
4. ROLLBACK : DELETE는 가능하지만 TRUNCATE는 불가능하다.
5. WHERE 절 : DELETE는 가능하지만 TRUNCATE는 불가능하다.
6. 외래키 제약조건이 있는 경우 TRUNCATE는 실패할 가능성이 있다.
7. 디스크 사용량 초기화, 저장공간을 재사용할 수 있도록 한다.
8. TRUNCATE는 AUTO COMMIT이다. (ORACLE)


`DCL`  
권한부여  
```sql
GRANT (INSERT, REMOVE, UPDATE 등..) ON table_name TO User_name
```

권한 삭제  
```sql
REVOKE (INSERT, REMOVE, UPDATE 등..) ON table_name TO User_name
```

권한 거부
```sql
DENY (INSERT, REMOVE, UPDATE 등..) ON table_name TO User_name
```
- 스키마 단위로 부여된 권한에 대해 테이블 단위의 권한을 거부시킨다.  (이는 권한 삭제로는 불가능하다.)  


