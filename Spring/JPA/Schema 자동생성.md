# 배경

JPA는 데이터베이스 스키마를 자동으로 생성하는 기능을 지원합니다. 클래스의 매핑 정보를 분석하여 어떤 테이블이 어떤 칼럼을 사용하는지 알 수 있고 데이터베이스 방언(dialect)에 따라 해당 데이터베이스에 맞는 스키마를 생성할 수 있습니다.

데이터베이스 방언이란?

데이터 타입이나 함수명, 페이징 처리 등 각 데이터베이스가 제공하는 고유 기능을 JPA에서는 방언(dialect)이라고 부릅니다. 개발자가 특정 데이터베이스에 종속되는 기능을 많이 사용하면 나중에 데이터베이스를 교체하기 어려운데, 이러한 문제를 해결하기위해 아래와 같이 다양한 방언클래스를 제공합니다.

- H2: org.hibernate.dialect.H2Dialect
- oracle 10g: org.hibernate.dialect.Oracle10gDialect
- MySQL: org.hibernate.dialect.MySQL5InnoDBDialect
이외에도 다양한 방언 클래스를확인하실 수 있습니다.

스키마 자동 생성 기능 사용을 위해선 아래와 같은 설정이 필요합니다.

- application.properties
```
spring.jpa.hibernate.ddl-auto=create
```
- application.yml
```
spring:
  jpa:
    hibernate:
      ddl-auto: create
    # show-sql: true # DDL 출력
```
위 속성을 추가하면 어플리케이션 실행 시점에 데이터베이스 테이블을 자동으로 생성합니다.

spring.jpa.hibernate.ddl-auto 속성
```
- create: 기존 테이블을 삭제하고 새로 생성 (DROP - CREATE)
- create-drop: create와 동일하나 어플리케이션 종료시 테이블 삭제 (DROP - CREATE - DROP)
- update: 데이터베이스 테이블 - 엔터티 매핑정보를 비교해서 변경사항만 수정
- validate: 데이터베이스 테이블 - 엔터티 매핑정보를 비교해서 차이가있으면 어플리케이션을 실행하지 않음
- none: 자동 생성 기능을 사용하지 않음
```

Member라는 엔터티 클래스를 작성한 뒤 어플리케이션을 실행하면,

```
import lombok.AccessLevel;
import lombok.NoArgsConstructor;

import javax.persistence.*;
import java.time.LocalDateTime;

@Entity
@NoArgsConstructor(access = AccessLevel.PROTECTED)
public class Member {
    @Id
    private String id;
    private String name;
    private Integer age;

    @Enumerated(EnumType.STRING)
    private Role role;

    @Temporal(TemporalType.TIMESTAMP)
    private LocalDateTime createdDate;

    @Temporal(TemporalType.TIMESTAMP)
    private LocalDateTime updatedDate;

    public enum Role {
        ADMIN, USER
    }
}
```
```
2019-09-30 15:45:19.784 DEBUG 13843 --- [  restartedMain] org.hibernate.SQL                        : create table member (id varchar(255) not null, age integer, created_date timestamp, name varchar(255), role varchar(255), updated_date timestamp, primary key (id))
Hibernate: create table member (id varchar(255) not null, age integer, created_date timestamp, name varchar(255), role varchar(255), updated_date timestamp, primary key (id))
```
이렇게 테이블을 생성해주는 로그를 확인할 수 있습니다.

---
참고 : https://jaime-note.tistory.com/9
