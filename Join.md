# JOIN 관련  


`EQUI JOIN 등가 조인`  
두 테이블 간의 동일한 값을 가진 행을 결합한다.  

INNER JOIN과의 차이점은 EQUI JOIN은 오직 '=' 연산자를 이용하여 JOIN한다.  
따라서 INNER JOIN이 더 광범위한 개념이다.  


`OUTER JOIN`  
LEFT : 좌측 테이블 기준으로 JOIN 우측 테이블에 NULL 발생  
RIGHT : 우측 테이블 기준으로 JOIN 좌측 테이블에 NULL 발생
FULL : 양쪽 테이블 기준으로 JOIN 양쪽 테이블에 NULL 발생

ORACLE 스타일 OUTER JOIN  
WHERE절에 A.게시판ID = B.게시판ID(+)  
FROM A LEFT OUTER JOIN B  
WHERE A.게시판ID=B.게시판ID   

+가 있는 쪽이 NULL이 발생한다는 의미이다.  

`SELF JOIN`  
자기 자신이랑 JOIN하는 경우로 별칭을 사용해야 한다.  
한 테이블 내에서 두 컬럼이 연관관계가 있는 경우 사용한다.  



