# 기타 몰랐던 부분들  

`BETWEEN 연산` 
A부터 B까지의 범위 (A와 B도 포함된다.) 
```sql
BETWEEN A AND B
```

`내장함수와 단일행-다중행 함수`  

내장함수는 이미 정의되어 있는 함수를 말한다.  
단일행 함수는 각각의 행에 대해서 독립적으로 작동하는 함수를 말한다.  
- ex) UPPER(), LOWER(), CAST() 등..
다중행 함수는 여러 행을 그룹으로 처리하고 단일 결과를 반환한다.  
- ex) COUNT(), AVG(), MAX() 등..

`ORACLE에서 DATE`  
ORACLE에서는 DATE의 정수 연산 +1은 +1일로 연산한다.  

`SEARCHED_CASE_EXPRESSION과 SIMPLE_CASE_EXPRESSION`  
SEARCHED_CASE_EXPRESSION
```sql
CASE
    WHEN column_name = value1 THEN result1
    WHEN column_name = value2 THEN result2
    ...
    ELSE resultN
END
```  

SIMPLE_CASE_EXPRESSION
```sql
CASE column_name
    WHEN value1 THEN result1
    WHEN value2 THEN result2
    ...
    ELSE resultN
END
```

`TOP() 함수`  

SQL Server에서 제공하는 함수  
쿼리 결과 상위 n개 행만 반환한다.  
WITH TIES를 같이 사용하면 동일 값에 대해 같이 반환한다.  

```sql
TOP(5) WITH TIES column_name
```  
WITH TIES가 없다면 항상 5개의 결과가 반환되지만  
WITH TIES가 있다면 동일한 값은 같이 출력되어 그 이상이 될 수 있다.  
ORDER BY가 없다면 기준을 알 수 없기때문에 무조건 ORDER BY와 함께 사용한다.  

`순수관계연산자`  

1. 선택(SELECTION, SELECT) : SQL의 WHERE에 해당 (관계대수 시그마) 
2. 추출(PROJECTION, PROJECT) : SQL의 SELECT에 해당 (관계대수 파이)
3. 결합(JOIN)
4. 나눗셈(DIVISION, DIVIDE)
5. 집합 연산(UNION, INTERSECTION, EXCEPT)

`CATERSIAN PRODUCT = CROSS JOIN`


`VIEW 뷰`  
특징  
- 기본 테이블로부터 유도된 테이블이기 때문에 기본 테이블과 같은 형태의 구조를 사용하며, 조작도 기본테이블과 거의 같다.  
- 가상 테이블이기 때문에 물리적으로 구현되어있지 않다.  
- 데이터의 논리적 독립성을 제공한다.
- 필요한 데이터만 뷰로 정의하여 관리가 용이하고 명령문이 간단해진다.  
- 뷰를 통해 접근하면 뷰에 나타나지 않는 데이터를 안전하게 보호하는 효율적인 기법이다.  
- 기본 테이블의 기본 키를 포함한 속성집합으로 구성해야만 삽입, 삭제 갱신이 가능하다.  
- 정의된 뷰는 다른 뷰 정의의 기초가 될 수 있다.  
- 뷰가 정의된 기본 테이블이나 뷰를 삭제하면 그 테이블이나 뷰를 기초로 정의한 다른 뷰도 자동으로 삭제된다.  

장점  
1. 논리적 데이터 독립성 제공
2. 동일 데이터에 대해 동시에 여러 사용자의 상이한 응용이나 요구 지원
3. 사용자의 데이터 관리를 간단하게 해준다.
4. 접근 제어를 통한 자동 보안 제공

단점  
1. 독립적인 인덱스를 가질 수 없다.
2. ALTER VIEW문을 사용할 수 없다. 즉, 수정이 불가능하다.
3. 뷰로 구성된 내용에 대한 삽입, 삭제 갱신에 제약이 따른다.  

생성  
```sql
CREATE VIEW view_name
AS SELECT column_name
FROM table_name
WHERE 조건
```  

삭제  
```sql
DROP VIEW view_name RESTRICT(OR CASCADE)
```  

`LEAD, LAG`  
LAG : 이전 행의 값을 리턴  
LEAD : 이후 행의 값을 리턴  


`PL/SQL`  
SQL을 확장한 절차적 언어이다.  
EXECUTE IMMEDIATE '구문'을 통해 DML, DDL, DCL 사용이 가능하다.  

`프로시저`  
절차형 SQL을 활용하여 특정 기능을 수행하는 일종의 트랜잭션 언어이다.  
호출을 통해 실행되어 미리 저장해놓은 SQL작업을 수행한다.  

```sql
CREATE PROCEDURE procedure_name
    BEGIN
    BODY
    END
```  

`트리거`  
DB시스템에서 삽입, 갱신, 삭제 등(DML) 이벤트가 발생할 때마다 자동으로 수행되는 절차형 SQL  

```sql
CREATE TRIGGER trigger_name (실행시기)(옵션) ON table_name
    FOR EACH Row
    BEGIN
    BODY
    END
```

