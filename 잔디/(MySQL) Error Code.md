## Error

## Fix
**[Error Code: 1175]**  

- You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column.
  To disable safe mode, toggle the option in Preferences -> SQL Editor and reconnect.
  
- 상황: 워크밴치에서 테이블의 행을 delete, update 할 때 오류  
  ```
  delete from Qudditch.customer_order where cid is null;
  ```
- 해결  
  1. 메세지에 나온대로 Preferences -> SQL Editor 에서 sate mode를 disable로 바꿔주는 방법
     ![image](https://github.com/wonlog/TIL/assets/149459170/ca8cbe9f-8700-4ecd-bce0-88d4da26e0f9)
  2. 일시적으로 제한 해제하는 방법
     ```
     -- 제한모드 해제
     set sql_safe_updates = 0;
     -- 제한모드 실행
     set sql_safe_updates = 1;
     ```

**[Error Code: 1217]**  

- Cannot delete or update a parent row: a foreign key constraint fails  
  
- 상황: 워크밴치에서 테이블의 여러 행을 delete할 때 오류  
  ```
  delete from Qudditch.customer_order where id > 0 and id < 110;
  ```
- 해결
  1. 해당 테이블 또는 행을 참조하고 있는 데이터를 먼저 삭제한 후에 실행한다.(가장 안전한 방법)
  2. 외래키 설정을 해제한 후 해당 테이블 또는 행을 삭제한다. (테이블 간의 관계 보장x)
