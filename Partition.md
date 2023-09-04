# Partition관련  


`PARTITION BY`  
```sql
집계함수(column_name) OVER (PARTITION BY column_name1 .... N 
                            ORDER BY절
                            WINDOWING절)
```
WINDOWING절에서 함수의 대상이되는 행 기준의 범위를 강력하게 지정할 수 있다.  

`RANK()`  

PARTITION내에서 순위를 구할 수도 있고 전체 데이터에 대한 순위를 구할 수 있다.  
동일한 값은 동일한 순위를 가진다.  

RANK() OVER (윈도함수)  
ORDER BY가 필수이다.  

DENSE_RANK()  
동일한 순의를 하나의 건수로 처리한다.  

RANK(): 1등, 2등, 3등  
DENSE_RANK(): 1등, 1등, 3등  

ROW_NUMBER()  
동일한 값도 고유한 순위를 부여한다.(기준은 ORDER BY이다. )  

`윈도 함수 범위 지정`   
```sql
BETWEEN 1 PRECEDING AND UNBOUNDED FOLLOWING
``` 
CURRENT ROW : 현재 행  
n PRECEDING : n행 앞  
n FOLLOWING : n행 뒤  
UNBOUNDED PRECEDING : 이전행 모두  
UNBOUNDED FOLLOWING : 이후행 모두  

