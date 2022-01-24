# 문제상황
JPA와 Mysql이 연동이 안되고 자꾸 컬럼명이 오류가 남

# 해결 방법
연동할때는 Spring에서 Entity의 column이 bookReport라면 Mysql에서는 book_report 이렇게 스네이크 형식으로 바꾸어야 한다.

ex) book_report
