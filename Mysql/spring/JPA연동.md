# 에러
```
java.sql.SQLException: Access denied for user 'root'@'localhost' (using password: YES)
```

# 해결방법

## 1. 입력문제
- 에러 이유 : application.properties에 적힌 mysql user의 아이디와 비밀번호가 잘못 입력되있다. (필자는 여기에 해당했음 - 띄워쓰기가 되어있어서 에러뜸;;)

- 해결 방법 : 아이디 비밀번호를 알맞게 수정하면 끝!



## 2. 권한이 없을 때
- 해결방법 : 
```
GRANT ALL PRIVILEGES ON *.*TO 'user_id'@'%' IDENTIFIED BY 'user_password' with GRANT OPTION;

FLUSH PRIVILEGES;
```
위의 것에 user_id에 아이디를, 'user_password'에는 비밀번호를 입력한다. (따옴표도 같이 입력해줘야 함)

## 3. 그래도 안된다! (이유 불명)
```
create user {username}@{ip} identified by '{password}';
```
위의 것처럼 다시 유저를 입력하고 권한을 준다.


예시

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpdOlE%2FbtrruoBcdGe%2FsIHitNKmktvOnkmBX2aC70%2Fimg.png)
