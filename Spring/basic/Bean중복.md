```에러코드
org.springframework.context.annotation.ConflictingBeanDefinitionException: 
Annotation-specified bean name 'testMapper' for bean class [com.xxx.v2.mapper.testMapper] conflicts 
with existing, non-compatible bean definition of same name and class [com.xxx.v1.mapper.testMapper]
	at org.springframework.context.annotation.ClassPathBeanDefinitionScanner.checkCandidate
```

## 해결방법
에러 코드를 잘 읽어보면 testMapper라는 Bean이 중복되었다는 뜻이다.

그럴때는 파일들을 잘 살펴보면서 중복된 testMapper를 삭제해주면 된다.


v1, v2로 나눠서 하는 경우라서 어쩔 수 없이 삭제가 불가능한 경우에는 아래 블로그 참조

https://blog.naver.com/PostView.naver?blogId=mering_k&logNo=222423540639&categoryNo=123&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=search 
