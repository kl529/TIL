# 에러
```
org.springframework.jdbc.BadSqlGrammarException: PreparedStatementCallback; bad SQL grammar [INSERT INTO SPRING_SESSION (PRIMARY_ID, SESSION_ID, CREATION_TIME, LAST_ACCESS_TIME, MAX_INACTIVE_INTERVAL, EXPIRY_TIME, PRINCIPAL_NAME) VALUES (?, ?, ?, ?, ?, ?, ?)]; nested exception is org.h2.jdbc.JdbcSQLSyntaxErrorException: Table "SPRING_SESSION" not found; SQL statement:

INSERT INTO SPRING_SESSION (PRIMARY_ID, SESSION_ID, CREATION_TIME, LAST_ACCESS_TIME, MAX_INACTIVE_INTERVAL, EXPIRY_TIME, PRINCIPAL_NAME) VALUES (?, ?, ?, ?, ?, ?, ?) [42102-200]

    at org.h2.message.DbException.getJdbcSQLException(DbException.java:453)

    at org.h2.message.DbException.getJdbcSQLException(DbException.java:429)

    at org.h2.message.DbException.get(DbException.java:205)

    at org.h2.message.DbException.get(DbException.java:181)

    at org.h2.command.Parser.readTableOrView(Parser.java:7628)

    at org.h2.command.Parser.readTableOrView(Parser.java:7599)

    at org.h2.command.Parser.parseInsert(Parser.java:1747)

    at org.h2.command.Parser.parsePrepared(Parser.java:954)

    at org.h2.command.Parser.parse(Parser.java:843)

    at org.h2.command.Parser.parse(Parser.java:815)
```
위와 같이 Spring_session과 Spring_session_Attribute Table이 없다고 에러가 뜸

# 해결 방법
아래 코드를 DB Table에 추가해주자
```
CREATE TABLE SPRING_SESSION (
	PRIMARY_ID CHAR(36) NOT NULL,
	SESSION_ID CHAR(36) NOT NULL,
	CREATION_TIME BIGINT NOT NULL,
	LAST_ACCESS_TIME BIGINT NOT NULL,
	MAX_INACTIVE_INTERVAL INT NOT NULL,
	EXPIRY_TIME BIGINT NOT NULL,
	PRINCIPAL_NAME VARCHAR(100),
	CONSTRAINT SPRING_SESSION_PK PRIMARY KEY (PRIMARY_ID)
);

CREATE UNIQUE INDEX SPRING_SESSION_IX1 ON SPRING_SESSION (SESSION_ID);
CREATE INDEX SPRING_SESSION_IX2 ON SPRING_SESSION (EXPIRY_TIME);
CREATE INDEX SPRING_SESSION_IX3 ON SPRING_SESSION (PRINCIPAL_NAME);

CREATE TABLE SPRING_SESSION_ATTRIBUTES (
	SESSION_PRIMARY_ID CHAR(36) NOT NULL,
	ATTRIBUTE_NAME VARCHAR(200) NOT NULL,
	ATTRIBUTE_BYTES LONGVARBINARY NOT NULL,
	CONSTRAINT SPRING_SESSION_ATTRIBUTES_PK PRIMARY KEY (SESSION_PRIMARY_ID, ATTRIBUTE_NAME),
	CONSTRAINT SPRING_SESSION_ATTRIBUTES_FK FOREIGN KEY (SESSION_PRIMARY_ID) REFERENCES SPRING_SESSION(PRIMARY_ID) ON DELETE CASCADE
);

```

를 추가해주기

---
참고 : 
https://github.com/spring-projects/spring-session/blob/main/spring-session-jdbc/src/main/resources/org/springframework/session/jdbc/schema-h2.sql
