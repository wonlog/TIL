## Error

## Fix
**[Error Code: 1175]**  
```
delete from Qudditch.customer_order where cid is null;
```
- 오류  
  You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column. To disable safe mode, toggle the option in Preferences -> SQL Editor and reconnect.  
- 상황  
  워크밴치에서 테이블의 행을 delete, update 할 때 생성된 오류 
- 해결  
  1. 메세지에 나온대로 Preferences -> SQL Editor 에서 sate mode를 disable로 바꿔주는 방법
     ![image](https://github.com/wonlog/TIL/assets/149459170/ca8cbe9f-8700-4ecd-bce0-88d4da26e0f9)
  2. 일시적으로 제한 해제하는 방법
     ```
     set sql_safe_updates=0;
     ```
