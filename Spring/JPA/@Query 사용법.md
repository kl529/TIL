# 배경

Spring boot를 통해서 개발을 하게 된다면, DB에 데이터를 삽입, 읽기 등 여러 가지 작동을 하기 위해서는 방식이 필요하다. 쿼리를 작동시키는 방식에는 여러 가지 방식이 존재한다.


특히 Spring JPA Data Doc은 레퍼런스도 있고, SQL이 자동생성되게 할 수 있습니다.

https://docs.spring.io/spring-data/jpa/docs/2.3.3.RELEASE/reference/html/#jpa.repositories

 

* ~~Repository에 @Query와 함께 메소드를 작성하면, Service에서 바로 사용할 수 있다.
* 직접적으로 DB에 쿼리문으로 접근할 수 있다.

 

# 사용방법
## 1. 쿼리를 직접쓰는 경우는 다음과 같은 조건이 있어야 한다

```
@Query("SELECT u FROM User u WHERE u.status = 1")
Collection<User> findAllActiveUsers(); 
```
⭐⭐⭐From table 별칭을 Select문 안에 넣어야 한다. 안그러면 오류를 만들어낸다⭐⭐⭐

 

## 2. DB에서처럼 쿼리를 작성하는 방식

``` 
@Query(
value = "SELECT * FROM USERS u WHERE u.status = 1",
nativeQuery = true)
Collection<User> findAllActiveUsersNative(); 
```
 nativeQuery = true 속성을 줘야만 가능하다.

 

## 3. Parameter를 전달해주기

1️⃣ ?를 통한 경우 -> parameter의 위치에 따른 숫자를 넣어주면 된다.

?1 -> parameter 첫번째 자리에 있는걸 넣겠다는 뜻.

```
public interface UserRepository extends JpaRepository<User, Long> {
@Query("select u from User u where u.emailAddress = ?1")
User findByEmailAddress(String emailAddress);
}
 ```

2️⃣ :name -> 파라미터의 이름으로 검색하는 경우

```
public interface UserRepository extends JpaRepository<User, Long> {
@Query("select u from User u where u.firstname = :firstname or u.lastname = :lastname")
User findByLastnameOrFirstname(@Param("lastname") String lastname,
@Param("firstname") String firstname);
@Query("select u from User u where u.firstname = :firstname or u.lastname = :lastname")
User findByLastnameOrFirstname(String lastname, String firstname); //이렇게도 사용 가능하다.
}
 ```

물론 이경우 말고도 여러가지 케이스가 존재한다. SPEL을 이용할 수도 있기도하고 Sorting하는 방식이라던가 진짜 여러가지 방식으로 활용 가능하다.

자세한건

https://docs.spring.io/spring-data/jpa/docs/2.3.3.RELEASE/reference/html/#jpa.repositories

----
참고 : https://sundries-in-myidea.tistory.com/91
