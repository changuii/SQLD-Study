# GROUP BY , ORDER BY관련



`GROUP BY시 NULL 그룹도 생성된다.`  
GROUP BY 연산을 통해서 NULL값만 모여있는 그룹도 생성된다.  
COUNT(*)은 모든 행을 계산 즉, NULL도 포함하여 계산한다.  
COUNT(column_name)은 NULL을 제외하여 계산한다.  

`GROUP BY사용 시 ORDER BY`  
GROUP BY를 사용할 경우 GROUP BY 표현식이 아닌 값은 ORDER BY에 올 수 없다.  

`ORDER BY`  

ODER BY (CASE WHEN ID = 999 THEN 0 ELSE ID END)  
- ID가 999인 값은 ID가 0인 값으로 간주하고 정렬한다.  

ORDER BY 정수가 온다면 정수 번째 값으로 정렬한다는 의미이다.  
```sql
ORDER BY 1, 3
```
즉, 해당 구문은 테이블의 1, 3번째 값으로 정렬한다는 의미이다.  


`집합 연산에서의 ORDER BY`  
첫 번째 쿼리의 별칭을 사용하고 맨 마지막 쿼리에 ORDER BY를 붙이면 된다.  

`계층형 쿼리`  
START WITH절은 계층 구조의 시작을 정의한다.(최상위 계층)    
```sql
START WITH C2 IS NULL 
```  
최상위 계층의 튜플은 결과값에 반드시 포함된다.  
최상위 계층의 튜플은 C2가 NULL이다.  

CONNECT BY절은 최초행 이후 다음 절을 어떤 조건으로 가져올지 정의한다.  
```sql
CONNECT BY PRIOR C1 = C2
```  
PRIOR 자식 = 부모는 순방향 전개  
이전행의 C1과 현재행의 C2가 같은 행을 가져온다. (Prior : 이전의)  

ORDER SIBLINGS BY는 같은 계층끼리의 정렬에 사용된다.  
```sql  
ORDER SIBLINGS BY C3 DESC
```  
같은 계층은 C3를 기준으로 내림차순 정렬한다.  
PRIOR은 SELECT와 WHERE절에도 사용가능하다.  

계층형 질의의 실행 순서  
FROM - START-WITH - CONNECT-BY - ORDER-SIBLINGS-BY - WHERE - SELECT  

`GROUP BY 집계`  

GROUP BY ROLLUP  
- 소그룹 간의 합계를 계산하는 함수  
- GROUP BY로 묶은 각각의 소그룹 합계와 전체 합계를 모두 구한다.  
- GROUP BY에 명시한 모든 컬럼에 대한 소그룹 합계가 아닌 맨 처음에 명시한 컬럼에 대해서만 소그룹 합계를 계산해준다.  

GROUP BY CUBE  
- ROLLUP과 달리 GROUP BY에서 명시한 모든 컬럼에 대해 소그룹 합계를 계산해준다.  

GROUP BY SETS  
- 특정 항목에 대한 소계를 계산한다.  
- 각 소그룹 별 합계만 간단하게 계산한다.  
- 각각 GROUP BY 한 결과를 UNION ALL한 결과와 같다.  



 



