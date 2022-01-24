# 에러
```
The bean 'jpaAuditingHandler' could not be registered. 
A bean with that name has already been defined and overriding is disabled.
```

# 해결방법
Application에 @EnableJpaAuditing이 선언되어 있을 텐데, 이걸 주석처리하거나, Configuration에 있는 @EnableJpaAuditing을 주석처리하자
