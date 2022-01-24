```에러코드
The error occurred in sqlmaps/empty.xml. 
The error occurred while applying a parameter map. 
Check the mapNamespace.id-InlineParameterMap. 
Check the statement (query failed). 
Cause: com.mysql.jdbc.exceptions.MySQLSyntaxErrorException: Unknown column 'columnName' in 'field list'
```

## 해결방법
해당하는 컬럼명(columnName)이 없다는 것. 오타일 확률이 높으니 눈을 크게 뜨고 찾아보자.

간간히 대소문자도 걸리던거 같던데 기준을 모르겠다.
