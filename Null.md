# 널 관련



`NULL 사칙연산, 조건연산`  
수직 연산 : 수직연산에 대해서는 NULL인 값을 제외시키고 연산을 진행한다.  
수평 연산 : 수평연산에 대해 NULL과 연산을 진행할 경우 항상 결과는 NULL이다.  

NULL은 오직 IS NULL, IS NOT NULL 연산을 통해서만 조건연산을 진행한다.  
(x != NULL, x <> NULL, NOT NULL은 불가능하다.)  

ORACLE에서는 '', 공백을 입력했을 때 IS NULL로 조회하여야 한다.  
(빈 문자열을 NULL로 인식한다.)  

`단일행 NULL관련 함수`  
ORACLE NVL(식1, 식2), SQL Server ISNULL(식1, 식2)
- 식1의 결과값이 NULL이면 식2를 출력
- 식1과 식2의 결과 데이터타입이 같아야 한다.  

NULLIF(식1, 식2)
- 식1과 식2가 같으면 NULL 다르면 식1을 출력

COALESCE(식1, 식2, 식3, ... 식N)  
- NULL이 아닌 최초의 값을 리턴한다.  
- 모두 NULL이면 NULL을 반환한다.  

`NULL값의 비교`  
ORACLE에서는 NULL을 가장 큰 값으로 간주  
SQL Server에서는 NULL을 가장 작은 값으로 간주한다.  
