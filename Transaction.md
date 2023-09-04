# 트랜잭션 관련


`트랜잭션의 격리성이 낮은 경우 발생하는 문제점`
1. Dirty Read : 한 트랜잭션이 아직 커밋되지 않은 다른 트랜잭션의 변경 내용을 읽는 경우
2. Non-Repeatable Read : 한 트랜잭션 내에서 같은 쿼리를 두 번 실행했을 때, 결과가 다르게 나오는 현상
3. Phantom Read : 한 트랜잭션 내에서 같은 쿼리를 두 번 실행했을 때, 첫 번째 쿼리에서 없던 행이 두 번째 쿼리에서 나타나는 현상
4. Lost Update : 두 개의 트랜잭션이 거의 동시에 같은 데이터를 수행할 때 마지막으로 실행된 업데이트만 반영되어 앞전 업데이트가 사라져버릴 수 있는 문제


`ROLLBACK, AUTO COMMIT`  
ROLLBACK은 아직 COMMIT되지 않은 상위의 모든 트랜잭션을 ROLLBACK(초기화) 시킨다.  
오라클에서는 DDL을 실행 후 AUTO COMMIT을 진행한다.  
SQL Server에서는 DDL 수행 후 AUTO COMMIT을 하지 않는다.  

```sql
SAVE TRANSACTION SP1;  
~~~
~~~
ROLLBACK TRANSACTION SP1;
```
SP1의 시점으로 롤백시킨다.  





